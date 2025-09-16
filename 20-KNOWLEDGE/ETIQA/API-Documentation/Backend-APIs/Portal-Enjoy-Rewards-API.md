---
created: 2025-01-15
updated: 2025-01-15
status: complete
area: Work
tags: [work, api, documentation, reference, enjoy, backend]
module: ENJOY
service: Portal-Enjoy-Rewards
---

# API Documentation – Portal Enjoy Rewards API

## Service Overview
- **Base URL**: `/api/backoffice/portal-enjoy-rewards`
- **Service**: Portal Enjoy Rewards
- **Module**: ENJOY
- **Authentication**: JWT Bearer Token
- **Version**: v1
- **Controller**: `PortalEnjoyRewardsProductsController`

## Authentication
```http
Authorization: Bearer <jwt_token>
```

**Required Guards:**
- `AdminGuard` - Validates JWT token
- `BackofficeRoleGuard` - Validates admin roles

**Required Permissions:**
- `VIEW_ENJOY_REWARD` - For read operations
- `MANAGE_ENJOY_REWARD` - For write operations

## Endpoints

### Tracker & Reporting

#### Search Enjoy Reward Tracker
```http
GET /portal-enjoy-rewards/tracker/list
Authorization: Bearer <token>
```

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| query | string[] | No | Filter conditions |
| page | number | Yes | Page number |
| limit | number | Yes | Items per page |
| sort | string | No | Sort order |

**Response (200):**
```json
{
  "data": [
    {
      "id": "tracker_id",
      "eventName": "voucher_claimed",
      "timestamp": "2025-01-15T10:00:00Z",
      "userId": "user123",
      "voucherId": "voucher456"
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "limit": 20,
      "total": 100
    }
  }
}
```

#### Download Enjoy Rewards Report
```http
GET /portal-enjoy-rewards/rewards/report/download
Authorization: Bearer <token>
```

**Response:** Excel file download with filename: `Enjoy_Rewards_Summary_YYYYMMDD_HHMMSS.xlsx`

### Voucher Instance Management

#### Upload Voucher Instances (Code-Based)
```http
POST /portal-enjoy-rewards/rewards/code-based/upload-voucher-instance-list
Content-Type: application/json
Authorization: Bearer <token>
```

**Request:**
```json
{
  "data": [
    {
      "gatewayId": 12345,
      "productName": "Sample Voucher",
      "productAmount": 50.00,
      "transactionId": "TXN123456",
      "expiryDate": "2025-12-31T23:59:59Z",
      "redemptionCode": "REDEEM123",
      "activationRedeemURL": "https://provider.com/redeem/abc123",
      "isProductBeingShown": true,
      "maxClaimedQuantityPerUser": 1,
      "voucherCode": "VOUCHER_CODE_123"
    }
  ],
  "notes": "Bulk upload for campaign XYZ",
  "maxClaimedQuantityPerUser": 1,
  "isProductBeingShown": true,
  "campaignCode": "CAMPAIGN2025"
}
```

**Response (200) - Small Upload:**
```json
{
  "data": [
    {
      "process": "[Success] Voucher instance created successfully",
      "data": {
        "voucherInstance": {
          "_id": "voucher_id_123",
          "redemptionCode": "REDEEM123",
          "status": "AVAILABLE"
        },
        "product": {
          "gatewayId": 12345,
          "name": "Sample Voucher"
        }
      }
    }
  ]
}
```

**Response (200) - Large Upload (>200 vouchers):**
```json
{
  "message": "Large voucher upload initiated. Processing in background.",
  "totalVouchers": 5000,
  "status": "processing",
  "estimatedTime": "50 minutes"
}
```

#### Get Voucher Details
```http
GET /portal-enjoy-rewards/rewards/voucher/{voucherId}
Authorization: Bearer <token>
```

