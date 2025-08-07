/**

* CDH-Etiqa+ Synchronization Test Data Generator

*

* This script generates random test data for CDH-Etiqa+ synchronization testing

* and provides functions to execute API calls with the generated data.

*/

  

const axios = require('axios');

const { v4: uuidv4 } = require('uuid');

const fs = require('fs');

const path = require('path');

  

// Configuration

const config = {

baseUrl: process.env.BASE_URL || 'http://localhost:11400',

userId: process.env.USER_ID || '68872f804dba512547573d41',

authToken: process.env.AUTH_TOKEN || '',

outputDir: path.join(__dirname, 'test-results')

};

  

// Ensure output directory exists

if (!fs.existsSync(config.outputDir)) {

fs.mkdirSync(config.outputDir, { recursive: true });

}

  

// Helper functions for generating random data

const generators = {

// Generate a random email

email: () => {

const domains = ['example.com', 'test.com', 'etiqa.com', 'mail.com', 'gmail.com'];

const prefixes = ['test', 'user', 'cdh', 'etiqa', 'sync'];

const randomPrefix = prefixes[Math.floor(Math.random() * prefixes.length)];

const randomDomain = domains[Math.floor(Math.random() * domains.length)];

const randomNum = Math.floor(Math.random() * 10000);

return `${randomPrefix}${randomNum}@${randomDomain}`;

},

// Generate a random phone number

phoneNumber: () => {

const prefixes = ['01', '03', '04', '05', '06', '07', '08', '09'];

const randomPrefix = prefixes[Math.floor(Math.random() * prefixes.length)];

const randomNum = Math.floor(Math.random() * 10000000).toString().padStart(7, '0');

return `${randomPrefix}${randomNum}`;

},

// Generate a random address

address: () => {

const streets = ['Jalan Ampang', 'Jalan Sultan Ismail', 'Jalan Bukit Bintang', 'Jalan Tun Razak', 'Jalan Imbi'];

const buildings = ['Tower', 'Apartment', 'Residence', 'Heights', 'Court', 'Plaza'];

const randomStreet = streets[Math.floor(Math.random() * streets.length)];

const randomBuilding = buildings[Math.floor(Math.random() * buildings.length)];

const randomNum = Math.floor(Math.random() * 100) + 1;

return `${randomNum} ${randomStreet}, ${randomBuilding}`;

},

// Generate a random postcode

postcode: () => {

const areas = ['50', '51', '52', '53', '54', '55', '56', '57', '58', '59', '60'];

const randomArea = areas[Math.floor(Math.random() * areas.length)];

const randomNum = Math.floor(Math.random() * 1000).toString().padStart(3, '0');

return `${randomArea}${randomNum}`;

},

// Generate a random city

city: () => {

const cities = ['Kuala Lumpur', 'Shah Alam', 'Petaling Jaya', 'Subang Jaya', 'Ampang', 'Cheras'];

return cities[Math.floor(Math.random() * cities.length)];

},

// Generate a random state

state: () => {

const states = [

{ name: 'Wilayah Persekutuan', code: 'KUL' },

{ name: 'Selangor', code: 'SEL' },

{ name: 'Penang', code: 'PNG' },

{ name: 'Johor', code: 'JHR' },

{ name: 'Melaka', code: 'MLK' }

];

return states[Math.floor(Math.random() * states.length)];

},

// Generate a random boolean

boolean: () => Math.random() > 0.5,

// Generate a random request ID

requestId: () => {

return uuidv4().replace(/-/g, '').substring(0, 32).replace(/(.{8})(.{4})(.{4})(.{4})(.*)/, '$1-$2-$3-$4-$5');

}

};

  

// API client

const apiClient = axios.create({

baseURL: config.baseUrl,

headers: {

'Content-Type': 'application/json',

'Authorization': `Bearer ${config.authToken}`

}

});

  

// Add request interceptor to log requests

apiClient.interceptors.request.use(request => {

console.log(`Making ${request.method.toUpperCase()} request to ${request.url}`);

return request;

});

  

// Add response interceptor to log responses

apiClient.interceptors.response.use(response => {

console.log(`Received ${response.status} response from ${response.config.url}`);

return response;

}, error => {

console.error(`Error ${error.response?.status || 'unknown'} from ${error.config?.url}`);

return Promise.reject(error);

});

  

// Test case generators

