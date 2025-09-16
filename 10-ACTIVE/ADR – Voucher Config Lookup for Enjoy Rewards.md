---
created: 2025-09-05
updated: 2025-09-05
status: draft
area: Work
tags: [#adr, #module/enjoy-rewards, #area/backoffice-x, #backend, #frontend]
---

# ADR – Voucher Config Lookup for Enjoy Rewards

Decision to add a lightweight “lookup” endpoint and migrate dropdown/typeahead UI to use it, replacing heavy list calls that return large payloads per request.

## Summary
- Add a new backend endpoint that returns only the minimal fields needed for a voucher-code picker, with fast, index‑friendly search and tight pagination.
- Update the voucher configuration dropdown in the backoffice‑x UI to call this endpoint with debounce and query gating.

## What is a “lookup” vs current implementation?
- Lookup (new)
  - Purpose‑built for dropdown/typeahead.
  - Minimal projection: `gatewayId, voucherCode, productName, availableQuantity, isProductBeingShown, campaignCode, updatedAt`.
  - Explicitly excludes heavy fields and relations such as `voucherInstanceList`.
  - Index‑friendly prefix search (e.g., `^term`, case‑insensitive) on `voucherCode`/`productName`.
  - Small page size (default 20), fast pagination, `.lean()` result (no hydration), no joins, no nested collections, no third‑party calls.
  - Optional `fields` param (whitelisted) to allow future extensions without payload bloat.

- Current list (existing)
  - Generic, multi‑purpose list returning large/derived/nested data per item.
  - Often used with broad “contains” search → poor index usage, high CPU, large response sizes.
  - Dropdown UI was calling this per keystroke/open → heavy server load, sluggish UX.

Bottom line: “Lookup” is a lean, cached, index‑optimized read for selection UIs; the existing list remains for grids/tables and full detail screens.

## Impacted APIs
- New (added)
  - `GET /api/backoffice/portal-enjoy-rewards/rewards/voucher-config/lookup`
    - Query: `term` (min 2 chars), `page`, `limit` (≤ 50), `fields` (whitelist)
    - Returns: minimal set only (see above); no `voucherInstanceList`.
    - Example:
      ```json
      {
        "docs": [
          { "gatewayId": 11668, "voucherCode": "GONG_CHA_10", "productName": "Gong cha RM10", "availableQuantity": 120, "isProductBeingShown": true, "campaignCode": "DM-SEP", "updatedAt": "2025-09-05T10:00:00.000Z" }
        ],
        "page": 1,
        "limit": 20,
        "totalDocs": 1,
        "totalPages": 1,
        "hasNextPage": false,
        "hasPrevPage": false
      }
      ```

- Existing (touched/related)
  - `GET /api/backoffice/portal-enjoy-rewards/rewards/voucher-copy-config-list`
    - Dropdowns will stop using this; reserved for grids/tables. Future: support `fields` to trim payload.
  - `GET /api/backoffice/portal-enjoy-rewards/rewards/voucher-config/:gatewayId`
    - Consider `fields` projection for UI reads.
  - `POST /rewards/voucher-config` · `PUT /rewards/voucher-config/:gatewayId` · `DELETE /rewards/voucher-config/:gatewayId`
    - Must invalidate lookup caches.

## Schema / Indexes
- `rewards.voucher.config` (Mongoose: `EnjoyVoucherConfig`)
  - Indexes added: `{ voucherCode: 1 }`, `{ productName: 1 }`, `{ updatedAt: -1 }`

## Impacted Frontend Pages (backoffice‑x)
- `src/app/(site)/enjoy-rewards/voucher-create/components/steps/VoucherConfigurationStep.tsx`
  - Switch dropdown search to `lookup` endpoint via React Query.
  - Gate by UI state: only fetch when dropdown open and `term.length >= 2`; debounce 300–500ms; `staleTime: 5m`, `gcTime: 15m`.

- `src/app/(site)/enjoy-rewards/voucher-create/page.tsx`
  - Indirect impact via stepper component above.

- Lists using full data (keep existing list, optional payload trim later)
  - `src/app/(site)/enjoy-rewards/voucher-list/page.tsx`
  - `src/app/(site)/enjoy-rewards/products-list/page.tsx`

## Migration Plan
1) Backend
   - [x] Add lookup endpoint with projection + `.lean()`; add indexes.
   - [ ] (Optional) Add Redis cache (TTL 5–10m) for hot terms and empty term; invalidate on create/update/delete.
   - [ ] (Optional) Add `fields` to existing list/detail endpoints.

2) Frontend
   - [ ] Refactor dropdown to use lookup with React Query gating and debounce.
   - [ ] Remove ad‑hoc stateful fetching; rely on query cache, cancel in‑flight via React Query.
   - [ ] Add min input length (2) and prefetch on focus.

## Acceptance Criteria
- Lookup endpoint P50 < 100ms, P95 < 300ms in SIT for typical terms.
- Response size < 25 KB for 20 options.
- Dropdown typing does not spike backend CPU; requests are gated and debounced.
- Cache hit rate > 60% for repeated terms (if cache enabled).

## Monitoring
- Log per‑endpoint latency and payload size; track slow queries (>200ms) and add index hints if needed.
- Frontend: log typeahead request counts and error rates.

## Open Questions
- Should lookup also support starts-with on `campaignCode`?
- Do we need “contains” search, or can we enforce starts-with for better index usage?
- Which pages (if any) besides voucher creation step use a voucher-code dropdown today?
