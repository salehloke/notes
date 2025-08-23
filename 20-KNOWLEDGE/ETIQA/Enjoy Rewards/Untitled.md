# Enjoy Rewards System - Data Flow Diagrams (DFD)

  

## Overview

This document contains Data Flow Diagrams (DFD) for the Enjoy Rewards system, showing how data flows between different system components, external entities, and data stores.

  

---

  

## 1. Context Level DFD (Level 0)

  

```plantuml

@startuml Context Level DFD

title Enjoy Rewards System - Context Level DFD

  

!define RECTANGLE class

  

package "External Entities" {

[Admin Users] as ADMIN

[End Users] as USERS

[Vendors] as VENDORS

[Payment Gateways] as PAYMENT

}

  

package "Enjoy Rewards System" {

[Enjoy Rewards Core] as CORE

}

  

package "External Systems" {

[Analytics Platform] as ANALYTICS

[Notification Service] as NOTIFY

[Authentication Service] as AUTH

}

  

ADMIN --> CORE : Manage voucher pool\nConfigure campaigns\nMonitor performance

USERS --> CORE : Participate in wheelspin\nClaim vouchers\nRedeem vouchers

VENDORS --> CORE : Provide voucher inventory\nUpdate voucher status

CORE --> PAYMENT : Process payments\nValidate transactions

CORE --> ANALYTICS : Send usage data\nPerformance metrics

CORE --> NOTIFY : Send notifications\nAlerts and reminders

CORE --> AUTH : Verify user identity\nCheck permissions

  

@enduml

```

  

---

  

## 2. Level 1 DFD - Main System Processes

  

```plantuml

@startuml Level 1 DFD

title Enjoy Rewards System - Level 1 DFD

  

!define RECTANGLE class

  

package "External Entities" {

[Admin Users] as ADMIN

[End Users] as USERS

[Vendors] as VENDORS

}

  

package "Main Processes" {

[1.0\nVoucher Pool\nManagement] as POOL_MGMT

[2.0\nCampaign\nManagement] as CAMPAIGN_MGMT

[3.0\nWheelspin\nEngine] as WHEELSPIN

[4.0\nVoucher\nAssignment] as ASSIGNMENT

[5.0\nUser Voucher\nManagement] as USER_MGMT

[6.0\nAnalytics &\nReporting] as ANALYTICS

}

  

package "Data Stores" {

[Voucher Pool] as POOL_DB

[Campaigns] as CAMPAIGN_DB

[User Vouchers] as USER_DB

[Vendor Master] as VENDOR_DB

[System Logs] as LOGS_DB

}

  

package "External Services" {

[Notification\nService] as NOTIFY

[Payment\nService] as PAYMENT

[Auth Service] as AUTH

}

  

' Admin flows

ADMIN --> POOL_MGMT : Add/Edit vouchers\nManage inventory

ADMIN --> CAMPAIGN_MGMT : Create campaigns\nSet quotas

ADMIN --> ANALYTICS : View reports\nMonitor performance

  

' Voucher pool flows

VENDORS --> POOL_MGMT : Provide voucher data

POOL_MGMT --> POOL_DB : Store voucher info

POOL_MGMT --> VENDOR_DB : Update vendor data

  

' Campaign flows

CAMPAIGN_MGMT --> CAMPAIGN_DB : Store campaign config

CAMPAIGN_MGMT --> POOL_DB : Check voucher availability

  

' User flows

USERS --> WHEELSPIN : Participate in wheelspin

WHEELSPIN --> CAMPAIGN_DB : Get campaign rules

WHEELSPIN --> POOL_DB : Check voucher availability

WHEELSPIN --> ASSIGNMENT : Trigger voucher assignment

  

' Assignment flows

ASSIGNMENT --> POOL_DB : Select voucher from pool

ASSIGNMENT --> USER_DB : Create user voucher record

ASSIGNMENT --> NOTIFY : Send win notification

  

' User management flows

USERS --> USER_MGMT : View/manage vouchers

USER_MGMT --> USER_DB : Retrieve user vouchers

USER_MGMT --> NOTIFY : Send expiry reminders

  

' Analytics flows

ANALYTICS --> USER_DB : Collect user data

ANALYTICS --> CAMPAIGN_DB : Collect campaign data

ANALYTICS --> POOL_DB : Collect pool data

ANALYTICS --> LOGS_DB : Store analytics data

  

@enduml

```

  

