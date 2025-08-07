# Mobile CDH Address API Testing Documentation

  

## Overview

This document contains test results for the Mobile CDH Address API endpoints that were refactored to use `userId` (MongoDB ObjectId) instead of `userIdNo` (business identifier). The refactoring ensures consistent parameter usage across all controller routes, method signatures, service calls, and internal logic.

  

## Test Environment

- **Backend**: NestJS v9.4.0

- **Database**: MongoDB v6.1.0

- **Test User**:

- MongoDB ObjectId: `68872f804dba512547573d41`

- ID Number: `771106015507`

- Name: `CdhTest bin thrity two`

  

## Test Cases and Results

  

### Address Endpoints

  

#### 1. GET /:userId/addresses

- **Endpoint**: `GET /api/v5/mobile-cdh/68872f804dba512547573d41/addresses`

- **Description**: Retrieves all addresses for a user

- **Test Command**:

```bash

curl -X 'GET' 'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/addresses' -H 'accept: */*'

```

- **Response**:

```json

{

"data": {

"success": true,

"code": "ADDRESSES_RETRIEVED",

"message": "Addresses retrieved successfully",

"logs": [

{

"api": "Addresses Retrieved Successfully",

"status": "success",

"data": {

"userId": "68872f804dba512547573d41",

"addressCount": 2

},

"timestamp": "2025-07-28T17:22:33.967Z"

}

],

"summary": {

"totalRequests": 1,

"successful": 1,

"failed": 0,

"warnings": 0,

"executionTime": "0.33s",

"executionTimeMs": 326,

"startTime": "2025-07-28T17:22:33.641Z",

"endTime": "2025-07-28T17:22:33.967Z"

},

"data": [

{

"addressType": "Home",

"address1": "2211",

"address2": null,

"address3": null,

"address4": null,

"address5": null,

"postcode": "54070",

"city": "Brickfields",

"state": "KUL",

"country": "MYS",

"isPrimary": false,

"_id": "68872f804dba512547573d40"

},

{

"addressType": "Office",

"address1": "789 Business Park",

"address2": "Building A",

"postcode": "50200",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true,

"_id": "6887b03e1ff9cec29bab2e76"

}

],

"metadata": {

"userId": "68872f804dba512547573d41",

"addressCount": 2

}

}

}

```

- **Result**: ✅ SUCCESS - Endpoint correctly accepts `userId` parameter and returns addresses data with proper metadata.

- **Observations**:

- The endpoint correctly accepts the MongoDB ObjectId as `userId` parameter

- The response includes proper logging with the `userId` in the logs

- The metadata correctly includes the `userId` field

- The response structure is consistent with the API design

- No references to `userIdNo` in the API path or response metadata

  

#### 2. GET /:userId/address/:addressId

- **Endpoint**: `GET /api/v5/mobile-cdh/68872f804dba512547573d41/address/6887b03e1ff9cec29bab2e76`

- **Description**: Retrieves a specific address for a user by address ID

- **Test Command**:

```bash

curl -X 'GET' 'http://localhost:10100/api/v5/mobile-cdh/68872f804dba512547573d41/address/6887b03e1ff9cec29bab2e76' -H 'accept: */*'

```

- **Response**:

```json

{

"data": {

"addressType": "Office",

"address1": "789 Business Park",

"address2": "Building A",

"postcode": "50200",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true,

"_id": "6887b03e1ff9cec29bab2e76"

}

}

```

- **Result**: ✅ SUCCESS - Endpoint correctly accepts both `userId` and `addressId` parameters and returns the specific address data.

- **Observations**:

- The endpoint correctly accepts the MongoDB ObjectId as `userId` parameter

- The endpoint correctly accepts the address ID as a path parameter

- The response structure is clean and returns only the requested address data

- No references to `userIdNo` in the API path or response