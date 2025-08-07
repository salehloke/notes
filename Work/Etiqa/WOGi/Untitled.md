# **Enjoy Rewards Testing Guide**

  

## **📋 Table of Contents**

1. [Prerequisites](#prerequisites)

2. [Database Cleanup](#database-cleanup)

3. [Voucher Instance Upload](#voucher-instance-upload)

4. [Environment Setup](#environment-setup)

5. [API Endpoints Testing](#api-endpoints-testing)

6. [Frontend Testing](#frontend-testing)

7. [Test Scenarios](#test-scenarios)

8. [Troubleshooting](#troubleshooting)

9. [Voucher Claiming Process Flow](#voucher-claiming-process-flow)

  

---

  

## **🔧 Prerequisites**

  

### **Required Services**

- Backend API (smile app) - Port 10100

- Backoffice API - Port 11400

- Micro-site (enjoy-rewards) - Port 3000

- MongoDB (for voucher data)

- WOGI API (external rewards provider)

  

### **Required Tools**

- Postman or similar API client

- MongoDB Compass or mongo shell

- Browser developer tools

  

---

  

## **🗄️ Database Cleanup**

  

### **⚠️ CRITICAL: Clear Test Data Before Testing**

  

Before running any tests, you **MUST** clear the following collections to ensure fresh testing:

  

### **1. Clear Reward Transactions**

```javascript

// Connect to MongoDB

use smile_core

  

// Clear all reward transactions

db.getCollection('reward.transaction').deleteMany({})

  

// Verify cleanup

db.getCollection('reward.transaction').countDocuments()

```

  

### **2. Clear Voucher Instances**

```javascript

// Clear all voucher instances

db.getCollection('rewards.voucher.instances').deleteMany({})

  

// Verify cleanup

db.getCollection('rewards.voucher.instances').countDocuments()

```

  

### **3. Clear Product Properties**

```javascript

// Clear reward product properties

db.getCollection('reward.product.properties').deleteMany({})

  

// Verify cleanup

db.getCollection('reward.product.properties').countDocuments()

```

  

### **4. Clear Enjoy Voucher Configs**

```javascript

// Clear enjoy voucher configs

db.getCollection('enjoy.voucher.config').deleteMany({})

  

// Verify cleanup

db.getCollection('enjoy.voucher.config').countDocuments()

```

  

### **5. Automated Cleanup Script**

Create a cleanup script for convenience:

  

```javascript

// cleanup-test-data.js

db.getCollection('reward.transaction').deleteMany({})

db.getCollection('rewards.voucher.instances').deleteMany({})

db.getCollection('reward.product.properties').deleteMany({})

db.getCollection('enjoy.voucher.config').deleteMany({})

  

print("✅ Test data cleared successfully")

```

  

---

  

## **📤 Voucher Instance Upload**

  

### **Step 1: Upload Voucher Instances**

  

**⚠️ IMPORTANT**: This step must be completed AFTER database cleanup to avoid "Voucher already Exists" errors.

  

#### **API Endpoint:**

```bash

POST http://localhost:11400/api/backoffice/portal-enjoy-rewards/rewards/upload-voucher-list

```

  

#### **Headers:**

```bash

Content-Type: application/json

Authorization: Bearer {your-admin-token}

```

  

#### **Sample Payload:**

```json

{

"data": [

{

"gatewayId": "9340",

"cardId": "25358189",

"productName": "Sofuto Voucher",

"productAmount": 3.9,

"transactionId": "6de3c02a-43b2-48e5-afc9-01c73e24beca",

"expiryDate": "2025-08-20T00:00:00.000Z",

"activationShortURL": "https://stg.wogi.dev/redeem/hnVu2e-1exeQ6xNNjSydJwYkYGEsrDNTsBC4TfMUBg-iL4sKh1L23-WLLxqAG-ys/activate",

"activationRedeemURL": "https://stg.wogi.dev/redeem/hnVu2e-1exeQ6xNNjSydJwYkYGEsrDNTsBC4TfMUBg-iL4sKh1L23-WLLxqAG-ys/activate",

"maxClaimedQuantityPerUser": 1,

"isProductBeingShown": true

}

],

"maxClaimedQuantityPerUser": 1,

"maxPurchaseQuantityPerVoucher": 1,

"isProductBeingShown": true,

"notes": "Uploaded Voucher + product by Admin (Version 1)"

}

```

  

#### **Expected Success Response:**

```json

{

"data": [

{

"process": "Create / Update Local Voucher Data",

"data": {

"voucherInstance": {

"cardId": "25358189",

"notes": "Uploaded Voucher + product by Admin (Version 1)",

"status": "success",

"gatewayId": 9340,

"productName": "Sofuto Voucher",

"productAmount": 3.9,

"transactionId": "6de3c02a-43b2-48e5-afc9-01c73e24beca",

"expiryDate": "2025-08-20T00:00:00.000Z",

"activationShortURL": "https://stg.wogi.dev/redeem/hnVu2e-1exeQ6xNNjSydJwYkYGEsrDNTsBC4TfMUBg-iL4sKh1L23-WLLxqAG-ys/activate",

"activationRedeemURL": "https://stg.wogi.dev/redeem/hnVu2e-1exeQ6xNNjSydJwYkYGEsrDNTsBC4TfMUBg-iL4sKh1L23-WLLxqAG-ys/activate",

"maxClaimedQuantityPerUser": 1,

"isProductBeingShown": true

},

"product": {

"gatewayId": "9340",

"productName": "Sofuto Voucher",

"maxClaimedQuantityPerUser": 1,

"availableQuantity": 1,

"isProductBeingShown": true,

"dataOperationStatus": "create-new"

}

}

}

]

}

```

  

#### **Error Response (If Vouchers Already Exist):**

```json

{

"data": [

{

"process": "Create / Update Local Voucher Data",

"data": {

"voucherInstance": {

"cardId": "25358189",

"notes": "Uploaded Voucher + product by Admin (Version 1)",

"status": "failed",

"error": "Failed to add. Voucher already Exists",

"gatewayId": 0,

"productName": "Sofuto Voucher",

"productAmount": 3.9,

"transactionId": "6de3c02a-43b2-48e5-afc9-01c73e24beca",

"expiryDate": "N/A",

"activationShortURL": "https://stg.wogi.dev/redeem/hnVu2e-1exeQ6xNNjSydJwYkYGEsrDNTsBC4TfMUBg-iL4sKh1L23-WLLxqAG-ys/activate",

"activationRedeemURL": "https://stg.wogi.dev/redeem/hnVu2e-1exeQ6xNNjSydJwYkYGEsrDNTsBC4TfMUBg-iL4sKh1L23-WLLxqAG-ys/activate",

"maxClaimedQuantityPerUser": 1,

"isProductBeingShown": true

},

"product": {

"gatewayId": "9340",

"productName": "Sofuto Voucher",

"maxClaimedQuantityPerUser": 1,

"availableQuantity": 0,

"isProductBeingShown": true,

"dataOperationStatus": "update-existing"

}

}

}

]

}

```

  

### **Step 2: Verify Upload Success**

  

#### **Check Database Collections:**

```javascript

// Check voucher instances

db.getCollection('rewards.voucher.instances').find({}).count()

  

// Check product properties

db.getCollection('reward.product.properties').find({}).count()

  

// Check enjoy voucher configs

db.getCollection('enjoy.voucher.config').find({}).count()

```

  

#### **Expected Results:**

- Voucher instances should be created with status `CREATED`

- Product properties should be created with `availableQuantity > 0`

- Enjoy voucher configs should be created

  

### **Step 3: Troubleshoot Upload Issues**

  

#### **If You Get "Voucher already Exists" Error:**

  

1. **Double-check database cleanup:**

```javascript

// Verify all collections are empty

db.getCollection('rewards.voucher.instances').countDocuments()

db.getCollection('reward.product.properties').countDocuments()

db.getCollection('enjoy.voucher.config').countDocuments()

```

  

2. **Check for specific voucher IDs:**

```javascript

// Check if specific cardId exists

db.getCollection('rewards.voucher.instances').findOne({

cardId: "25358189"

})

  

// Check if specific transactionId exists

db.getCollection('rewards.voucher.instances').findOne({

transactionId: "6de3c02a-43b2-48e5-afc9-01c73e24beca"

})

```

  

3. **Force delete specific vouchers:**

```javascript

// Delete specific voucher if it exists

db.getCollection('rewards.voucher.instances').deleteMany({

cardId: "25358189"

})

  

// Delete specific product if it exists

db.getCollection('reward.product.properties').deleteMany({

gatewayId: "9340"

})

```

  

---

  

## **⚙️ Environment Setup**

  

### **1. Backend Configuration**

Ensure these environment variables are set in your `pm2/local.config.js`:

  

```javascript

// WOGI Rewards API Configuration

WOGI_CLIENT_ID: "api_etiqa_digital_sdn_bhd_service_my_dd5x3h",

WOGI_CLIENT_SECRET: "M2rLfQ62FUXkFNNxq7CyFzNZDBC_sAP1",

WOGI_B64_AUTH: "Basic YXBpX2V0aXFhX2RpZ2l0YWxfc2RuX2JoZF9zZXJ2aWNlX215X2RkNXgzaDpNMnJMZlE2MkZVWGtGTk54cTdDeUZ6TlpEQkNfc0FQMQ==",

WOGI_HOST_AUTH: "https://gateway.wogi.dev",

DATAPOWER_WOGI_HOST_PRIME: "https://smile-uat.etiqa.com.my/datapower/api/my/rt/wogi/v1",

DATAPOWER_WOGI_HOST_AUTH: "https://smile-uat.etiqa.com.my/datapower/api/my/rt/wogi/v1",

```

  

### **2. Micro-site Configuration**

Ensure the enjoy-rewards micro-site is running:

  

```bash

cd micro-site/enjoy

npm install

npm run dev

```

  

### **3. Authentication Setup**

Get a valid authentication token for testing:

  

```bash

# Login to get access token

curl -X POST http://localhost:10100/api/v5/auth/login \

-H "Content-Type: application/json" \

-d '{

"username": "testuser",

"password": "testpass"

}'

```

  

---

  

## **🔌 API Endpoints Testing**

  

### **1. Product Listing Endpoints**

  

#### **Get All Products**

```bash

GET /api/v5/third-party/rewards/product-list-all-wogi?limit=10&page=1&priceMin=0

```

  

#### **Get Products by Category**

```bash

GET /api/v5/third-party/rewards/product-list-by-category/{categoryId}

```

  

#### **Get Deals of the Month**

```bash

GET /api/v5/third-party/rewards/deals-of-month

```

  

### **2. Voucher Management Endpoints**

  

#### **Claim Voucher**

```bash

POST /api/v5/third-party/rewards/products/claim-voucher

Content-Type: application/json

Authorization: Bearer {token}

  

{

"productId": "9340"

}

```

  

#### **Use Voucher**

```bash

POST /api/v5/third-party/rewards/products/use-voucher

Content-Type: application/json

Authorization: Bearer {token}

  

{

"transactionReferenceNumber": "6de3c02a-43b2-48e5-afc9-01c73e24beca"

}

```

  

#### **Preview Voucher**

```bash

POST /api/v5/third-party/rewards/products/preview-voucher

Content-Type: application/json

Authorization: Bearer {token}

  

{

"transactionReferenceNumber": "6de3c02a-43b2-48e5-afc9-01c73e24beca"

}

```

  

### **3. Transaction Endpoints**

  

#### **Get Active Vouchers**

```bash

GET /api/v5/third-party/rewards/transactions/active-list

Authorization: Bearer {token}

```

  

#### **Get Past Vouchers**

```bash

GET /api/v5/third-party/rewards/transactions/past-list

Authorization: Bearer {token}

```

  

#### **Get Transaction Details**

```bash

GET /api/v5/third-party/rewards/transactions/{transactionId}

Authorization: Bearer {token}

```

  

---

  

## **🌐 Frontend Testing**

  

### **1. Micro-site Pages**

  

#### **Home Page**

- URL: `http://localhost:3000`

- Test: Product listing, deals of the month

  

#### **Product Details**

- URL: `http://localhost:3000/product/{productId}`

- Test: Product information, claim button

  

#### **My Rewards**

- URL: `http://localhost:3000/my-rewards`

- Test: Active and past vouchers

  

#### **Voucher Details**

- URL: `http://localhost:3000/my-rewards/active-voucher/{id}`

- Test: Voucher usage, preview

  

### **2. Key Frontend Functions**

  

#### **Product Listing**

```typescript

// Test these functions in wogi-voucher.service.ts

getNewlyAddedVouchers()

getProductListByCategory(categoryId)

getDealsOfTheMonth()

```

  

#### **Voucher Operations**

```typescript

// Test these functions

postVoucherClaim(productId)

postUseVoucher(transactionReferenceNumber)

postPreviewVoucher(transactionReferenceNumber)

```

  

#### **Transaction Management**

```typescript

// Test these functions

getActiveList()

getPastList()

getTransactionDetailsById(id)

```

  

---

  

## **🧪 Test Scenarios**

  

### **Scenario 1: Complete Voucher Lifecycle**

  

#### **Step 1: Verify Voucher Upload**

```javascript

// Check uploaded vouchers

db.getCollection('rewards.voucher.instances').find({

gatewayId: 9340

}).pretty()

```

  

#### **Step 2: Browse Products**

```bash

# Get available products

GET /api/v5/third-party/rewards/product-list-all-wogi?limit=10&page=1&priceMin=0

```

  

**Expected Result:**

- Returns list of available vouchers including Sofuto Voucher

- Product has `gatewayId: 9340`, `productName: "Sofuto Voucher"`

  

#### **Step 3: Claim Voucher**

```bash

# Claim the Sofuto Voucher

POST /api/v5/third-party/rewards/products/claim-voucher

{

"productId": "9340"

}

```

  

**Expected Result:**

- Creates entry in `rewards.voucher.instances` with status `CLAIMED`

- Creates entry in `reward.transaction`

- Returns `transactionReferenceNumber`

  

#### **Step 4: View Active Vouchers**

```bash

# Get user's active vouchers

GET /api/v5/third-party/rewards/transactions/active-list

```

  

**Expected Result:**

- Shows claimed Sofuto Voucher with status `CLAIMED`

- Includes `transactionReferenceNumber`

  

#### **Step 5: Use Voucher**

```bash

# Use the voucher

POST /api/v5/third-party/rewards/products/use-voucher

{

"transactionReferenceNumber": "6de3c02a-43b2-48e5-afc9-01c73e24beca"

}

```

  

**Expected Result:**

- Updates voucher status to `SUCCESS`

- Updates transaction status to `SUCCESS`

- Sets `usage.used = true`

  

#### **Step 6: Verify in Database**

```javascript

// Check voucher instance

db.getCollection('rewards.voucher.instances').findOne({

transactionReferenceNumber: "6de3c02a-43b2-48e5-afc9-01c73e24beca"

})

  

// Check transaction

db.getCollection('reward.transaction').findOne({

transactionReferenceNumber: "6de3c02a-43b2-48e5-afc9-01c73e24beca"

})

```

  

### **Scenario 2: Voucher Expiration**

  

#### **Step 1: Claim Voucher**

```bash

POST /api/v5/third-party/rewards/products/claim-voucher

{

"productId": "9340"

}

```

  

#### **Step 2: Wait for Expiration**

- Set voucher expiry to short duration for testing

- Or manually update expiry date in database

  

#### **Step 3: Check Expired Status**

```javascript

// Check if voucher is expired

db.getCollection('rewards.voucher.instances').findOne({

transactionReferenceNumber: "6de3c02a-43b2-48e5-afc9-01c73e24beca"

})

```

  

**Expected Result:**

- Status should be `EXPIRED`

- `expiresAt` should be in the past

  

### **Scenario 3: Error Handling**

  

#### **Test Invalid Product ID**

```bash

POST /api/v5/third-party/rewards/products/claim-voucher

{

"productId": "99999"

}

```

  

**Expected Result:**

- Returns error response

- No database entries created

  

#### **Test Duplicate Claim**

```bash

# Try to claim same product twice

POST /api/v5/third-party/rewards/products/claim-voucher

{

"productId": "9340"

}

```

  

**Expected Result:**

- Returns error about already claimed

- No duplicate entries created

  

---

  

## **🔍 Database Verification**

  

### **1. Check Voucher Instances**

```javascript

// View all voucher instances

db.getCollection('rewards.voucher.instances').find({}).pretty()

  

// Check specific voucher

db.getCollection('rewards.voucher.instances').findOne({

transactionReferenceNumber: "6de3c02a-43b2-48e5-afc9-01c73e24beca"

})

```

  

### **2. Check Transactions**

```javascript

// View all transactions

db.getCollection('reward.transaction').find({}).pretty()

  

// Check specific transaction

db.getCollection('reward.transaction').findOne({

transactionReferenceNumber: "6de3c02a-43b2-48e5-afc9-01c73e24beca"

})

```

  

### **3. Check Status History**

```javascript

// View status history for a voucher

db.getCollection('rewards.voucher.instances').findOne({

transactionReferenceNumber: "6de3c02a-43b2-48e5-afc9-01c73e24beca"

}, {statusHistory: 1})

```

  

---

  

## **🚨 Troubleshooting**

  

### **Common Issues**

  

#### **1. "Voucher already Exists" Error**

**Solution:**

```javascript

// Clear all voucher-related collections

db.getCollection('rewards.voucher.instances').deleteMany({})

db.getCollection('reward.product.properties').deleteMany({})

db.getCollection('enjoy.voucher.config').deleteMany({})

```

  

#### **2. 404 Errors on API Calls**

- Check if backend service is running

- Verify API endpoints are correct

- Check authentication token

  

#### **3. Database Connection Issues**

```bash

# Test MongoDB connection

mongo --host localhost --port 27017 smile_core

```

  

#### **4. WOGI API Issues**

- Check WOGI credentials in config

- Verify network connectivity to WOGI

- Check WOGI API status

  

#### **5. Frontend Not Loading**

```bash

# Check micro-site logs

cd micro-site/enjoy

npm run dev

```

  

### **Debug Commands**

  

#### **Check Service Status**

```bash

# Check PM2 processes

pm2 status

  

# Check backend logs

pm2 logs smile

```

  

#### **Check Database Collections**

```javascript

// List all collections

show collections

  

// Check collection counts

db.getCollection('reward.transaction').countDocuments()

db.getCollection('rewards.voucher.instances').countDocuments()

```

  

#### **Check API Health**

```bash

# Test API health

curl http://localhost:10100/api/v5/health

```

  

---

  

## **✅ Test Checklist**

  

### **Pre-Testing**

- [ ] Database cleanup completed

- [ ] Voucher instances uploaded successfully

- [ ] Backend services running

- [ ] Micro-site running

- [ ] Authentication token obtained

- [ ] WOGI API accessible

  

### **Core Functionality**

- [ ] Product listing works

- [ ] Voucher claiming works

- [ ] Voucher usage works

- [ ] Transaction history works

- [ ] Error handling works

  

### **Database Verification**

- [ ] Voucher instances created correctly

- [ ] Transactions recorded properly

- [ ] Status updates working

- [ ] No duplicate entries

  

### **Frontend Testing**

- [ ] All pages load correctly

- [ ] Navigation works

- [ ] Forms submit properly

- [ ] Error messages display

  

---

  

## **🔄 Voucher Claiming Process Flow**

  

### **Complete Flow Diagram**

  

```mermaid

flowchart TD

A[User Initiates Voucher Claim] --> B[Frontend: postVoucherClaim]

B --> C[Get User ID from Token]

C --> D[Prepare API Request]

D --> E[POST /api/v5/third-party/rewards/products/claim-voucher]

E --> F{Authentication Valid?}

F -->|No| G[Return 401 Unauthorized]

F -->|Yes| H[Validate Product ID: 9340]

H --> I{Product Exists in Database?}

I -->|No| J[Return 404 Product Not Found]

I -->|Yes| K[Check Product Availability]

K --> L{Product Available?}

L -->|No| M[Return Error: Product Unavailable]

L -->|Yes| N[Check User Claim Limits]

N --> O{User Can Claim More?}

O -->|No| P[Return Error: Claim Limit Reached]

O -->|Yes| Q[Find Available Voucher Instance]

Q --> R{Available Voucher Found?}

R -->|No| S[Return Error: No Vouchers Available]

R -->|Yes| T[Update Voucher Instance Status]

T --> U[Set Status: CLAIMED]

U --> V[Set issuedTo.userId]

V --> W[Set issuedAt: Current Timestamp]

W --> X[Generate Transaction Reference Number]

X --> Y[Create Transaction Record]

Y --> Z[Set Transaction Status: CLAIMED]

Z --> AA[Link to Voucher Instance]

AA --> BB[Update Product Available Quantity]

BB --> CC[Log Transaction Event]

CC --> DD[Return Success Response]

DD --> EE[Frontend Updates UI]

EE --> FF[Show Success Message]

FF --> GG[Redirect to My Rewards]

%% Error Handling Paths

G --> H1[Show Login Error]

J --> H2[Show Product Not Found]

M --> H3[Show Unavailable Message]

P --> H4[Show Limit Reached]

S --> H5[Show No Vouchers Available]

```

  

### **Sample API Call**

  

```bash

curl -X 'POST' \

'http://localhost:10100/api/v5/third-party/rewards/products/claim-voucher' \

-H 'accept: */*' \

-H 'Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI2NjM5YjlkZjlmODc2MmM0YzUxYzExNDgiLCJpZCI6IjY2MzliOWRmOWY4NzYyYzRjNTFjMTE0OCIsInV1aWQiOm51bGwsInRpbWVzdGFtcCI6MTc1NDI5NTIzNTk3NCwib3JpZ2luIjoiTVkiLCJpYXQiOjE3NTQyOTUyMzUsImV4cCI6MTc1NDI5NjEzNSwiaXNzIjoiRXRpcWErIn0.i0iHi0jEIl9__SiZ4cqpyot1a5GqP_8W_phgd7St2dmYvsuIN0Hd7ET3ZVHe9yfJj99zZyTKhnjJMfiwqWL-wGFFJp0gjcefQIuAazzx4jQZ-wPVGGwGMovANXHnF6LrYWGaLzMKRNTPPDOkYUjhR2B_h5KlljuPTr2S7OZwLf-oMCC7kiG91xFmHeAJPjH73fyT846x20GbYUqbjRS2bd5LFATOmrhTGDk0EmPLox5m5Jd43Swyfgq0xiQhRI7aCp1t2UHwv_D8vFGU-ok6qAZG0yqg_RPPSxxoyFaD0xnDpybGnOatLsqUwjlkzavuzi1rQdVcQ5zqXgq5exFATQ' \

-H 'Content-Type: application/json' \

-d '{

"productId": "9340"

}'

```

  

### **Success Response**

  

```json

{

"data": {

"productId": 9340,

"transactionReferenceNumber": "68906bfbff72925644ec4d66",

"status": "claimed"

}

}

```

  

### **Database State Changes**

  

#### **Before Claim:**

```javascript

// Voucher Instance

{

cardId: "25358189",

status: "CREATED",

issuedTo: null,

issuedAt: null

}

  

// Product Properties

{

gatewayId: "9340",

availableQuantity: 15

}

```

  

#### **After Claim:**

```javascript

// Voucher Instance

{

cardId: "25358189",

status: "CLAIMED",

issuedTo: {

userId: "6639b9df9f8762c4c51c1148"

},

issuedAt: "2025-01-15T10:30:00.000Z"

}

  

// Transaction Record

{

transactionReferenceNumber: "68906bfbff72925644ec4d66",

gatewayId: 9340,

status: "CLAIMED",

issuedTo: {

userId: "6639b9df9f8762c4c51c1148"

},

issuedAt: "2025-01-15T10:30:00.000Z"

}

  

// Product Properties

{

gatewayId: "9340",

availableQuantity: 14

}

```

  

---

  

## **🎯 Key Testing Points**

  

### **Remember These Critical Points:**

  

1. **ALWAYS clear `reward.transaction` and `rewards.voucher.instances` before testing**

2. **Upload voucher instances FIRST using the backoffice API**

3. **Test complete voucher lifecycle** (claim → use → verify)

4. **Check both database collections** after each operation

5. **Verify status transitions** in status history

6. **Test error scenarios** and edge cases

7. **Monitor API responses** for proper error handling

  

This testing guide ensures comprehensive coverage of the enjoy-rewards functionality while maintaining data integrity through proper cleanup procedures.