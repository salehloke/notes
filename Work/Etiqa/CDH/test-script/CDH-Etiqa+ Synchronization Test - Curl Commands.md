# CDH-Etiqa+ Synchronization Test - Curl Commands

  

This document provides curl commands for manually testing the CDH-Etiqa+ synchronization process. These commands correspond to the test cases documented in the test result files.

  

## Environment Variables

  

```bash

# Set these variables before running the commands

BASE_URL="http://localhost:11400"

USER_ID="68872f804dba512547573d41"

AUTH_TOKEN="your-auth-token-here"

```

  

## Test Case 1: Email Update and Synchronization

  

### Step 1: Retrieve Initial User Data

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 1a2b3c4d-5e6f-7g8h-9i0j-1k2l3m4n5o6p"

```

  

### Step 2: Update User Email

```bash

curl -X PUT "$BASE_URL/api/backoffice/portal-user/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 0j1k2l3m-4n5o-6p7q-8r9s-0t1u2v3w4x5y" \

-d '{

"fullName": "CDH Test User",

"email": "new@email.com",

"isEmailVerified": true,

"emails": [

{

"_id": "68872f014dba512547573ce2",

"emailType": "1",

"emailAddress": "current@email.com",

"isPrimary": false,

"isVerified": false

},

{

"emailType": "1",

"emailAddress": "new@email.com",

"isPrimary": true,

"isVerified": true

}

]

}'

```

  

### Step 3: Trigger CDH Synchronization

```bash

curl -X POST "$BASE_URL/api/backoffice/portal-user/$USER_ID/cdh-sync" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 1k2l3m4n-5o6p-7q8r-9s0t-1u2v3w4x5y6z" \

-d '{}'

```

  

### Step 4: Verify Synchronization

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 2l3m4n5o-6p7q-8r9s-0t1u-2v3w4x5y6z7a"

```

  

## Test Case 2: Contact Update and Synchronization

  

### Step 1: Retrieve Initial User Data

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 5e6f7g8h-9i0j-1k2l-3m4n-5o6p7q8r9s0t"

```

  

### Step 2: Update User Contact

```bash

curl -X PUT "$BASE_URL/api/backoffice/portal-user/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 6f7g8h9i-0j1k-2l3m-4n5o-6p7q8r9s0t1u" \

-d '{

"fullName": "CDH Test User",

"countryCode": "+61",

"phoneNo": "9988776655",

"isPhoneNoVerified": true,

"contacts": [

{

"_id": "68872f014dba512547573ce1",

"contactType": "M",

"countryCode": "+60",

"contactNo": "1122334455",

"isPrimary": false,

"isVerified": false

},

{

"contactType": "M",

"countryCode": "+61",

"contactNo": "9988776655",

"isPrimary": true,

"isVerified": true

}

]

}'

```

  

### Step 3: Trigger CDH Synchronization

```bash

curl -X POST "$BASE_URL/api/backoffice/portal-user/$USER_ID/cdh-sync" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 7g8h9i0j-1k2l-3m4n-5o6p-7q8r9s0t1u2v" \

-d '{}'

```

  

### Step 4: Verify Synchronization

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 8h9i0j1k-2l3m-4n5o-6p7q-8r9s0t1u2v3w"

```

  

## Test Case 3: Address Update and Synchronization

  

### Step 1: Retrieve Initial User Data

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 9i0j1k2l-3m4n-5o6p-7q8r-9s0t1u2v3w4x"

```

  

### Step 2: Update User Address

```bash

curl -X PUT "$BASE_URL/api/backoffice/portal-user/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 0j1k2l3m-4n5o-6p7q-8r9s-0t1u2v3w4x5y" \

-d '{

"fullName": "CDH Test User",

"addresses": [

{

"_id": "68872f014dba512547573ce3",

"addressType": "Home",

"address1": "123 Current Street",

"address2": "",

"address3": "",

"address4": "",

"address5": "",

"postcode": "50000",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": false

},

{

"addressType": "Mailing",

"address1": "456 New Avenue",

"address2": "",

"address3": "",

"address4": "",

"address5": "",

"postcode": "40100",

"city": "Shah Alam",

"state": "SEL",

"country": "MYS",

"isPrimary": true

}

]

}'

```

  

### Step 3: Trigger CDH Synchronization

```bash

curl -X POST "$BASE_URL/api/backoffice/portal-user/$USER_ID/cdh-sync" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 1k2l3m4n-5o6p-7q8r-9s0t-1u2v3w4x5y6z" \

-d '{}'

