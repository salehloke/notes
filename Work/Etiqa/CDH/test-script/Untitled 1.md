# CDH-Etiqa+ Backoffice Synchronization Test Results

**Test Execution Time:** Thu Jul 31 01:01:42 +08 2025
**Test Environment:** http://localhost:11400
**Test User ID:** 68872f804dba512547573d41

## Test Summary

This document contains the results of automated CDH-Etiqa+ backoffice synchronization tests.

## Test Cases Executed

1. **Test Case 1:** Email Update and Synchronization
2. **Test Case 2:** Contact Update and Synchronization  
3. **Test Case 3:** Address Update and Synchronization
4. **Test Case 4:** Multiple Updates and Primary Designation
5. **Test Case 5:** Update verification status

---

## Test Case: Email-Update-Verified

### Test Configuration
- Email Verification: true
- Phone Verification: false

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Email-Update-Verified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894905",
  "email": "test-Email-Update-Verified-1753894905@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894905",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Email-Update-Verified-1753894905@example.com",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T16:51:10.785Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
```json
[1;33mUpdating user data for test: Email-Update-Verified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:45.575Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Email-Update-Verified Analysis

### Verification Status
| Field | Value | Expected | Status |
|-------|-------|----------|--------|
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |

### Raw Values
- Root-level isEmailVerified: true
- Root-level isPhoneNoVerified: true
- Contacts array isVerified: true
true
true
false
false
- Emails array isVerified: true
true
false
true
false

---

## Test Case: Email-Update-Verified

### Test Configuration
- Email Verification: true
- Phone Verification: false

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Email-Update-Verified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894905",
  "email": "test-Email-Update-Verified-1753894905@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894905",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Email-Update-Verified-1753894905@example.com",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T16:51:10.785Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
```json
[1;33mUpdating user data for test: Email-Update-Verified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:45.575Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Email-Update-Verified Analysis

### Verification Status
| Field | Value | Expected | Status |
|-------|-------|----------|--------|
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |

### Raw Values
- Root-level isEmailVerified: true
- Root-level isPhoneNoVerified: true
- Contacts array isVerified: true
true
true
false
false
- Emails array isVerified: true
true
false
true
false

---

## Test Case: Contact-Update-Verified

### Test Configuration
- Email Verification: false
- Phone Verification: true

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Contact-Update-Verified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894908",
  "email": "test-Contact-Update-Verified-1753894908@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894908",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Contact-Update-Verified-1753894908@example.com",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:47.384Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
```json
[1;33mUpdating user data for test: Contact-Update-Verified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:49.115Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Test Case: Contact-Update-Verified

### Test Configuration
- Email Verification: false
- Phone Verification: true

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Contact-Update-Verified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894909",
  "email": "test-Contact-Update-Verified-1753894909@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894909",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Contact-Update-Verified-1753894909@example.com",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:47.384Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
```json
[1;33mUpdating user data for test: Contact-Update-Verified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:49.115Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Contact-Update-Verified Analysis

### Verification Status
| Field | Value | Expected | Status |
|-------|-------|----------|--------|
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |
## Contact-Update-Verified Analysis


### Raw Values
### Verification Status
- Root-level isEmailVerified: true
| Field | Value | Expected | Status |
- Root-level isPhoneNoVerified: true
|-------|-------|----------|--------|
- Contacts array isVerified: true
true
true
false
false
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
- Emails array isVerified: true
true
false
true
false
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |


---
### Raw Values

- Root-level isEmailVerified: true
- Root-level isPhoneNoVerified: true
- Contacts array isVerified: true
true
true
false
false
- Emails array isVerified: true
true
false
true
false

---

## Test Case: Address-Update-Unverified

### Test Configuration
- Email Verification: false
- Phone Verification: false

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Address-Update-Unverified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894911",
  "email": "test-Address-Update-Unverified-1753894911@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894911",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Address-Update-Unverified-1753894911@example.com",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:49.938Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
```json
[1;33mUpdating user data for test: Address-Update-Unverified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:51.505Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Test Case: Address-Update-Unverified

### Test Configuration
- Email Verification: false
- Phone Verification: false

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
## Address-Update-Unverified Analysis
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \

  -H "Content-Type: application/json" \
### Verification Status
  -H "Authorization: Bearer $AUTH_TOKEN" \
| Field | Value | Expected | Status |
  -d '{
  "username": "testUser40",
  "fullName": "Test User Address-Update-Unverified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894911",
  "email": "test-Address-Update-Unverified-1753894911@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
|-------|-------|----------|--------|
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894911",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Address-Update-Unverified-1753894911@example.com",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
```
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |


### API Responses
### Raw Values
#### Initial Response
- Root-level isEmailVerified: true
```json
- Root-level isPhoneNoVerified: true
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:49.938Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
- Contacts array isVerified: true
true
true
false
false
```
- Emails array isVerified: true
true
false
true
false


#### Update Response
---
```json

[1;33mUpdating user data for test: Address-Update-Unverified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:51.505Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Address-Update-Unverified Analysis

### Verification Status
| Field | Value | Expected | Status |
|-------|-------|----------|--------|
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |

### Raw Values
- Root-level isEmailVerified: true
- Root-level isPhoneNoVerified: true
- Contacts array isVerified: true
true
true
false
false
- Emails array isVerified: true
true
false
true
false

---

## Test Case: Multiple-Updates-Verified

### Test Configuration
- Email Verification: true
- Phone Verification: true

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Multiple-Updates-Verified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894916",
  "email": "test-Multiple-Updates-Verified-1753894916@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894916",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Multiple-Updates-Verified-1753894916@example.com",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:53.932Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
```json
[1;33mUpdating user data for test: Multiple-Updates-Verified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
## Test Case: Multiple-Updates-Verified

[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:56.066Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
### Test Configuration
```
- Email Verification: true

- Phone Verification: true

### API Requests
#### Initial Data Request
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
```

#### Update Request
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Multiple-Updates-Verified",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894916",
  "email": "test-Multiple-Updates-Verified-1753894916@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894916",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Multiple-Updates-Verified-1753894916@example.com",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:53.932Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
```json
[1;33mUpdating user data for test: Multiple-Updates-Verified[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```

#### Updated Data Response
```json
[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:56.066Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Multiple-Updates-Verified Analysis

### Verification Status
| Field | Value | Expected | Status |
|-------|-------|----------|--------|
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |

### Raw Values
- Root-level isEmailVerified: true
- Root-level isPhoneNoVerified: true
- Contacts array isVerified: true
true
true
false
false
- Emails array isVerified: true
true
false
true
false

---
## Multiple-Updates-Verified Analysis


### Verification Status
| Field | Value | Expected | Status |
|-------|-------|----------|--------|
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |

### Raw Values
- Root-level isEmailVerified: true
- Root-level isPhoneNoVerified: true
- Contacts array isVerified: true
true
true
false
false
- Emails array isVerified: true
true
false
true
false

---

## Test Case: Verification-Status-Mixed
## Test Case: Verification-Status-Mixed


### Test Configuration
### Test Configuration
- Email Verification: true
- Email Verification: true
- Phone Verification: false
- Phone Verification: false


### API Requests
### API Requests
#### Initial Data Request
#### Initial Data Request
```bash
```bash
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
curl -X GET "http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41" \
  -H "Authorization: Bearer $AUTH_TOKEN"
  -H "Authorization: Bearer $AUTH_TOKEN"
```
```


#### Update Request
#### Update Request
```bash
```bash
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
curl -X PUT "http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $AUTH_TOKEN" \
  -d '{
  "username": "testUser40",
  "fullName": "Test User Verification-Status-Mixed",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894918",
  "email": "test-Verification-Status-Mixed-1753894918@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894918",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Verification-Status-Mixed-1753894918@example.com",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
  -d '{
  "username": "testUser40",
  "fullName": "Test User Verification-Status-Mixed",
  "idType": "NRIC",
  "idNo": "000522055323",
  "registrationIdNo": "000522055323",
  "countryCode": "+60",
  "phoneNo": "0172099-1753894918",
  "email": "test-Verification-Status-Mixed-1753894918@example.com",
  "pfNo": "",
  "activePolicyNo": "",
  "ecif": "PIMYS2507WRA9DE92FE",
  "isMeVerified": false,
  "isMCSVerified": false,
  "isWellnessEnrolled": false,
  "skipAgentChecking": false,
  "id": "68872f804dba512547573d41",
  "contacts": [
    {
      "cdhContactId": 1112,
      "contactType": "M",
      "countryCode": "+60",
      "contactNo": "0172099-1753894918",
      "isPrimary": true,
      "isVerified": false,
      "_id": "6889f5491d67183d970e4126"
    }
  ],
  "emails": [
    {
      "cdhEmailId": 968,
      "emailType": "1",
      "emailAddress": "test-Verification-Status-Mixed-1753894918@example.com",
      "isPrimary": true,
      "isVerified": true,
      "_id": "6889f5491d67183d970e4127"
    }
  ],
  "addresses": []
}'
```

```
### API Responses

#### Initial Response
```json
### API Responses
#### Initial Response
```json
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:56.786Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

#### Update Response
[1;33mGetting initial user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:56.786Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```json
```
[1;33mUpdating user data for test: Verification-Status-Mixed[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}

```
#### Update Response

```json
#### Updated Data Response
[1;33mUpdating user data for test: Verification-Status-Mixed[0m
{"statusCode":403,"errorCode":"JWT.INVALID","message":"Invalid token signature."}
```json
```

[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:57.918Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
#### Updated Data Response
```
```json

[1;33mGetting updated user data...[0m
{"data":{"_id":"68872f804dba512547573d41","username":"CdhTest32","email":"retest.primary.email@example.com","isEmailVerified":true,"fullName":"CDH Test User Retest January 30","idType":"NRIC","idNo":"771106015599","registrationIdNo":"771106015507","countryCode":"+60","phoneNo":"0123456789","isPhoneNoVerified":true,"password":"","secretWord":"testCdh32","avatar":null,"activePolicyNo":"","isMcsVerified":false,"isMeVerified":false,"isWellnessEnrolled":false,"staffInfo":null,"identityInfo":{"smileUuid":null,"cwpId":null},"legacyProfiles":[],"isAccountLocked":false,"accountStatusReason":"","passwordHistories":[],"lastLogin":null,"dateBlockUntil":"2025-07-27T08:06:24.448Z","listOfDeviceDetail":[],"isAccountDeleted":false,"fieldChangesHistories":[],"isMultiSession":false,"skipAgentChecking":false,"isCrashDetectionEnabled":false,"contacts":[{"contactType":"M","countryCode":"+60","contactNo":"0172222232","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422b"},{"contactType":"H","countryCode":"+60","contactNo":"0123456789","isPrimary":true,"isVerified":true,"_id":"6889fc331d67183d970e422c"},{"contactType":"M","countryCode":"+60","contactNo":"0173456789","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422d"},{"contactType":"M","countryCode":"+60","contactNo":"172044342","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423f","id":1077},{"contactType":"O","countryCode":"+60","contactNo":"0312345678","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6a"}],"emails":[{"emailType":"1","emailAddress":"updated.email@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422e"},{"emailType":"1","emailAddress":"test_email_20250730_2348@example.com","isPrimary":false,"isVerified":true,"_id":"6889fc331d67183d970e422f"},{"emailType":"1","emailAddress":"test@emaillll.com","isPrimary":false,"isVerified":false,"_id":"6889fc4a1d67183d970e423e"},{"emailType":"1","emailAddress":"retest.primary.email@example.com","isPrimary":true,"isVerified":true,"_id":"688a435d1be5272f3016df6b"},{"emailType":"2","emailAddress":"retest.secondary.email@example.com","isPrimary":false,"isVerified":false,"_id":"688a435d1be5272f3016df6c"}],"addresses":[{"addressType":"Home","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4230"},{"addressType":"Office","address1":"789 Business Park","address2":"Suite 123","address3":"Business District","address4":"Tower B","address5":"Level 5","postcode":"50470","city":"Kuala Lumpur","state":"Wilayah Persekutuan","country":"Malaysia","isPrimary":false,"_id":"6889fc331d67183d970e4231"},{"addressType":"H","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true,"_id":"688a435d1be5272f3016df6d"}],"ecif":"PIMYS2507V0HL39034D","emergencyContacts":[],"createdAt":"2025-07-28T08:06:24.651Z","updatedAt":"2025-07-30T17:01:57.918Z","__v":0,"address":{"addressType":"MAILING","address1":"123 Random Street","address2":"Unit 45","address3":"Taman Random","address4":"District 7","address5":"Section 8","postcode":"43200","city":"Cheras","state":"Selangor","country":"Malaysia","isPrimary":true},"city":"Cheras","country":"Malaysia","postcode":"43200","state":"Selangor","lastSyncedFromCdh":"2025-07-30T16:07:57.111Z"}}
```

## Verification-Status-Mixed Analysis
## Verification-Status-Mixed Analysis


### Verification Status
### Verification Status
| Field | Value | Expected | Status |
| Field | Value | Expected | Status |
|-------|-------|----------|--------|
|-------|-------|----------|--------|
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Email Verified | true | true
true
false
true
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |
| Root Phone Verified | true | true
true
true
false
false | ❌ Mismatch |


### Raw Values
### Raw Values
- Root-level isEmailVerified: true
- Root-level isEmailVerified: true
- Root-level isPhoneNoVerified: true
- Root-level isPhoneNoVerified: true
- Contacts array isVerified: true
- Contacts array isVerified: true
true
true
true
true
false
false
false
false
- Emails array isVerified: true
- Emails array isVerified: true
true
true
false
true
false
false
true
false


---
---


## Test Summary
## Test Summary


### Verification Checklist
### Verification Checklist


- [ ] Primary email updates user.email
- [ ] Primary email updates user.email
- [ ] Primary contact updates user.phoneNo and user.countryCode
- [ ] Primary contact updates user.phoneNo and user.countryCode
- [ ] Primary address updates user.address
- [ ] Primary address updates user.address
- [ ] Verification status properly updates user.isPhoneNoVerified and user.isEmailVerified
- [ ] Verification status properly updates user.isPhoneNoVerified and user.isEmailVerified
- [ ] Only one primary item exists in each category
- [ ] Only one primary item exists in each category
- [ ] All updates from Etiqa+ are synchronized with CDH
- [ ] All updates from Etiqa+ are synchronized with CDH
- [ ] All data from CDH is correctly reflected in Etiqa+
- [ ] All data from CDH is correctly reflected in Etiqa+
- [ ] Verify that each value is able to be updated
- [ ] Verify that each value is able to be updated
- [ ] Verify that each contact value in the contacts array has cdhContactId after sync to CDH
- [ ] Verify that each contact value in the contacts array has cdhContactId after sync to CDH
- [ ] Verify that each email value in the emails array has cdhEmailId after sync to CDH
- [ ] Verify that each email value in the emails array has cdhEmailId after sync to CDH
- [ ] Verify that each address value in the addresses array has cdhAddressId after sync to CDH
- [ ] Verify that each address value in the addresses array has cdhAddressId after sync to CDH


### Test Execution Log
### Test Execution Log


Full test execution log can be found in: test-results/test-execution.log
Full test execution log can be found in: test-results/test-execution.log


### Next Steps
### Next Steps


1. Review the verification status analysis for each test case
2. Review the verification status analysis for each test case
3. Check for any ❌ Mismatch statuses in the results
4. Check for any ❌ Mismatch statuses in the results
5. Verify that all checklist items are properly tested
6. Verify that all checklist items are properly tested
7. If issues are found, investigate the root cause and implement fixes
8. If issues are found, investigate the root cause and implement fixes


