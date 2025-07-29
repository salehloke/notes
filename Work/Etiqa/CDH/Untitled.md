# CDH and Etiqa+ Synchronization Testing

  

## Overview

This document tracks the testing of synchronization between Etiqa+ database and CDH. The goal is to ensure data consistency across both systems, particularly for user profile information including emails, contacts, and addresses.

  

## Test Process

We'll follow these steps for each test case:

1. Perform an API operation (POST/PUT/PATCH)

2. Check the updated values in Etiqa+ database

3. Obtain the idNo from Etiqa+ response

4. Call CDH API to retrieve details using the idNo

5. Verify if primary values are correctly reflected in the user model

6. Check verification status synchronization

7. Compare values between Etiqa+ and CDH

  

## Available API Operations for Testing

  

### Email Management APIs

- GET `/api/v5/mobile-cdh/:userId/emails` - Get all emails for a user

- GET `/api/v5/mobile-cdh/:userId/email/:emailId` - Get email by ID

- POST `/api/v5/mobile-cdh/:userId/email` - Add a new email

- PUT `/api/v5/mobile-cdh/:userId/email/:emailId` - Update an existing email

- DELETE `/api/v5/mobile-cdh/:userId/email/:emailId` - Remove an email

- PATCH `/api/v5/mobile-cdh/:userId/email/:emailId/primary` - Set an email as primary

- PATCH `/api/v5/mobile-cdh/:userId/email/:emailId/verify` - Mark an email as verified

  

### Contact Management APIs

- GET `/api/v5/mobile-cdh/:userId/contacts` - Get all contacts for a user

- POST `/api/v5/mobile-cdh/:userId/contact` - Add a new contact

- PUT `/api/v5/mobile-cdh/:userId/contact/:contactId` - Update an existing contact

- DELETE `/api/v5/mobile-cdh/:userId/contact/:contactId` - Remove a contact

- PATCH `/api/v5/mobile-cdh/:userId/contact/:contactId/primary` - Set a contact as primary

- PATCH `/api/v5/mobile-cdh/:userId/contact/:contactId/verify` - Mark a contact as verified

  

### Address Management APIs

- GET `/api/v5/mobile-cdh/:userId/addresses` - Get all addresses for a user

- GET `/api/v5/mobile-cdh/:userId/address/:addressId` - Get address by ID

- POST `/api/v5/mobile-cdh/:userId/address` - Add a new address

- PUT `/api/v5/mobile-cdh/:userId/address/:addressId` - Update an existing address

- DELETE `/api/v5/mobile-cdh/:userId/address/:addressId` - Remove an address

- PATCH `/api/v5/mobile-cdh/:userId/address/:addressId/primary` - Set an address as primary

  

### Synchronization APIs

- GET `/api/v5/mobile-cdh/sync-cdh-into-eplus/:userId` - Sync CDH data into Etiqa+

- POST `/api/v5/mobile-cdh/retrieve-details-direct-cdh/no-logs` - Retrieve details from CDH directly

  

## Test Case 1: Email Management

  

### Step 1: Perform API Operation

We'll test adding a new email with the following API call:

  

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/email' \

-H 'accept: application/json' \

-H 'Content-Type: application/json' \

-d '{

"emailType": "1",

"emailAddress": "test_email@example.com",

"isPrimary": true,

"isVerified": true

}'

```

  

**Response:**

```json

