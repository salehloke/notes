## CDH — Update Mobile Number (E2E)

This guide covers updating an existing mobile contact in CDH for a user. OTP verification is enforced via the `otp` field in the contact payload.

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

2) Obtain OTP
   - Request OTP via Mobile API (requires mobile bearer auth)
   - Host: `http://localhost:10101`
   - POST `/api/v5/mobile/profile/request-otp/mobile-no/cdh`
   - Body: `{ "countryCode": "+60", "phoneNo": "987654321" }`
   - Example:
   ```bash
   curl -X POST \
     "http://localhost:10101/api/v5/mobile/profile/request-otp/mobile-no/cdh" \
     -H "Authorization: Bearer $MOBILE_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{
       "countryCode": "+60",
       "phoneNo": "987654321"
     }'
   ```
   - Use the received OTP value in the `otp` field when calling CDH.

3) Update contact (mobile)
   - PUT `/api/v5/mobile-cdh/contact/:contactId`
   - Body:
     - `contactType`: "M"
     - `countryCode`: e.g. "+60"
     - `contactNo`: updated number without country code
     - `isPrimary` (optional)
     - `otp`: OTP from step 2
   - Example:
   ```bash
   curl -X PUT \
     "$BASE_URL/api/v5/mobile-cdh/contact/$CONTACT_ID" \
     -H "Authorization: Bearer $MOBILE_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{
       "contactType": "M",
       "countryCode": "+60",
       "contactNo": "987654321",
       "isPrimary": true,
       "otp": "123456"
     }'
   ```

Notes
- `otp` is mandatory and validates the change against the target mobile number.
- Ensure you pass the correct `contactId` for the mobile contact to be updated.
- The authenticated user is derived from the bearer token; `:userId` is not part of the path.
- OTP is sent to the target mobile number, and SMS notification is sent to the user's primary mobile number.
