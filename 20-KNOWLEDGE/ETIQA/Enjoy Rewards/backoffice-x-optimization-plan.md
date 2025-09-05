# Enjoy Rewards Backoffice-X Optimization Plan

tags: [backoffice-x, enjoy-rewards, performance, frontend]
status: draft
owners: [platform-web]
last-updated: 2025-09-05

## Scope
- Target app: `smile-aio/backoffice-x` (Next.js 14, App Router, React 18, Tailwind, Flowbite, React Query).
- Target areas: Enjoy Rewards pages (product catalog, products, vouchers), Excel flows, table UX, data fetching.
- Goals: reduce JS payload, avoid main-thread blocks, improve perceived latency, add observability.

## Success Metrics
- Bundle: −20–40% JS on first load for Enjoy Rewards pages (via dynamic imports and split heavy libs).
- UX: Excel upload parse time no longer blocks UI (>90% work off main thread).
- Data: smooth pagination/filtering (<200ms UI updates with keep-previous-data and debouncing).
- Quality: tracked Web Vitals (LCP/INP/CLS) and error rate for Enjoy Rewards routes.

## Phase 1 — Quick Wins (Week 1)
- [ ] Dynamic-import heavy modals in Enjoy Rewards pages (defers `exceljs` until needed).
  - Targets:
    - `src/app/(site)/enjoy-rewards/product-catalog-list/page.tsx`
    - `src/app/(site)/enjoy-rewards/products-list/page.tsx`
    - `src/app/(site)/enjoy-rewards/voucher-list/page.tsx`
  - Replace static imports with:
    - `const EnjoyRewardsAddProductModal = dynamic(() => import('./modal/AddProductListModal'), { ssr: false });`
    - `const EnjoyRewardsAddVoucherInstanceModal = dynamic(() => import('./modal/AddDataModal'), { ssr: false });`
    - `const EnjoyRewardsViewProductModal = dynamic(() => import('./modal/ViewDataModal'), { ssr: false });`

- [ ] Trim `next/font` usage to minimal weights/styles.
  - File: `src/app/layout.tsx`
  - From: `Lato({ weight: ['400','100','300','700','900'], style: ['normal','italic'] })`
  - To: `Lato({ weight: ['400','700'], style: ['normal'] })` (adjust if design needs others).

- [ ] React Query tuning on lists.
  - Voucher/Product Catalog pages: `staleTime: 30s`, `gcTime: 5m`, `keepPreviousData: true`, `retry: 1–2`.
  - Disable `refetchOnWindowFocus` on admin-heavy views.

- [ ] Debounce filter inputs (300–500ms) before firing requests.
  - Files: Enjoy Rewards list pages using `react-hook-form` + React Query.

## Phase 2 — Performance Deep Dives (Week 2–3)
- [ ] Web Worker for Excel parsing (avoid main-thread blocking).
  - Create `src/workers/excelParser.worker.ts` with `exceljs` parsing logic.
  - Update `AddProductListModal.tsx` and `AddDataModal.tsx` to use worker (postMessage/MessageChannel).
  - Show progress UI during parse; handle cancel.

- [ ] Bundle analysis & code-splitting hygiene.
  - Add `@next/bundle-analyzer` and script: `ANALYZE=true next build`.
  - Identify largest Enjoy Rewards chunks (expect `exceljs`, `sweetalert2`, `flowbite-react`).
  - Ensure heavy libs used elsewhere (Survey, ApexCharts, React JSON View, Quill) are dynamically imported and not statically included in Enjoy Rewards bundles.

- [ ] Optimize images on Enjoy Rewards (optional, if images present).
  - Adopt `next/image` with `remotePatterns` for voucher/product media.
  - Ensure `basePath: '/backoffice'` works with static assets.

- [ ] Virtualize large tables if needed.
  - Add row virtualization to `src/component/table/data-table.tsx` when row counts are high to keep paint times low.

## Phase 3 — Observability & CI (Week 3+)
- [ ] Web Vitals reporting.
  - Implement `reportWebVitals` and send to backend/logging for Enjoy Rewards routes.

- [ ] Error tracking (optional).
  - Integrate lightweight client error telemetry (Sentry or custom endpoint) limited to admin paths.

- [ ] CI improvements.
  - Add `yarn lint` and `next build` checks to PRs.
  - Track bundle sizes with `size-limit`/`bundlesize` and fail on regressions beyond threshold.

## Next.js Build/Runtime Tweaks
- [ ] `next.config.js`
  - Add `output: 'standalone'`.
  - Add `compiler.removeConsole: { exclude: ['error','warn'] }` for production.
  - Keep PWA (`next-pwa`) but verify caching excludes admin data and respects `basePath`.

## Risks & Assumptions
- PWA caching must not serve stale admin data; validate runtime caching rules.
- Ensure dynamic imports don’t break SSR expectations; many pages are client components already.
- Web Worker build config: Next 14 supports workers; verify bundling with `exceljs` works (fallback to smaller parser if needed).

## Rollback Plan
- Dynamic import issues: revert files to static imports (single commit revert).
- Worker issues: feature flag worker path; fallback to existing in-thread parsing.
- Bundle analyzer: dev-only; no runtime impact.

## Useful Commands
- Dev backoffice-x: `cd smile-aio/backoffice-x && yarn dev -p 11400`
- Build analyze: `cd smile-aio/backoffice-x && ANALYZE=true yarn build`
- Lint: `cd smile-aio/backoffice-x && yarn lint`

## Open Questions
- Do we need italics or extra `Lato` weights in UI?
- Do Enjoy Rewards pages render product images today (to justify `next/image` work)?
- Which flows are most critical: catalog upload vs voucher lists vs products list?

