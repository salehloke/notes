Identity and linkage

- Use uuid: Should the AI step’s uuid be the canonical transaction id to link all steps? 
	- answer: yes
- Server state: Do we currently persist server-side state for step 1 that step 2/3 can check? 
	- answer: maybe no. currently we do save a tracker on each of the step can refer back to the api service.
- Mandatory linkage: Is it acceptable to reject step 3 unless a valid step-1 uuid is presented? 
	- answer: (Yes. BUT ONLY FOR REGIONAL APP. and make it backward compatible. and make it non mandatory input for etiqa plus app)
- Validation gating: Is it acceptable to reject step 3 unless step 2 (manual validation) is completed? 
	- answer: (Yes. only for regional app)

Binding and integrity

- User binding: Can we bind the uuid to the authenticated userId and policyNo at step 1 and enforce the same at steps 2/3?
	- answer: yes. but only for regional app
- Device binding: Can we bind to a device identifier (e.g., mobile deviceId) across steps? 
	- answer: no. but i would like to know how and why do we need to implement this.
- Image/hash binding: Can we persist image hashes from step 1 and require the same images (or hash match) at step 3? 
	- answer: no. sounds like too much effort. but i also would like an explanation on this implementation.
- Location/time checks: Can we enforce GPS/time consistency thresholds across steps (e.g., within X minutes/meters)? 
	- answer: no need.

Tokens and compatibility

- Step token: Can we issue a short-lived, server-signed step token (JWT) carrying userId, policyNo, vehicleNo, uuid,
step-state, and require it at step 2/3? 
	answer: no
- Backward compatibility: Do we need to keep existing flows working for older app versions during a transition? 
	- answer: yes
- Replay defense: Can we enforce single-use uuid/token (idempotency + replay prevention)? 
	- answer: i dont understand on this one. can ignore first

Scope and constraints

- ESB immutability: Are ESB payload contracts off-limits (i.e., we can only change our mobile APIs)? (Yes/No)
	- answer: yes
- App parity: Must the enhancement behave identically for ETIQA_PLUS and ETIQA_REGIONAL? 
	- answer: enhancement should only apply for ETIQA_REGIONAL. i believe we are able to cater that due to clear separation on the services and method
- Client-side signing: Can the mobile app compute an HMAC over critical fields (policyNo, vehicleNo, mileage, timestamps) with
a per-app secret?
	answer: no. i don't understand this. what are the implementation purposes?
- Data minimization: Are we allowed to include PII (policyNo/vehicleNo) inside step tokens, or must we use opaque ids only?
	- answer: maybe no. i want to keep the implementation simple
(Yes/No)

## second question

Quick Confirmations (Yes/No)

- Adopt Option A with phased enforcement per Option B for ETIQA_REGIONAL?:
	- adopt option C
- TTL for mobile_dlsm_steps: 72 hours acceptable?
	- answer: what is TTL? 
- Error codes/messages above OK to implement?
	- answer: yes
- Add optional uuid field to Step 3 request body (no change to ESB), and document for Regional use?
	- answer: it should be yes if we pick option C right?
	  
	  
on top of these, i do need documentation in my notes as well


  1. Scope of Features: What types of features would you typically want to
  control remotely? (e.g., feature flags, service integrations, UI toggles,
  business logic switches, API rate limits, etc.)
  - it can be anything
  1. Configuration Data Types: Besides boolean toggles like getCdhMode(),
  what other data types would you need? (strings, numbers, JSON objects,
  arrays, etc.)it can be any type, depends on the context of the usage. but in this context of the example given, that is using boolean.
  2. Access Control: Should different admin roles have different permissions
   to modify certain configurations? Or should all backoffice users have the
   same access?
   - only certain role. but normally, for any feature that we want to implement, we just need to create a migration data, so that we can pump in the value in the collection through database migration, and so that we could use it. example of configuration migration: smile-aio/database/migrations/20240610082234-backoffice-motor-inquiry-configuration.js
     or smile-aio/database/migrations/20231213054112-add-travel-configuration.js
  1. Categorization: Would you want configurations grouped by categories
  (like the existing schema has) such as "integrations", "ui-features",
  "business-rules", etc.?
  - i havent decided yet. could you suggests a list of categories? currently this is not mandatory
  1. Environment Handling: Should configurations be environment-specific
  (different values for SIT/UAT/PRD) or global across all environments?
  - since this is based on the data, so the codes should be the same accross all environments, however the behaviour would be depneds on the dataq in that environment
  1. Validation Rules: Do you need validation for configuration values?
  (e.g., URL format validation, numeric ranges, regex patterns). no
  2. Change History: Should the system track who changed what configuration
  and when, similar to the audit trail pattern you already have? this can refer to the api available here: smile-aio/backend/apps/backoffice/src/portal/portal-configuration/portal-configuration.controller.ts
  3. Caching Strategy: Should configurations be cached for performance, and
  if so, how should cache invalidation work? answer: not sure. keep in view this one. 
  4. Real-time Updates: Do you need configurations to take effect
  immediately, or is it acceptable to require service
  restarts/redeployments? this one will be real-time update due to depending on api calls and value in database
  5. Default Values: How should the system handle missing configurations -
  fallback to hardcoded defaults or fail gracefully? this will depends on the implemmentation context. use the example given as reference

  These details will help me create a comprehensive guidance document that
  covers all your use cases and follows your existing architectural
  patterns.