const testCases = {

// Generate test case for email update

emailUpdate: async (initialData = null) => {

// If no initial data provided, fetch it

if (!initialData) {

try {

const response = await apiClient.get(`/api/backoffice/portal-user/sync-cdh-into-eplus/${config.userId}`, {

headers: { 'X-Request-ID': generators.requestId() }

});

initialData = response.data.data.user;

} catch (error) {

console.error('Error fetching initial user data:', error.message);

return null;

}

}

// Generate new email data

const newEmail = generators.email();

const existingEmails = initialData.emails || [];

// Create updated emails array

const updatedEmails = existingEmails.map(email => ({

...email,

isPrimary: false,

isVerified: email.isVerified

}));

// Add new primary email

updatedEmails.push({

emailType: "1",

emailAddress: newEmail,

isPrimary: true,

isVerified: true

});

// Create request body

const requestBody = {

fullName: initialData.fullName,

email: newEmail,

isEmailVerified: true,

emails: updatedEmails

};

return {

testName: 'Email Update and Synchronization',

requestBody,

initialData: {

fullName: initialData.fullName,

email: initialData.email,

isEmailVerified: initialData.isEmailVerified,

emails: existingEmails

}

};

},

// Generate test case for contact update

contactUpdate: async (initialData = null) => {

// If no initial data provided, fetch it

if (!initialData) {

try {

const response = await apiClient.get(`/api/backoffice/portal-user/sync-cdh-into-eplus/${config.userId}`, {

headers: { 'X-Request-ID': generators.requestId() }

});

initialData = response.data.data.user;

} catch (error) {

console.error('Error fetching initial user data:', error.message);

return null;

}

}

// Generate new contact data

const newContactNo = generators.phoneNumber();

const countryCode = "+60";

const existingContacts = initialData.contacts || [];

// Create updated contacts array

const updatedContacts = existingContacts.map(contact => ({

...contact,

isPrimary: false,

isVerified: contact.isVerified

}));

// Add new primary contact

updatedContacts.push({

contactType: "M",

countryCode: countryCode,

contactNo: newContactNo,

isPrimary: true,

isVerified: true

});

// Create request body

const requestBody = {

fullName: initialData.fullName,

countryCode: countryCode,

phoneNo: newContactNo,

isPhoneNoVerified: true,

contacts: updatedContacts

};

return {

testName: 'Contact Update and Synchronization',

requestBody,

initialData: {

fullName: initialData.fullName,

phoneNo: initialData.phoneNo,

countryCode: initialData.countryCode,

isPhoneNoVerified: initialData.isPhoneNoVerified,

contacts: existingContacts

}

};

},

// Generate test case for address update

addressUpdate: async (initialData = null) => {

// If no initial data provided, fetch it

if (!initialData) {

try {

const response = await apiClient.get(`/api/backoffice/portal-user/sync-cdh-into-eplus/${config.userId}`, {

headers: { 'X-Request-ID': generators.requestId() }

});

initialData = response.data.data.user;

} catch (error) {

console.error('Error fetching initial user data:', error.message);

return null;

}

}

// Generate new address data

const newAddress = generators.address();

const newPostcode = generators.postcode();

const newCity = generators.city();

const newState = generators.state();

const existingAddresses = initialData.addresses || [];

// Create updated addresses array

const updatedAddresses = existingAddresses.map(address => ({

...address,

isPrimary: false

}));

// Add new primary address

updatedAddresses.push({

addressType: "Home",

address1: newAddress,

address2: "",

address3: "",

address4: "",

address5: "",

postcode: newPostcode,

city: newCity,

state: newState.code,

country: "MYS",

isPrimary: true

});

// Create request body

const requestBody = {

fullName: initialData.fullName,

addresses: updatedAddresses

};

return {

testName: 'Address Update and Synchronization',

requestBody,

initialData: {

fullName: initialData.fullName,

addresses: existingAddresses,

address: initialData.address

}

};

},

// Generate test case for multiple updates

multipleUpdates: async (initialData = null) => {

// If no initial data provided, fetch it

if (!initialData) {

try {

const response = await apiClient.get(`/api/backoffice/portal-user/sync-cdh-into-eplus/${config.userId}`, {

headers: { 'X-Request-ID': generators.requestId() }

});

initialData = response.data.data.user;

} catch (error) {

console.error('Error fetching initial user data:', error.message);

return null;

}

}

// Generate new data

const newEmail = generators.email();

const newContactNo = generators.phoneNumber();

const countryCode = "+60";

const newAddress = generators.address();

const newPostcode = generators.postcode();

const newCity = generators.city();

const newState = generators.state();

// Create updated arrays

const updatedEmails = (initialData.emails || []).map(email => ({

...email,

isPrimary: false,

isVerified: email.isVerified

}));

const updatedContacts = (initialData.contacts || []).map(contact => ({

...contact,

isPrimary: false,

isVerified: contact.isVerified

}));

const updatedAddresses = (initialData.addresses || []).map(address => ({

...address,

isPrimary: false

}));

// Add new primary items

updatedEmails.push({

emailType: "1",

emailAddress: newEmail,

isPrimary: true,

isVerified: true

});

updatedContacts.push({

contactType: "M",

countryCode: countryCode,

contactNo: newContactNo,

isPrimary: true,

isVerified: true

});

updatedAddresses.push({

addressType: "Home",

address1: newAddress,

address2: "",

address3: "",

address4: "",

address5: "",

postcode: newPostcode,

city: newCity,

state: newState.code,

country: "MYS",

isPrimary: true

});

// Create request body

const requestBody = {

fullName: initialData.fullName,

email: newEmail,

countryCode: countryCode,

phoneNo: newContactNo,

isEmailVerified: true,

isPhoneNoVerified: true,

emails: updatedEmails,

contacts: updatedContacts,

addresses: updatedAddresses

};

return {

testName: 'Multiple Updates and Synchronization',

requestBody,

initialData: {

fullName: initialData.fullName,

email: initialData.email,

phoneNo: initialData.phoneNo,

countryCode: initialData.countryCode,

isEmailVerified: initialData.isEmailVerified,

isPhoneNoVerified: initialData.isPhoneNoVerified,

emails: initialData.emails || [],

contacts: initialData.contacts || [],

addresses: initialData.addresses || [],

address: initialData.address

}

};

}

};

  

