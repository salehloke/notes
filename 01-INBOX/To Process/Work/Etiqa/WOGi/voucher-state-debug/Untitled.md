# Voucher System Data Model & Architecture

## Overview

This document provides a comprehensive understanding of the voucher system's data model, business logic, and the relationship between different entities. It clarifies why both `voucherRewardTransactionModel` and `voucherInstanceModel` are needed and their distinct purposes.

## Data Model Architecture

### **Entity Relationship Diagram**

```mermaid
erDiagram
    RewardProductProperties ||--o{ EnjoyVoucherConfig : "gatewayId"
    EnjoyVoucherConfig ||--o{ EnjoyRewardVoucherInstance : "gatewayId"
    EnjoyRewardVoucherInstance ||--o{ EnjoyRewardTransaction : "transactionReferenceNumber"
    EnjoyRewardTransaction }o--|| MobileUser : "issuedTo.userId"
    EnjoyRewardVoucherInstance }o--|| MobileUser : "issuedTo.userId"

    RewardProductProperties {
        number gatewayId PK
        string name
        string description
        boolean isProductBeingShown
        number maxClaimedQuantityPerUser
        object brand
        object priceMin
        object priceMax
    }

    EnjoyVoucherConfig {
        number gatewayId PK
        string productName
        number maxClaimedQuantityPerUser
        number availableQuantity
        boolean isProductBeingShown
    }

    EnjoyRewardVoucherInstance {
        string _id PK
        number gatewayId FK
        string transactionReferenceNumber UK
        number cardId UK
        string productName
        string productAmount
        string status
        object issuedTo
        date issuedAt
        date expiresAt
        object usage
        object metadata
        array statusHistory
    }

    EnjoyRewardTransaction {
        string _id PK
        string transactionReferenceNumber FK
        number gatewayId FK
        string status
        object issuedTo
        date issuedAt
        date expiresAt
        object usage
        object metadata
    }

    MobileUser {
        string _id PK
        string userId
        string email
    }
```

## Business Logic Flow

### **Voucher Lifecycle Diagram**

```mermaid
stateDiagram-v2
    [*] --> CREATED : Voucher instance created
    
    CREATED --> CLAIMED : User claims voucher
    note right of CLAIMED
        - Voucher instance: status = CLAIMED
        - Transaction created: status = CLAIMED
        - issuedTo.userId = claiming user
    end note
    
    CLAIMED --> SUCCESS : User uses voucher
    note right of SUCCESS
        - Voucher instance: status = SUCCESS
        - Transaction: status = SUCCESS
        - usage.used = true
    end note
    
    CLAIMED --> EXPIRED : Voucher expires
    note right of EXPIRED
        - Voucher instance: status = EXPIRED
        - Transaction: status = EXPIRED
        - Voucher stays with original user
    end note
    
    SUCCESS --> EXPIRED : Post-usage expiration
    note right of EXPIRED
        - Voucher instance: status = EXPIRED
        - Transaction: status = EXPIRED
        - History preserved
    end note
```

## Entity Responsibilities

### **1. RewardProductProperties (Product Template)**

**Purpose**: Master product template and catalog
**Collection**: `reward.products`

```mermaid
graph TD
    A[Product Template] --> B[Gateway ID: 123]
    B --> C[Product Name: Burger Voucher]
    B --> D[Price: $10.00]
    B --> E[Brand: McDonald's]
    B --> F[Terms & Conditions]
    B --> G[Redemption Instructions]
```

**Key Fields**:
- `gatewayId`: Unique product identifier
- `name`, `description`: Product details
- `brand`: Brand information
- `priceMin`, `priceMax`: Pricing
- `isProductBeingShown`: Visibility flag

### **2. EnjoyVoucherConfig (Backoffice Configuration)**

**Purpose**: Backoffice configuration for product display
**Collection**: `enjoy.voucher.config`

```mermaid
graph TD
    A[Backoffice Config] --> B[Gateway ID: 123]
    B --> C[Max Claims Per User: 5]
    B --> D[Available Quantity: 1000]
    B --> E[Is Product Being Shown: true]
    B --> F[Display Settings]
```

**Key Fields**:
- `gatewayId`: Links to product template
- `maxClaimedQuantityPerUser`: Claim limits
- `availableQuantity`: Available inventory
- `isProductBeingShown`: Display control

### **3. EnjoyRewardVoucherInstance (Physical Voucher)**

**Purpose**: Individual voucher instances that can be assigned to users
**Collection**: `rewards.voucher.instances`

```mermaid
graph TD
    A[Voucher Instance #001] --> B[Card ID: 1001]
    A --> C[Transaction Ref: ABC123]
    A --> D[Status: CLAIMED]
    A --> E[Issued To: User A]
    A --> F[Product: Burger Voucher]
    A --> G[Status History]
```

**Key Fields**:
- `cardId`: Unique voucher instance identifier
- `transactionReferenceNumber`: Links to transaction
- `status`: Current voucher state
- `issuedTo`: Current owner
- `statusHistory`: Complete audit trail

### **4. EnjoyRewardTransaction (User's Voucher History)**

**Purpose**: Tracks user's complete voucher transaction history
**Collection**: `reward.transaction`

```mermaid
graph TD
    A[User Transaction] --> B[Transaction ID: TXN001]
    A --> C[User: User A]
    A --> D[Voucher: Instance #001]
    A --> E[Status: EXPIRED]
    A --> F[Claimed: 2024-01-01]
    A --> G[Expired: 2024-02-01]
```

