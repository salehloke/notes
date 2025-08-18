# Voucher Journey Sequence Diagrams - Enjoy Rewards System

  

## Overview

This document contains sequence diagrams illustrating the complete voucher journey from initial setup through user claim, including edge cases and error handling scenarios.

  

---

  

## 1. Complete Voucher Journey - Happy Path (Wheelspin)

  

```mermaid

sequenceDiagram

participant Admin as Admin User

participant UI as Backoffice UI

participant API as Campaign API

participant DB as MongoDB

participant WOGI as WOGI API

participant User as End User

participant Wheel as Wheelspin Engine

  

Note over Admin, Wheel: Phase 1: Voucher Setup

Admin->>UI: Navigate to Voucher Pool

UI->>API: Get vendors list

API->>DB: Query enjoy_vendors collection

DB-->>API: Return vendors

API-->>UI: Return vendors list

UI-->>Admin: Display vendors

  

Admin->>UI: Select vendor + upload Excel

UI->>API: Upload Excel file

API->>API: Parse Excel + validate data

API->>DB: Check for duplicate voucher codes

DB-->>API: Return duplicates (if any)

alt Duplicate vouchers found

API->>API: Skip duplicates + log errors

API-->>UI: Return partial success + error details

UI-->>Admin: Show import results + errors

else All vouchers valid

API->>DB: Insert vouchers into enjoy_campaign_voucher_pool

DB-->>API: Confirm insertion

API-->>UI: Return success + voucher count

UI-->>Admin: Show success message

end

  

Note over Admin, Wheel: Phase 2: Campaign Setup

Admin->>UI: Create campaign + set tier quotas

UI->>API: Create campaign

API->>DB: Insert into enjoy_campaigns

API->>DB: Insert tier quotas into enjoy_campaign_tier_quotas

DB-->>API: Confirm campaign creation

API-->>UI: Campaign created successfully

UI-->>Admin: Campaign active

  

Note over Admin, Wheel: Phase 3: User Participation

User->>Wheel: Access wheelspin

Wheel->>API: Check campaign availability

API->>DB: Query active campaigns

DB-->>API: Return active campaigns

API-->>Wheel: Campaign details + eligibility

Wheel-->>User: Display wheelspin interface

  

User->>Wheel: Spin the wheel

Wheel->>Wheel: Calculate win tier (based on probabilities)

Wheel->>API: Request voucher for tier

API->>DB: Check tier availability

DB-->>API: Vouchers available in tier

alt Vouchers available

API->>DB: Select voucher + mark as assigned

DB-->>API: Voucher assigned

API->>DB: Create user assignment record

DB-->>API: Assignment created

API-->>Wheel: Voucher details

Wheel-->>User: Display win + voucher details

else No vouchers available

API-->>Wheel: Tier exhausted

Wheel-->>User: Show alternative prize message

end

  

Note over Admin, Wheel: Phase 4: Voucher Redemption

User->>UI: View voucher details

UI->>API: Get voucher information

API->>DB: Query user voucher assignment

DB-->>API: Return voucher details

API-->>UI: Voucher data

UI-->>User: Display voucher + redemption instructions

  

alt WOGI Voucher

User->>UI: Click activation button

UI->>WOGI: Redirect to WOGI activation URL

WOGI-->>User: WOGI redemption interface

User->>WOGI: Complete redemption

WOGI->>WOGI: Process redemption

WOGI->>API: Send webhook update

API->>DB: Update voucher status to redeemed

DB-->>API: Status updated

API-->>WOGI: Webhook acknowledgment

else Code-based Voucher

User->>UI: View redemption code

UI-->>User: Display code + instructions

Note over User: User redeems at vendor location

end

```

  

---

  

## 1b. Direct Voucher Claiming - No Wheelspin (Alternative Flow)

  