// Test execution functions

const testExecutor = {

// Run a complete test case

runTest: async (testType) => {

console.log(`\n=== Starting ${testType} Test ===\n`);

// Step 1: Retrieve initial user data

console.log('Step 1: Retrieving initial user data...');

let initialData;

try {

const response = await apiClient.get(`/api/backoffice/portal-user/sync-cdh-into-eplus/${config.userId}`, {

headers: { 'X-Request-ID': generators.requestId() }

});

initialData = response.data.data.user;

console.log('Initial data retrieved successfully.');

} catch (error) {

console.error('Error fetching initial user data:', error.message);

return null;

}

// Step 2: Generate test case and update user

console.log('Step 2: Generating test data and updating user...');

let testCase;

try {

testCase = await testCases[testType](initialData);

const updateResponse = await apiClient.put(`/api/backoffice/portal-user/${config.userId}`, testCase.requestBody, {

headers: { 'X-Request-ID': generators.requestId() }

});

console.log('User updated successfully.');

testCase.updateResponse = updateResponse.data;

} catch (error) {

console.error('Error updating user:', error.message);

return null;

}

// Step 3: Trigger CDH synchronization

console.log('Step 3: Triggering CDH synchronization...');

try {

const syncResponse = await apiClient.post(`/api/backoffice/portal-user/${config.userId}/cdh-sync`, {}, {

headers: { 'X-Request-ID': generators.requestId() }

});

console.log('CDH synchronization triggered successfully.');

testCase.syncResponse = syncResponse.data;

} catch (error) {

console.error('Error triggering CDH synchronization:', error.message);

return null;

}

// Step 4: Verify synchronization

console.log('Step 4: Verifying synchronization...');

try {

const verifyResponse = await apiClient.get(`/api/backoffice/portal-user/sync-cdh-into-eplus/${config.userId}`, {

headers: { 'X-Request-ID': generators.requestId() }

});

console.log('Verification data retrieved successfully.');

testCase.finalData = verifyResponse.data.data.user;

} catch (error) {

console.error('Error verifying synchronization:', error.message);

return null;

}

// Generate test result document

const testResult = generateTestResult(testCase);

// Save test result to file

const timestamp = new Date().toISOString().replace(/[:.]/g, '-');

const fileName = `test-result-${testType}-${timestamp}.md`;

const filePath = path.join(config.outputDir, fileName);

fs.writeFileSync(filePath, testResult);

console.log(`\n=== Test completed and results saved to ${filePath} ===\n`);

return testCase;

}

};

  

// Generate test result document in markdown format