---

  

## 3. Level 2 DFD - Voucher Pool Management

  

```plantuml

@startuml Voucher Pool Management DFD

title Voucher Pool Management - Level 2 DFD

  

!define RECTANGLE class

  

package "External Entities" {

[Admin Users] as ADMIN

[Vendors] as VENDORS

}

  

package "Voucher Pool Processes" {

[1.1\nAdd Vouchers] as ADD_VOUCHERS

[1.2\nUpdate Inventory] as UPDATE_INV

[1.3\nTier Assignment] as TIER_ASSIGN

[1.4\nExpiry Management] as EXPIRY_MGMT

[1.5\nPool Monitoring] as POOL_MONITOR

}

  

package "Data Stores" {

[Voucher Pool] as POOL_DB

[Vendor Master] as VENDOR_DB

[Tier Configuration] as TIER_DB

[Inventory Logs] as INVENTORY_LOG

}

  

package "External Services" {

[Notification\nService] as NOTIFY

[Validation\nService] as VALIDATE

}

  

' Admin flows

ADMIN --> ADD_VOUCHERS : Input voucher details

ADMIN --> TIER_ASSIGN : Set tier levels

ADMIN --> POOL_MONITOR : View pool status

  

' Vendor flows

VENDORS --> ADD_VOUCHERS : Provide voucher data

VENDORS --> UPDATE_INV : Update voucher status

  

' Process flows

ADD_VOUCHERS --> VALIDATE : Validate voucher data

ADD_VOUCHERS --> POOL_DB : Store voucher info

ADD_VOUCHERS --> VENDOR_DB : Update vendor info

  

TIER_ASSIGN --> TIER_DB : Get tier configuration

TIER_ASSIGN --> POOL_DB : Update voucher tier

  

UPDATE_INV --> POOL_DB : Modify inventory

UPDATE_INV --> INVENTORY_LOG : Log changes

  

EXPIRY_MGMT --> POOL_DB : Check expiry dates

EXPIRY_MGMT --> NOTIFY : Send expiry alerts

EXPIRY_MGMT --> POOL_DB : Mark expired vouchers

  

POOL_MONITOR --> POOL_DB : Read pool status

POOL_MONITOR --> INVENTORY_LOG : Read inventory history

  

@enduml

```

  

---

  

## 4. Level 2 DFD - Campaign Management

  

```plantuml

@startuml Campaign Management DFD

title Campaign Management - Level 2 DFD

  

!define RECTANGLE class

  

package "External Entities" {

[Admin Users] as ADMIN

}

  

package "Campaign Processes" {

[2.1\nCreate Campaign] as CREATE_CAMP

[2.2\nConfigure Quotas] as CONFIG_QUOTA

[2.3\nSet Probabilities] as SET_PROB

[2.4\nCampaign Control] as CAMP_CONTROL

[2.5\nPerformance\nMonitoring] as PERF_MONITOR

}

  

package "Data Stores" {

[Campaigns] as CAMPAIGN_DB

[Tier Quotas] as QUOTA_DB

[Win Probabilities] as PROB_DB

[Campaign Logs] as CAMP_LOG

}

  

package "External Services" {

[Validation\nService] as VALIDATE

[Notification\nService] as NOTIFY

}

  

' Admin flows

ADMIN --> CREATE_CAMP : Input campaign details

ADMIN --> CONFIG_QUOTA : Set tier quotas

ADMIN --> SET_PROB : Configure win probabilities

ADMIN --> CAMP_CONTROL : Start/Stop campaigns

ADMIN --> PERF_MONITOR : View performance

  

' Process flows

CREATE_CAMP --> VALIDATE : Validate campaign data

CREATE_CAMP --> CAMPAIGN_DB : Store campaign info

  

CONFIG_QUOTA --> QUOTA_DB : Store quota settings

CONFIG_QUOTA --> CAMPAIGN_DB : Link quotas to campaign

  

SET_PROB --> PROB_DB : Store probability settings

SET_PROB --> CAMPAIGN_DB : Link probabilities to campaign

  

CAMP_CONTROL --> CAMPAIGN_DB : Update campaign status

CAMP_CONTROL --> NOTIFY : Send campaign notifications

  

PERF_MONITOR --> CAMPAIGN_DB : Read campaign data

PERF_MONITOR --> CAMP_LOG : Read performance logs

  

@enduml

```

  