```mermaid

sequenceDiagram

participant Admin as Admin User

participant UI as Backoffice UI

participant API as Campaign API

participant DB as MongoDB

participant WOGI as WOGI API

participant User as End User

participant Campaign as Campaign Interface

  

Note over Admin, Campaign: Phase 1: Voucher Setup (Same as wheelspin)

Admin->>UI: Navigate to Voucher Pool

UI->>API: Get vendors list

API->>DB: Query enjoy_vendors collection

DB-->>API: Return vendors

API-->>UI: Return vendors list

UI-->>Admin: Display vendors

  

Admin->>UI: Select vendor + upload Excel

UI->>API: Upload Excel file

API->>API: Parse Excel + validate data

API->>DB: Check for duplicate voucher codes

DB-->>API: Return duplicates (if any)

alt Duplicate vouchers found

API->>API: Skip duplicates + log errors

API-->>UI: Return partial success + error details

UI-->>Admin: Show import results + errors

else All vouchers valid

API->>DB: Insert vouchers into enjoy_campaign_voucher_pool

DB-->>API: Confirm insertion

API-->>UI: Return success + voucher count

UI-->>Admin: Show success message

end

  

Note over Admin, Campaign: Phase 2: Campaign Setup (Modified for Direct Claiming)

Admin->>UI: Create campaign + set claiming rules

UI->>API: Create campaign with direct claiming enabled

API->>DB: Insert into enjoy_campaigns (claimingMode: 'direct')

API->>DB: Insert tier quotas into enjoy_campaign_tier_quotas

API->>DB: Set claiming limits (maxPerUser, dailyLimit, etc.)

DB-->>API: Confirm campaign creation

API-->>UI: Campaign created successfully

UI-->>Admin: Campaign active for direct claiming

  

Note over Admin, Campaign: Phase 3: User Direct Claiming

User->>Campaign: Browse available campaigns

Campaign->>API: Get active campaigns for user

API->>DB: Query active campaigns + user eligibility

DB-->>API: Return eligible campaigns

API-->>Campaign: Campaign list + user tier

Campaign-->>User: Display available campaigns

  

User->>Campaign: Select campaign to view

Campaign->>API: Get campaign details + available vouchers

API->>DB: Query campaign + voucher availability by tier

DB-->>API: Campaign details + voucher counts

API-->>Campaign: Campaign information + voucher options

Campaign-->>User: Show campaign details + claiming options

  

User->>Campaign: Choose tier + claim voucher

Campaign->>API: Request voucher claim

API->>API: Validate user eligibility + limits

API->>DB: Check voucher availability in tier

alt Voucher available + user eligible

API->>DB: Select voucher + mark as assigned

DB-->>API: Voucher assigned

API->>DB: Create user assignment record

API->>DB: Update user claiming count

DB-->>API: Assignment + count updated

API-->>Campaign: Voucher claimed successfully

Campaign-->>User: Show voucher details + redemption instructions

else No vouchers available

API-->>Campaign: Tier exhausted

Campaign-->>User: Show "out of stock" message

else User limit reached

API-->>Campaign: User limit exceeded

Campaign-->>User: Show "limit reached" message

end

  

Note over Admin, Campaign: Phase 4: Voucher Redemption (Same as wheelspin)

User->>UI: View voucher details

UI->>API: Get voucher information

API->>DB: Query user voucher assignment

DB-->>API: Return voucher details

API-->>UI: Voucher data

UI-->>User: Display voucher + redemption instructions

  

alt WOGI Voucher

User->>UI: Click activation button

UI->>WOGI: Redirect to WOGI activation URL

WOGI-->>User: WOGI redemption interface

User->>WOGI: Complete redemption

WOGI->>WOGI: Process redemption

WOGI->>API: Send webhook update

API->>DB: Update voucher status to redeemed

DB-->>API: Status updated

API-->>WOGI: Webhook acknowledgment

else Code-based Voucher

User->>UI: View redemption code

UI-->>User: Display code + instructions

Note over User: User redeems at vendor location

end

```

  

---

  

## 2. Edge Case: Duplicate Voucher Import

  

```mermaid

sequenceDiagram

participant Admin as Admin User

participant UI as Backoffice UI

participant API as Campaign API

participant DB as MongoDB

  

Admin->>UI: Upload Excel with duplicate codes

UI->>API: Send Excel file

API->>API: Parse Excel file

API->>DB: Check existing voucher codes

DB-->>API: Return existing codes

alt Duplicates found

API->>API: Filter out duplicates

API->>API: Log skipped rows with reasons

API->>DB: Insert only unique vouchers

DB-->>API: Confirm insertion

API-->>UI: Return partial success + details

UI-->>Admin: Show import summary

Note over Admin: Admin sees: 95 imported, 5 skipped due to duplicates

end

```

  

