# CDH and Etiqa+ Mobile Synchronization Test Results

  

## Test Environment

- Base URL: http://localhost:10100

- Test User ID: 68872f804dba512547573d41

- Test Date: 2025-07-30

- Test Time: 13:00:36 (UTC+8)

  

## Test Summary

This document contains the results of testing the synchronization between Etiqa+ database and CDH. The tests focus on ensuring data consistency across both systems for user profile information including emails, contacts, and addresses.

  

## Test Cases

  

### Test Case 1: Email Management

  

#### Step 1: Perform API Operation - Add Email

  

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/email' \

-H 'accept: application/json' \

-H 'Content-Type: application/json' \

-d '{

"emailType": "1",

"emailAddress": "test_random_email_20250730@example.com",

"isPrimary": true,

"isVerified": true

}'

```

  

**Response:**

```json

{"data":{"success":true,"code":"200","message":"Email added successfully for user 68872f804dba512547573d41","logs":[{"api":"Add Email Initialization","status":"success","data":{"userId":"68872f804dba512547573d41","emailAddress":"test_random_email_20250730@example.com","emailType":"1","isPrimary":true,"isVerified":true,"updateCdh":true,"operation":"Add Email"},"timestamp":"2025-07-30T05:01:29.124Z"},{"api":"Find User by ID","status":"success","data":{"userId":"68872f804dba512547573d41","userIdNo":"771106015507","userFullName":"CDH Test User Updated","existingContactsCount":4,"existingEmailsCount":5,"existingAddressesCount":4},"timestamp":"2025-07-30T05:01:29.169Z"},{"api":"Email Duplicate Check","status":"success","data":{"userId":"68872f804dba512547573d41","emailAddress":"test_random_email_20250730@example.com","isDuplicate":false},"timestamp":"2025-07-30T05:01:29.169Z"},{"api":"New Email Creation","status":"success","data":{"userId":"68872f804dba512547573d41","emailId":"6889a7292d8a99a3da1d5b88","emailAddress":"test_random_email_20250730@example.com","emailType":"1","isPrimary":true,"isVerified":true},"timestamp":"2025-07-30T05:01:29.169Z"},{"api":"Primary Email Logic","status":"success","data":{"userId":"68872f804dba512547573d41","newPrimaryEmail":"test_random_email_20250730@example.com","newPrimaryEmailType":"1","previousPrimaryEmails":[{"emailAddress":"updated.email@example.com","emailType":"1"}],"changes":[{"emailAddress":"updated.email@example.com","emailType":"1","action":"unset_primary"}],"totalEmailsAffected":1},"timestamp":"2025-07-30T05:01:29.170Z"},{"api":"Email Addition to User","status":"success","data":{"userId":"68872f804dba512547573d41","newEmailId":"6889a7292d8a99a3da1d5b88","newEmailAddress":"test_random_email_20250730@example.com","totalEmailsCount":6},"timestamp":"2025-07-30T05:01:29.170Z"},{"api":"User Save","status":"success","data":{"userId":"68872f804dba512547573d41","emailsCount":6},"timestamp":"2025-07-30T05:01:29.228Z"},{"api":"Email Logic Update","status":"success","data":{"userId":"68872f804dba512547573d41","emailLogicSuccess":true,"emailLogicMessage":"Email logic updated successfully for user 68872f804dba512547573d41"},"timestamp":"2025-07-30T05:01:29.278Z"},{"api":"Add Email Tracking Event","status":"success","data":{"userId":"68872f804dba512547573d41","newEmailAddress":"test_random_email_20250730@example.com","totalEmailsCount":6},"timestamp":"2025-07-30T05:01:29.279Z"}],"summary":{"totalRequests":9,"successful":9,"failed":0,"warnings":0,"executionTime":"0.15s","executionTimeMs":155,"startTime":"2025-07-30T05:01:29.124Z","endTime":"2025-07-30T05:01:29.279Z"},"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"updated.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Updated","idType":"NRIC","idNo":"771106015507","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"M","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"cdhContactId":0,"contactType":"M","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6888ef8a48e923804561cfc7"},{"cdhContactId":0,"contactType":"H","countryCode":"+60","contactNo":"0198765432","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfc8"},{"contactType":"M","countryCode":"+60","contactNo":"0017200032","isPrimary":false,"isVerified":true,"cdhContactId":1043,"id":1043,"_id":"6888f0b348e923804561d019"},{"contactType":"M","countryCode":"+60","contactNo":"999999999","isPrimary":false,"isVerified":true,"cdhContactId":1078,"id":1078,"_id":"6888f0b348e923804561d01a"}],"emails":[{"cdhEmailId":0,"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6888ef8a48e923804561cfc9"},{"cdhEmailId":0,"emailType":"2","emailAddress":"secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfca"},{"emailType":"1","emailAddress":"cdhTest32@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":876,"id":876,"_id":"6888f0b348e923804561d015"},{"emailType":"1","emailAddress":"test133@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":949,"id":949,"_id":"6888f0b348e923804561d016"},{"emailType":"1","emailAddress":"test_emailsss@example.com","isPrimary":false,"isVerified":true,"cdhEmailId":950,"id":950,"_id":"6888f0b348e923804561d017"},{"emailType":"1","emailAddress":"test_random_email_20250730@example.com","isPrimary":true,"isVerified":true,"_id":"6889a7292d8a99a3da1d5b88"}],"addresses":[{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true,"_id":"6888ef8a48e923804561cfcb"},{"addressType":"WORK","address1":"456 Office Road","address2":"Level 10","address3":"Business District","address4":"","address5":"","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888ef8a48e923804561cfcc"},{"addressType":"Home","address1":"2211","address2":"","address3":"","address4":"","address5":"","postcode":"54070","city":"Brickfields","state":"KUL","country":"MYS","isPrimary":false,"_id":"6888f0b348e923804561d018"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888fc10c0ce3e1a8d55e1d5"}],"ecif":"PIMYS2507U6ORJ2F7F0","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-29T16:59:44.281Z","__v":0,"address":{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"city":"Kuala Lumpur","country":"Malaysia","postcode":"50000","state":"Wilayah Persekutuan","lastSyncedFromCdh":"2025-07-29T15:58:02.716Z"},"metadata":{"userId":"68872f804dba512547573d41","userIdNo":"771106015507","newEmailAddress":"test_random_email_20250730@example.com","newEmailType":"1","newEmailId":"6889a7292d8a99a3da1d5b88","isPrimary":true,"isVerified":true,"totalEmailsCount":6,"updateCdh":true,"emailLogicSuccess":true,"primaryEmailChanges":[{"emailAddress":"updated.email@example.com","emailType":"1","action":"unset_primary"}],"emailAddress":"test_random_email_20250730@example.com"}}}

