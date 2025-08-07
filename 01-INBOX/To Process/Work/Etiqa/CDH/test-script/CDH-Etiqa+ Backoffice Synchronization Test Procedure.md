# CDH-Etiqa+ Backoffice Synchronization Test Procedure

  

## Overview

This document outlines the test procedure for verifying the synchronization between Etiqa+ and CDH systems. The tests focus on ensuring that user data updates in Etiqa+ are properly synchronized with CDH and vice versa.

  

**IMPORTANT: All API calls MUST be executed using curl commands. No manual simulation or assumptions are allowed. Every API call must be actually executed and its full request and response must be documented.**

  

For each test, create a new file with the naming format: {Timestamp}-cdh-bo-sync-test-results.md (example: 202507301922-cdh-bo-sync-test-results.md).

  

## Test Environment

- Base URL: http://localhost:11400

- Test User ID: 68872f804dba512547573d41

  

## API Endpoints

  

### Authentication API

- POST `/api/backoffice/portal/login` - Login to get authentication token

  

```bash

curl -X POST "$BASE_URL/api/backoffice/portal/login" \

-H "Content-Type: application/json" \

-d '{

"pfNumber": "admin01",

"password": "123456",

"isLocalAccount": true

}'

```

  

#### Response

```json

{

"data": {

"accessToken": "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...",

"refreshToken": "Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9...",

"pfNumber": "admin01",

"name": "System Admin",

"roleId": "650427c5a36ca981f65ca412",

"lastLogin": "2025-07-30T10:26:32.127Z",

"roleName": "Super Admin",

"email": "",

"permissions": [...]

}

}

```

  

> **Important**: Use the `accessToken` value from the response in the `Authorization` header for all subsequent API calls.

  

### Backoffice Synchronization APIs

- GET `/api/backoffice/portal-user/sync-cdh-into-eplus/:userId` - Sync CDH data into Etiqa+

  

#### Retrieve Initial User Data && sync CDH data into Etiqa+

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 5e6f7g8h-9i0j-1k2l-3m4n-5o6p7q8r9s0t"

```

  

- POST `/api/backoffice/portal-user/retrieve-details-direct-cdh/no-logs` - Retrieve details from CDH directly

  

### Backoffice Update APIs

- PUT `/api/backoffice/portal-user/:userId` - Update user data in Etiqa+

```bash

curl -X PUT "$BASE_URL/api/backoffice/portal-user/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 6f7g8h9i-0j1k-2l3m-4n5o-6p7q8r9s0t1u" \

-d '{

"username": "testUser40",

"fullName": "Test User Bin fortwenty",

"idType": "NRIC",

"idNo": "000522055323",

"registrationIdNo": "000522055323",

"countryCode": "+60",

"phoneNo": "0172099100",

"email": "email-email-email-email-email7@email.com",

"pfNo": "",

"activePolicyNo": "",

"ecif": "PIMYS2507WRA9DE92FE",

"isMeVerified": false,

"isMCSVerified": false,

"isWellnessEnrolled": false,

"skipAgentChecking": false,

"id": "68898a2f73740e5730e0cc44",

"contacts": [

{

"cdhContactId": 1112,

"contactType": "M",

"countryCode": "+60",

"contactNo": "0172099100",

"isPrimary": true,

"isVerified": false,

"_id": "6889f5491d67183d970e4126",

"id": 1112

}

],

"emails": [

{

"cdhEmailId": 968,

"emailType": "1",

"emailAddress": "email-email-email-email-email7@email.com",

"isPrimary": true,

"isVerified": false,

"_id": "6889f5491d67183d970e4127",

"id": 968

}

],

"addresses": []

}'

