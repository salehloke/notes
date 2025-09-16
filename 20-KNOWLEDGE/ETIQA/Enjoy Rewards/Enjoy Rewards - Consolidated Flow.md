# Enjoy Rewards — Consolidated Flow

## System Overview
- Components: Backoffice-X (admin), Portal (customer), Backend (NestJS), WOGI provider, MongoDB/Prisma.
- Key domains: Product Catalog, Voucher Instances, Voucher Config, Tracking/Reports.
- Related notes: 
  - Voucher journey: ./Voucher Journey Sequence Diagrams - Enjoy Rewards System.md
  - DFD overview: ./Untitled.md
  - One Million Campaign: ../../../01-INBOX/To Process/Discussion {ENJOY} One million Campaign.md

## Core Flows
- Product Catalog (code-based)
  - Admin creates/updates products: POST /rewards/code-based/product-catalog
  - Required: priceMin, priceMax (with Currency), brand.objectClass = 'Brand'
  - UI source: Backoffice-X > Enjoy Rewards > Voucher Create > Basic Product Info
- Voucher Instance Upload
  - Admin uploads XLSX: POST /rewards/code-based/upload-voucher-instance-list
  - Each row requires redemptionCode or activationRedeemURL (HTTPS)
  - Validations: productAmount > 0, expiryDate in future, gatewayId/productName present
  - UI source: VoucherInstanceManager + VoucherUploadModal
- Claim & Redemption (Portal)
  - User claims voucher (limits/eligibility), system assigns from pool
  - Redemption via code (merchant) or activation URL (provider)
  - Tracking: status transitions, error handling, retry paths (see sequence diagrams)

## Data Models (essentials)
- ProductData
  - name, descriptiveName, validity, maxClaimedQuantityPerUser, isProductBeingShown
  - priceMin/priceMax: { amount, cents, formatted, currency{id, symbol, isoCode, ...} }
  - brand: { objectClass: 'Brand', name, category, redemptionMethod[], ... }
- VoucherInstance
  - gatewayId, productName, productAmount, expiryDate
  - redemptionCode OR activationRedeemURL, transactionId?, cardId?
  - status history, metadata, usage

## Backoffice UX (Excel)
- Columns: Redemption Code (A), Amount (B optional), Expiry Date (C)
- Mapping: A → redemptionCode; amount defaults to 0.01 if blank; dates normalized
- Large files: parse in Web Worker, chunk to ~200/req with progress, CSV of failures

## Key APIs
- Product Catalog: POST /api/backoffice/portal-enjoy-rewards/rewards/code-based/product-catalog
- Voucher Upload: POST /api/backoffice/portal-enjoy-rewards/rewards/code-based/upload-voucher-instance-list
- Images: POST /rewards/voucher/upload-background-image, /rewards/voucher/upload-logo-image
- Reports/Tracker: GET /rewards/report/download, GET /tracker/list

## Operations & Limits
- Preflight duplicates (optional): check existing redemption codes to reduce fails
- Idempotency: unique (gatewayId, redemptionCode); avoid re-inserts
- Error taxonomy: invalid amount/date, missing config (voucherCode), duplicate code, provider/API down

## Notes & Campaigns
- One Million Campaign: separate pools and flows; do not mix with normal rewards stock
- Tracker events and PO meeting follow-ups captured in Active Tickets and Inbox notes

## Next Up (curation)
- Embed latest sequence diagram snapshots into this note
- Add preflight duplicate-check doc and background-job flow for >10k rows
- Link UI screenshots for Create Product and Upload Instances screens
