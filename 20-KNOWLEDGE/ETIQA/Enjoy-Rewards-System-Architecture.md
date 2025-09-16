---
created: 2025-01-15
updated: 2025-01-15
status: complete
area: Work
tags: [work, enjoy, architecture, documentation]
module: ENJOY
---

# Enjoy Rewards System Architecture

## Overview
Comprehensive analysis of the Enjoy Rewards system implementation across the Smile AIO platform, covering the admin interface, backend APIs, and customer interface.

## System Architecture

The Enjoy Rewards system follows a 3-tier architecture:
- **Admin Interface**: Next.js admin panel for voucher/product management
- **Backend**: NestJS APIs handling business logic and data management  
- **Customer Interface**: Next.js customer-facing application for voucher redemption

## Admin Interface (BackOffice-X)

### Location
```
smile-aio/backoffice-x/src/app/(site)/enjoy-rewards/
```

### Key Features
1. **Voucher Creation & Management**
   - Manual voucher creation via stepper wizard
   - Bulk voucher upload via Excel (with 1000 voucher limit)
   - Voucher instance management with duplicate checking
   - Image upload for background and logo assets

2. **Product Management**
   - Product catalog list management
   - Product configuration and properties
   - Provider product synchronization (WOGI integration)
   - Category setup and management

3. **Monitoring & Reporting**
   - Enjoy rewards tracker logs
   - Excel report generation
   - Voucher status monitoring
   - Admin activity tracking

### Technical Stack
- **Framework**: Next.js 14.0.4 with App Router
- **UI Library**: Flowbite React, Radix UI components
- **State Management**: React Query (TanStack Query)
- **Forms**: React Hook Form with Zod validation
- **File Processing**: ExcelJS for Excel uploads
- **Styling**: TailwindCSS

### Key Components

#### VoucherCreationStepper
Multi-step wizard for creating vouchers manually:
- Basic Product Info Step
- Voucher Configuration Step  
- Voucher Instance Step
- Redemption Terms Step

#### VoucherUploadModal
Handles bulk voucher upload with:
- Excel file validation
- 1000 voucher hard limit (configurable)
- Duplicate checking with async batch processing
- Progress tracking and error handling

#### VoucherInstanceManager
Core component for voucher processing:
- Asynchronous batch processing (500 vouchers per batch)
- Duplicate detection using Set-based O(1) lookups
- Debug logging for performance monitoring
- Memory-efficient processing with `setTimeout` yielding

### API Integration
Frontend communicates with backend via axios service layer:
```typescript
// Base path: /api/backoffice/portal-enjoy-rewards
const basePath = "/api/backoffice/portal-enjoy-rewards";

// Key endpoints:
- uploadVoucherInstances() // Standard upload
- uploadVoucherInstancesInBackground() // High-volume chunked upload  
- getProductListData()
- getCategoryGroupingListData()
- syncProductList()
```

## Backend (NestJS APIs)

### Location
```
smile-aio/backend/apps/backoffice/src/portal/portal-enjoy-rewards/
```

### Architecture Pattern
- **Controller**: `portal-enjoy-rewards.controller.ts` - HTTP request handling
- **Service**: `portal-enjoy-rewards.service.ts` - Business logic implementation
- **DTOs**: Type-safe data transfer objects with validation
- **Guards**: Role-based access control (AdminGuard, BackOfficeRoleGuard)

### Key API Endpoints

#### Voucher Management
```typescript
// High-volume voucher upload with async processing
@Post('rewards/code-based/upload-voucher-instance-list')
async excelUploadCodeBasedVoucherInstanceList()

// Standard voucher upload 
@Post('rewards/upload-voucher-list')
async excelUploadVoucherList()

// Individual voucher operations
@Get('rewards/voucher/:voucherId')
@Put('rewards/voucher/:voucherId')
```

#### Product Catalog Management
```typescript
// Product catalog CRUD operations
@Get('rewards/product-catalog-list')
@Post('rewards/code-based/product-catalog') 
@Delete('rewards/product-catalog/:productId')

// Deals of the Month feature
@Get('rewards/deals-of-month')
@Put('rewards/deals-of-month')
```

#### Asset Management
```typescript
// Voucher image uploads
@Post('rewards/voucher/upload-background-image')
@Post('rewards/voucher/upload-logo-image')
```

### Business Logic Features

#### Performance Optimization
- **High-Count Detection**: Requests >200 vouchers trigger async processing
- **Event-Driven Architecture**: Uses EventEmitter2 for background processing
- **Immediate Response**: Returns status for large uploads to prevent UI freezing

#### Security & Validation
- **JWT Authentication**: Bearer token validation on all endpoints
- **Role-Based Access**: Permission checks via decorators
- **Input Validation**: ValidationPipe with DTO transformations
- **File Upload Security**: Multipart form validation for images

#### Integration Points
- **WOGI Provider**: External voucher provider integration
- **MongoDB**: Primary data storage via Mongoose
- **Redis**: Caching layer for performance
- **File Storage**: Asset management for voucher images

## Customer Interface (Micro-site/Enjoy)