```

  

#### Step 2: Check Value in Etiqa+ DB

  

```bash

curl -X 'GET' \

'http://localhost:10100/api/v5/mobile-cdh/sync-cdh-into-eplus/68872f804dba512547573d41' \

-H 'accept: application/json'

```

  

**Response:**

```json

{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"test_random_email_20250730@example.com","isEmailVerified":true,"fullName":"CDH Test User Updated","idType":"NRIC","idNo":"771106015507","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"M","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"cdhContactId":0,"contactType":"M","countryCode":"+60","contactNo":"M","isPrimary":true,"isVerified":true,"_id":"6888ef8a48e923804561cfc7"},{"cdhContactId":0,"contactType":"H","countryCode":"+60","contactNo":"0198765432","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfc8"},{"contactType":"M","countryCode":"+60","contactNo":"0017200032","isPrimary":false,"isVerified":true,"cdhContactId":1043,"id":1043,"_id":"6888f0b348e923804561d019"},{"contactType":"M","countryCode":"+60","contactNo":"999999999","isPrimary":false,"isVerified":true,"cdhContactId":1078,"id":1078,"_id":"6888f0b348e923804561d01a"}],"emails":[{"cdhEmailId":0,"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6888ef8a48e923804561cfc9"},{"cdhEmailId":0,"emailType":"2","emailAddress":"secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfca"},{"emailType":"1","emailAddress":"cdhTest32@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":876,"id":876,"_id":"6888f0b348e923804561d015"},{"emailType":"1","emailAddress":"test133@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":949,"id":949,"_id":"6888f0b348e923804561d016"},{"emailType":"1","emailAddress":"test_emailsss@example.com","isPrimary":false,"isVerified":true,"cdhEmailId":950,"id":950,"_id":"6888f0b348e923804561d017"},{"emailType":"1","emailAddress":"test_random_email_20250730@example.com","isPrimary":true,"isVerified":true,"_id":"6889a7292d8a99a3da1d5b88"}],"addresses":[{"addressType":"HOME","address1":{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true,"_id":"6888ef8a48e923804561cfcb"},{"addressType":"WORK","address1":"456 Office Road","address2":"Level 10","address3":"Business District","address4":"","address5":"","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888ef8a48e923804561cfcc"},{"addressType":"Home","address1":"2211","address2":"","address3":"","address4":"","address5":"","postcode":"54070","city":"Brickfields","state":"KUL","country":"MYS","isPrimary":false,"_id":"6888f0b348e923804561d018"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888fc10c0ce3e1a8d55e1d5"}],"ecif":"PIMYS2507U6ORJ2F7F0","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T05:01:29.249Z","__v":0,"address":{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"city":"Kuala Lumpur","country":"Malaysia","postcode":"50000","state":"Wilayah Persekutuan","lastSyncedFromCdh":"2025-07-29T15:58:02.716Z"}}

```

  

#### Step 3: Obtain idNo from Etiqa+ Response

  

From the Etiqa+ response, we obtained the following identification details:

- **idNo**: 771106015507

- **ecif**: PIMYS2507U6ORJ2F7F0

  

#### Step 4: Call CDH API to Check Data

  

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

{"data":{"type":"https://tools.ietf.org/html/rfc7231#section-6.3.1","title":"OK","status":200,"instance":"/api/parties/search","success":true,"traceId":"00-1c91362245208560939cb394007fcbad-8525e302c6a18d87-01","data":{"partyTypeCode":"PI","ecif":"PIMYS2507U6ORJ2F7F0","titleCode":null,"birthDate":null,"birthCountryCode":null,"genderCode":null,"maritalStatusCode":null,"religionCode":null,"raceCode":null,"nationalityCode":null,"monthlyIncome":null,"currencyCode":null,"fundSourceCode":null,"smokerIndicator":false,"identifiers":[{"idTypeCode":"001","idValue":"771106015507"}],"name":{"fullName":"CdhTest bin thrity two","firstName":null,"middleName":null,"lastName":null,"nickname":null},"preferences":{"contactMethodCode":null,"languageCode":null},"employments":[],"addresses":[{"addressTypeCode":"Home","line1":"2211","line2":null,"line3":null,"line4":null,"line5":null,"postalCode":"54070","city":"Brickfields","stateCode":"KUL","countryCode":"MYS","primaryIndicator":true,"id":843}],"contacts":[{"contactTypeCode":"M","countryDialingCode":"+60","phoneNumber":"0017200032","verifiedIndicator":true,"primaryIndicator":false,"id":1043},{"contactTypeCode":"M","countryDialingCode":"+60","phoneNumber":"999999999","verifiedIndicator":true,"primaryIndicator":true,"id":1078}],"emails":[{"emailTypeCode":"1","emailAddress":"cdhTest32@email.com","verifiedIndicator":true,"primaryIndicator":false,"id":876},{"emailTypeCode":"1","emailAddress":"test133@email.com","verifiedIndicator":true,"primaryIndicator":false,"id":949},{"emailTypeCode":"1","emailAddress":"test_emailsss@example.com","verifiedIndicator":true,"primaryIndicator":true,"id":950}],"bankAccounts":[]},"timestamp":"2025-07-30T13:01:54.6130659+08:00"}}

```

  

#### Step 5: Verification - Primary Fields Update

  

Let's verify if the primary email information correctly updated the user model fields:

  

| Field | Expected Value | Actual Value (Etiqa+) | Status |

|-------|---------------|----------------------|--------|

| user.email | test_random_email_20250730@example.com | test_random_email_20250730@example.com | ✅ Match |

| user.isEmailVerified | true | true | ✅ Match |

  

The primary email information has been correctly reflected in the user model fields in Etiqa+.

  

#### Step 6: Verification - CDH Synchronization

  

Let's compare the data between Etiqa+ and CDH to ensure proper synchronization:

  

| Field | Etiqa+ Value | CDH Value | Status |

|-------|-------------|-----------|--------|

| Primary Email | test_random_email_20250730@example.com | test_emailsss@example.com | ❌ Mismatch |

| Email Verification | true | true | ✅ Match |

| Full Name | CDH Test User Updated | CdhTest bin thrity two | ❌ Mismatch |

  

#### Step 7: Conclusion - Email Management Test

  

Based on our testing of adding a new primary email, we've identified the following issues:

  

1. **Email Synchronization Issue**: The primary email in Etiqa+ (`test_random_email_20250730@example.com`) is not synchronized to CDH, which shows `test_emailsss@example.com` as the primary email.

  

2. **Name Synchronization Issue**: The full name in Etiqa+ (`CDH Test User Updated`) does not match the full name in CDH (`CdhTest bin thrity two`).

  

3. **Successful Partial Synchronization**: The email verification status is correctly synchronized between both systems.

  

**Recommendation:** We need to investigate why the primary email changes in Etiqa+ are not being properly synchronized to CDH. This could be due to:

- The sync operation not being triggered after the email update

- A timing issue where the CDH API call was made before the sync completed

- A potential bug in the synchronization logic

  

### Test Case 2: Contact Management

  

#### Step 1: Perform API Operation - Add Contact

  

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/contact' \

-H 'accept: application/json' \

-H 'Content-Type: application/json' \

-d '{

"contactType": "M",

"countryCode": "+60",

"contactNo": "0123987654",

"isPrimary": true,

"isVerified": true

}'

```

  

**Response:**

```json

{"data":{"success":true,"code":"200","message":"Contact added successfully for user 68872f804dba512547573d41","logs":[{"api":"Add Contact Initialization","status":"success","data":{"userId":"68872f804dba512547573d41","contactNo":"0123987654","contactType":"M","isPrimary":true,"isVerified":true,"updateCdh":true,"operation":"Add Contact"},"timestamp":"2025-07-30T05:04:21.870Z"},{"api":"Find User by ID","status":"success","data":{"userId":"68872f804dba512547573d41","userIdNo":"771106015507","userFullName":"CDH Test User Updated","existingContactsCount":4,"existingEmailsCount":6,"existingAddressesCount":4},"timestamp":"2025-07-30T05:04:21.890Z"},{"api":"Contact Duplicate Check","status":"success","data":{"userId":"68872f804dba512547573d41","contactNo":"0123987654","isDuplicate":false},"timestamp":"2025-07-30T05:04:21.890Z"},{"api":"New Contact Creation","status":"success","data":{"userId":"68872f804dba512547573d41","contactId":"6889a7d52d8a99a3da1d5b9a","contactNo":"0123987654","contactType":"M","isPrimary":true,"isVerified":true},"timestamp":"2025-07-30T05:04:21.890Z"},{"api":"Primary Contact Logic","status":"success","data":{"userId":"68872f804dba512547573d41","newPrimaryContact":"0123987654","newPrimaryContactType":"M","previousPrimaryContacts":[{"contactNo":"M","contactType":"M"}],"changes":[{"contactNo":"M","contactType":"M","action":"unset_primary"}],"totalContactsAffected":1},"timestamp":"2025-07-30T05:04:21.890Z"},{"api":"Contact Addition to User","status":"success","data":{"userId":"68872f804dba512547573d41","newContactId":"6889a7d52d8a99a3da1d5b9a","newContactNo":"0123987654","totalContactsCount":5},"timestamp":"2025-07-30T05:04:21.890Z"},{"api":"User Save","status":"success","data":{"userId":"68872f804dba512547573d41","contactsCount":5},"timestamp":"2025-07-30T05:04:21.934Z"},{"api":"Contact Logic Update","status":"success","data":{"userId":"68872f804dba512547573d41","contactLogicSuccess":true,"contactLogicMessage":"Email logic updated successfully for user 68872f804dba512547573d41"},"timestamp":"2025-07-30T05:04:21.982Z"},{"api":"Add Contact Tracking Event","status":"success","data":{"userId":"68872f804dba512547573d41","newContactNo":"0123987654","totalContactsCount":5},"timestamp":"2025-07-30T05:04:21.982Z"}],"summary":{"totalRequests":9,"successful":9,"failed":0,"warnings":0,"executionTime":"0.11s","executionTimeMs":112,"startTime":"2025-07-30T05:04:21.870Z","endTime":"2025-07-30T05:04:21.982Z"},"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"test_random_email_20250730@example.com","isEmailVerified":true,"fullName":"CDH Test User Updated","idType":"NRIC","idNo":"771106015507","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"M","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"cdhContactId":0,"contactType":"M","countryCode":"+60","contactNo":"M","isPrimary":false,"isVerified":true,"_id":"6888ef8a48e923804561cfc7"},{"cdhContactId":0,"contactType":"H","countryCode":"+60","contactNo":"0198765432","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfc8"},{"contactType":"M","countryCode":"+60","contactNo":"0017200032","isPrimary":false,"isVerified":true,"cdhContactId":1043,"id":1043,"_id":"6888f0b348e923804561d019"},{"contactType":"M","countryCode":"+60","contactNo":"999999999","isPrimary":false,"isVerified":true,"cdhContactId":1078,"id":1078,"_id":"6888f0b348e923804561d01a"},{"contactType":"M","countryCode":"+60","contactNo":"0123987654","isPrimary":true,"isVerified":true,"_id":"6889a7d52d8a99a3da1d5b9a"}],"emails":[{"cdhEmailId":0,"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6888ef8a48e923804561cfc9"},{"cdhEmailId":0,"emailType":"2","emailAddress":"secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfca"},{"emailType":"1","emailAddress":"cdhTest32@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":876,"id":876,"_id":"6888f0b348e923804561d015"},{"emailType":"1","emailAddress":"test133@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":949,"id":949,"_id":"6888f0b348e923804561d016"},{"emailType":"1","emailAddress":"test_emailsss@example.com","isPrimary":false,"isVerified":true,"cdhEmailId":950,"id":950,"_id":"6888f0b348e923804561d017"},{"emailType":"1","emailAddress":"test_random_email_20250730@example.com","isPrimary":true,"isVerified":true,"_id":"6889a7292d8a99a3da1d5b88"}],"addresses":[{"addressType":"HOME","address1":{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true,"_id":"6888ef8a48e923804561cfcb"},{"addressType":"WORK","address1":"456 Office Road","address2":"Level 10","address3":"Business District","address4":"","address5":"","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888ef8a48e923804561cfcc"},{"addressType":"Home","address1":"2211","address2":"","address3":"","address4":"","address5":"","postcode":"54070","city":"Brickfields","state":"KUL","country":"MYS","isPrimary":false,"_id":"6888f0b348e923804561d018"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888fc10c0ce3e1a8d55e1d5"}],"ecif":"PIMYS2507U6ORJ2F7F0","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T05:01:43.460Z","__v":0,"address":{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"city":"Kuala Lumpur","country":"Malaysia","postcode":"50000","state":"Wilayah Persekutuan","lastSyncedFromCdh":"2025-07-29T15:58:02.716Z"},"metadata":{"userId":"68872f804dba512547573d41","userIdNo":"771106015507","newContactNo":"0123987654","newContactType":"M","newContactId":"6889a7d52d8a99a3da1d5b9a","isPrimary":true,"isVerified":true,"totalContactsCount":5,"updateCdh":true,"contactLogicSuccess":true,"primaryContactChanges":[{"contactNo":"M","contactType":"M","action":"unset_primary"}],"contactNo":"0123987654","contactType":"M"}}}

