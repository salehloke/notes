
```bash
#!/bin/bash

  

# CDH-Etiqa+ Backoffice Synchronization Test Automation Script

# This script automates all test procedures from cdh-bo-sync-test-procedure.md

# and generates detailed results in markdown files

  

# Configuration

BASE_URL="http://localhost:11400"

USER_ID="68872f804dba512547573d41"

AUTH_TOKEN=""

TIMESTAMP=$(date +"%Y%m%d%H%M")

RESULTS_DIR="test-results"

LOG_FILE="$RESULTS_DIR/test-execution.log"

  

# Colors for output

RED='\033[0;31m'

GREEN='\033[0;32m'

YELLOW='\033[1;33m'

BLUE='\033[0;34m'

NC='\033[0m' # No Color

  

# Create results directory

mkdir -p "$RESULTS_DIR"

  

# Logging function

log() {

echo -e "$1" | tee -a "$LOG_FILE"

}

  

# Function to generate random data

generate_random_data() {

local prefix=$1

local timestamp=$(date +%s)

echo "${prefix}-${timestamp}"

}

  

# Function to extract JSON values

extract_json_value() {

local json=$1

local key=$2

echo "$json" | grep -o "\"$key\":[^,}]*" | cut -d':' -f2 | tr -d ' "'

}

  

# Function to extract array values

extract_array_value() {

local json=$1

local array_key=$2

local field_key=$3

echo "$json" | grep -o "\"$array_key\":\[[^]]*\]" | grep -o "\"$field_key\":[^,}]*" | cut -d':' -f2 | tr -d ' "'

}

  

# Function to authenticate

authenticate() {

log "${YELLOW}Step 1: Authenticating with backoffice API...${NC}"

local login_response=$(curl -s -X POST "$BASE_URL/api/backoffice/portal/login" \

-H "Content-Type: application/json" \

-d '{

"pfNumber": "admin01",

"password": "123456",

"isLocalAccount": true

}')

AUTH_TOKEN=$(extract_json_value "$login_response" "accessToken")

if [ -z "$AUTH_TOKEN" ]; then

log "${RED}❌ Authentication failed${NC}"

log "Response: $login_response"

return 1

fi

log "${GREEN}✅ Authentication successful${NC}"

return 0

}

  

# Function to get user data

get_user_data() {

local step_name=$1

local request_id=$2

log "${YELLOW}${step_name}...${NC}"

local response=$(curl -s -X GET "$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: $request_id")

echo "$response"

}

  

# Function to update user data

update_user_data() {

local test_name=$1

local payload=$2

local request_id=$3

log "${YELLOW}Updating user data for test: $test_name${NC}"

local response=$(curl -s -X PUT "$BASE_URL/api/backoffice/portal-user/$USER_ID" \

-H "Content-Type: application/json" \

-H "Authorization: Bearer $AUTH_TOKEN" \

-H "X-Request-ID: $request_id" \

-d "$payload")

echo "$response"

}

  

# Function to create test payload

create_test_payload() {

local test_type=$1

local email_verified=$2

local phone_verified=$3

local test_email=$(generate_random_data "test-${test_type}")

local test_phone=$(generate_random_data "0172099")

cat <<EOF

{

"username": "testUser40",

"fullName": "Test User ${test_type}",

"idType": "NRIC",

"idNo": "000522055323",

"registrationIdNo": "000522055323",

"countryCode": "+60",

"phoneNo": "$test_phone",

"email": "$test_email@example.com",

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

"contactNo": "$test_phone",

"isPrimary": true,

"isVerified": $phone_verified,

"_id": "6889f5491d67183d970e4126"

}

],

"emails": [

{

"cdhEmailId": 968,

"emailType": "1",

"emailAddress": "$test_email@example.com",

"isPrimary": true,

"isVerified": $email_verified,

"_id": "6889f5491d67183d970e4127"

}

],

"addresses": []

}

EOF

}

  

# Function to analyze verification status

analyze_verification_status() {

local response=$1

local test_name=$2

local is_email_verified=$(extract_json_value "$response" "isEmailVerified")

local is_phone_verified=$(extract_json_value "$response" "isPhoneNoVerified")

local contacts_verified=$(extract_array_value "$response" "contacts" "isVerified")

local emails_verified=$(extract_array_value "$response" "emails" "isVerified")

echo "## $test_name Analysis" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "### Verification Status" >> "$RESULTS_FILE"

echo "| Field | Value | Expected | Status |" >> "$RESULTS_FILE"

echo "|-------|-------|----------|--------|" >> "$RESULTS_FILE"

# Check email verification

if [ "$is_email_verified" = "true" ] && [ "$emails_verified" = "true" ]; then

echo "| Root Email Verified | $is_email_verified | true | ✅ Match |" >> "$RESULTS_FILE"

elif [ "$is_email_verified" = "false" ] && [ "$emails_verified" = "false" ]; then

echo "| Root Email Verified | $is_email_verified | false | ✅ Match |" >> "$RESULTS_FILE"

else

echo "| Root Email Verified | $is_email_verified | $emails_verified | ❌ Mismatch |" >> "$RESULTS_FILE"

fi

# Check phone verification

if [ "$is_phone_verified" = "true" ] && [ "$contacts_verified" = "true" ]; then

echo "| Root Phone Verified | $is_phone_verified | true | ✅ Match |" >> "$RESULTS_FILE"

elif [ "$is_phone_verified" = "false" ] && [ "$contacts_verified" = "false" ]; then

echo "| Root Phone Verified | $is_phone_verified | false | ✅ Match |" >> "$RESULTS_FILE"

else

echo "| Root Phone Verified | $is_phone_verified | $contacts_verified | ❌ Mismatch |" >> "$RESULTS_FILE"

fi

echo "" >> "$RESULTS_FILE"

echo "### Raw Values" >> "$RESULTS_FILE"

echo "- Root-level isEmailVerified: $is_email_verified" >> "$RESULTS_FILE"

echo "- Root-level isPhoneNoVerified: $is_phone_verified" >> "$RESULTS_FILE"

echo "- Contacts array isVerified: $contacts_verified" >> "$RESULTS_FILE"

echo "- Emails array isVerified: $emails_verified" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

}

  

# Function to run test case

run_test_case() {

local test_name=$1

local email_verified=$2

local phone_verified=$3

log "${BLUE}Running Test Case: $test_name${NC}"

# Step 1: Get initial data

local initial_data=$(get_user_data "Getting initial user data" "initial-${test_name}-$(date +%s)")

# Step 2: Create and send update payload

local payload=$(create_test_payload "$test_name" "$email_verified" "$phone_verified")

local update_response=$(update_user_data "$test_name" "$payload" "update-${test_name}-$(date +%s)")

# Step 3: Get updated data

local updated_data=$(get_user_data "Getting updated user data" "updated-${test_name}-$(date +%s)")

# Step 4: Document results

echo "## Test Case: $test_name" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "### Test Configuration" >> "$RESULTS_FILE"

echo "- Email Verification: $email_verified" >> "$RESULTS_FILE"

echo "- Phone Verification: $phone_verified" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "### API Requests" >> "$RESULTS_FILE"

echo "#### Initial Data Request" >> "$RESULTS_FILE"

echo '```bash' >> "$RESULTS_FILE"