**Response (200):**
```json
{
  "data": {
    "_id": "voucher_id_123",
    "gatewayId": 12345,
    "redemptionCode": "REDEEM123",
    "activationRedeemURL": "https://provider.com/redeem/abc123",
    "productAmount": 50.00,
    "expiryDate": "2025-12-31T23:59:59Z",
    "status": "AVAILABLE",
    "createdAt": "2025-01-15T10:00:00Z",
    "updatedAt": "2025-01-15T10:00:00Z"
  }
}
```

#### Update Voucher Instance
```http
PUT /portal-enjoy-rewards/rewards/voucher/{voucherId}
Content-Type: application/json
Authorization: Bearer <token>
```

**Request:**
```json
{
  "redemptionCode": "NEW_REDEEM123",
  "activationRedeemURL": "https://newprovider.com/redeem/xyz789",
  "productAmount": 75.00,
  "expiryDate": "2025-12-31T23:59:59Z",
  "notes": "Updated voucher details"
}
```

### Product Catalog Management

#### Add Product Catalog
```http
POST /portal-enjoy-rewards/rewards/code-based/product-catalog
Content-Type: application/json
Authorization: Bearer <token>
```

**Request:**
```json
{
  "data": [
    {
      "name": "Premium Dining Voucher",
      "description": "Enjoy fine dining at premium restaurants",
      "descriptiveName": "Premium Restaurant Voucher",
      "validity": "Valid for 12 months",
      "priceMin": {
        "amount": 50,
        "currency": {
          "id": "MYR",
          "symbol": "RM",
          "isoCode": "MYR"
        }
      },
      "priceMax": {
        "amount": 200,
        "currency": {
          "id": "MYR", 
          "symbol": "RM",
          "isoCode": "MYR"
        }
      },
      "brand": {
        "objectClass": "Brand",
        "name": "Premium Restaurants",
        "category": "dining"
      },
      "isProductBeingShown": true,
      "maxClaimedQuantityPerUser": 2
    }
  ],
  "notes": "New product catalog for dining campaign"
}
```

#### Get Product Catalog List
```http
GET /portal-enjoy-rewards/rewards/product-catalog-list
Authorization: Bearer <token>
```

**Parameters:**
| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| page | number | Yes | Page number |
| limit | number | Yes | Items per page |
| search | string | No | Search term |

#### Delete Product Catalog
```http
DELETE /portal-enjoy-rewards/rewards/product-catalog/{productId}
Authorization: Bearer <token>
```

**Response (200):**
```json
{
  "message": "Product catalog deleted successfully"
}
```

### Voucher Configuration Management

#### Create Voucher Config
```http
POST /portal-enjoy-rewards/rewards/voucher-config
Content-Type: application/json
Authorization: Bearer <token>
```

**Request:**
```json
{
  "voucherCode": "DINING_VOUCHER_2025",
  "maxClaimedQuantityPerUser": 2,
  "maxPurchaseQuantityPerVoucher": 0,
  "availableQuantity": 1000,
  "totalClaimedQuantity": 0,
  "isProductBeingShown": true,
  "campaignCode": "DINING2025",
  "validity": "Valid until Dec 31, 2025",
  "noOfExpiryDaysAfterClaim": 90,
  "notes": "Dining voucher configuration for 2025 campaign"
}
```

#### Get Voucher Config
```http
GET /portal-enjoy-rewards/rewards/voucher-config/{productId}
Authorization: Bearer <token>
```

**Response (200):**
```json
{
  "data": {
    "_id": "config_id_123",
    "gatewayId": 12345,
    "voucherCode": "DINING_VOUCHER_2025",
    "maxClaimedQuantityPerUser": 2,
    "maxPurchaseQuantityPerVoucher": 0,
    "availableQuantity": 1000,
    "totalClaimedQuantity": 45,
    "isProductBeingShown": true,
    "campaignCode": "DINING2025",
    "validity": "Valid until Dec 31, 2025",
    "createdAt": "2025-01-15T10:00:00Z",
    "updatedAt": "2025-01-15T12:30:00Z",
    "vouchers": []
  }
}
```