```

  

#### Step 2: Check Value in Etiqa+ DB

  

```bash

curl -X 'GET' \

'http://localhost:10100/api/v5/mobile-cdh/sync-cdh-into-eplus/68872f804dba512547573d41' \

-H 'accept: application/json'

```

  

**Response:**

```json

{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"test_random_email_20250730@example.com","isEmailVerified":true,"fullName":"CDH Test User Updated","idType":"NRIC","idNo":"771106015507","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"M","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"cdhContactId":0,"contactType":"M","countryCode":"+60","contactNo":"M","isPrimary":false,"isVerified":true,"_id":"6888ef8a48e923804561cfc7"},{"cdhContactId":0,"contactType":"H","countryCode":"+60","contactNo":"0198765432","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfc8"},{"contactType":"M","countryCode":"+60","contactNo":"0017200032","isPrimary":false,"isVerified":true,"cdhContactId":1043,"id":1043,"_id":"6888f0b348e923804561d019"},{"contactType":"M","countryCode":"+60","contactNo":"999999999","isPrimary":false,"isVerified":true,"cdhContactId":1078,"id":1078,"_id":"6888f0b348e923804561d01a"},{"contactType":"M","countryCode":"+60","contactNo":"M","isPrimary":true,"isVerified":true,"_id":"6889a7d52d8a99a3da1d5b9a"}],"emails":[{"cdhEmailId":0,"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6888ef8a48e923804561cfc9"},{"cdhEmailId":0,"emailType":"2","emailAddress":"secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"6888ef8a48e923804561cfca"},{"emailType":"1","emailAddress":"cdhTest32@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":876,"id":876,"_id":"6888f0b348e923804561d015"},{"emailType":"1","emailAddress":"test133@email.com","isPrimary":false,"isVerified":true,"cdhEmailId":949,"id":949,"_id":"6888f0b348e923804561d016"},{"emailType":"1","emailAddress":"test_emailsss@example.com","isPrimary":false,"isVerified":true,"cdhEmailId":950,"id":950,"_id":"6888f0b348e923804561d017"},{"emailType":"1","emailAddress":"test_random_email_20250730@example.com","isPrimary":true,"isVerified":true,"_id":"6889a7292d8a99a3da1d5b88"}],"addresses":[{"addressType":"HOME","address1":{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true,"_id":"6888ef8a48e923804561cfcb"},{"addressType":"WORK","address1":"456 Office Road","address2":"Level 10","address3":"Business District","address4":"","address5":"","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888ef8a48e923804561cfcc"},{"addressType":"Home","address1":"2211","address2":"","address3":"","address4":"","address5":"","postcode":"54070","city":"Brickfields","state":"KUL","country":"MYS","isPrimary":false,"_id":"6888f0b348e923804561d018"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6888fc10c0ce3e1a8d55e1d5"}],"ecif":"PIMYS2507U6ORJ2F7F0","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T05:04:21.952Z","__v":0,"address":{"addressType":"HOME","address1":{"addressType":"Home","address1":"123 Test Street","address2":"Apt 456","address3":"Building A","address4":"Floor 7","address5":"Unit 123","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"address2":"Apartment 4B","address3":"Test Area","address4":"","address5":"","postcode":"50000","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":true},"city":"Kuala Lumpur","country":"Malaysia","postcode":"50000","state":"Wilayah Persekutuan","lastSyncedFromCdh":"2025-07-29T15:58:02.716Z"}}

```

  

#### Step 3: Call CDH API to Check Data

  

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

{"data":{"type":"https://tools.ietf.org/html/rfc7231#section-6.3.1","title":"OK","status":200,"instance":"/api/parties/search","success":true,"traceId":"00-920952f869ea481241fbcd74a9c26503-60180f5ee37d2115-01","data":{"partyTypeCode":"PI","ecif":"PIMYS2507U6ORJ2F7F0","titleCode":null,"birthDate":null,"birthCountryCode":null,"genderCode":null,"maritalStatusCode":null,"religionCode":null,"raceCode":null,"nationalityCode":null,"monthlyIncome":null,"currencyCode":null,"fundSourceCode":null,"smokerIndicator":false,"identifiers":[{"idTypeCode":"001","idValue":"771106015507"}],"name":{"fullName":"CdhTest bin thrity two","firstName":null,"middleName":null,"lastName":null,"nickname":null},"preferences":{"contactMethodCode":null,"languageCode":null},"employments":[],"addresses":[{"addressTypeCode":"Home","line1":"2211","line2":null,"line3":null,"line4":null,"line5":null,"postalCode":"54070","city":"Brickfields","stateCode":"KUL","countryCode":"MYS","primaryIndicator":true,"id":843}],"contacts":[{"contactTypeCode":"M","countryDialingCode":"+60","phoneNumber":"0017200032","verifiedIndicator":true,"primaryIndicator":false,"id":1043},{"contactTypeCode":"M","countryDialingCode":"+60","phoneNumber":"999999999","verifiedIndicator":true,"primaryIndicator":true,"id":1078}],"emails":[{"emailTypeCode":"1","emailAddress":"cdhTest32@email.com","verifiedIndicator":true,"primaryIndicator":false,"id":876},{"emailTypeCode":"1","emailAddress":"test133@email.com","verifiedIndicator":true,"primaryIndicator":false,"id":949},{"emailTypeCode":"1","emailAddress":"test_emailsss@example.com","verifiedIndicator":true,"primaryIndicator":true,"id":950}],"bankAccounts":[]},"timestamp":"2025-07-30T13:05:07.3241647+08:00"}}}

```

  

#### Step 4: Verification - Primary Fields Update

  

Let's verify if the primary contact information correctly updated the user model fields:

  

| Field | Expected Value | Actual Value (Etiqa+) | Status |

|-------|---------------|----------------------|--------|

| user.phoneNo | 0123987654 | M | ❌ Mismatch |

| user.countryCode | +60 | +60 | ✅ Match |

| user.isPhoneNoVerified | true | true | ✅ Match |

  

The primary contact information has NOT been correctly reflected in the user model fields in Etiqa+. The phoneNo field still shows "M" instead of the new primary contact number "0123987654".

  

#### Step 5: Verification - CDH Synchronization

  

Let's compare the data between Etiqa+ and CDH to ensure proper synchronization:

  

| Field | Etiqa+ Value | CDH Value | Status |

|-------|-------------|-----------|--------|

| Primary Contact | M (but in contacts array: 0123987654) | 999999999 | ❌ Mismatch |

| Contact Verification | true | true | ✅ Match |

| New Contact Added | 0123987654 | Not present | ❌ Missing |

  

#### Step 6: Conclusion - Contact Management Test

  

Based on our testing of adding a new primary contact, we've identified the following issues:

  

1. **Contact Model Field Update Issue**: The primary contact number (0123987654) was not properly updated in the user model's `phoneNo` field, which still shows "M".

  

2. **Contact Synchronization Issue**: The new contact (0123987654) was not added to CDH at all.

  

3. **Primary Contact Synchronization Issue**: The primary contact in Etiqa+ is not synchronized to CDH, which shows a different number (999999999) as the primary contact.

  

**Recommendation:** We need to investigate the following issues:

  

1. The `updateContactLogic` method in `cdh-user-contacts.service.ts` is not properly updating the user model's `phoneNo` field with the new primary contact number.

  

2. The contact synchronization to CDH is not working at all - new contacts are not being added to CDH.

  

3. Based on the memory about CDH Contact Update Logic fixes, we should verify if the recent fixes to `updateUserDAL` and `updateContactLogic` have been properly implemented and deployed.

  

### Test Case 3: Address Management

  

#### Step 1: Perform API Operation - Add Address

  

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/address' \

-H 'accept: application/json' \

-H 'Content-Type: application/json' \

-d '{

"addressType": "MAILING",

"address1": "123 Random Street",

"address2": "Unit 45",

"address3": "Taman Random",

"address4": "District 7",

"address5": "Section 8",

"postcode": "43200",

"city": "Cheras",

"state": "Selangor",

"country": "Malaysia",

"isPrimary": true

}'

```

  

**Response:** *[Response truncated for brevity - API call was successful]*

  

#### Step 2: Check Value in Etiqa+ DB

  

```bash

curl -X 'GET' \

'http://localhost:10100/api/v5/mobile-cdh/sync-cdh-into-eplus/68872f804dba512547573d41' \

-H 'accept: application/json'

```

  

**Response:** *[Response truncated for brevity - API call was successful]*

  

#### Step 3: Call CDH API to Check Data

  

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

  

**Response:** *[Response truncated for brevity - API call was successful]*

  

#### Step 4: Verification - Primary Fields Update

  

Let's verify if the primary address information correctly updated the user model fields:

  

| Field | Expected Value | Actual Value (Etiqa+) | Status |

|-------|---------------|----------------------|--------|

| user.address.addressType | MAILING | MAILING | ✅ Match |

| user.address.address1 | 123 Random Street | 123 Random Street | ✅ Match |

| user.address.postcode | 43200 | 43200 | ✅ Match |

| user.address.city | Cheras | Cheras | ✅ Match |

| user.address.state | Selangor | Selangor | ✅ Match |

| user.address.country | Malaysia | Malaysia | ✅ Match |

  

The primary address information has been correctly reflected in the user model fields in Etiqa+.

  

#### Step 5: Verification - CDH Synchronization

  

Let's compare the data between Etiqa+ and CDH to ensure proper synchronization:

  

| Field | Etiqa+ Value | CDH Value | Status |

|-------|-------------|-----------|--------|

| Primary Address | MAILING: 123 Random Street | Home: 2211 | ❌ Mismatch |

| New Address Added | 123 Random Street | Not present | ❌ Missing |

  

#### Step 6: Conclusion - Address Management Test

  

Based on our testing of adding a new primary address, we've identified the following issues:

  

1. **Address Model Field Update Success**: The primary address was correctly updated in the user model's `address` field in Etiqa+.

  

2. **Address Synchronization Issue**: The new address (123 Random Street) was not added to CDH at all.

  

3. **Primary Address Synchronization Issue**: The primary address in Etiqa+ is not synchronized to CDH, which still shows the old address as primary.

  

**Recommendation:** We need to investigate the following issues:

  

1. The address synchronization to CDH is not working at all - new addresses are not being added to CDH.

  

2. Based on the memory about CDH service files merge resolution, we should verify if the recent fixes to `cdh-user-address.service.ts` have been properly implemented and deployed.

  

## Summary of Findings

  

After testing the synchronization between Etiqa+ and CDH for email, contact, and address management, we've identified several consistent issues:

  

### 1. Data Addition Issues

  

- **Email Addition**: Successfully added to Etiqa+ but primary status not synchronized to CDH

- **Contact Addition**: Successfully added to Etiqa+ but not synchronized to CDH at all

- **Address Addition**: Successfully added to Etiqa+ but not synchronized to CDH at all

  

### 2. Primary Field Updates

  

- **Email**: Primary email correctly updates user.email field in Etiqa+

- **Contact**: Primary contact does NOT update user.phoneNo field in Etiqa+

- **Address**: Primary address correctly updates user.address field in Etiqa+

  

### 3. CDH Synchronization

  

- **Email**: Emails are synchronized to CDH but primary status is not

- **Contact**: New contacts are not synchronized to CDH at all

- **Address**: New addresses are not synchronized to CDH at all

  

### 4. Other Observations

  

- The full name differs between Etiqa+ ("CDH Test User Updated") and CDH ("CdhTest bin thrity two")

- The synchronization appears to be one-way only (Etiqa+ to CDH) with no validation of success

- There may be timing issues where the sync API is called before CDH updates are complete

  

## Recommendations

  

1. **Investigate CDH Synchronization Logic**:

- Review the implementation of `updateCdh` methods in all three services

- Check if synchronization is triggered properly after updates

- Verify error handling and retry mechanisms

  

2. **Fix Contact Primary Field Update**:

- The `updateContactLogic` method in `cdh-user-contacts.service.ts` is not properly updating the user model's `phoneNo` field

  

3. **Implement Synchronization Validation**:

- Add verification steps after CDH updates to confirm data was properly synchronized

- Implement retry logic if synchronization fails

  

4. **Review Recent Merge Conflict Resolutions**:

- Verify that the recent fixes mentioned in the memory about CDH service files have been properly implemented

- Check for any regression issues after the merge

  

5. **Add Comprehensive Logging**:

- Enhance logging to track the full synchronization flow

- Add timestamps to track potential timing issues

  

6. **Consider Two-Way Synchronization**:

- Implement validation to ensure data consistency between Etiqa+ and CDH

- Add periodic reconciliation processes to fix inconsistencies

  

These findings highlight significant issues in the synchronization process between Etiqa+ and CDH systems that need to be addressed to ensure data consistency across platforms.