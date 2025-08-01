
# CDH-Etiqa+ Backoffice Synchronization Test Automation

  

This directory contains automated test scripts for the CDH-Etiqa+ backoffice synchronization functionality.

  

## Files Overview

  

### 1. `cdh-bo-sync-test-automation.sh`

**Main automated test script** that converts the manual test procedures from `cdh-bo-sync-test-procedure.md` into an automated testing solution.

  

### 2. `test-verification-script.sh`

**Focused verification test script** that specifically tests the `isVerified` values propagation issue.

  

### 3. `test-verification-issue.md`

**Detailed analysis document** explaining the verification status bug and proposed fix.

  

## Quick Start

  

### Prerequisites

- Bash shell environment

- `curl` command available

- Backoffice API running on `http://localhost:11400`

- Valid test user ID (default: `68872f804dba512547573d41`)

  

### Running the Main Test Automation

  

```bash

# Make script executable (if not already done)

chmod +x cdh-bo-sync-test-automation.sh

  

# Run the complete test suite

./cdh-bo-sync-test-automation.sh

```

  

### Running the Verification Test Only

  

```bash

# Make script executable (if not already done)

chmod +x test-verification-script.sh

  

# Run the verification test

./test-verification-script.sh

```

  

## What the Main Script Does

  

The `cdh-bo-sync-test-automation.sh` script automatically:

  

### 1. **Authentication**

- Logs into the backoffice API using admin credentials

- Retrieves and stores the authentication token

  

### 2. **Test Execution**

Runs 5 comprehensive test cases:

  

1. **Email Update and Synchronization** (verified email)

2. **Contact Update and Synchronization** (verified phone)

3. **Address Update and Synchronization** (both unverified)

4. **Multiple Updates and Primary Designation** (both verified)

5. **Update verification status** (mixed verification)

  

### 3. **Data Generation**

- Generates unique test data for each test case

- Uses timestamps to avoid conflicts

- Creates realistic email addresses and phone numbers

  

### 4. **API Interaction**

For each test case:

- Retrieves initial user data

- Updates user data with test payload

- Retrieves updated user data

- Analyzes verification status

  

### 5. **Results Generation**

Creates detailed markdown files with:

- Complete API requests and responses

- Verification status analysis

- Test configuration details

- Comparison tables

- Checklist verification

  

## Output Files

  

### Generated Files Structure

```

test-results/

├── 202501301922-cdh-bo-sync-test-results.md # Main results file

└── test-execution.log # Execution log

```

  

### Results File Content

Each results file contains:

  

1. **Test Summary**

- Execution timestamp

- Test environment details

- List of executed test cases

  

2. **Per Test Case Documentation**

- Test configuration

- Complete API requests (curl commands)

- Full API responses (JSON)

- Verification status analysis

- Comparison tables

  

3. **Verification Analysis**

- Root-level vs array-level verification status

- Match/mismatch indicators

- Raw values for debugging

  

4. **Checklist**

- All verification points from the original procedure

- Status tracking for each requirement

  

## Configuration

  

### Environment Variables

You can modify these variables in the script:

  

```bash

BASE_URL="http://localhost:11400" # API base URL

USER_ID="68872f804dba512547573d41" # Test user ID

RESULTS_DIR="test-results" # Results directory

```

  

### Authentication

The script uses these default credentials:

- **Username:** `admin01`

- **Password:** `123456`

- **Local Account:** `true`

  

## Test Cases Explained

  

### Test Case 1: Email Update and Synchronization

- **Purpose:** Verify email updates and verification status propagation

- **Configuration:** Email verified = true, Phone verified = false

- **Expected:** `user.isEmailVerified` should match primary email's `isVerified`

  

### Test Case 2: Contact Update and Synchronization

- **Purpose:** Verify phone number updates and verification status propagation

- **Configuration:** Email verified = false, Phone verified = true

- **Expected:** `user.isPhoneNoVerified` should match primary contact's `isVerified`

  

### Test Case 3: Address Update and Synchronization

- **Purpose:** Verify address updates with unverified contact/email

- **Configuration:** Email verified = false, Phone verified = false

- **Expected:** Both verification fields should remain false

  

### Test Case 4: Multiple Updates and Primary Designation

- **Purpose:** Verify multiple field updates with verified status

- **Configuration:** Email verified = true, Phone verified = true

- **Expected:** Both verification fields should be true

  

### Test Case 5: Update verification status (Mixed)

- **Purpose:** Verify mixed verification status handling

- **Configuration:** Email verified = true, Phone verified = false

- **Expected:** Email verified = true, Phone verified = false

  

## Verification Analysis

  

The script automatically analyzes:

  

### Root-Level vs Array-Level Verification

- `user.isEmailVerified` vs `user.emails[0].isVerified`

- `user.isPhoneNoVerified` vs `user.contacts[0].isVerified`

  

### Status Indicators

- ✅ **Match:** Root and array values are consistent

- ❌ **Mismatch:** Root and array values are inconsistent (indicates a bug)

  

## Troubleshooting

  

### Common Issues

  

1. **Authentication Failed**

- Check if the backoffice API is running

- Verify the credentials in the script

- Check network connectivity

  

2. **User Not Found**

- Verify the `USER_ID` exists in the system

- Check if the user is accessible via the API

  

3. **API Errors**

- Check the execution log for detailed error messages

- Verify API endpoint availability

- Check request/response format

  

### Debug Mode

To see more detailed output, you can modify the script to add `-v` flag to curl commands:

  

```bash

# In the script, change:

curl -s -X GET ...

  

# To:

curl -v -X GET ...

```

  

## Integration with CI/CD

  

The script can be integrated into CI/CD pipelines:

  

```yaml

# Example GitHub Actions step

- name: Run CDH Sync Tests

run: |

chmod +x ./cdh-bo-sync-test-automation.sh

./cdh-bo-sync-test-automation.sh

- name: Upload Test Results

uses: actions/upload-artifact@v2

with:

name: test-results

path: test-results/

```

  

## Customization

  

### Adding New Test Cases

To add a new test case, modify the `main()` function:

  

```bash

# Add new test case

run_test_case "New-Test-Name" "true" "false"

```

  

### Modifying Test Data

Edit the `create_test_payload()` function to change:

- Test data generation logic

- Payload structure

- Field values

  

### Changing Analysis Logic

Modify the `analyze_verification_status()` function to:

- Add new verification checks

- Change comparison logic

- Modify output format

  

## Benefits of Automation

  

1. **Consistency:** All tests run with the same configuration

2. **Completeness:** No manual steps are missed

3. **Documentation:** Full audit trail of all API interactions

4. **Reproducibility:** Tests can be run multiple times with same results

5. **Efficiency:** Saves hours of manual testing time

6. **Accuracy:** Eliminates human error in test execution

  

## Next Steps

  

After running the tests:

  

1. **Review Results:** Check the generated markdown file for any ❌ mismatches

2. **Investigate Issues:** Use the detailed API responses to debug problems

3. **Implement Fixes:** Apply the verification status fix if needed

4. **Re-run Tests:** Verify that fixes resolve the issues

5. **Document Changes:** Update test procedures based on findings