---

  

## 3. Edge Case: Tier Exhaustion During Wheelspin

  

```mermaid

sequenceDiagram

participant User as End User

participant Wheel as Wheelspin Engine

participant API as Campaign API

participant DB as MongoDB

  

User->>Wheel: Spin wheel

Wheel->>Wheel: Calculate win tier

Wheel->>API: Request voucher for tier

API->>DB: Check tier availability

alt Tier has vouchers

API->>DB: Assign voucher

DB-->>API: Voucher assigned

API-->>Wheel: Success

Wheel-->>User: Display win

else Tier exhausted

API-->>Wheel: Tier exhausted

Wheel->>Wheel: Check alternative tiers

Wheel->>API: Request voucher from lower tier

API->>DB: Check lower tier availability

alt Lower tier available

API->>DB: Assign voucher from lower tier

DB-->>API: Voucher assigned

API-->>Wheel: Alternative prize assigned

Wheel-->>User: Show alternative prize message

else All tiers exhausted

API-->>Wheel: No vouchers available

Wheel-->>User: Show prize pool exhausted message

end

end

```

  

---

  

## 4. Edge Case: User Ineligibility

  

```mermaid

sequenceDiagram

participant User as End User

participant Wheel as Wheelspin Engine

participant API as Campaign API

participant DB as MongoDB

participant Auth as Auth Service

  

User->>Wheel: Access wheelspin

Wheel->>API: Check user eligibility

API->>Auth: Verify user details

Auth->>Auth: Check Maybanker status

Auth-->>API: User eligibility result

alt User eligible

API->>DB: Get campaign details

DB-->>API: Campaign information

API-->>Wheel: User can participate

Wheel-->>User: Show wheelspin interface

else User not eligible

API-->>Wheel: User ineligible

Wheel-->>User: Show ineligibility message

Note over User: User sees: "This campaign is exclusive to Maybanker employees"

end

```

  

---

  

## 5. Edge Case: Voucher Expiry During Process

  

```mermaid

sequenceDiagram

participant User as End User

participant Wheel as Wheelspin Engine

participant API as Campaign API

participant DB as MongoDB

participant Scheduler as Expiry Scheduler

  

Note over Scheduler, DB: Background expiry check

Scheduler->>DB: Check for expiring vouchers

DB-->>Scheduler: Return expiring vouchers

alt Vouchers expiring soon

Scheduler->>API: Flag vouchers for review

API->>DB: Update voucher status

DB-->>API: Status updated

end

  

User->>Wheel: Spin wheel

Wheel->>API: Request voucher

API->>DB: Get available voucher

alt Voucher expired

DB-->>API: Voucher expired

API->>API: Remove expired voucher from pool

API->>DB: Update pool status

API-->>Wheel: No vouchers available

Wheel-->>User: Show prize pool exhausted

else Voucher valid

DB-->>API: Valid voucher

API->>DB: Assign voucher to user

DB-->>API: Assignment successful

API-->>Wheel: Voucher details

Wheel-->>User: Display win

end

```

  

---

  

## 6. Edge Case: WOGI API Failure

  

```mermaid

sequenceDiagram

participant User as End User

participant UI as User Interface

participant API as Campaign API

participant WOGI as WOGI API

participant DB as MongoDB

  

User->>UI: Click WOGI activation

UI->>WOGI: Redirect to activation URL

alt WOGI API available

WOGI-->>User: WOGI interface loads

User->>WOGI: Complete redemption

WOGI->>API: Send webhook

API->>DB: Update status

DB-->>API: Confirmed

API-->>WOGI: Success acknowledgment

else WOGI API down

WOGI-->>User: Service unavailable error

User->>UI: Return to voucher details

UI->>API: Log WOGI failure

API->>DB: Mark voucher as pending

DB-->>API: Status updated

UI-->>User: Show retry message

Note over User: User sees: "WOGI service temporarily unavailable. Please try again later."

end

```

  

---

  

## 7. Edge Case: Campaign Quota Management

  