---

  

## 5. Level 2 DFD - Wheelspin Engine

  

```plantuml

@startuml Wheelspin Engine DFD

title Wheelspin Engine - Level 2 DFD

  

!define RECTANGLE class

  

package "External Entities" {

[End Users] as USERS

}

  

package "Wheelspin Processes" {

[3.1\nUser Authentication] as USER_AUTH

[3.2\nEligibility Check] as ELIGIBILITY

[3.3\nWheelspin Logic] as SPIN_LOGIC

[3.4\nWin Determination] as WIN_DETERMINE

[3.5\nResult Processing] as RESULT_PROC

}

  

package "Data Stores" {

[User Profiles] as USER_DB

[Campaigns] as CAMPAIGN_DB

[Tier Quotas] as QUOTA_DB

[Win Probabilities] as PROB_DB

[Spin History] as SPIN_LOG

}

  

package "External Services" {

[Auth Service] as AUTH

[Notification\nService] as NOTIFY

}

  

' User flows

USERS --> USER_AUTH : Login/Verify identity

USERS --> SPIN_LOGIC : Trigger wheelspin

  

' Process flows

USER_AUTH --> AUTH : Verify user credentials

USER_AUTH --> USER_DB : Get user profile

  

ELIGIBILITY --> CAMPAIGN_DB : Check campaign rules

ELIGIBILITY --> USER_DB : Verify user eligibility

  

SPIN_LOGIC --> ELIGIBILITY : Check eligibility first

SPIN_LOGIC --> SPIN_LOG : Log spin attempt

  

WIN_DETERMINE --> PROB_DB : Get win probabilities

WIN_DETERMINE --> QUOTA_DB : Check tier availability

WIN_DETERMINE --> SPIN_LOG : Record spin result

  

RESULT_PROC --> NOTIFY : Send win notification

RESULT_PROC --> SPIN_LOG : Update spin history

RESULT_PROC --> USER_DB : Update user status

  

@enduml

```

  

---

  

## 6. Level 2 DFD - Voucher Assignment

  

```plantuml

@startuml Voucher Assignment DFD

title Voucher Assignment - Level 2 DFD

  

!define RECTANGLE class

  

package "External Entities" {

[Wheelspin Engine] as WHEELSPIN

}

  

package "Assignment Processes" {

[4.1\nTier Selection] as TIER_SELECT

[4.2\nVoucher Selection] as VOUCHER_SELECT

[4.3\nPool Update] as POOL_UPDATE

[4.4\nUser Record\nCreation] as USER_RECORD

[4.5\nAssignment\nConfirmation] as ASSIGN_CONFIRM

}

  

package "Data Stores" {

[Voucher Pool] as POOL_DB

[User Vouchers] as USER_DB

[Assignment Logs] as ASSIGN_LOG

[Tier Configuration] as TIER_DB

}

  

package "External Services" {

[Notification\nService] as NOTIFY

[Analytics\nService] as ANALYTICS

}

  

' Input flows

WHEELSPIN --> TIER_SELECT : Win tier information

  

' Process flows

TIER_SELECT --> TIER_DB : Get tier configuration

TIER_SELECT --> VOUCHER_SELECT : Pass tier info

  

VOUCHER_SELECT --> POOL_DB : Query available vouchers

VOUCHER_SELECT --> POOL_UPDATE : Pass selected voucher

  

POOL_UPDATE --> POOL_DB : Remove voucher from pool

POOL_UPDATE --> ASSIGN_LOG : Log pool change

  

USER_RECORD --> USER_DB : Create user voucher record

USER_RECORD --> ASSIGN_LOG : Log assignment

  

ASSIGN_CONFIRM --> NOTIFY : Send confirmation

ASSIGN_CONFIRM --> ANALYTICS : Update metrics

ASSIGN_CONFIRM --> ASSIGN_LOG : Log confirmation

  

@enduml

```

  