### Location
```
smile-aio/micro-site/enjoy/
```

### Purpose
Customer-facing application for voucher browsing and redemption

### Technical Stack
- **Framework**: Next.js 15.1.3 with App Router
- **React**: v19.0.0 (latest)
- **UI Library**: Radix UI with custom components
- **State Management**: TanStack React Query v5.64.1
- **Styling**: TailwindCSS with animations
- **Forms**: React Hook Form v7.54.2

### Key Features
1. **Authentication & Session Management**
   - Secure storage for user sessions
   - JWT token handling
   - Session expiry management

2. **Voucher Operations**
   - Browse voucher categories
   - View voucher details
   - My rewards dashboard
   - Active/past voucher management
   - Terms & conditions display

3. **User Experience**
   - Mobile-responsive design (runs on port 11600)
   - Lottie animations for loading states
   - Progressive Web App capabilities
   - Offline support considerations

### API Integration
```typescript
// Base API path: /api/v5/third-party/rewards/
const basePath = "/api/v5/third-party/rewards/";

// Key service methods:
- ListCategoryResponse // Voucher categories
- Voucher redemption APIs
- User voucher history
```

### Routing Structure
```
/(site)/
  ├── my-rewards/
  │   ├── active-voucher/[id]/
  │   ├── past-voucher/[id]/
  │   └── page.tsx
  ├── voucher-details/[gatewayId]/
  ├── voucher-list-by-category/[category-id]/
  └── session-expired/
```

## Data Flow Architecture

### Voucher Creation Flow
1. **Admin Upload** (Admin Interface)
   - Excel file parsed client-side
   - Data validation and duplicate checking
   - Batch processing for large uploads
   
2. **API Processing** (Backend)
   - DTO validation and transformation
   - Business logic execution
   - Database persistence
   - Event emission for async processing

3. **Customer Access** (Customer Interface)
   - Authenticated API calls
   - Real-time voucher status
   - Redemption tracking

### Performance Optimizations

#### Frontend (Admin Interface)
- **Async Batch Processing**: 500-voucher chunks with `setTimeout` yielding
- **Memory Management**: Set-based duplicate detection (O(1) lookups)
- **Hard Limits**: 1000 voucher maximum to prevent memory issues
- **Progress Feedback**: Real-time upload status and error reporting

#### Backend
- **Threshold-Based Processing**: >200 vouchers trigger background processing
- **Event-Driven Architecture**: Non-blocking async processing
- **Chunked Responses**: Immediate API responses for large operations
- **Connection Pooling**: Efficient database resource management

#### Customer Interface
- **React Query**: Intelligent caching and background updates
- **Code Splitting**: Lazy loading for optimal bundle size
- **Mobile Optimization**: Responsive design with touch interactions

## Technology Integration Points

### External Services
- **WOGI Provider**: Third-party voucher provider integration
- **MongoDB**: Primary database with Mongoose ODM
- **Redis**: Caching and session management
- **File Storage**: Asset management for voucher images

### Development Tools
- **TypeScript**: Full type safety across all layers
- **ESLint/Prettier**: Code quality and formatting
- **Zod**: Runtime type validation
- **React Hook Form**: Form state management
- **TanStack Query**: Server state synchronization

## Security Considerations

### Authentication & Authorization
- JWT-based authentication with refresh tokens
- Role-based access control (RBAC)
- Permission-based API endpoint protection
- Secure session storage

### Data Protection
- Input validation and sanitization
- File upload security measures
- SQL injection prevention via ORMs
- XSS protection through React's built-in escaping

### API Security
- Bearer token validation
- Rate limiting considerations
- CORS configuration
- Request/response validation

## Scalability & Performance

### Current Limitations
- 1000 voucher frontend limit (configurable)
- 200 voucher backend async threshold
- Single-threaded duplicate checking
- In-memory processing constraints

### Optimization Strategies
- Batch processing with configurable chunk sizes
- Event-driven architecture for long-running operations
- Caching layers for frequently accessed data
- Database indexing for query optimization

## Monitoring & Observability

### Logging
- Comprehensive debug logging with emojis (📤, 📝, 🚀, 🌐, 🔄)
- Performance timing measurements
- Error tracking and reporting
- Admin activity audit trails

### Metrics
- Upload success/failure rates
- Processing times for different batch sizes
- Memory usage during operations
- API response times

## Deployment Configuration

### Development Ports
- **Customer Interface**: 11600
- **Admin Interface**: 11400 (inferred from architecture)

### Environment Management
- Separate configurations for local/SIT/UAT/PRD
- Environment-specific build processes
- Docker containerization support

## Related Work
- [[Task {ENJOY} ES-3813- To Fix Enjoy Rewards GE Tracker]]

## References
- smile-aio/backoffice-x/src/app/(site)/enjoy-rewards/
- smile-aio/backend/apps/backoffice/src/portal/portal-enjoy-rewards/
- smile-aio/micro-site/enjoy/

---

*Analysis conducted on: 2025-01-15*
*Repository: smile-aio-2/smile-aio*
*Systems analyzed: backoffice-x, backend, micro-site/enjoy*