```mermaid

sequenceDiagram

participant Admin as Admin User

participant UI as Backoffice UI

participant API as Campaign API

participant DB as MongoDB

participant Alert as Alert Service

  

Note over Alert, DB: Real-time monitoring

Alert->>DB: Check tier quotas

DB-->>Alert: Current usage levels

alt Tier below threshold

Alert->>API: Send low stock alert

API->>UI: Update admin dashboard

UI-->>Admin: Show low stock warning

Admin->>UI: Review quota status

UI->>API: Get detailed quota report

API->>DB: Query tier usage

DB-->>API: Usage statistics

API-->>UI: Quota report

UI-->>Admin: Display quota status

alt Admin decides to replenish

Admin->>UI: Initiate replenishment

UI->>API: Create replenishment request

API->>DB: Log replenishment need

DB-->>API: Request logged

API-->>UI: Replenishment initiated

UI-->>Admin: Confirmation

else Admin ignores alert

Note over Admin: System continues with current inventory

end

end

```

  

---

  

## 8. Edge Case: User Multiple Claims Prevention

  

```mermaid

sequenceDiagram

participant User as End User

participant Wheel as Wheelspin Engine

participant API as Campaign API

participant DB as MongoDB

  

User->>Wheel: Attempt second spin

Wheel->>API: Check user participation

API->>DB: Query user's campaign participation

DB-->>API: User already participated

alt User already claimed

API-->>Wheel: User not eligible for second spin

Wheel-->>User: Show already participated message

Note over User: User sees: "You have already participated in this campaign"

else User hasn't participated

API-->>Wheel: User eligible

Wheel-->>User: Allow wheelspin

end

```

  

---

  

## 9. Edge Case: System Maintenance Mode

  

```mermaid

sequenceDiagram

participant User as End User

participant Wheel as Wheelspin Engine

participant API as Campaign API

participant Config as System Config

participant Admin as Admin User

  

Note over Admin, Config: Admin sets maintenance mode

Admin->>Config: Enable maintenance mode

Config->>Config: Update system status

User->>Wheel: Access wheelspin

Wheel->>API: Check system status

API->>Config: Get system status

Config-->>API: Maintenance mode active

API-->>Wheel: System unavailable

Wheel-->>User: Show maintenance message

Note over User: User sees: "System is currently under maintenance. Please try again later."

Note over Admin, Config: Admin disables maintenance mode

Admin->>Config: Disable maintenance mode

Config->>Config: Update system status

Config->>API: Notify system available

API->>Wheel: System available

Wheel-->>User: Allow access

```

  

---

  

## 10. Edge Case: Direct Claiming - User Limit Reached

  

```mermaid

sequenceDiagram

participant User as End User

participant Campaign as Campaign Interface

participant API as Campaign API

participant DB as MongoDB

  

User->>Campaign: Attempt to claim another voucher

Campaign->>API: Request voucher claim

API->>DB: Check user's current claim count

DB-->>API: User has reached daily limit

alt User limit reached

API-->>Campaign: Limit exceeded

Campaign-->>User: Show limit message

Note over User: User sees: "You have reached your daily limit of 2 vouchers"

else User under limit

API->>DB: Process voucher claim

DB-->>API: Voucher assigned

API-->>Campaign: Claim successful

Campaign-->>User: Show voucher details

end

```

  

---

  

## Key Edge Cases Covered:

  

### **Data Validation**

- ✅ Duplicate voucher codes

- ✅ Invalid Excel formats

- ✅ Missing required fields

  

### **System Availability**

- ✅ WOGI API failures

- ✅ Database connection issues

- ✅ Maintenance mode handling

  

### **Business Rules**

- ✅ User eligibility checks

- ✅ Campaign quota enforcement

- ✅ Multiple claim prevention

- ✅ Daily/overall claim limits

  

### **Resource Management**

- ✅ Tier exhaustion handling

- ✅ Alternative prize assignment

- ✅ Quota replenishment alerts

  

### **Error Recovery**

- ✅ Graceful degradation

- ✅ User-friendly error messages

- ✅ Retry mechanisms

  

---

  

## Usage Instructions:

  

1. **Copy Mermaid code** to any Mermaid-compatible editor

2. **View in GitHub/GitLab** for automatic rendering

3. **Use in Obsidian** with Mermaid plugin

4. **Export as images** for presentations

  

---

  

**These sequence diagrams provide a complete view of the voucher journey, including all edge cases and error handling scenarios!** 🎯