---

  

## 7. Level 2 DFD - User Voucher Management

  

```plantuml

@startuml User Voucher Management DFD

title User Voucher Management - Level 2 DFD

  

!define RECTANGLE class

  

package "External Entities" {

[End Users] as USERS

}

  

package "User Management Processes" {

[5.1\nVoucher Display] as VOUCHER_DISPLAY

[5.2\nExpiry Monitoring] as EXPIRY_MONITOR

[5.3\nRedemption\nProcessing] as REDEMPTION

[5.4\nStatus Updates] as STATUS_UPDATE

[5.5\nUser Analytics] as USER_ANALYTICS

}

  

package "Data Stores" {

[User Vouchers] as USER_DB

[Voucher Pool] as POOL_DB

[Redemption History] as REDEMPTION_DB

[User Activity] as ACTIVITY_DB

}

  

package "External Services" {

[Notification\nService] as NOTIFY

[Payment\nService] as PAYMENT

[Analytics\nService] as ANALYTICS

}

  

' User flows

USERS --> VOUCHER_DISPLAY : View vouchers

USERS --> REDEMPTION : Redeem vouchers

  

' Process flows

VOUCHER_DISPLAY --> USER_DB : Get user vouchers

VOUCHER_DISPLAY --> POOL_DB : Get voucher details

  

EXPIRY_MONITOR --> USER_DB : Check expiry dates

EXPIRY_MONITOR --> NOTIFY : Send expiry reminders

  

REDEMPTION --> USER_DB : Validate voucher

REDEMPTION --> PAYMENT : Process payment if needed

REDEMPTION --> REDEMPTION_DB : Log redemption

REDEMPTION --> STATUS_UPDATE : Update voucher status

  

STATUS_UPDATE --> USER_DB : Update voucher status

STATUS_UPDATE --> ACTIVITY_DB : Log user activity

  

USER_ANALYTICS --> USER_DB : Collect user data

USER_ANALYTICS --> ACTIVITY_DB : Collect activity data

USER_ANALYTICS --> ANALYTICS : Send analytics data

  

@enduml

```

  

---

  

## 8. Level 2 DFD - Analytics and Reporting

  

```plantuml

@startuml Analytics and Reporting DFD

title Analytics and Reporting - Level 2 DFD

  

!define RECTANGLE class

  

package "External Entities" {

[Admin Users] as ADMIN

[System Processes] as SYSTEM

}

  

package "Analytics Processes" {

[6.1\nData Collection] as DATA_COLLECT

[6.2\nData Processing] as DATA_PROCESS

[6.3\nMetrics Calculation] as METRICS_CALC

[6.4\nReport Generation] as REPORT_GEN

[6.5\nData Export] as DATA_EXPORT

}

  

package "Data Stores" {

[Raw Data] as RAW_DB

[Processed Data] as PROCESSED_DB

[Analytics Results] as ANALYTICS_DB

[Report Templates] as REPORT_DB

}

  

package "External Services" {

[Notification\nService] as NOTIFY

[Export Service] as EXPORT

}

  

' Input flows

SYSTEM --> DATA_COLLECT : Send system data

ADMIN --> REPORT_GEN : Request reports

  

' Process flows

DATA_COLLECT --> RAW_DB : Store raw data

DATA_COLLECT --> DATA_PROCESS : Pass data for processing

  

DATA_PROCESS --> RAW_DB : Read raw data

DATA_PROCESS --> PROCESSED_DB : Store processed data

  

METRICS_CALC --> PROCESSED_DB : Read processed data

METRICS_CALC --> ANALYTICS_DB : Store calculated metrics

  

REPORT_GEN --> ANALYTICS_DB : Read metrics

REPORT_GEN --> REPORT_DB : Get report templates

REPORT_GEN --> NOTIFY : Send report notifications

  

DATA_EXPORT --> ANALYTICS_DB : Read analytics data

DATA_EXPORT --> EXPORT : Export data in various formats

  

@enduml

```

  

