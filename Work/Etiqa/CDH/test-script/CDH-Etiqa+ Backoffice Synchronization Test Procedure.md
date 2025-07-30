# CDH-Etiqa+ Backoffice Synchronization Test Procedure

  

## Overview

This document outlines the test procedure for verifying the synchronization between Etiqa+ and CDH systems. The tests focus on ensuring that user data updates in Etiqa+ are properly synchronized with CDH and vice versa.

  

## Test Environment

- Base URL: http://localhost:11400

- Test User ID: 68872f804dba512547573d41

  

## API Endpoints

  

### Backoffice Synchronization APIs

- GET `/api/backoffice/portal-user/sync-cdh-into-eplus/:userId` - Sync CDH data into Etiqa+

- POST `/api/backoffice/portal-user/retrieve-details-direct-cdh/no-logs` - Retrieve details from CDH directly

  

### Backoffice Update APIs

- PUT `/api/backoffice/portal-user/:userId` - Update user data in Etiqa+

- POST `/api/backoffice/portal-user/:userId/cdh-sync` - Sync data from Etiqa+ to CDH

  

## Test Process

  

### Step 1: Retrieve Initial User Data

1. Call the sync-cdh-into-eplus API to get the current user data

2. Record the initial values for key fields:

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

  

### Step 3: Trigger CDH Synchronization

1. Call the POST `/api/backoffice/portal-user/:userId/cdh-sync` API to sync the updated data to CDH

  

### Step 4: Verify Synchronization

1. Call the sync-cdh-into-eplus API again to get the updated user data

2. Compare the before and after values for key fields

3. Verify that:

- Primary email in emails array replaced user.email

- Primary contact in contacts array replaced user.phoneNo and user.countryCode

- Primary address in addresses array replaced user.address

- Verification status is correctly reflected in user.isPhoneNoVerified and user.isEmailVerified

- Only one item is marked as primary in each category (emails, contacts, addresses)

  

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