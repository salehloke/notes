# CDH Requirements

## Overview
This document outlines the requirements and behavior specifications for the Customer Data Hub (CDH) integration in the Backoffice-X application. CDH mode can be enabled or disabled, which affects how user data is handled, displayed, and synchronized.

## User Edit Form Requirements

### General Requirements
1. The application must support both CDH-enabled and CDH-disabled modes
2. CDH mode configuration should be fetched from `getCdhModeConfig` service
3. The UI should adapt based on the CDH mode status

### When CDH Mode is Enabled

#### Display Requirements
1. Show specialized components for detailed data management:
   - `ContactsManager` for managing multiple contact numbers
   - `EmailsManager` for managing multiple email addresses
   - `AddressesManager` for managing multiple addresses
2. Main form fields for email, phone number, and country code should be read-only.

#### Data Handling
1. Primary contact and email from the detailed arrays should be synchronized to the main form fields
   - Setting a contact as primary in the contacts array will update the main `phoneNo` and `countryCode` fields
   - Setting an email as primary in the emails array will update the main `email` field
   - Setting an address as primary in the addresses array will update the main address fields
2. Validation must ensure at least one contact and one email exist
3. Changes to contacts, emails, and addresses should be displayed in the compare-and-save dialog
4. After successful update, data should be synchronized to CDH via `syncAllUserDataToCdh`

### When CDH Mode is Disabled

#### Display Requirements
1. Hide specialized components (ContactsManager, EmailsManager, AddressesManager)
2. Main form fields for email, phone number, and country code should be editable

#### Data Handling
1. Main form fields (email, phoneNo, countryCode) should update or create primary entries in the contacts and emails arrays
2. The addresses array should be emptied to avoid validation issues with existing data
3. Contacts, emails, and addresses should NOT be shown in the compare-and-save dialog
4. No CDH synchronization should be performed after update

## Data Structure Requirements

### User Data Model
1. Main user data should include fields for email, phoneNo, and countryCode
2. Detailed data should be stored in arrays for contacts, emails, and addresses
3. Each contact should include: contactType, countryCode, contactNo, isPrimary, isVerified
4. Each email should include: emailType, emailAddress, isPrimary, isVerified
5. Each address should include: addressType, address lines, postcode, city, state, country, isPrimary.
6. 

### CDH Synchronization
1. Primary contact/email in the arrays should match the main form fields
2. New contacts/emails created from main form fields should have required CDH properties (cdhContactId, cdhEmailId)
3. Data synchronization should only occur when CDH mode is enabled

## API Requirements
1. User data should be fetched via  `getSyncWithCdhUserDataById`, if the flag for CDH is enabled
2. User data updates should be performed via `updateUserDetails`
3. CDH synchronization should be triggered via `syncAllUserDataToCdh`, in the backend.
4. All API calls should include appropriate error handling and user feedback

## User Experience Requirements
1. Users should be informed of all changes before saving via the compare-and-save dialog
2. Success/error messages should be displayed after operations complete
3. The UI should prevent invalid data submissions based on the active mode

## Implementation Notes
1. The `compareAndSave` function handles the conditional logic based on CDH mode
2. Type safety should be maintained with proper TypeScript interfaces for all data structures
3. Helper functions should be used for formatting and displaying data consistently.
4. All process sync to backend must always be done in backend
5. Sync to CDH will check a Configuration in the Mongo DB to check for user exemption.
6. Etiqa+ will always be the source of truth for user data.
7. ### The emailTypeCode sent to CDH must be: 

| Code | Type | Description |
|------|------|-------------|
| 1    | PERSONAL | Personal email addresses |
| 2    | OFFICIAL | Work/business email addresses |
| 3    | OTHERS   | Any other email type |

8. ### The contactTypeCode sent to CDH must be:

| Code | Type | Description |
|------|------|-------------|
| H    | HOME | Home/landline phone numbers |
| M    | MOBILE | Mobile phone numbers |
| E    | EMERGENCY | Emergency contact numbers |
| O    | OFFICE | Office/work phone numbers |
| F    | FAX | Fax numbers |
| T    | TELEX | Telex numbers |

9. ### The addressTypeCode sent to CDH must be: 

| Address Type | Description |
|-------------|-------------|
| Home        | Residential or personal address |
| Billing     | Address where billing or invoices should be sent |
| Mailing     | General correspondence address (may differ from home or work) |
| Work        | Office/Work address |
| Primary     | The main address associated with the individual or entity |

10. ### The idTypeCode sent to CDH must be: 

| Code | Type | Description |
|------|------|-------------|
| 001  | IC | Malaysian Identity Card |
| 002  | Birth Certificate | Birth Certificate |
| 003  | Army IC | Army IC |
| 004  | Police IC | Police IC |
| 005  | Passport | Passport |
| 006  | Business Registration | Business Registration |
| 007  | Certificate of Incorporation | Certificate of Incorporation |
| 008  | Certificate of Registration | Certificate of Registration |
| 099  | Others | Others |
| 009  | MyPR | MyPR |

11. ### The primary values of emails, addresses and contacts must be: 
   - Primary email updates `user.email` field in Etiqa+
   - Primary contact updates `user.phoneNo` and `user.countryCode` fields in Etiqa+
   - Primary address updates `user.address` fields in Etiqa+
   - Process must happen in Backend

12. On each updates on emails and phone no, requires OTP verification.