{

"data": {

"success": true,

"code": "200",

"message": "Email added successfully for user 68872f804dba512547573d41",

"logs": [...],

"summary": {

"totalRequests": 9,

"successful": 9,

"failed": 0,

"warnings": 0,

"executionTime": "2.35s",

"executionTimeMs": 2347,

"startTime": "2025-07-28T17:52:36.342Z",

"endTime": "2025-07-28T17:52:38.689Z"

},

"data": {

"_id": "68872f804dba512547573d41",

"username": "CdhTest32",

"email": "test133@email.com",

"isEmailVerified": true,

"fullName": "CdhTest bin thrity two",

"idType": "NRIC",

"idNo": "771106015507",

"emails": [

{

"cdhEmailId": 876,

"emailType": "1",

"emailAddress": "cdhtest32@email.com",

"isPrimary": false,

"isVerified": true,

"_id": "68872f804dba512547573d3f",

"id": 876

},

{

"emailType": "1",

"emailAddress": "cdhTest32@email.com",

"isPrimary": false,

"isVerified": true,

"cdhEmailId": 876,

"id": 876,

"_id": "688732d26d2116836e8aa4d1"

},

{

"emailType": "1",

"emailAddress": "test133@email.com",

"isPrimary": false,

"isVerified": true,

"_id": "6887ae161ff9cec29bab2e55"

},

{

"emailType": "1",

"emailAddress": "test_email@example.com",

"isPrimary": true,

"isVerified": true,

"_id": "6887b8e4deb98c1e2e4f5fda"

}

]

}

}

}

```

  

### Step 2: Check Value in Etiqa+ DB

```bash

curl -X 'GET' \

'http://localhost:10100/api/v5/mobile-cdh/sync-cdh-into-eplus/68872f804dba512547573d41' \

-H 'accept: application/json'

```

  

**Response:**

```json

{

"data": {

"_id": "68872f804dba512547573d41",

"username": "CdhTest32",

"email": "test_email@example.com",

"isEmailVerified": true,

"fullName": "CdhTest bin thrity two",

"idType": "NRIC",

"idNo": "771106015507",

"registrationIdNo": "771106015507",

"countryCode": "+60",

"phoneNo": "0017200032",

"isPhoneNoVerified": true,

"emails": [

{

"cdhEmailId": 876,

"emailType": "1",

"emailAddress": "cdhtest32@email.com",

"isPrimary": false,

"isVerified": true,

"_id": "68872f804dba512547573d3f",

"id": 876

},

{

"emailType": "1",

"emailAddress": "cdhTest32@email.com",

"isPrimary": false,

"isVerified": true,

"cdhEmailId": 876,

"id": 876,

"_id": "688732d26d2116836e8aa4d1"

},

{

"emailType": "1",

"emailAddress": "test133@email.com",

"isPrimary": false,

"isVerified": true,

"_id": "6887ae161ff9cec29bab2e55"

},

{

"emailType": "1",

"emailAddress": "test_email@example.com",

"isPrimary": true,

"isVerified": true,

"_id": "6887b8e4deb98c1e2e4f5fda"

}

],

"ecif": "PIMYS2507U6ORJ2F7F0"

}

}

```

  

### Step 3: Obtain idNo from Etiqa+ Response

From the Etiqa+ response, we obtained the following identification details:

- **idNo**: 771106015507

- **ecif**: PIMYS2507U6ORJ2F7F0

  

### Step 4: Call CDH API to Check Data

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/retrieve-details-direct-cdh/no-logs' \

-H 'accept: */*' \

-H 'Content-Type: application/json' \

-d '{

"client": {

"idType": "001",

"idValue": "771106015507",

"ecif": ""

}

}'

```

  

**Response:**

```json

{

"data": {

"type": "https://tools.ietf.org/html/rfc7231#section-6.3.1",

"title": "OK",

"status": 200,

"instance": "/api/parties/search",

"success": true,

"traceId": "00-e5d9f7f31afb2d6f509b415f9b009ba2-91526b95301da169-01",

"data": {

"partyTypeCode": "PI",

"ecif": "PIMYS2507U6ORJ2F7F0",

"name": {

"fullName": "CdhTest bin thrity two",

"firstName": null,

"middleName": null,

"lastName": null,

"nickname": null

},

"identifiers": [

{

"idTypeCode": "001",

"idValue": "771106015507"

}

],

"addresses": [

{

"addressTypeCode": "Home",

"line1": "2211",

"line2": null,

"line3": null,

"line4": null,

"line5": null,

"postalCode": "54070",

"city": "Brickfields",

"stateCode": "KUL",

"countryCode": "MYS",

"primaryIndicator": true,

"id": 843

}

],

"contacts": [

{

"contactTypeCode": "M",

"countryDialingCode": "+60",

"phoneNumber": "0017200032",

"verifiedIndicator": true,

"primaryIndicator": true,

"id": 1043

}

],

"emails": [

{

"emailTypeCode": "1",

"emailAddress": "cdhTest32@email.com",

"verifiedIndicator": true,

"primaryIndicator": true,

"id": 876

}

]

},

"timestamp": "2025-07-29T01:53:11.7631762+08:00"

}

}

```

  

