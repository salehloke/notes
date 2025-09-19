---
title: DLSM Enhancement Roadmap — Linkage Options A/B/C
aliases:
  - DLSM Linkage Options
tags: [dlsm, roadmap, linkage]
---

# DLSM Enhancement Roadmap — Linkage Options A/B/C

Context
- Pentest flagged lack of linkage across stepwise APIs.
- Goal: Improve integrity with minimal disruption.

Options
- Option A — UUID-Gated Stateful Flow (Recommended future)
  - Create a `mobile_dlsm_steps` state keyed by `uuid` with statuses: CAPTURED → VALIDATED → CONSUMED.
  - Regional gating: Step 3 requires `uuid` in VALIDATED state; single-use.
  - Needs small persistence + TTL (e.g., 72h).
  - Pros: Strong guarantees, auditability. Cons: adds state and transitions.

- Option B — Soft Gating + Progressive Enforcement
  - Add flags for Regional: `regional_dlsm_uuid_required`, `regional_dlsm_validation_required`.
  - Phase-in: warn-only → enforce.
  - Requires Option A (or at least state for VALIDATED check) to fully enforce validation.

- Option C — Minimal Linkage (Adopted now)
  - Require presence of Step-1 `uuid` at Step 3 for Regional; no validation gating.
  - No ESB changes. ETIQA_PLUS unchanged.
  - Pros: Quick, compatible. Cons: Weakest linkage (format-only unless state added later).

Non-Chosen Controls (for now)
- Device binding: Adds client work and limited security value vs user/policy binding.
- Image-hash binding: Higher effort and complexity; potential false mismatches due to compression/metadata.
- Client-side HMAC: Adds secret management and app complexity; limited benefit if client is controlled.

Next Steps
- Implement Option C (Regional-only). Monitor and measure.
- Plan migration to Option A with phased flags as follow-up.

See also: [[DLSM Enhancement Plan — Step Linkage (Option C)]], [[DLSM Mobile — Index]]

Last updated: 2025-09-16

