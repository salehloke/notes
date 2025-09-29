## CDH — Add Email (E2E)

This guide covers adding a new email in CDH for a user. OTP verification is enforced via the `otp` field in the email payload.

### Base
- Prefix: `/api/v5`
- Module: `/mobile-cdh`

### Flow
1) Sync CDH data into Etiqa+
   - GET `/api/v5/mobile-cdh/sync-cdh-into-eplus`
   - Example:
   ```bash
   curl -X GET \
     "$BASE_URL/api/v5/mobile-cdh/sync-cdh-into-eplus" \
     -H "Authorization: Bearer $MOBILE_TOKEN"
   ```

2) Obtain OTP (email)
   - Request OTP via Mobile API (requires mobile bearer auth)
   - Host: `http://localhost:10101`
   - POST `/api/v5/mobile/profile/request-otp/email/cdh`
   - Body: `{ "email": "user.new@example.com" }`
   - Example:
   ```bash
   curl -X POST \
     "http://localhost:10101/api/v5/mobile/profile/request-otp/email/cdh" \
     -H "Authorization: Bearer $MOBILE_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{
       "email": "user.new@example.com"
     }'
   ```
   - Use the received OTP value in the `otp` field when calling CDH.

3) Add email in CDH
   - POST `/api/v5/mobile-cdh/email`
   - Body:
     - `emailType`: e.g. `1` (PERSONAL)
     - `emailAddress`: e.g. `user.new@example.com`
     - `isPrimary` (optional)
     - `isVerified` (optional)
     - `otp`: OTP from step 2
   - Example:
   ```bash
   curl -X POST \
     "$BASE_URL/api/v5/mobile-cdh/email" \
     -H "Authorization: Bearer $MOBILE_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{
       "emailType": "1",
       "emailAddress": "user.new@example.com",
       "isPrimary": true,
       "otp": "123456"
     }'
   ```

Notes
- `otp` is mandatory and validates the change against the target email address.
- If adding a new primary email, set `isPrimary: true`.
- The authenticated user is derived from the bearer token; `:userId` is not part of the path.
- OTP is sent to the target email address, and SMS notification is sent to the user's primary mobile number.