### Step 5: Verify Primary Values

We need to verify if the primary values are correctly reflected in the user model:

  

**In Etiqa+ DB:**

- Primary email: `test_email@example.com` (set as primary: true)

- User model email field: `test_email@example.com` (correctly reflects primary email)

- Primary phone: `0017200032` (set as primary: true)

- User model phoneNo field: `0017200032` (correctly reflects primary phone)

  

**In CDH:**

- Primary email: `cdhTest32@email.com` (set as primaryIndicator: true)

- Primary phone: `0017200032` (set as primaryIndicator: true)

  

**Observation:** The primary email in CDH does not match the primary email in Etiqa+. This indicates a synchronization issue between the two systems.

  

### Step 6: Check Email Verification Status

**In Etiqa+ DB:**

- Primary email (`test_email@example.com`) is verified (isVerified: true)

- User model isEmailVerified field: true (correctly reflects primary email verification status)

  

**In CDH:**

- Email (`cdhTest32@email.com`) is verified (verifiedIndicator: true)

  

### Step 7: Check Phone Verification Status

**In Etiqa+ DB:**

- Primary phone (`0017200032`) is verified (isVerified: true)

- User model isPhoneNoVerified field: true (correctly reflects primary phone verification status)

  

**In CDH:**

- Phone (`0017200032`) is verified (verifiedIndicator: true)

  

### Step 8: Compare Values Between Etiqa+ and CDH

  

| Field | Etiqa+ Value | CDH Value | Match Status |

|-------|-------------|-----------|---------------|

| Primary Email | test_email@example.com | cdhTest32@email.com | ❌ Mismatch |

| Email Verification | true | true | ✅ Match |

| Primary Phone | 0017200032 | 0017200032 | ✅ Match |

| Phone Verification | true | true | ✅ Match |

| Primary Address | Office (789 Business Park) | Home (2211) | ❌ Mismatch |

| Full Name | CdhTest bin thrity two | CdhTest bin thrity two | ✅ Match |

  

### Step 9: Conclusion

Based on our testing of adding a new primary email, we've identified the following issues:

  

1. **Email Synchronization Issue**: The primary email in Etiqa+ (`test_email@example.com`) is not synchronized to CDH, which still shows `cdhTest32@email.com` as the primary email.

  

2. **Address Synchronization Issue**: The primary address in Etiqa+ (Office address) does not match the primary address in CDH (Home address).

  

3. **Successful Synchronization**: The phone number, verification statuses, and full name are correctly synchronized between both systems.

  

**Recommendation:** We need to investigate why the primary email and address changes in Etiqa+ are not being properly synchronized to CDH. This could be due to:

- The sync operation not being triggered after the email update

- A timing issue where the CDH API call was made before the sync completed

- A potential bug in the synchronization logic

  

## Test Case 2: Contact Management

  

### Step 1: Perform API Operation

We'll test adding a new contact with the following API call:

  

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/contact' \

-H 'accept: application/json' \

-H 'Content-Type: application/json' \

-d '{

"contactType": "M",

"countryCode": "+60",

"contactNo": "0123456789",

"isPrimary": true,

"isVerified": true

}'

```

  

**Response:**

```json