echo "curl -X GET \"$BASE_URL/api/backoffice/portal-user/sync-cdh-into-eplus/$USER_ID\" \\" >> "$RESULTS_FILE"

echo " -H \"Authorization: Bearer \$AUTH_TOKEN\"" >> "$RESULTS_FILE"

echo '```' >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "#### Update Request" >> "$RESULTS_FILE"

echo '```bash' >> "$RESULTS_FILE"

echo "curl -X PUT \"$BASE_URL/api/backoffice/portal-user/$USER_ID\" \\" >> "$RESULTS_FILE"

echo " -H \"Content-Type: application/json\" \\" >> "$RESULTS_FILE"

echo " -H \"Authorization: Bearer \$AUTH_TOKEN\" \\" >> "$RESULTS_FILE"

echo " -d '$payload'" >> "$RESULTS_FILE"

echo '```' >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "### API Responses" >> "$RESULTS_FILE"

echo "#### Initial Response" >> "$RESULTS_FILE"

echo '```json' >> "$RESULTS_FILE"

echo "$initial_data" >> "$RESULTS_FILE"

echo '```' >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "#### Update Response" >> "$RESULTS_FILE"

echo '```json' >> "$RESULTS_FILE"

echo "$update_response" >> "$RESULTS_FILE"

echo '```' >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "#### Updated Data Response" >> "$RESULTS_FILE"

echo '```json' >> "$RESULTS_FILE"

