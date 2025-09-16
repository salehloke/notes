---
created: 2025-09-05
updated: 2025-09-05
status: active
area: Work
project: [[Project – Enjoy Rewards Backoffice-X Optimization]]
tags: [#module/enjoy-rewards, #area/backoffice-x, #type/project]
---

# Project – Enjoy Rewards Backoffice‑X Optimization

Context: Optimize the Enjoy Rewards admin flows in `backoffice-x` (Next.js 14, App Router) to reduce JS payload, keep the UI responsive during Excel operations, improve perceived latency on lists, and add observability.

Links
- Repo: `smile-aio/backoffice-x`
- Knowledge: [[Enjoy Rewards - Consolidated Flow]] · [[Portal-Enjoy-Rewards-API]]

## Goals / Success Criteria
- JS bundle −20–40% on first load for Enjoy Rewards pages (code‑split heavy modals/libs).
- Excel uploads parse off the main thread (>90%), with progress UI.
- Lists feel snappy: pagination/filter changes don’t jank; requests debounced.
- Web Vitals (LCP/INP/CLS) and client errors logged for Enjoy Rewards routes.

## Impacted APIs (Backend – portal‑enjoy‑rewards)
- Current heavy endpoint (dropdown source):
  - GET `/api/backoffice/portal-enjoy-rewards/rewards/voucher-copy-config-list`
  - Issues: large payload per item (nested/derived data), unbounded projection, costly "contains" search, potential N+1 calls.
  - Actions:
    - [ ] Add lightweight lookup endpoint: GET `/api/backoffice/portal-enjoy-rewards/rewards/voucher-config/lookup?term=&limit=&cursor=`
      - Returns: `[{ gatewayId, voucherCode, productName, availableQuantity, isProductBeingShown, campaignCode, updatedAt }]`
      - No joins, no third‑party calls; DB projection + `.lean()`.
      - Enforce `minTermLength=2`, `limit<=20`.
    - [ ] Add `fields` query param support on list endpoints to explicitly control projection (default to minimal set above).
    - [ ] Pagination: prefer cursor‑based; otherwise index‑based paging with low `limit`.
    - [ ] Indexes: `{ voucherCode: 1 }` (case‑insensitive handling or normalized field), `{ productName: 1 }` if used for fallback search, `{ updatedAt: -1 }` for sorting.
    - [ ] If substring search remains, consider text index and constrain to top N results (acknowledge limits vs prefix search).
    - [ ] Caching: Redis read‑through for hot terms and empty term, TTL 5–10m; invalidate on create/update/delete.
    - [ ] Transport: confirm gzip/br enabled at gateway.
    - [ ] Observability: log P50/P95 latency, payload size, cache hit/miss; add slow‑query threshold (e.g., >200ms) logging.

- Single config read:
  - GET `/api/backoffice/portal-enjoy-rewards/rewards/voucher-config/:gatewayId`
  - Actions: [ ] Support `fields` projection and `.lean()` for UI reads; ensure it doesn’t pull large child collections by default.

- Writes that must invalidate cache:
  - POST `/rewards/voucher-config` · PUT `/rewards/voucher-config/:gatewayId` · DELETE `/rewards/voucher-config/:gatewayId`
  - Actions: [ ] Invalidate lookup keys (by term + empty), [ ] validate constraints (unique `voucherCode` per gatewayId), [ ] return minimal DTO.

- Acceptance criteria
  - [ ] Lookup endpoint P50 < 100ms, P95 < 300ms in SIT.
  - [ ] Response size < 25 KB for 20 options.
  - [ ] No upstream/provider calls during lookup.
  - [ ] Cache hit rate > 60% for frequent terms.

- Frontend contract
  - [ ] Voucher config dropdown uses lookup endpoint with `enabled` gating (open + `term.length>=2`), debounce 300–500ms, `staleTime: 5m`.
  - [ ] Fallback to initial prefetch on focus when term empty (first page only).

## Phase 1 — Quick Wins (Week 1)
- [ ] Dynamic‑import heavy modals to defer `exceljs` and other libs until opened.
  - Targets:
    - `src/app/(site)/enjoy-rewards/product-catalog-list/page.tsx`
    - `src/app/(site)/enjoy-rewards/products-list/page.tsx`
    - `src/app/(site)/enjoy-rewards/voucher-list/page.tsx`
  - Use: `dynamic(() => import('./modal/…'), { ssr: false })`
- [ ] Trim `next/font` Lato to minimal weights (likely `['400','700']`) and drop italics unless needed.
- [ ] React Query page tuning: `staleTime: 30s`, `gcTime: 5m`, `keepPreviousData: true`, `retry: 1–2`, `refetchOnWindowFocus: false` where appropriate.
- [ ] Debounce filter inputs (300–500ms) before issuing requests.
  
  Backend/API quick win for dropdowns
  - [x] Implement lookup endpoint + projection + index on `voucherCode` (excludes `voucherInstanceList`).
  - [ ] Wire frontend dropdown to lookup; gate queries by open state and min term.

## Phase 2 — Deep Dives (Week 2–3)
- [ ] Move Excel parsing to a Web Worker for `AddProductListModal` and `AddDataModal`.
  - Add `src/workers/excelParser.worker.ts` and wire postMessage/MessageChannel.
  - Show parse progress + allow cancel.
- [ ] Bundle analysis and hygiene.
  - Add `@next/bundle-analyzer`; run `ANALYZE=true next build`.
  - Verify heavy libs (Survey, ApexCharts, React JSON View, Quill) are dynamically imported; confirm they don’t leak into Enjoy Rewards chunks.
- [ ] Optimize images (if used): adopt `next/image` with `remotePatterns` and confirm `basePath` works.
- [ ] Consider table row virtualization for very large datasets.
  
  Backend/API deep dive
  - [ ] Add Redis caching layer with invalidation hooks on config writes.
  - [ ] Add `fields` param to existing list/detail endpoints and enforce default minimal projection.
  - [ ] Add monitoring for slow queries and payload sizes.

## Phase 3 — Observability & CI (Week 3+)
- [ ] Web Vitals: implement `reportWebVitals` and log per‑route metrics.
- [ ] Client error tracking (Sentry or custom endpoint limited to admin paths).
- [ ] CI: add `yarn lint` + `next build` checks; track bundle sizes (`size-limit`/`bundlesize`).

## Next.js Build/Runtime Tweaks
- [ ] `next.config.js`: `output: 'standalone'`.
- [ ] `compiler.removeConsole: { exclude: ['error','warn'] }` for production.
- [ ] Review `next-pwa` runtime caching to avoid stale admin data; ensure `basePath: '/backoffice'` respected.

## Risks / Assumptions
- PWA caching must not serve stale admin data.
- Dynamic imports must not break SSR for any server components (most targets are client‑side already).
- Worker bundling with `exceljs` may need config or a smaller parser fallback.

## Rollback Plan
- Revert dynamic imports to static if route breaks (single commit revert).
- Feature‑flag worker path; fallback to current in‑thread parsing.
- Analyzer is dev‑only; no runtime impact.

## Commands
- Dev: `cd smile-aio/backoffice-x && yarn dev -p 11400`
- Analyze: `cd smile-aio/backoffice-x && ANALYZE=true yarn build`
- Lint: `cd smile-aio/backoffice-x && yarn lint`

## Backlog / Notes
- [ ] Prefetch next page data on pagination hover for perceived speed.
- [ ] Audit `react-icons` imports; consider `modularizeImport` or local icon set if needed.
- [ ] Confirm which Lato weights are actually used in UI.