{

"data": {

"success": true,

"code": "200",

"message": "Contact added successfully for user 68872f804dba512547573d41",

"logs": [...],

"summary": {

"totalRequests": 9,

"successful": 9,

"failed": 0,

"warnings": 0,

"executionTime": "3.70s",

"executionTimeMs": 3702,

"startTime": "2025-07-28T17:56:04.613Z",

"endTime": "2025-07-28T17:56:08.315Z"

},

"data": {

"_id": "68872f804dba512547573d41",

"username": "CdhTest32",

"email": "test_email@example.com",

"isEmailVerified": true,

"fullName": "CdhTest bin thrity two",

"idType": "NRIC",

"idNo": "771106015507",

"countryCode": "+60",

"phoneNo": "0017200032",

"isPhoneNoVerified": true,

"contacts": [

{

"cdhContactId": 1043,

"contactType": "M",

"countryCode": "+60",

"contactNo": "0017200032",

"isPrimary": false,

"isVerified": true,

"_id": "68872f804dba512547573d3e",

"id": 1043

},

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "0123456789",

"isPrimary": true,

"isVerified": true,

"_id": "6887b9b5deb98c1e2e4f5fe9"

}

]

},

"metadata": {

"userId": "68872f804dba512547573d41",

"userIdNo": "771106015507",

"newContactNo": "0123456789",

"newContactType": "M",

"newContactId": "6887b9b5deb98c1e2e4f5fe9",

"isPrimary": true,

"isVerified": true,

"totalContactsCount": 2,

"updateCdh": true,

"contactLogicSuccess": true,

"primaryContactChanges": [

{

"contactNo": "0017200032",

"contactType": "M",

"action": "unset_primary"

}

]

}

}

}

```

  

### Step 2: Check Value in Etiqa+ DB

```bash

curl -X 'GET' \

'http://localhost:10100/api/v5/mobile-cdh/sync-cdh-into-eplus/68872f804dba512547573d41' \

-H 'accept: application/json'

```

  

**Response:**

```json

{

"data": {

"_id": "68872f804dba512547573d41",

"username": "CdhTest32",

"email": "test_email@example.com",

"isEmailVerified": true,

"fullName": "CdhTest bin thrity two",

"idType": "NRIC",

"idNo": "771106015507",

"registrationIdNo": "771106015507",

"countryCode": "+60",

"phoneNo": "M",

"isPhoneNoVerified": true,

"contacts": [

{

"cdhContactId": 1043,

"contactType": "M",

"countryCode": "+60",

"contactNo": "0017200032",

"isPrimary": false,

"isVerified": true,

"_id": "68872f804dba512547573d3e",

"id": 1043

},

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "M",

"isPrimary": true,

"isVerified": true,

"_id": "6887b9b5deb98c1e2e4f5fe9"

}

],

"ecif": "PIMYS2507U6ORJ2F7F0"

}

}

```

  

### Step 3: Obtain idNo from Etiqa+ Response

From the Etiqa+ response, we obtained the following identification details:

- **idNo**: 771106015507

- **ecif**: PIMYS2507U6ORJ2F7F0

  

### Step 4: Call CDH API to Check Data

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/retrieve-details-direct-cdh/no-logs' \

-H 'accept: */*' \

-H 'Content-Type: application/json' \

-d '{

"client": {

"idType": "001",

"idValue": "771106015507",

"ecif": ""

}

}'

```

  

**Response:**

```json

{

"data": {

"type": "https://tools.ietf.org/html/rfc7231#section-6.3.1",

"title": "OK",

"status": 200,

"instance": "/api/parties/search",

"success": true,

"traceId": "00-95b36bb9c6d42c673a7744d20190ebfa-13a827fa2f0d97f9-01",

"data": {

"partyTypeCode": "PI",

"ecif": "PIMYS2507U6ORJ2F7F0",

"name": {

"fullName": "CdhTest bin thrity two"

},

"identifiers": [

{

"idTypeCode": "001",

"idValue": "771106015507"

}

],

"addresses": [

{

"addressTypeCode": "Home",

"line1": "2211",

"postalCode": "54070",

"city": "Brickfields",

"stateCode": "KUL",

"countryCode": "MYS",

"primaryIndicator": true,

"id": 843

}

],

"contacts": [

{

"contactTypeCode": "M",

"countryDialingCode": "+60",

"phoneNumber": "0017200032",

"verifiedIndicator": true,

"primaryIndicator": true,

"id": 1043

}

],

"emails": [

{

"emailTypeCode": "1",

"emailAddress": "cdhTest32@email.com",

"verifiedIndicator": true,

"primaryIndicator": true,

"id": 876

}

]

}

}

}

```

  

