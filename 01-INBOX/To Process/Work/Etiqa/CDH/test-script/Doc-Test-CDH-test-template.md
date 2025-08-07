# CDH-Etiqa+ Synchronization Test Result

  

## Test Information

- **Test Date**: YYYY-MM-DD

- **Test ID**: TEST-CDH-SYNC-001

- **User ID**: 68872f804dba512547573d41

- **Test Case**: [Email/Contact/Address/Multiple] Update and Synchronization

  

## Initial Data

### Step 1: Initial User Data from CDH

```json

{

"user": {

"fullName": "Initial Full Name",

"email": "initial@email.com",

"phoneNo": "1234567890",

"countryCode": "+60",

"isPhoneNoVerified": false,

"isEmailVerified": false,

"contacts": [

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "1234567890",

"isPrimary": true,

"isVerified": false

}

],

"emails": [

{

"emailType": "1",

"emailAddress": "initial@email.com",

"isPrimary": true,

"isVerified": false

}

],

"addresses": [

{

"addressType": "Home",

"address1": "Initial Address Line 1",

"postcode": "10000",

"city": "Initial City",

"state": "Initial State",

"country": "MYS",

"isPrimary": true

}

]

}

}

```

  

## Test Execution

### Step 2: Update User Data

**Request:**

```json

{

"fullName": "Updated Full Name",

"countryCode": "+60",

"phoneNo": "9876543210",

"email": "updated@email.com",

"contacts": [

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "1234567890",

"isPrimary": false,

"isVerified": false

},

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "9876543210",

"isPrimary": true,

"isVerified": true

}

],

"emails": [

{

"emailType": "1",

"emailAddress": "initial@email.com",

"isPrimary": false,

"isVerified": false

},

{

"emailType": "1",

"emailAddress": "updated@email.com",

"isPrimary": true,

"isVerified": true

}

],

"addresses": [

{

"addressType": "Home",

"address1": "Updated Address Line 1",

"postcode": "20000",

"city": "Updated City",

"state": "Updated State",

"country": "MYS",

"isPrimary": true

}

]

}

```

  

**Response:**

```json

{

"status": 200,

"message": "User updated successfully",

"data": {

// Include relevant response data

}

}

```

  

### Step 3: Trigger CDH Synchronization

**Request:**

```

POST http://localhost:11400/api/backoffice/portal-user/68872f804dba512547573d41/cdh-sync

```

  

**Response:**

```json

{

"status": 200,

"message": "Data synchronized with CDH successfully",

"data": {

// Include relevant response data

}

}

```

  

### Step 4: Verify Synchronization

**Request:**

```

GET http://localhost:11400/api/backoffice/portal-user/sync-cdh-into-eplus/68872f804dba512547573d41

```

  

**Response:**

```json

{

"user": {

"fullName": "Updated Full Name",

"email": "updated@email.com",

"phoneNo": "9876543210",

"countryCode": "+60",

"isPhoneNoVerified": true,

"isEmailVerified": true,

"contacts": [

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "1234567890",

"isPrimary": false,

"isVerified": false

},

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "9876543210",

"isPrimary": true,

"isVerified": true

}

],

"emails": [

{

"emailType": "1",

"emailAddress": "initial@email.com",

"isPrimary": false,

"isVerified": false

},

{

"emailType": "1",

"emailAddress": "updated@email.com",

"isPrimary": true,

"isVerified": true

}

],

"addresses": [

{

"addressType": "Home",

"address1": "Updated Address Line 1",

"postcode": "20000",

"city": "Updated City",

"state": "Updated State",

"country": "MYS",

"isPrimary": true

}

]

}

}

```

  

## Verification Results

| Field | Before | After | Verified |

|-------|--------|-------|----------|

| user.fullName | Initial Full Name | Updated Full Name | ✅ |

| user.email | initial@email.com | updated@email.com | ✅ |

| user.phoneNo | 1234567890 | 9876543210 | ✅ |

| user.countryCode | +60 | +60 | ✅ |

| user.isPhoneNoVerified | false | true | ✅ |

| user.isEmailVerified | false | true | ✅ |

| Primary email | initial@email.com | updated@email.com | ✅ |

| Primary contact | 1234567890 | 9876543210 | ✅ |

| Primary address | Initial Address Line 1 | Updated Address Line 1 | ✅ |

  

## Verification Checklist

- [x] Primary email updates user.email

- [x] Primary contact updates user.phoneNo and user.countryCode

- [x] Primary address updates user.address

- [x] Verification status properly updates user.isPhoneNoVerified and user.isEmailVerified

- [x] Only one primary item exists in each category

- [x] All updates from Etiqa+ are synchronized with CDH

- [x] All data from CDH is correctly reflected in Etiqa+

  

## Notes

- Add any observations, issues, or additional information here

- Document any unexpected behavior or edge cases encountered

- Include recommendations for improvements if applicable