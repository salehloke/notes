---
title: DLSM Enhancement Plan — Step Linkage (Option C)
aliases:
  - DLSM Option C Plan
tags: [dlsm, enhancement, linkage, regional]
---

# DLSM Enhancement Plan — Step Linkage (Option C)

Decision: Adopt Option C (Minimal Linkage) for ETIQA_REGIONAL only. No changes for ETIQA_PLUS.

Purpose
- Address pentest finding that APIs are designed to be called step-by-step but lack linkage between steps.
- Provide a quick, low-risk linkage by requiring a `uuid` from Step 1 at Step 3 for Regional.

Scope
- App: ETIQA_REGIONAL only.
- Steps:
  - Step 1: AI read (returns `uuid`).
  - Step 2: Manual validation (no gating under Option C).
  - Step 3: Submission to ESB (requires `uuid` presence for Regional).
- ESB: No changes to ESB payload/contracts.

API Changes (Backward Compatible)
- Endpoint: `POST /api/v5/mobile-coverage/upload/dlsm`
  - Add optional field: `uuid` (string)
  - Behavior:
    - If `x-app-id = ETIQA_REGIONAL`:
      - Require `uuid` to be present in request (format check: non-empty string; UUID v4 format preferred).
      - If missing → 400 `DLSM.UUID_REQUIRED` with message “uuid is required for Regional submissions.”
      - Do not block on Step 2 validation; proceed as-is (Option C minimal linkage).
    - If `x-app-id = ETIQA_PLUS`:
      - `uuid` is optional and ignored for gating; logged for correlation only.

Validation & Logging
- Validate `uuid` format (UUID v4 regex) to prevent trivial bypass/mistakes.
- Log correlation context when `uuid` is provided (userId, policyNo, appId, step: "upload/dlsm").
- (Optional) Warn-only flag: `regional_dlsm_uuid_required_enforce=false` to allow soft rollout.

Error Semantics
- 400 `DLSM.UUID_REQUIRED` (Regional only): uuid is required for Regional submissions.
- Maintain existing success payloads (no ESB change).

Backwards Compatibility
- ETIQA_PLUS: No behavior change.
- Regional: Enable warn-only mode initially if needed; then flip to enforce.

Rollout Steps
1. Add optional `uuid` param to Step 3 DTO and controller.
2. Implement Regional-only gating (presence check) with feature flag support.
3. Add logs/metrics for presence rate and failures.
4. Update Postman collections and developer docs.

---

## Engineering Checklist (Option C)

- DTO/controller
  - Add optional `uuid: string` to Step 3 request (multipart text field).
  - In `mobile-coverage.controller.ts` (uploadDlsm), read `uuid` from body when present.
  - When `x-app-id = ETIQA_REGIONAL`, enforce presence of `uuid`; return 400 `DLSM.UUID_REQUIRED` if missing.

- Validation & logging
  - Validate non-empty string (optionally UUID v4 format).
  - Log correlation: { uuid, userId, policy_no, appId: ETIQA_REGIONAL }.
  - Metrics: count missing/invalid uuid attempts.

- Feature flag (optional for soft rollout)
  - `regional_dlsm_uuid_required_enforce` (default: false → warn-only; true → enforce 400).

- Documentation
  - Update per-app guides: Regional requires `uuid` at Step 3; Plus optional.
  - Update overview and detailed guides; point to this plan.
  - Update glossary for TTL (future Option A) — done.

- Postman & tests
  - Add a Regional upload example including `uuid` and `x-app-id: ETIQA_REGIONAL`.
  - E2E: one positive (with uuid), one negative (missing uuid) for Regional.

---

Documentation Updates
- Per-app guides: note `uuid` presence requirement at Step 3 for Regional.
- Overview & Detailed docs: cross-link this plan.
- Glossary: add TTL definition for future options.

Out of Scope (for Option C)
- Server-side step state, Device binding, Image hash matching, Validation gating.

Future Considerations (Option A/B)
- Move to stateful flow with VALIDATED gating for Regional (Option A) using a small `mobile_dlsm_steps` store and TTL.
- Phase-in via warn-only flags (Option B) to maintain compatibility.

Open Questions
- Should we enforce UUID v4 format strictly or allow any non-empty string for initial adoption?

Last updated: 2025-09-16