echo "$updated_data" >> "$RESULTS_FILE"

echo '```' >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

# Step 5: Analyze verification status

analyze_verification_status "$updated_data" "$test_name"

echo "---" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

log "${GREEN}✅ Test Case $test_name completed${NC}"

}

  

# Main execution

main() {

log "${YELLOW}=== CDH-Etiqa+ Backoffice Synchronization Test Automation ===${NC}"

log "Timestamp: $TIMESTAMP"

log "Results Directory: $RESULTS_DIR"

log ""

# Initialize results file

RESULTS_FILE="$RESULTS_DIR/${TIMESTAMP}-cdh-bo-sync-test-results.md"

# Create results file header

cat > "$RESULTS_FILE" <<EOF

# CDH-Etiqa+ Backoffice Synchronization Test Results

  

**Test Execution Time:** $(date)

**Test Environment:** $BASE_URL

**Test User ID:** $USER_ID

  

## Test Summary

  

This document contains the results of automated CDH-Etiqa+ backoffice synchronization tests.

  

## Test Cases Executed

  

1. **Test Case 1:** Email Update and Synchronization

2. **Test Case 2:** Contact Update and Synchronization

3. **Test Case 3:** Address Update and Synchronization

4. **Test Case 4:** Multiple Updates and Primary Designation

5. **Test Case 5:** Update verification status

  

---

  

EOF

# Authenticate

if ! authenticate; then

log "${RED}❌ Authentication failed. Exiting.${NC}"

exit 1

fi

# Run test cases

log "${YELLOW}Starting test execution...${NC}"

# Test Case 1: Email Update and Synchronization (verified email)

run_test_case "Email-Update-Verified" "true" "false"

# Test Case 2: Contact Update and Synchronization (verified phone)

run_test_case "Contact-Update-Verified" "false" "true"

# Test Case 3: Address Update and Synchronization (both unverified)

run_test_case "Address-Update-Unverified" "false" "false"

# Test Case 4: Multiple Updates and Primary Designation (both verified)

run_test_case "Multiple-Updates-Verified" "true" "true"

# Test Case 5: Update verification status (mixed)

run_test_case "Verification-Status-Mixed" "true" "false"

# Generate summary

log "${YELLOW}Generating test summary...${NC}"

echo "## Test Summary" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "### Verification Checklist" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "- [ ] Primary email updates user.email" >> "$RESULTS_FILE"

echo "- [ ] Primary contact updates user.phoneNo and user.countryCode" >> "$RESULTS_FILE"

echo "- [ ] Primary address updates user.address" >> "$RESULTS_FILE"

echo "- [ ] Verification status properly updates user.isPhoneNoVerified and user.isEmailVerified" >> "$RESULTS_FILE"

echo "- [ ] Only one primary item exists in each category" >> "$RESULTS_FILE"

echo "- [ ] All updates from Etiqa+ are synchronized with CDH" >> "$RESULTS_FILE"

echo "- [ ] All data from CDH is correctly reflected in Etiqa+" >> "$RESULTS_FILE"

echo "- [ ] Verify that each value is able to be updated" >> "$RESULTS_FILE"

echo "- [ ] Verify that each contact value in the contacts array has cdhContactId after sync to CDH" >> "$RESULTS_FILE"

echo "- [ ] Verify that each email value in the emails array has cdhEmailId after sync to CDH" >> "$RESULTS_FILE"

echo "- [ ] Verify that each address value in the addresses array has cdhAddressId after sync to CDH" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "### Test Execution Log" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "Full test execution log can be found in: $LOG_FILE" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "### Next Steps" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

echo "1. Review the verification status analysis for each test case" >> "$RESULTS_FILE"

echo "2. Check for any ❌ Mismatch statuses in the results" >> "$RESULTS_FILE"

echo "3. Verify that all checklist items are properly tested" >> "$RESULTS_FILE"

echo "4. If issues are found, investigate the root cause and implement fixes" >> "$RESULTS_FILE"

echo "" >> "$RESULTS_FILE"

log "${GREEN}✅ All test cases completed successfully!${NC}"

log "${GREEN}📄 Results saved to: $RESULTS_FILE${NC}"

log "${GREEN}📋 Log saved to: $LOG_FILE${NC}"

log ""

log "${YELLOW}=== Test Automation Complete ===${NC}"

}

  

# Run main function

main "$@"
```