```

  

### Request Body Requirements

  

**IMPORTANT:** The backoffice user update API requires a complete payload with all fields shown above. Do not skip any fields in the request body, even if you're only updating specific attributes.

  

- All fields shown in the example request body are required

- Empty strings (`""`) are acceptable for optional fields like `pfNo` and `activePolicyNo`

- Boolean fields (`isMeVerified`, `isMCSVerified`, `isWellnessEnrolled`, `skipAgentChecking`) must be explicitly included

- The `id` field must match the user ID in the URL path

- Arrays (`contacts`, `emails`, `addresses`) must be included even if empty

- When updating arrays, include the complete array with all existing items plus any modifications

  

Omitting any of these fields will result in a 400 Bad Request error. The API does not support partial updates.

  
  

## Test Process

  

### Step 1: Retrieve Initial User Data

1. Call the sync-cdh-into-eplus API to get the current user data

2. Record the initial values for key fields, and record the full response:

- user.name.fullName or user.fullName

- user.contacts

- user.phoneNo

- user.countryCode

- user.email

- user.isPhoneNoVerified

- user.isEmailVerified

  

### Step 2: Update User Data

1. Prepare a request body with updated user data:

- Add new emails with one marked as primary

- Add new contacts with one marked as primary

- Add new addresses with one marked as primary

2. Call the PUT `/api/backoffice/portal-user/:userId` API to update the user data

3. CDH sync to Etiqa+ will be called in this API as well, so no need to call the cdh-sync API

  

### Step 3: Verify Synchronization

1. Call the sync-cdh-into-eplus API again to get the updated user data

2. Compare the before and after values for key fields

3. Document the comparison results in a table format:

  

```markdown

| Field | Etiqa+ Value | CDH Value | Match Status |

|-------|-------------|-----------|---------------|

| Primary Email | example@email.com | example@email.com | ✅ Match |

| Email Verification | true | true | ✅ Match |

| Primary Phone | +60 0123456789 | +60 0123456789 | ✅ Match |

| Phone Verification | true | true | ✅ Match |

| Primary Address | Home (123 Main St) | Home (123 Main St) | ✅ Match |

| Full Name | Test User | Test User | ✅ Match |

```

  

4. Verify that:

- Primary email in emails array replaced user.email

- Primary contact in contacts array replaced user.phoneNo and user.countryCode

- Primary address in addresses array replaced user.address

- Verification status is correctly reflected in user.isPhoneNoVerified and user.isEmailVerified

- Only one item is marked as primary in each category (emails, contacts, addresses)

- after updating values to cdh, when sync from CDH into Eplus, each of values in the contacts array, must have cdhContactId

- after updating values to cdh, when sync from CDH into Eplus, each of values in the emails array, must have cdhEmailId

- after updating values to cdh, when sync from CDH into Eplus, each of values in the addresses array, must have cdhAddressId

  

## Test Cases

  

### Test Case 1: Email Update and Synchronization

- Update primary email and verify it updates the root user.email field

- Verify email verification status is properly synchronized

  

### Test Case 2: Contact Update and Synchronization

- Update primary contact and verify it updates the root user.phoneNo and user.countryCode fields

- Verify contact verification status is properly synchronized to user.isPhoneNoVerified

  

### Test Case 3: Address Update and Synchronization

- Update primary address and verify it updates the root user.address field

  

### Test Case 4: Multiple Updates and Primary Designation

- Add multiple emails, contacts, and addresses

- Verify only one item is primary in each category

- Change which item is primary and verify the root fields update accordingly

  

### Test case 5: Update verification status

- Update primary email and verify it updates the root user.email field

- Verify email verification status is properly synchronized

  

## Data Generation Guidelines

- Use randomly generated data for each test to avoid conflicts

- Ensure email addresses follow valid format (e.g., username@domain.com)

- Use valid phone number formats with country codes

- Use realistic address data

  

## Documentation

- For each test case, create a separate test-result-{n}.md file

- Include all API requests and responses

- Highlight the key fields before and after synchronization

- Document any issues or unexpected behavior

  

## Verification Checklist

- [ ] Primary email updates user.email

- [ ] Primary contact updates user.phoneNo and user.countryCode

- [ ] Primary address updates user.address

- [ ] Verification status properly updates user.isPhoneNoVerified and user.isEmailVerified

- [ ] Only one primary item exists in each category

- [ ] All updates from Etiqa+ are synchronized with CDH

- [ ] All data from CDH is correctly reflected in Etiqa+

- [ ] Verify that each value is able to be updated

- [ ] Verify that each contact value in the contacts array has cdhContactId after sync to CDH. Check this when call api sync-cdh-into-eplus

- [ ] Verify that each email value in the emails array has cdhEmailId after sync to CDH. Check this when call api sync-cdh-into-eplus

- [ ] Verify that each address value in the addresses array has cdhAddressId after sync to CDH. Check this when call api sync-cdh-into-eplus