#### Update Voucher Config
```http
PUT /portal-enjoy-rewards/rewards/voucher-config/{gatewayId}
Content-Type: application/json
Authorization: Bearer <token>
```

**Request:**
```json
{
  "maxClaimedQuantityPerUser": 3,
  "availableQuantity": 1500,
  "isProductBeingShown": false,
  "notes": "Updated campaign limits"
}
```

#### Delete Voucher Config
```http
DELETE /portal-enjoy-rewards/rewards/voucher-config/{gatewayId}
Authorization: Bearer <token>
```

**Response (200):**
```json
{
  "success": true
}
```

### Deals of the Month

#### Set Deals of the Month
```http
PUT /portal-enjoy-rewards/rewards/deals-of-month
Content-Type: application/json
Authorization: Bearer <token>
```

**Request:**
```json
{
  "productId": 12345,
  "isDealsOfMonth": true
}
```

**Response (200):**
```json
{
  "message": "Deals of the Month updated successfully"
}
```

#### Get Deals of the Month
```http
GET /portal-enjoy-rewards/rewards/deals-of-month
Authorization: Bearer <token>
```

**Response (200):**
```json
{
  "data": {
    "productId": 12345,
    "name": "Premium Dining Voucher",
    "isDealsOfMonth": true,
    "setAt": "2025-01-15T10:00:00Z"
  }
}
```

### Image Upload

#### Upload Voucher Background Image
```http
POST /portal-enjoy-rewards/rewards/voucher/upload-background-image
Content-Type: multipart/form-data
Authorization: Bearer <token>
```

**Form Data:**
```
backgroundImage: [FILE]
gatewayId: "12345"
notes: "Updated background for dining campaign"
```

**Response (200):**
```json
{
  "data": {
    "success": true,
    "message": "Background image uploaded successfully",
    "imageUrl": "https://storage.domain.com/vouchers/background/12345.jpg",
    "gatewayId": "12345",
    "imageType": "background"
  }
}
```

#### Upload Voucher Logo Image
```http
POST /portal-enjoy-rewards/rewards/voucher/upload-logo-image
Content-Type: multipart/form-data
Authorization: Bearer <token>
```

**Form Data:**
```
logoImage: [FILE]
gatewayId: "12345"
notes: "Brand logo for dining campaign"
```

### Global Configuration

#### Get Global Config
```http
GET /portal-enjoy-rewards/rewards/global-config
Authorization: Bearer <token>
```

#### Update Global Config
```http
PUT /portal-enjoy-rewards/rewards/global-config
Content-Type: application/json
Authorization: Bearer <token>
```

**Request:**
```json
{
  "maxVouchersPerUpload": 1000,
  "defaultExpiryDays": 90,
  "enableBackgroundProcessing": true
}
```

## Data Models

### VoucherInstance
```typescript
interface VoucherInstance {
  _id: string;
  gatewayId: number;
  productName: string;
  productAmount: number;
  transactionId?: string;
  expiryDate: Date;
  redemptionCode?: string;
  activationRedeemURL?: string;
  activationShortURL?: string;
  isProductBeingShown: boolean;
  maxClaimedQuantityPerUser: number;
  voucherCode?: string;
  status: 'AVAILABLE' | 'CLAIMED' | 'EXPIRED' | 'FAILED';
  createdAt: Date;
  updatedAt: Date;
  metadata?: {
    notes?: string;
    uploadBatch?: string;
    adminId?: string;
  };
}
```

### ProductCatalog
```typescript
interface ProductCatalog {
  gatewayId?: number;
  name: string;
  description?: string;
  descriptiveName?: string;
  validity?: string;
  productDiscountRate?: string;
  priceMin: Price;
  priceMax: Price;
  brand: Brand;
  isProductBeingShown: boolean;
  maxClaimedQuantityPerUser: number;
}

interface Price {
  amount: number;
  currency: {
    id: string;
    symbol: string;
    isoCode: string;
  };
}

interface Brand {
  objectClass: 'Brand';
  name: string;
  category: string;
  image?: string;
  logo?: string;
}
```