function generateTestResult(testCase) {

const today = new Date().toISOString().split('T')[0];

const testId = `TEST-CDH-SYNC-${Math.floor(Math.random() * 1000).toString().padStart(3, '0')}`;

let result = `# CDH-Etiqa+ Synchronization Test Result - ${testCase.testName}\n\n`;

// Test Information

result += `## Test Information\n`;

result += `- **Test Date**: ${today}\n`;

result += `- **Test ID**: ${testId}\n`;

result += `- **User ID**: ${config.userId}\n`;

result += `- **Test Case**: ${testCase.testName}\n\n`;

// Initial Data

result += `## Initial Data\n`;

result += `\`\`\`json\n${JSON.stringify(testCase.initialData, null, 2)}\n\`\`\`\n\n`;

// Test Execution

result += `## Test Execution\n`;

// Step 2: Update User Data

result += `### Step 2: Update User Data\n`;

result += `**Request:**\n`;

result += `\`\`\`json\n${JSON.stringify(testCase.requestBody, null, 2)}\n\`\`\`\n\n`;

result += `**Response:**\n`;

result += `\`\`\`json\n${JSON.stringify(testCase.updateResponse, null, 2)}\n\`\`\`\n\n`;

// Step 3: Trigger CDH Synchronization

result += `### Step 3: Trigger CDH Synchronization\n`;

result += `**Response:**\n`;

result += `\`\`\`json\n${JSON.stringify(testCase.syncResponse, null, 2)}\n\`\`\`\n\n`;

// Step 4: Verify Synchronization

result += `### Step 4: Verify Synchronization\n`;

result += `**Response:**\n`;

result += `\`\`\`json\n${JSON.stringify(testCase.finalData, null, 2)}\n\`\`\`\n\n`;

// Verification Results

result += `## Verification Results\n`;

// Create verification table based on test type

result += `| Field | Before | After | Verified |\n`;

result += `|-------|--------|-------|----------|\n`;

if (testCase.testName.includes('Email')) {

result += `| user.email | ${testCase.initialData.email || ''} | ${testCase.finalData.email || ''} | ${testCase.initialData.email !== testCase.finalData.email ? '✅' : '❌'} |\n`;

result += `| user.isEmailVerified | ${testCase.initialData.isEmailVerified} | ${testCase.finalData.isEmailVerified} | ${testCase.finalData.isEmailVerified === true ? '✅' : '❌'} |\n`;

result += `| Primary email | ${getPrimaryItem(testCase.initialData.emails, 'emailAddress')} | ${getPrimaryItem(testCase.finalData.emails, 'emailAddress')} | ${getPrimaryItem(testCase.initialData.emails, 'emailAddress') !== getPrimaryItem(testCase.finalData.emails, 'emailAddress') ? '✅' : '❌'} |\n`;

}

if (testCase.testName.includes('Contact')) {

result += `| user.phoneNo | ${testCase.initialData.phoneNo || ''} | ${testCase.finalData.phoneNo || ''} | ${testCase.initialData.phoneNo !== testCase.finalData.phoneNo ? '✅' : '❌'} |\n`;

result += `| user.countryCode | ${testCase.initialData.countryCode || ''} | ${testCase.finalData.countryCode || ''} | ${testCase.initialData.countryCode === testCase.finalData.countryCode ? '✅' : '❌'} |\n`;

result += `| user.isPhoneNoVerified | ${testCase.initialData.isPhoneNoVerified} | ${testCase.finalData.isPhoneNoVerified} | ${testCase.finalData.isPhoneNoVerified === true ? '✅' : '❌'} |\n`;

result += `| Primary contact | ${getPrimaryItem(testCase.initialData.contacts, 'contactNo')} | ${getPrimaryItem(testCase.finalData.contacts, 'contactNo')} | ${getPrimaryItem(testCase.initialData.contacts, 'contactNo') !== getPrimaryItem(testCase.finalData.contacts, 'contactNo') ? '✅' : '❌'} |\n`;

}

if (testCase.testName.includes('Address')) {

const initialAddress = testCase.initialData.address ? testCase.initialData.address.address1 : '';

const finalAddress = testCase.finalData.address ? testCase.finalData.address.address1 : '';

result += `| Primary address | ${initialAddress} | ${finalAddress} | ${initialAddress !== finalAddress ? '✅' : '❌'} |\n`;

}

// Verification Checklist

result += `\n## Verification Checklist\n`;

if (testCase.testName.includes('Email')) {

result += `- [${testCase.finalData.email === getPrimaryItem(testCase.finalData.emails, 'emailAddress') ? 'x' : ' '}] Primary email updates user.email\n`;

}

if (testCase.testName.includes('Contact')) {

result += `- [${testCase.finalData.phoneNo === getPrimaryItem(testCase.finalData.contacts, 'contactNo') ? 'x' : ' '}] Primary contact updates user.phoneNo\n`;

// Check for contact corruption issue

const primaryContact = testCase.finalData.contacts.find(c => c.isPrimary);

const hasCorruption = primaryContact && testCase.finalData.phoneNo === primaryContact.contactType;

if (hasCorruption) {

result += `- [x] **ISSUE DETECTED**: Contact corruption found - user.phoneNo is set to contactType (${primaryContact.contactType}) instead of contactNo (${primaryContact.contactNo})\n`;

}

}

if (testCase.testName.includes('Address')) {

const primaryAddress = testCase.finalData.addresses.find(a => a.isPrimary);

const addressMatch = primaryAddress && testCase.finalData.address &&

primaryAddress.address1 === testCase.finalData.address.address1;

result += `- [${addressMatch ? 'x' : ' '}] Primary address updates user.address\n`;

}

result += `- [${countPrimaryItems(testCase.finalData.emails) <= 1 ? 'x' : ' '}] Only one primary email exists\n`;

result += `- [${countPrimaryItems(testCase.finalData.contacts) <= 1 ? 'x' : ' '}] Only one primary contact exists\n`;

result += `- [${countPrimaryItems(testCase.finalData.addresses) <= 1 ? 'x' : ' '}] Only one primary address exists\n`;

// Notes

result += `\n## Notes\n`;

result += `- Test executed automatically using CDH-Etiqa+ Synchronization Test Data Generator\n`;

// Add note about contact corruption if detected

const primaryContact = testCase.finalData.contacts.find(c => c.isPrimary);

if (primaryContact && testCase.finalData.phoneNo === primaryContact.contactType) {

result += `- **CRITICAL ISSUE**: Contact data corruption detected. After CDH sync, user.phoneNo is set to the contactType value (${primaryContact.contactType}) instead of the actual phone number (${primaryContact.contactNo}).\n`;

result += `- This confirms the previously reported issue where primary phone number is corrupted during CDH synchronization.\n`;

}

return result;

}

  

