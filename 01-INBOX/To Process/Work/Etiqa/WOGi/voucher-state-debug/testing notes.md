# backend/test/README.md
# Voucher System REST API Testing Guide

## Overview
This directory contains REST client tests for the voucher system API endpoints.

## Prerequisites
1. Backend server running on `http://localhost:3000`
2. MongoDB running with test data
3. REST client (VS Code REST Client, Postman, or similar)

## Test Files
- `voucher-api-tests.http` - Basic API endpoint tests
- `voucher-test-scenarios.http` - Complete test scenarios
- `setup-test-data.sh` - Script to setup test data

## Running Tests

### 1. Setup Test Environment
```bash
# Start backend server
npm run dev:smile

# Setup test data
chmod +x test/scripts/setup-test-data.sh
./test/scripts/setup-test-data.sh
```

### 2. Run Tests with VS Code REST Client
1. Open `voucher-api-tests.http` in VS Code
2. Install REST Client extension if not installed
3. Click "Send Request" for each endpoint
4. Verify responses match expected format

### 3. Run Complete Scenarios
1. Open `voucher-test-scenarios.http`
2. Run scenarios sequentially
3. Verify each step produces expected results

## Test Scenarios

### Scenario 1: Complete Voucher Lifecycle
1. **Login** - Get authentication token
2. **Browse Vouchers** - Get available vouchers
3. **Claim Voucher** - Claim a specific voucher
4. **Check Active** - Verify voucher appears in active list
5. **Use Voucher** - Use the claimed voucher
6. **Check History** - Verify voucher appears in past list

### Scenario 2: Error Handling
1. **Invalid Product** - Try to claim non-existent voucher
2. **Already Used** - Try to use already used voucher
3. **Expired Voucher** - Try to use expired voucher

### Scenario 3: Edge Cases
1. **Duplicate Claim** - Try to claim same voucher twice
2. **Empty Inventory** - Try to claim when no vouchers available

## Expected Responses

### Successful Claim Response
```json
{
  "statusCode": 201,
  "message": "Voucher claimed successfully",
  "data": {
    "transactionReferenceNumber": "TXN_123456",
    "gatewayId": 123,
    "productName": "Test Coffee Voucher",
    "status": "CLAIMED",
    "issuedAt": "2024-01-01T10:00:00Z"
  }
}
```

### Error Response
```json
{
  "statusCode": 400,
  "message": "No vouchers available for this product",
  "errorCode": "VOUCHERS_FULLY_REDEEMED"
}
```

## Test Data
Test data includes:
- Test user: `testuser` / `testpass`
- Test vouchers with various statuses
- Test transactions for history verification

## Troubleshooting
1. **Authentication Issues** - Check if login endpoint works
2. **Database Issues** - Verify test data setup script ran successfully
3. **Server Issues** - Ensure backend server is running and accessible