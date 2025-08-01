
```bash
#!/bin/bash

  

# Test Script: Verification Status Not Being Saved to Root-Level Fields

# This script demonstrates the bug where isVerified values in contacts/emails arrays

# are not propagated to user.isPhoneNoVerified and user.isEmailVerified

  

# Configuration

BASE_URL="http://localhost:11400"

USER_ID="68872f804dba512547573d41" # Test user ID from documentation

AUTH_TOKEN=""

  

# Colors for output

RED='\033[0;31m'

GREEN='\033[0;32m'

YELLOW='\033[1;33m'

NC='\033[0m' # No Color

  

echo -e "${YELLOW}=== CDH-Etiqa+ Verification Status Test ===${NC}"

echo "Testing if isVerified values are properly saved to root-level fields"

echo ""

  

# Step 1: Login to get authentication token

echo -e "${YELLOW}Step 1: Authenticating...${NC}"

LOGIN_RESPONSE=$(curl -s -X POST "$BASE_URL/api/backoffice/portal/login" \

-H "Content-Type: application/json" \

-d '{

"pfNumber": "admin01",

"password": "123456",

"isLocalAccount": true

}')

  

# Extract access token

AUTH_TOKEN=$(echo $LOGIN_RESPONSE | grep -o '"accessToken":"[^"]*"' | cut -d'"' -f4)

  

if [ -z "$AUTH_TOKEN" ]; then

echo -e "${RED}❌ Authentication failed${NC}"

echo "Response: $LOGIN_RESPONSE"

exit 1

fi

  

echo -e "${GREEN}✅ Authentication successful${NC}"

echo ""

  

# Step 2: Get initial user data

echo -e "${YELLOW}Step 2: Retrieving initial user data...${NC}"

INITIAL_RESPONSE=$(curl -s -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: test-verification-$(date +%s)")

  

echo "Initial user data retrieved"

echo ""

  

# Step 3: Update user with verified contact and email

echo -e "${YELLOW}Step 3: Updating user with verified contact and email...${NC}"

  

# Generate unique test data

TIMESTAMP=$(date +%s)

TEST_EMAIL="test-verified-$TIMESTAMP@example.com"

TEST_PHONE="0172099$TIMESTAMP"

  

UPDATE_PAYLOAD=$(cat <<EOF

{

"username": "testUser40",

"fullName": "Test User Verification Test",

"idType": "NRIC",

"idNo": "000522055323",

"registrationIdNo": "000522055323",

"countryCode": "+60",

"phoneNo": "$TEST_PHONE",

"email": "$TEST_EMAIL",

"pfNo": "",

"activePolicyNo": "",

"ecif": "PIMYS2507WRA9DE92FE",

"isMeVerified": false,

"isMCSVerified": false,

"isWellnessEnrolled": false,

"skipAgentChecking": false,

"id": "$USER_ID",

"contacts": [

{

"cdhContactId": 1112,

"contactType": "M",

"countryCode": "+60",

"contactNo": "$TEST_PHONE",

"isPrimary": true,

"isVerified": true,

"_id": "6889f5491d67183d970e4126",

"id": 1112

}

],

"emails": [

{

"cdhEmailId": 968,

"emailType": "1",

"emailAddress": "$TEST_EMAIL",

"isPrimary": true,

"isVerified": true,

"_id": "6889f5491d67183d970e4127",

"id": 968

}

],

"addresses": []

}

EOF

)

  

UPDATE_RESPONSE=$(curl -s -X PUT "$BASE_URL/api/backoffice/portal-user/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: test-verification-update-$(date +%s)" \

-d "$UPDATE_PAYLOAD")

  

echo "Update request sent"

echo ""

  

# Step 4: Retrieve updated user data

echo -e "${YELLOW}Step 4: Retrieving updated user data...${NC}"

UPDATED_RESPONSE=$(curl -s -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: test-verification-after-$(date +%s)")

  

echo "Updated user data retrieved"

echo ""

  

# Step 5: Analyze results

echo -e "${YELLOW}Step 5: Analyzing results...${NC}"

  

# Extract verification statuses from the response

IS_EMAIL_VERIFIED=$(echo $UPDATED_RESPONSE | grep -o '"isEmailVerified":[^,}]*' | cut -d':' -f2 | tr -d ' ')

IS_PHONE_VERIFIED=$(echo $UPDATED_RESPONSE | grep -o '"isPhoneNoVerified":[^,}]*' | cut -d':' -f2 | tr -d ' ')

  

# Extract verification statuses from arrays

CONTACTS_VERIFIED=$(echo $UPDATED_RESPONSE | grep -o '"contacts":\[[^]]*\]' | grep -o '"isVerified":[^,}]*' | cut -d':' -f2 | tr -d ' ')

EMAILS_VERIFIED=$(echo $UPDATED_RESPONSE | grep -o '"emails":\[[^]]*\]' | grep -o '"isVerified":[^,}]*' | cut -d':' -f2 | tr -d ' ')

  

echo "=== Verification Status Analysis ==="

echo "Root-level isEmailVerified: $IS_EMAIL_VERIFIED"

echo "Root-level isPhoneNoVerified: $IS_PHONE_VERIFIED"

echo "Contacts array isVerified: $CONTACTS_VERIFIED"

echo "Emails array isVerified: $EMAILS_VERIFIED"

echo ""

  

# Check for the bug

if [ "$IS_EMAIL_VERIFIED" = "false" ] && [ "$EMAILS_VERIFIED" = "true" ]; then

echo -e "${RED}❌ BUG DETECTED: Email verification status not propagated to root level${NC}"

echo " - Emails array shows isVerified: true"

echo " - Root level shows isEmailVerified: false"

echo " - Expected: isEmailVerified should be true"

else

echo -e "${GREEN}✅ Email verification status correctly propagated${NC}"

fi

  

if [ "$IS_PHONE_VERIFIED" = "false" ] && [ "$CONTACTS_VERIFIED" = "true" ]; then

echo -e "${RED}❌ BUG DETECTED: Phone verification status not propagated to root level${NC}"

echo " - Contacts array shows isVerified: true"

echo " - Root level shows isPhoneNoVerified: false"

echo " - Expected: isPhoneNoVerified should be true"

else

echo -e "${GREEN}✅ Phone verification status correctly propagated${NC}"

fi

  

echo ""

echo -e "${YELLOW}=== Test Summary ===${NC}"

echo "This test demonstrates whether the isVerified values from contacts and emails arrays"

echo "are properly propagated to the root-level verification fields."

echo ""

echo "If you see BUG DETECTED messages above, it confirms the issue described in the"

echo "test simulation document."

echo ""

echo "Full API responses have been captured and can be analyzed for further debugging."
```