// Helper function to get primary item value

function getPrimaryItem(items, field) {

if (!items || !Array.isArray(items)) return '';

const primaryItem = items.find(item => item.isPrimary);

return primaryItem ? primaryItem[field] : '';

}

  

// Helper function to count primary items

function countPrimaryItems(items) {

if (!items || !Array.isArray(items)) return 0;

return items.filter(item => item.isPrimary).length;

}

  

// Command line interface

async function main() {

console.log('\nCDH-Etiqa+ Synchronization Test Data Generator');

console.log('===========================================');

console.log(`Base URL: ${config.baseUrl}`);

console.log(`User ID: ${config.userId}`);

console.log(`Auth Token: ${config.authToken ? '********' : 'Not set'}`);

console.log('===========================================\n');

if (!config.authToken) {

console.log('WARNING: Auth token not set. Please set the AUTH_TOKEN environment variable.');

process.exit(1);

}

console.log('Available test types:');

console.log('1. Email Update and Synchronization');

console.log('2. Contact Update and Synchronization');

console.log('3. Address Update and Synchronization');

console.log('4. Multiple Updates and Synchronization');

console.log('0. Exit');

const readline = require('readline').createInterface({

input: process.stdin,

output: process.stdout

});

readline.question('\nEnter your choice (0-4): ', async (choice) => {

let testType;

switch (choice) {

case '1':

testType = 'emailUpdate';

break;

case '2':

testType = 'contactUpdate';

break;

case '3':

testType = 'addressUpdate';

break;

case '4':

testType = 'multipleUpdates';

break;

case '0':

console.log('Exiting...');

process.exit(0);

default:

console.log('Invalid choice. Exiting...');

process.exit(1);

}

try {

await testExecutor.runTest(testType);

} catch (error) {

console.error('Error executing test:', error.message);

}

readline.close();

});

}

  

// Run the main function if this script is executed directly

if (require.main === module) {

main();

}

  

// Export functions for use in other scripts

module.exports = {

generators,

testCases,

testExecutor

};