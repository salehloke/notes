
```JSON
{

"info": {

"name": "Enjoy Rewards API Tests",

"description": "Collection for testing Enjoy Rewards voucher and tracking endpoints",

"schema": "https://schema.getpostman.com/json/collection/v2.1.0/collection.json"

},

"variable": [],

"item": [

{

"name": "Authentication",

"item": [

{

"name": "Login - ETIQA_PLUS",

"event": [

{

"listen": "prerequest",

"script": {

"exec": [

"// Log current environment and credentials",

"console.log('🔧 Environment: ' + pm.environment.name);",

"console.log('🌐 Auth URL: ' + pm.environment.get('baseAuthUrl'));",

"console.log('👤 Username: ' + pm.environment.get('username'));",

"console.log('🔑 Login System: ' + pm.environment.get('loginSystem'));",

"console.log('--- Starting login process ---');"

],

"type": "text/javascript"

}

},

{

"listen": "test",

"script": {

"exec": [

"// Check if login was successful",

"if (pm.response.code === 200) {",

" const responseJson = pm.response.json();",

" ",

" // Extract the access token from the response",

" if (responseJson.data && responseJson.data.accessToken) {",

" const accessToken = responseJson.data.accessToken;",

" ",

" // Update the authToken environment variable",

" pm.environment.set('authToken', accessToken);",

" ",

" // Log success message",

" console.log('✅ Login successful! Auth token updated automatically.');",

" console.log('Token: ' + accessToken.substring(0, 50) + '...');",

" console.log('🔄 All subsequent requests will use the new token.');",

" } else {",

" console.log('❌ Login response does not contain accessToken');",

" console.log('Response structure: ' + JSON.stringify(responseJson, null, 2));",

" }",

"} else {",

" console.log('❌ Login failed with status: ' + pm.response.code);",

" console.log('Response: ' + pm.response.text());",

"}"

],

"type": "text/javascript"

}

}

],

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"username\": \"{{username}}\",\n \"password\": \"{{password}}\",\n \"loginSystem\": \"{{loginSystem}}\"\n}"

},

"url": {

"raw": "{{baseAuthUrl}}/login",

"host": ["{{baseAuthUrl}}"],

"path": ["login"]

}

},

"response": []

},

{

"name": "Login - Default",

"event": [

{

"listen": "prerequest",

"script": {

"exec": [

"// Log current environment and credentials",

"console.log('🔧 Environment: ' + pm.environment.name);",

"console.log('🌐 Auth URL: ' + pm.environment.get('baseAuthUrl'));",

"console.log('👤 Username: ' + pm.environment.get('username'));",

"console.log('🔑 Login System: Default (no loginSystem specified)');",

"console.log('--- Starting login process ---');"

],

"type": "text/javascript"

}

},

{

"listen": "test",

"script": {

"exec": [

"// Check if login was successful",

"if (pm.response.code === 200) {",

" const responseJson = pm.response.json();",

" ",

" // Extract the access token from the response",

" if (responseJson.data && responseJson.data.accessToken) {",

" const accessToken = responseJson.data.accessToken;",

" ",

" // Update the authToken environment variable",

" pm.environment.set('authToken', accessToken);",

" ",

" // Log success message",

" console.log('✅ Login successful! Auth token updated automatically.');",

" console.log('Token: ' + accessToken.substring(0, 50) + '...');",

" console.log('🔄 All subsequent requests will use the new token.');",

" } else {",

" console.log('❌ Login response does not contain accessToken');",

" console.log('Response structure: ' + JSON.stringify(responseJson, null, 2));",

" }",

"} else {",

" console.log('❌ Login failed with status: ' + pm.response.code);",

" console.log('Response: ' + pm.response.text());",

"}"

],

"type": "text/javascript"

}

}

],

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"username\": \"{{username}}\",\n \"password\": \"{{password}}\"\n}"

},

"url": {

"raw": "{{baseAuthUrl}}/login",

"host": ["{{baseAuthUrl}}"],

"path": ["login"]

}

},

"response": []

}

]

},

{

"name": "Voucher Endpoints",

"item": [

{

"name": "Get Available Vouchers",

"request": {

"method": "GET",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

}

],

"url": {

"raw": "{{baseUrl}}/rewards/product-list-all",

"host": ["{{baseUrl}}"],

"path": ["rewards", "product-list-all"]

}

},

"response": []

},

{

"name": "Get User's Claimed Vouchers (Active List)",

"request": {

"method": "GET",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

}

],

"url": {

"raw": "{{baseUrl}}/rewards/active-list",

"host": ["{{baseUrl}}"],

"path": ["rewards", "active-list"]

}

},

"response": []

},

{

"name": "Get User's Voucher History (Past List)",

"request": {

"method": "GET",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

}

],

"url": {

"raw": "{{baseUrl}}/rewards/past-list",

"host": ["{{baseUrl}}"],

"path": ["rewards", "past-list"]

}

},

"response": []

},

{

"name": "Claim a Voucher",

"request": {

"method": "POST",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

},

{

"key": "Content-Type",

"value": "application/json"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"productId\": \"123\"\n}"

},

"url": {

"raw": "{{baseUrl}}/rewards/products/claim-voucher",

"host": ["{{baseUrl}}"],

"path": ["rewards", "products", "claim-voucher"]

}

},

"response": []

},

{

"name": "Use a Voucher",

"request": {

"method": "POST",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

},

{

"key": "Content-Type",

"value": "application/json"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"transactionReferenceNumber\": \"TXN_TEST_001\"\n}"

},

"url": {

"raw": "{{baseUrl}}/rewards/products/use-voucher",

"host": ["{{baseUrl}}"],

"path": ["rewards", "products", "use-voucher"]

}

},

"response": []

},

{

"name": "Preview a Voucher",

"request": {

"method": "POST",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

},

{

"key": "Content-Type",

"value": "application/json"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"transactionReferenceNumber\": \"TXN_TEST_001\"\n}"

},

"url": {

"raw": "{{baseUrl}}/rewards/products/preview-voucher",

"host": ["{{baseUrl}}"],

"path": ["rewards", "products", "preview-voucher"]

}

},

"response": []

}

]

},

{

"name": "Voucher Details",

"item": [

{

"name": "Get Voucher Details by ID (Valid)",

"request": {

"method": "GET",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

}

],

"url": {

"raw": "{{baseUrl}}/rewards/single-product-properties-database/VOUCHER_123",

"host": ["{{baseUrl}}"],

"path": ["rewards", "single-product-properties-database", "VOUCHER_123"]

}

},

"response": []

},

{

"name": "Get Voucher Details by ID (Invalid)",

"request": {

"method": "GET",

"header": [

{

"key": "Authorization",

"value": "Bearer {{authToken}}"

}

],

"url": {

"raw": "{{baseUrl}}/rewards/single-product-properties-database/INVALID_VOUCHER_ID",

"host": ["{{baseUrl}}"],

"path": ["rewards", "single-product-properties-database", "INVALID_VOUCHER_ID"]

}

},

"response": []

},

{

"name": "Get Voucher Details by ID (No Auth)",

"request": {

"method": "GET",

"header": [],

"url": {

"raw": "{{baseUrl}}/rewards/single-product-properties-database/VOUCHER_123",

"host": ["{{baseUrl}}"],

"path": ["rewards", "single-product-properties-database", "VOUCHER_123"]

}

},

"response": []

}

]

},

{

"name": "Tracking/Analytics",

"item": [

{

"name": "Track Voucher Claim (Logged In)",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

},

{

"key": "Authorization",

"value": "Key {{apiKeyTracker}}"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Login\",\n \"eventName\": \"login_ontap_enjoy_claim_voucher\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"tapFrom\": \"Explore Icon\",\n \"clickTarget\": \"\",\n \"deviceId\": \"test-device-123\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"iPhone 14\",\n \"phoneOs\": \"iOS\",\n \"phoneOsVersion\": \"16.0\",\n \"session\": \"test-session-123\",\n \"itemDetails\": {\n \"voucherId\": \"VOUCHER_123\",\n \"voucherName\": \"Test Voucher\",\n \"brandName\": \"Test Brand\",\n \"etiqaExpiryDate\": \"2025-01-01\",\n \"voucherExpiryDate\": \"2025-02-02\"\n }\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

},

{

"name": "Track Voucher Claim (Pre-Login)",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

},

{

"key": "Authorization",

"value": "Key {{apiKeyTracker}}"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Pre-Login\",\n \"eventName\": \"prelogin_claim_voucher\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"tapFrom\": \"Explore Icon\",\n \"clickTarget\": \"\",\n \"deviceId\": \"test-device-456\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"Samsung Galaxy S23\",\n \"phoneOs\": \"Android\",\n \"phoneOsVersion\": \"13.0\",\n \"session\": \"test-session-456\",\n \"itemDetails\": {\n \"voucherId\": \"VOUCHER_456\",\n \"voucherName\": \"Pre-Login Voucher\",\n \"brandName\": \"Pre-Login Brand\"\n }\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

},

{

"name": "Track My Rewards Tap",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

},

{

"key": "Authorization",

"value": "Key {{apiKeyTracker}}"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Login\",\n \"eventName\": \"login_ontap_enjoy_myrewards\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"tapFrom\": \"My Rewards Button\",\n \"clickTarget\": \"My Rewards\",\n \"deviceId\": \"test-device-789\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"iPhone 15\",\n \"phoneOs\": \"iOS\",\n \"phoneOsVersion\": \"17.0\",\n \"session\": \"test-session-789\",\n \"itemDetails\": {\n \"voucherId\": \"VOUCHER_789\",\n \"voucherName\": \"My Rewards Voucher\",\n \"brandName\": \"My Rewards Brand\"\n }\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

},

{

"name": "Track Use Deal Now",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

},

{

"key": "Authorization",

"value": "Key {{apiKeyTracker}}"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Login\",\n \"eventName\": \"login_ontap_enjoy_usedealnow\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"tapFrom\": \"Use Deal Now Button\",\n \"clickTarget\": \"Use Deal Now\",\n \"deviceId\": \"test-device-101\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"Google Pixel 7\",\n \"phoneOs\": \"Android\",\n \"phoneOsVersion\": \"14.0\",\n \"session\": \"test-session-101\",\n \"itemDetails\": {\n \"voucherId\": \"VOUCHER_101\",\n \"voucherName\": \"Use Deal Voucher\",\n \"brandName\": \"Use Deal Brand\"\n }\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

},

{

"name": "Track Continue Browsing",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

},

{

"key": "Authorization",

"value": "Key {{apiKeyTracker}}"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Login\",\n \"eventName\": \"login_ontap_enjoy_continuebrowsing\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"tapFrom\": \"Continue Browsing Button\",\n \"clickTarget\": \"Continue Browsing\",\n \"deviceId\": \"test-device-202\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"OnePlus 11\",\n \"phoneOs\": \"Android\",\n \"phoneOsVersion\": \"13.0\",\n \"session\": \"test-session-202\",\n \"itemDetails\": {\n \"voucherId\": \"VOUCHER_202\",\n \"voucherName\": \"Continue Browsing Voucher\",\n \"brandName\": \"Continue Browsing Brand\"\n }\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

},

{

"name": "Track Close Deal",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

},

{

"key": "Authorization",

"value": "Key {{apiKeyTracker}}"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Login\",\n \"eventName\": \"login_close_deal\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"tapFrom\": \"Close Deal Button\",\n \"clickTarget\": \"Close Deal\",\n \"deviceId\": \"test-device-303\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"Xiaomi 13\",\n \"phoneOs\": \"Android\",\n \"phoneOsVersion\": \"13.0\",\n \"session\": \"test-session-303\",\n \"itemDetails\": {\n \"voucherId\": \"VOUCHER_303\",\n \"voucherName\": \"Close Deal Voucher\",\n \"brandName\": \"Close Deal Brand\"\n }\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

},

{

"name": "Track Event (Invalid API Key)",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

},

{

"key": "Authorization",

"value": "Key invalid.invalid-api-key"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Login\",\n \"eventName\": \"login_claim_voucher\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"tapFrom\": \"Explore Icon\",\n \"clickTarget\": \"\",\n \"deviceId\": \"test-device-error\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"Test Device\",\n \"phoneOs\": \"Test OS\",\n \"phoneOsVersion\": \"1.0\",\n \"session\": \"test-session-error\",\n \"itemDetails\": {\n \"voucherId\": \"VOUCHER_ERROR\",\n \"voucherName\": \"Error Voucher\",\n \"brandName\": \"Error Brand\"\n }\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

},

{

"name": "Track Event (No Auth)",

"request": {

"method": "POST",

"header": [

{

"key": "Content-Type",

"value": "application/json"

}

],

"body": {

"mode": "raw",

"raw": "{\n \"category\": \"Login\",\n \"eventName\": \"login_claim_voucher\",\n \"trackingType\": \"onTap\",\n \"module\": \"Enjoy\",\n \"screenName\": \"voucher-details\",\n \"deviceId\": \"no-auth-device\",\n \"appVersion\": \"1.0.0\",\n \"phoneModel\": \"No Auth Device\",\n \"phoneOs\": \"No Auth OS\",\n \"phoneOsVersion\": \"1.0\"\n}"

},

"url": {

"raw": "{{trackingUrl}}/tracking/on-tap",

"host": ["{{trackingUrl}}"],

"path": ["tracking", "on-tap"]

}

},

"response": []

}

]

}

]

}
```