### Step 5: Verify Primary Values

We need to verify if the primary values are correctly reflected in the user model:

  

**In Etiqa+ DB:**

- Primary contact: There's an issue with the contact data in Etiqa+. The contactNo shows as "M" instead of "0123456789".

- User model phoneNo field: Shows "M" (incorrect, should be "0123456789")

  

**In CDH:**

- Primary contact: Still shows "0017200032" as primary (not updated to "0123456789")

  

**Observation:** There are data corruption issues with the contact data in Etiqa+, and the primary contact in CDH was not updated.

  

### Step 6: Check Email Verification Status

**In Etiqa+ DB:**

- Email verification status remains the same as in Test Case 1

  

**In CDH:**

- Email verification status remains the same as in Test Case 1

  

### Step 7: Check Phone Verification Status

**In Etiqa+ DB:**

- Primary contact (with incorrect value "M") is verified (isVerified: true)

- User model isPhoneNoVerified field: true

  

**In CDH:**

- Phone ("0017200032") is verified (verifiedIndicator: true)

  

### Step 8: Compare Values Between Etiqa+ and CDH

  

| Field | Etiqa+ Value | CDH Value | Match Status |

|-------|-------------|-----------|---------------|

| Primary Email | test_email@example.com | cdhTest32@email.com | ❌ Mismatch |

| Email Verification | true | true | ✅ Match |

| Primary Phone | M (corrupted) | 0017200032 | ❌ Mismatch |

| Phone Verification | true | true | ✅ Match |

| Primary Address | Office (789 Business Park) | Home (2211) | ❌ Mismatch |

| Full Name | CdhTest bin thrity two | CdhTest bin thrity two | ✅ Match |

  

### Step 9: Conclusion

Based on our testing of adding a new primary contact, we've identified the following issues:

  

1. **Contact Data Corruption**: The contact number in Etiqa+ is corrupted, showing "M" (which is the contact type) instead of the actual phone number "0123456789".

  

2. **Contact Synchronization Issue**: The new primary contact in Etiqa+ is not synchronized to CDH, which still shows the old contact as primary.

  

3. **User Model Update Issue**: The user model's phoneNo field in Etiqa+ is incorrectly updated with "M" instead of the actual phone number.

  

4. **Consistent Issues**: Similar to the email test case, we're seeing synchronization issues between Etiqa+ and CDH for primary values.

  

**Recommendation:** There appears to be a bug in the contact update logic that is causing data corruption and improper synchronization. This needs to be investigated and fixed in the following components:

  

1. The contact addition/update logic in mobile-cdh-ver2.controller.ts

2. The updateContactLogic method in the CDH User Contacts Service

3. The synchronization mechanism between Etiqa+ and CDH

  

## Test Case 3: Address Management

  

### Step 1: Perform API Operation

We'll test adding a new address with the following API call:

  

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/address' \

-H 'accept: application/json' \

-H 'Content-Type: application/json' \

-d '{

"addressType": "Mailing",

"address1": "123 Test Street",

"address2": "Unit 45",

"postcode": "50250",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true

}'

```

  

**Response:**

```json

