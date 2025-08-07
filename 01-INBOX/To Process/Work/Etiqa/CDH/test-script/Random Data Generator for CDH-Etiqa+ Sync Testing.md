# Random Data Generator for CDH-Etiqa+ Sync Testing

  

This document provides guidelines and examples for generating random test data for CDH-Etiqa+ synchronization testing. Using random data helps avoid conflicts and ensures tests are independent.

  

## Email Generation

  

### Format

- Use the pattern: `test-{random-string}@{domain}.com`

- Example domains: testdomain.com, etiqa-test.com, cdh-test.net

- Random string should be 8-12 alphanumeric characters

  

### Examples

```javascript

// JavaScript example for generating random email

function generateRandomEmail() {

const randomString = Math.random().toString(36).substring(2, 10);

const domains = ['testdomain.com', 'etiqa-test.com', 'cdh-test.net'];

const domain = domains[Math.floor(Math.random() * domains.length)];

return `test-${randomString}@${domain}`;

}

  

// Example usage:

// test-a7b3c9d2@testdomain.com

// test-x8y5z2p9@etiqa-test.com

```

  

## Phone Number Generation

  

### Format

- Malaysian format: 01X-XXX XXXX (where X is a digit)

- Country codes: +60 (Malaysia), +65 (Singapore), +62 (Indonesia), +63 (Philippines)

  

### Examples

```javascript

// JavaScript example for generating random phone number

function generateRandomPhone() {

const prefix = '01';

const firstPart = Math.floor(Math.random() * 10).toString() +

Math.floor(Math.random() * 10).toString() +

Math.floor(Math.random() * 10).toString();

const secondPart = Math.floor(Math.random() * 10000).toString().padStart(4, '0');

return `${prefix}${firstPart}${secondPart}`;

}

  

function getRandomCountryCode() {

const countryCodes = ['+60', '+65', '+62', '+63'];

return countryCodes[Math.floor(Math.random() * countryCodes.length)];

}

  

// Example usage:

// +60 0123456789

// +65 0187654321

```

  

## Address Generation

  

### Format

Use realistic Malaysian addresses with the following components:

- Address line 1: Building number + Street name

- Address line 2: Unit/Apartment number (optional)

- Postcode: 5-digit Malaysian postcodes

- City: Malaysian cities

- State: Malaysian state codes

- Country: MYS (Malaysia)

  

### Examples

```javascript

// JavaScript example for generating random address

function generateRandomAddress() {

const buildingNumbers = ['123', '456', '789', '101', '202', '303'];

const streetNames = [

'Jalan Bukit Bintang', 'Jalan Sultan Ismail', 'Jalan Ampang',

'Jalan Tun Razak', 'Jalan Imbi', 'Jalan Pudu'

];

const units = ['Unit A-12', 'Suite 25-01', 'Block C-3', ''];

const postcodes = ['50100', '40150', '47500', '68000', '43650'];

const cities = ['Kuala Lumpur', 'Shah Alam', 'Petaling Jaya', 'Subang Jaya', 'Ampang'];

const states = ['KUL', 'SEL', 'JHR', 'PNG', 'PRK'];

return {

address1: `${buildingNumbers[Math.floor(Math.random() * buildingNumbers.length)]} ${streetNames[Math.floor(Math.random() * streetNames.length)]}`,

address2: units[Math.floor(Math.random() * units.length)],

postcode: postcodes[Math.floor(Math.random() * postcodes.length)],

city: cities[Math.floor(Math.random() * cities.length)],

state: states[Math.floor(Math.random() * states.length)],

country: 'MYS'

};

}

  

// Example usage:

// Address1: 123 Jalan Bukit Bintang

// Address2: Unit A-12

// Postcode: 50100

// City: Kuala Lumpur

// State: KUL

// Country: MYS

```

  

## Full Name Generation

  

### Format

- Malaysian names with common prefixes

- Format: [Prefix] + First Name + [Middle Name] + Last Name

  

### Examples

```javascript

// JavaScript example for generating random Malaysian names

function generateRandomName() {

const prefixes = ['', 'Dato\'', 'Tan Sri', 'Dr.', 'Ir.'];

const firstNames = ['Ahmad', 'Ali', 'Chong', 'David', 'Fatimah', 'Gopal', 'Hui Ling'];

const middleNames = ['bin', 'binti', 'a/l', 'a/p', ''];

const lastNames = ['Abdullah', 'Ibrahim', 'Tan', 'Kumar', 'Singh', 'Lee', 'Wong'];

const prefix = prefixes[Math.floor(Math.random() * prefixes.length)];

const firstName = firstNames[Math.floor(Math.random() * firstNames.length)];

const middleName = middleNames[Math.floor(Math.random() * middleNames.length)];

const lastName = lastNames[Math.floor(Math.random() * lastNames.length)];

return `${prefix} ${firstName} ${middleName} ${lastName}`.trim();

}

  

// Example usage:

// Ahmad bin Abdullah

// Dr. Fatimah binti Ibrahim

// Chong Wei Lee

```

  

## Complete User Data Example

  

```json

{

"fullName": "Ahmad bin Abdullah",

"email": "test-a7b3c9d2@testdomain.com",

"countryCode": "+60",

"phoneNo": "0123456789",

"contacts": [

{

"contactType": "M",

"countryCode": "+60",

"contactNo": "0123456789",

"isPrimary": true,

"isVerified": true

},

{

"contactType": "M",

"countryCode": "+65",

"contactNo": "0187654321",

"isPrimary": false,

"isVerified": false

}

],

"emails": [

{

"emailType": "1",

"emailAddress": "test-a7b3c9d2@testdomain.com",

"isPrimary": true,

"isVerified": true

},

{

"emailType": "1",

"emailAddress": "test-x8y5z2p9@etiqa-test.com",

"isPrimary": false,

"isVerified": false

}

],

"addresses": [

{

"addressType": "Home",

"address1": "123 Jalan Bukit Bintang",

"address2": "Unit A-12",

"postcode": "50100",

"city": "Kuala Lumpur",

"state": "KUL",

"country": "MYS",

"isPrimary": true

},

{

"addressType": "Office",

"address1": "456 Jalan Sultan Ismail",

"address2": "Suite 25-01",

"postcode": "40150",

"city": "Shah Alam",

"state": "SEL",

"country": "MYS",

"isPrimary": false

}

]

}

```

  

## Usage in Testing

  

1. For each test case, generate new random data using these patterns

2. Ensure primary fields are properly designated

3. Use different data for each test to avoid conflicts

4. Document the generated data in the test result files

5. Verify that the generated data is properly synchronized between Etiqa+ and CDH

  

## Data Validation Rules

  

When generating random data, ensure it follows these validation rules:

  

1. Email addresses must be valid format (username@domain.tld)

2. Phone numbers should be 10-12 digits excluding country code

3. Malaysian postcodes are 5 digits

4. Names should be reasonable length (2-50 characters)

5. Address lines should be reasonable length (5-100 characters)

  

Following these guidelines will help ensure your test data is realistic and valid for testing purposes.