```

  

### Step 4: Verify Synchronization

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 2l3m4n5o-6p7q-8r9s-0t1u-2v3w4x5y6z7a"

```

  

## Test Case 5: Primary Designation Changes

  

### Step 1: Retrieve Initial User Data

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 1a2b3c4d-5e6f-7g8h-9i0j-1k2l3m4n5o6p"

```

  

### Step 2: Update Primary Designations for All Data Types

```bash

curl -X PUT "$BASE_URL/api/backoffice/portal-user/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 2b3c4d5e-6f7g-8h9i-0j1k-2l3m4n5o6p7q" \

-d '{

"fullName": "CDH Test User",

"countryCode": "+60",

"phoneNo": "3344556677",

"email": "secondary@email.com",

"isPhoneNoVerified": true,

"isEmailVerified": true,

"contacts": [

{

"_id": "68872f014dba512547573ce1",

"contactType": "M",

"countryCode": "+60",

"contactNo": "1122334455",

"isPrimary": false,

"isVerified": false

},

{

"_id": "68872f014dba512547573ce4",

"contactType": "H",

"countryCode": "+60",

"contactNo": "3344556677",

"isPrimary": true,

"isVerified": true

}

],

"emails": [

{

"_id": "68872f014dba512547573ce2",

"emailType": "1",

"emailAddress": "current@email.com",

"isPrimary": false,

"isVerified": false

},

{

"_id": "68872f014dba512547573ce5",

"emailType": "2",

"emailAddress": "secondary@email.com",

"isPrimary": true,

"isVerified": true

}

],

"addresses": [

{

"_id": "68872f014dba512547573ce3",

"addressType": "Home",

"address1": "123 Current Street",

"address2": "",

"address3": "",

"address4": "",

"address5": "",

"postcode": "50000",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": false

},

{

"_id": "68872f014dba512547573ce6",

"addressType": "Office",

"address1": "456 Work Avenue",

"address2": "",

"address3": "",

"address4": "",

"address5": "",

"postcode": "40100",

"city": "Shah Alam",

"state": "SEL",

"country": "MYS",

"isPrimary": true

}

]

}'

```

  

### Step 3: Trigger CDH Synchronization

```bash

curl -X POST "$BASE_URL/api/backoffice/portal-user/$USER_ID/cdh-sync" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 3c4d5e6f-7g8h-9i0j-1k2l-3m4n5o6p7q8r" \

-d '{}'

```

  

### Step 4: Verify Synchronization

```bash

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: 4d5e6f7g-8h9i-0j1k-2l3m-4n5o6p7q8r9s"

```

  

## Helper Script

  

You can use the following bash script to set up environment variables and run the tests more easily:

  

```bash

#!/bin/bash

  

# Set environment variables

export BASE_URL="http://localhost:11400"

export USER_ID="68872f804dba512547573d41"

export AUTH_TOKEN="your-auth-token-here"

  

# Function to generate a random request ID

generate_request_id() {

cat /dev/urandom | tr -dc 'a-z0-9' | fold -w 32 | head -n 1 | sed 's/\(.\{8\}\)\(.\{4\}\)\(.\{4\}\)\(.\{4\}\)\(.*\)/\1-\2-\3-\4-\5/'

}

  

# Example usage

run_test_case_1() {

echo "Running Test Case 1: Email Update and Synchronization"

# Step 1: Retrieve Initial User Data

echo "Step 1: Retrieving initial user data..."

REQUEST_ID=$(generate_request_id)

curl -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: $REQUEST_ID"

echo -e "\n\nPress Enter to continue to Step 2..."

read

# Continue with other steps...

}

  

# Main menu

echo "CDH-Etiqa+ Synchronization Test Script"

echo "--------------------------------------"

echo "1. Run Test Case 1: Email Update and Synchronization"

echo "2. Run Test Case 2: Contact Update and Synchronization"

echo "3. Run Test Case 3: Address Update and Synchronization"

echo "4. Run Test Case 5: Primary Designation Changes"

echo "0. Exit"

  

read -p "Enter your choice: " choice

  

case $choice in

1) run_test_case_1 ;;

# Add other test cases as needed

0) echo "Exiting..."; exit 0 ;;

*) echo "Invalid choice" ;;

esac

```

  

## Notes on Using Curl Commands

  

1. Replace `your-auth-token-here` with a valid JWT token for authentication.

2. The X-Request-ID headers are included for traceability but can be replaced with any unique identifier.

3. Ensure the MongoDB IDs in the request bodies match the actual IDs in your database.

4. These commands are designed to be run sequentially for each test case.

5. You may need to adjust the request bodies based on your actual data structure.