{

"data": {

"success": false,

"code": "500",

"message": "Add Address failed: address.address1.toLowerCase is not a function",

"logs": [

{

"api": "Add Address - Final Error Handler",

"status": "failed",

"error": {

"message": "address.address1.toLowerCase is not a function"

},

"data": {

"errorStack": "TypeError: address.address1.toLowerCase is not a function\n at /Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:53246:41\n at Proxy.some (<anonymous>)\n at CdhUserManagementService.addAddress (/Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:53244:50)\n at processTicksAndRejections (node:internal/process/task_queues:95:5)\n at MobileCdhVer2Service.addAddress (/Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:10648:26)\n at MobileCdhVer2Controller.addAddress (/Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:9132:30)\n at /Users/salehloke/Developer/smile-aio/backend/node_modules/@opentelemetry/instrumentation-nestjs-core/src/instrumentation.ts:222:16",

"userId": "68872f804dba512547573d41",

"addressData": {

"addressType": "Mailing",

"address1": "123 Test Street",

"address2": "Unit 45",

"postcode": "50250",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true

}

},

"timestamp": "2025-07-28T17:58:24.189Z"

},

{

"api": "Find User by ID",

"status": "success",

"data": {

"userId": "68872f804dba512547573d41",

"userIdNo": "771106015507",

"userFullName": "CdhTest bin thrity two",

"existingContactsCount": 2,

"existingEmailsCount": 4,

"existingAddressesCount": 2

},

"timestamp": "2025-07-28T17:58:24.177Z"

},

{

"api": "Add Address Initialization",

"status": "success",

"data": {

"userId": "68872f804dba512547573d41",

"address1": "123 Test Street",

"address2": "Unit 45",

"postcode": "50250",

"city": "Kuala Lumpur",

"state": "KUL",

"addressType": "Mailing",

"isPrimary": true,

"updateCdh": true,

"operation": "Add Address"

},

"timestamp": "2025-07-28T17:58:24.139Z"

}

],

"summary": {

"totalRequests": 3,

"successful": 2,

"failed": 1,

"warnings": 0,

"executionTime": "0.05s",

"executionTimeMs": 52,

"startTime": "2025-07-28T17:58:24.139Z",

"endTime": "2025-07-28T17:58:24.191Z"

},

"data": null,

"metadata": {

"userId": "68872f804dba512547573d41",

"addressData": {

"addressType": "Mailing",

"address1": "123 Test Street",

"address2": "Unit 45",

"postcode": "50250",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true

},

"errorType": "TypeError",

"errorStack": "TypeError: address.address1.toLowerCase is not a function\n at /Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:53246:41\n at Proxy.some (<anonymous>)\n at CdhUserManagementService.addAddress (/Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:53244:50)\n at processTicksAndRejections (node:internal/process/task_queues:95:5)\n at MobileCdhVer2Service.addAddress (/Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:10648:26)\n at MobileCdhVer2Controller.addAddress (/Users/salehloke/Developer/smile-aio/backend/dist/apps/smile/main.js:9132:30)\n at /Users/salehloke/Developer/smile-aio/backend/node_modules/@opentelemetry/instrumentation-nestjs-core/src/instrumentation.ts:222:16",

"address1": "123 Test Street",

"addressType": "Mailing"

},

"error": {}

}

}

```

  

### Step 2-4: Unable to Continue Testing

Due to the error encountered in Step 1, we are unable to proceed with the remaining steps of the address management test case.

  

### Step 5: Conclusion and Bug Analysis

  

We encountered a backend error when attempting to add a new address. The error message indicates a type error in the address handling logic:

  

```

TypeError: address.address1.toLowerCase is not a function

```

  

This suggests that the code is expecting `address.address1` to be a string, but it's receiving a different data type. Looking at the error stack trace, the issue is occurring in the `CdhUserManagementService.addAddress` method.

  

By examining the existing address data in the user object from previous tests, we can see a potential issue with the address structure. In the user object, one of the existing addresses has a nested structure where `address1` is an object rather than a string:

  

```json

{

"addressType": "Office",

"address1": {

"addressType": "Office",

"address1": "789 Business Park",

"address2": "Building A",

"postcode": "50200",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true

},

"address2": "Building A",

"postcode": "50200",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true,

"_id": "6887b03e1ff9cec29bab2e76"

}

```

  

**Potential Causes:**

  

1. There might be inconsistent data structures for addresses in the database, with some addresses having `address1` as a string and others having it as an object.

  

2. The code in `CdhUserManagementService.addAddress` is not properly handling different address data structures or validating the input before attempting to call `toLowerCase()`.

  

3. There might be a data corruption issue similar to what we observed with contacts, where the address data structure is not being properly maintained.

  

**Recommendations for Fixing:**

  

1. Review the `CdhUserManagementService.addAddress` method to add proper type checking before calling `toLowerCase()`.

  

2. Standardize the address data structure across the application to ensure consistency.

  

3. Add data validation to ensure that address fields are of the expected types before processing.

  

4. Consider implementing a data migration to fix any existing corrupted address data in the database.

  

This bug needs to be fixed before we can continue with the address management testing.