### VoucherConfig
```typescript
interface VoucherConfig {
  _id: string;
  gatewayId: number;
  voucherCode: string;
  productName?: string;
  maxClaimedQuantityPerUser: number;
  maxPurchaseQuantityPerVoucher: number;
  availableQuantity: number;
  totalClaimedQuantity: number;
  isProductBeingShown: boolean;
  campaignCode?: string;
  validity?: string;
  noOfExpiryDaysAfterClaim?: number;
  createdAt: Date;
  updatedAt: Date;
  vouchers: VoucherInstance[];
}
```

## Error Codes
| Code | HTTP Status | Description |
|------|-------------|-------------|
| VALIDATION_ERROR | 400 | Input validation failed |
| UNAUTHORIZED | 401 | Invalid or missing JWT token |
| FORBIDDEN | 403 | Insufficient permissions |
| NOT_FOUND | 404 | Resource not found |
| DUPLICATE_RESOURCE | 409 | Duplicate voucher code or resource |
| INTERNAL_ERROR | 500 | Server internal error |

## Performance Features

### Asynchronous Processing
- **High-Volume Threshold**: >200 vouchers trigger background processing
- **Event-Driven**: Uses EventEmitter2 for non-blocking operations
- **Progress Tracking**: Real-time status updates for large uploads

### Validation & Security
- **Strict Validation**: ValidationPipe with whitelisting
- **Role-Based Access**: Permission checks on all endpoints
- **File Upload Security**: Multipart form validation
- **Duplicate Prevention**: Multiple validation layers

### Monitoring & Logging
- **Comprehensive Tracking**: Request/response logging
- **Error Categorization**: Detailed error classification
- **Admin Activity**: Audit trail for all operations
- **Performance Metrics**: Processing time estimation

## Usage Examples

### Bulk Voucher Upload
```bash
curl -X POST \
  "http://localhost:10100/api/backoffice/portal-enjoy-rewards/rewards/code-based/upload-voucher-instance-list" \
  -H "Authorization: Bearer <token>" \
  -H "Content-Type: application/json" \
  -d '{
    "data": [
      {
        "gatewayId": 12345,
        "productName": "Test Voucher",
        "productAmount": 50,
        "expiryDate": "2025-12-31T23:59:59Z",
        "redemptionCode": "TEST123",
        "isProductBeingShown": true,
        "maxClaimedQuantityPerUser": 1
      }
    ],
    "notes": "Test upload",
    "maxClaimedQuantityPerUser": 1,
    "isProductBeingShown": true
  }'
```

### Image Upload Example
```bash
curl -X POST \
  "http://localhost:10100/api/backoffice/portal-enjoy-rewards/rewards/voucher/upload-background-image" \
  -H "Authorization: Bearer <token>" \
  -F "backgroundImage=@/path/to/image.jpg" \
  -F "gatewayId=12345" \
  -F "notes=Campaign background image"
```

## Related APIs
- [[Auth-Service-API]] - Authentication service
- [[Smile-Service-API]] - Main customer services
- [[WOGI-Provider-API]] - External voucher provider

## Related Work
- [[Task {ENJOY} ES-3813- To Fix Enjoy Rewards GE Tracker]]
- [[Enjoy-Rewards-System-Architecture]]
- [[Enjoy Rewards - Consolidated Flow]]

## Notes
- **Voucher Business Rule**: Each voucher must have either `redemptionCode` OR `activationRedeemURL`
- **Large Upload Handling**: Files >200 vouchers are processed asynchronously to prevent UI freezing
- **Duplicate Detection**: System checks both redemption codes and activation URLs for duplicates
- **Image Storage**: Uses MinIO cloud storage for voucher images
- **Campaign Isolation**: One Million Campaign uses separate flows and should not mix with normal rewards

---
*Last updated: 2025-01-15*
*Environment: Local/SIT/UAT/PRD*
*Base URL: http://localhost:10100 (local)*