---

  

## 9. Data Dictionary

  

### **Data Stores**

  

#### **Voucher Pool (POOL_DB)**

- `voucher_id`: Unique identifier

- `vendor_id`: Reference to vendor

- `name`: Voucher name

- `description`: Voucher description

- `value`: Monetary value

- `tier_level`: Tier assignment (1, 2, 3...)

- `vendor_expiry`: Original vendor expiry date

- `system_expiry_days`: Days from claim to expiry

- `quantity`: Available quantity

- `status`: Active/Inactive/Expired

- `created_at`: Creation timestamp

- `updated_at`: Last update timestamp

  

#### **Campaigns (CAMPAIGN_DB)**

- `campaign_id`: Unique identifier

- `name`: Campaign name

- `description`: Campaign description

- `start_date`: Campaign start date

- `end_date`: Campaign end date

- `status`: Draft/Active/Paused/Ended

- `eligibility_rules`: JSON configuration

- `created_at`: Creation timestamp

- `updated_at`: Last update timestamp

  

#### **Tier Quotas (QUOTA_DB)**

- `quota_id`: Unique identifier

- `campaign_id`: Reference to campaign

- `tier_level`: Tier number

- `voucher_limit`: Maximum vouchers for tier

- `vouchers_used`: Current usage count

- `win_probability`: Win percentage

- `created_at`: Creation timestamp

  

#### **User Vouchers (USER_DB)**

- `user_voucher_id`: Unique identifier

- `user_id`: Reference to user

- `voucher_id`: Reference to voucher

- `campaign_id`: Reference to campaign

- `claimed_at`: Claim timestamp

- `system_expiry`: System expiry date

- `status`: Active/Expired/Redeemed

- `redemption_details`: Redemption information

- `created_at`: Creation timestamp

  

#### **Vendor Master (VENDOR_DB)**

- `vendor_id`: Unique identifier

- `name`: Vendor name

- `category`: Vendor category

- `contact_info`: Contact details

- `redemption_instructions`: How to redeem

- `status`: Active/Inactive

- `created_at`: Creation timestamp

  

### **Data Flows**

  

#### **Voucher Addition Flow**

1. Admin inputs voucher details

2. System validates data

3. Voucher stored in pool

4. Inventory updated

5. Confirmation sent

  

#### **Campaign Creation Flow**

1. Admin configures campaign

2. System validates configuration

3. Campaign stored in database

4. Quotas and probabilities set

5. Campaign activated

  

#### **Wheelspin Flow**

1. User authenticates

2. System checks eligibility

3. User spins wheel

4. System determines win

5. Voucher assigned

6. Pool updated

7. User notified

  

#### **Voucher Assignment Flow**

1. Win tier determined

2. Voucher selected from pool

3. Pool inventory updated

4. User record created

5. Assignment confirmed

6. Analytics updated

  

---

  

## 10. System Integration Points

  

### **External Service Integrations**

- **Authentication Service**: User verification and session management

- **Notification Service**: Push notifications, emails, SMS

- **Payment Service**: Transaction processing and validation

- **Analytics Platform**: Data aggregation and reporting

- **Vendor APIs**: Real-time voucher status updates

  

### **Data Synchronization**

- **Real-time Updates**: Pool status, campaign metrics

- **Batch Processing**: Daily expiry checks, analytics generation

- **Event-driven Updates**: Voucher assignments, status changes

- **Scheduled Tasks**: Pool monitoring, report generation

  

---

  

## Usage Instructions

  

1. **Copy each PlantUML code block** into a PlantUML editor

2. **Generate DFD diagrams** for system documentation

3. **Export as PNG/SVG** for presentations and documentation

4. **Update diagrams** as system architecture evolves

  

These DFDs provide a comprehensive view of data flow in the Enjoy Rewards system and can be used for:

- System architecture planning

- Database design

- API development

- Integration planning

- Security analysis

- Performance optimization