**Key Fields**:
- `transactionReferenceNumber`: Links to voucher instance
- `issuedTo`: User who claimed
- `status`: Transaction status
- `issuedAt`: When claimed
- `expiresAt`: When expires

## Data Flow Diagrams

### **Voucher Claiming Process**

```mermaid
sequenceDiagram
    participant U as User
    participant API as API
    participant VI as Voucher Instance
    participant T as Transaction
    participant P as Product Config

    U->>API: Claim voucher (gatewayId: 123)
    API->>P: Check availability
    P-->>API: Available: true
    API->>VI: Find available instance
    VI-->>API: Instance #001 (status: CREATED)
    API->>VI: Update status to CLAIMED
    API->>VI: Set issuedTo = User
    API->>T: Create transaction record
    T-->>API: Transaction created
    API-->>U: Voucher claimed successfully
```

### **Voucher Usage Process**

```mermaid
sequenceDiagram
    participant U as User
    participant API as API
    participant VI as Voucher Instance
    participant T as Transaction

    U->>API: Use voucher (transactionRef: ABC123)
    API->>T: Find transaction
    T-->>API: Transaction found
    API->>VI: Find voucher instance
    VI-->>API: Instance found
    API->>VI: Update status to SUCCESS
    API->>VI: Add status history entry
    API->>T: Update status to SUCCESS
    API-->>U: Voucher used successfully
```

### **Voucher Expiration Process**

```mermaid
sequenceDiagram
    participant S as System
    participant VI as Voucher Instance
    participant T as Transaction

    S->>VI: Check for expired vouchers
    VI-->>S: Found expired instances
    S->>VI: Update status to EXPIRED
    S->>VI: Add status history entry
    S->>T: Update status to EXPIRED
    Note over S: Voucher stays with original user
```

## API Endpoint Mapping

### **Active Vouchers (Voucher Instance)**

```mermaid
graph LR
    A[GET /rewards/active-list] --> B[claimedRewardProductList]
    B --> C[voucherInstanceModel.find]
    C --> D[status: CLAIMED]
    C --> E[issuedTo.userId: currentUser]
```

**Purpose**: Show user's currently claimable vouchers
**Data Source**: `voucherInstanceModel`
**Filter**: `status: CLAIMED` + `issuedTo.userId: currentUser`

### **Past Transactions (Transaction Model)**

```mermaid
graph LR
    A[GET /rewards/past-list] --> B[rewardHistoriesByUser]
    B --> C[voucherRewardTransactionModel.find]
    C --> D[status: SUCCESS or EXPIRED]
    C --> E[issuedTo.userId: currentUser]
```

**Purpose**: Show user's complete voucher history
**Data Source**: `voucherRewardTransactionModel`
**Filter**: `status: [SUCCESS, EXPIRED]` + `issuedTo.userId: currentUser`

## Why Both Models Are Needed

### **Business Logic Requirements**

```mermaid
graph TD
    A[Voucher Instance] --> B[Physical Voucher Management]
    A --> C[Status Tracking]
    A --> D[Inventory Control]
    A --> E[Voucher Lifecycle]

    F[Transaction Model] --> G[User History]
    F --> H[Past Transactions]
    F --> I[Claim Validation]
    F --> J[Audit Trail]

    B --> K[Prevents Voucher Reuse]
    G --> L[Shows User's History]
```

### **Key Differences**

| Aspect | Voucher Instance | Transaction Model |
|--------|------------------|-------------------|
| **Purpose** | Physical voucher management | User's transaction history |
| **Reusability** | ❌ Cannot be reused | ✅ Historical record |
| **Status** | Current voucher state | Transaction status |
| **User Assignment** | Current owner | Original claimant |
| **Data Retention** | Permanent | Permanent |

## Migration Strategy (Updated)

### **Keep Both Models**

**Reason**: Both models serve distinct business purposes and cannot be consolidated without losing critical functionality.

### **Optimization Opportunities**

1. **Status History**: Already implemented in voucher instance
2. **Data Consistency**: Ensure both models stay in sync
3. **Performance**: Optimize queries for each use case
4. **Monitoring**: Track data consistency between models

### **Implementation Plan**

```mermaid
gantt
    title Voucher System Optimization Timeline
    dateFormat  YYYY-MM-DD
    section Current State
    Status History Implementation    :done,    history, 2024-01-01, 2024-01-15
    section Optimization
    Data Consistency Checks         :active,  checks,   2024-01-16, 2024-01-30
    Performance Optimization        :         perf,     2024-01-31, 2024-02-15
    Monitoring Implementation       :         monitor,  2024-02-16, 2024-02-28
```

## Conclusion

Both `voucherRewardTransactionModel` and `voucherInstanceModel` are essential components of the voucher system:

- **Voucher Instance**: Manages physical vouchers and prevents reuse
- **Transaction Model**: Tracks user history and provides audit trail

The key is maintaining data consistency between both models while optimizing for their specific use cases.



graph TD
    A[E2E Tests] --> B[Integration Tests]
    B --> C[Unit Tests]
    
    A1[Few E2E Tests] --> A2[Critical User Journeys]
    B1[API Integration Tests] --> B2[Database Integration]
    C1[Service Layer Tests] --> C2[Helper Method Tests]
    
    A1 -.-> A
    B1 -.-> B
    C1 -.-> C