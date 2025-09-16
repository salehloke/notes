---
title: DLSM Mobile — Glossary
aliases:
  - DLSM Glossary
tags: [dlsm, glossary]
---

# DLSM Mobile — Glossary

- uuid: Unique transaction identifier returned by the AI step; used to correlate manual validation and to reference generated images.
- POI start date (poi_start_date): Point-of-inception date for DLSM activation context.
- FNA file: Sidecar file (e.g., `.fna`) generated per uploaded image (odometer/plate) and stored alongside images on the server during submission processing.
- AI validation: Manual confirmation step (user-provided) that ties back to a `uuid`. Confirms or corrects the mileage extracted by AI.
- Fraud detection log: Non-blocking tracking emitted when `dlsm_fraud_detection_mode` is on; includes `uuid`, `imageUrl`, and request/response for manual review.
- App ID (`x-app-id`): Header identifying the consuming app. Defaults to `ETIQA_PLUS` when omitted. `ETIQA_REGIONAL` triggers Regional-specific submission behavior.

See also: [[DLSM Mobile — Index]]
