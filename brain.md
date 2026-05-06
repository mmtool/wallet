

# 🧠 DW MoMoney System Design — AI Brain File

**Document Title:** DW MoMoney — Comprehensive System Design & Knowledge Base (AI Agent Reference)
**Version:** 1.0 | **Generated:** 2026-05-06 | **Sources:** Company Data Space (MOAG), TEC, MD Spaces
**Purpose:** This document serves as the single source of truth "brain file" enabling AI/AI Agents to understand the current MoMoney Digital Wallet (DW) system, respond to user/Product Manager queries, and support new feature requests, BRDs, and CRs.

---

## I. SYSTEM OVERVIEW

### 1.1 What is DW MoMoney?
MoMoney is a **Digital Wallet (DW) / Mobile Financial Services (MFS)** platform operated by MO Company, built on AWS infrastructure. It provides stored-value accounts, P2P transfers, bill payments, QR payments, bank linking, lending (BNPL/EWA), loyalty, and merchant/agent/corporate services. The platform is backed by **Shwe Bank** for banking and settlement.

**Core Platform Components:**
- **Digital Wallet (DW)** — The core engine: transaction processing, GL posting, wallet management, service configuration, offer management
- **Payment Hub** — Separate VPC for payment gateway routing
- **Integration Layer** — Bank INT, Biller INT, 3rd-party connectors
- **Admin/BackOffice Portal** — DW operator portal (administrator.momoney.com.mm)
- **Mobile Apps** — Subscriber (MoMoney), Agent, Merchant, MoBiz (Corporate)
- **Web Portals** — MoBiz Portal, Merchant Portal, Biller Portal, Loyalty Portal, AMS Portal, DSE App

---

## II. CHANNELS

| # | Channel | Type | Description |
|---|---|---|---|
| 1 | **MoMoney Wallet App** | Mobile (iOS/Android) | Consumer app — P2P, bill pay, QR, bank link, cash in/out |
| 2 | **MoBiz App** | Mobile (iOS/Android) | Corporate/Business user mobile app |
| 3 | **Agent App** | Mobile (iOS/Android) | Agent cash-in/out, interbank, services |
| 4 | **Merchant App** | Mobile (iOS/Android) | Merchant payment acceptance, QR, settlement |
| 5 | **MoBiz Portal** | Web Portal | Corporate portal — payroll, bulk transfer, interbank, EWA, reports |
| 6 | **Merchant Portal** | Web Portal | Merchant management —  |
| 7 | **DW BackOffice Portal** | Web Portal | Admin portal —  |
| 8 | **Biller Portal** | Web Portal | Biller management — 
|
| 9 | **Loyalty Portal** | Web Portal | Loyalty configuration —  |
| 10 | **AMS Portal** | Web Portal | Agent Management System |
| 11 | **DSE App** | Mobile App | Direct Sales Executive tracking |


---

## III. CLIENTS / ACTORS

| Actor | Offer Level | Description |
|---|---|---|
| **Subscriber** | Subscriber L2, Employee L1, Employee L3, Mo Employee | End-user consumers with MoMoney wallet |
| **Agent** | Agent, Master Agent | Cash-in/out points, earn commission |
| **Merchant** | Online Merchant, Offline Merchant | Accept payments, QR, settlement |
| **MoBiz** | Individual, Business, Corporate Class A (Portal User) | Corporate users with portal access |
| **Operator/Officer** | DW Admin | Back-office operations team |
| **Biller** | 3rd Party Biller | Electricity, Water, Telecom providers |
| **Aggregator** | Payment Aggregator | Payment routing intermediaries |
| **Bank** | Shwe Bank, KBZ, YOMA, AGD, MCB, MEB | Interbank transfer partners |

---

## IV. APPLICATION ARCHITECTURE

### 4.1 High-Level Architecture
```
┌─────────────────────────────────────────────────────────┐
│                    CLIENT LAYER                          │
│  MoMoney App │ Agent App │ Merchant App │ MoBiz App     │
│  MoBiz Portal│ Admin Portal│ Biller Portal│ Loyalty     │
└───────────────────────┬─────────────────────────────────┘
                        │ HTTPS/CloudFront/WAF
┌───────────────────────▼─────────────────────────────────┐
│                   API LAYER                              │
│  WSO2 API Manager │ LoadBalancers │ CloudFront CDN      │
│  Nginx Reverse Proxy (Blockage Solution)                │
└───────────────────────┬─────────────────────────────────┘
                        │
┌───────────────────────▼─────────────────────────────────┐
│               APPLICATION LAYER (EKS)                    │
│  DW Backend │ Corporate Backend │ Loyalty Backend        │
│  Merchant Backend │ ThirdParty Backend │ Bank INT        │
│  Payment Gateway │ LoanUnit │ MoBills INT │ Cronjob     │
│  AMS Backend                                             │
└───────────┬───────────┬──────────────┬──────────────────┘
            │           │              │
┌───────────▼──┐ ┌──────▼──────┐ ┌────▼────────────────┐
│   DATA LAYER │ │  CACHE LAYER│ │  INTEGRATION LAYER  │
│ MongoDB Atlas│ │  ElastiCache│ │  Shwe Bank (VPN)    │
│ MOMONEY-     │ │  Redis      │ │  CBM NET            │
│ WALLET-DB    │ │  SQS        │ │  3rd Party Billers  │
│ PostgreSQL   │ │  EventBridge│ │  RPA Selenium       │
│ (AMS)        │ │             │ │  Firebase (Push)    │
└──────────────┘ └─────────────┘ └─────────────────────┘
```

### 4.2 Infrastructure Summary (AWS)
| Component | Technology | Configuration |
|---|---|---|
| **Compute** | AWS EKS (Kubernetes) | Multiple namespaces per service, t3a.medium/c5.xlarge nodes |
| **Database** | MongoDB Atlas (M30) | Cluster: MOMONEY-WALLET-DB, Replica Set - 3 nodes |
| **Cache** | AWS ElastiCache (Redis) | 3 nodes, cache.t3.medium, shared across DW/Corporate/Loyalty |
| **CDN** | AWS CloudFront + Nginx | Static frontend hosting, API routing |
| **WAF** | AWS WAF | IP-based ACLs, rate limiting per portal |
| **DNS** | MTG DNS Controller | momoney.com.mm domain |
| **API Gateway** | WSO2 APIM | c5.xlarge (4CPU/8GB), manages external API access |
| **CI/CD** | Jenkins on EC2 | momoney-prod-CICD-JENKINS |
| **Secrets** | HashiCorp Vault on EC2 | momoney-prod-VAULT-SECRETS |
| **Logging** | ELK (Elastic Cloud) | MetricBeat + FluentBit + Fluentd → ElasticSearch |
| **Message Queue** | AWS SQS (FIFO) | Loyalty events, transaction processing |
| **Event Streaming** | AWS EventBridge | MongoDB → SQS event bridge |
| **VPN** | AWS Site-to-Site VPN | Shwe Bank connectivity |
| **Storage** | AWS S3 | Static sites, logs, upload files |
| **RPA** | Selenium on EC2 | Bank portal automation for cash-in |
| **Push Notifications** | Firebase Cloud Messaging | Mobile push notifications |


### 4.3 Key Applications & Databases
| Application | Database | Namespace |
|---|---|---|
| Digital Wallet | MongoDB Atlas: MOMONEY-WALLET-DB | momoney-wallet-prod-ns |
| Corporate/MoBiz | MongoDB Atlas: MOMONEY-WALLET-DB | corporate-prod-ns |
| Loyalty | MongoDB Atlas: MOMONEY-WALLET-DB | loyalty-prod-ns |
| Loan Unit / EWA | MongoDB Atlas: MOMONEY-WALLET-DB | momoney-loanunit-prod-ns |
| Merchant | MongoDB Atlas: MOMONEY-WALLET-DB | merchantportal-prod-ns |
| Bank INT | MongoDB Atlas: momoney-bank-int-prod-db | momoney-bank-int-prod-ns |
| AMS | PostgreSQL RDS (db.t3.small) | Separate VPC |
| MoPayment | Aurora RDS Cluster (db.t3.medium) | Separate VPC/Account |
| MoBills | Aurora RDS Cluster (db.t3.medium) | Separate VPC/Account |
| ARA | PostgreSQL RDS (db.t3.small) | prod-momoney-bss VPC |

---

## V. PORTALS DETAIL

| Portal | URL | Backend | Function |
|---|---|---|---|
| DW Admin |  | DW Backend (EKS) | Service config, offer management, GL, reports, user management |
| MoBiz Portal |  | Corporate Backend (EKS) | Payroll, interbank, EWA, reports, maker/checker |
| Merchant Portal |  | Merchant Backend (EKS) | Merchant management, settlement, QR |
| Biller Portal |  | ThirdParty Backend (EKS) | Biller config, bill upload, settlement |
| Loyalty Portal |  | Loyalty Backend (EKS) | Points, tiers, campaigns, vouchers |
| Loyalty Business |  | Loyalty Backend (EKS) | Company loyalty management |
| Loan Unit |  | LoanUnit Backend (EKS) | EWA, lending management |
| AMS Backoffice |  | ARA Backend (EC2) | Agent registry, management |
| API Developer |  | WSO2 APIM (EC2) | External API documentation |

---

## VI. SERVICES & TRANSACTION DESIGN

### 6.1 Service Configuration (DW Portal)
The DW portal uses a **factory-based configuration model** where each service is assembled from reusable components:

| Step | Configuration Item | Location in DW Portal |
|---|---|---|
| 1 | **Create Biller** | Operations → Biller Management → Create |
| 2 | **Create Service** | Product Management → Service → Add New |
| 3 | **Create Transaction Design** | Product Management → Transaction Design |
| 4 | **Create Fee / Distribution / Discount** | Product Management → Fee / Distribution / Discount |
| 5 | **Create Notification** | Notifications → Notification Template → Create |
| 6 | **Add Service to Offer** | Offer → Offer Factory → Choose Offer |


### 6.2 Service Fields
| # | Field | Details |
|---|---|---|
| 1 | **Code** | Unique code for each service |
| 2 | **Name** | Service Name (shown in transaction fields) |
| 3 | **Full Name** | Service Full Name |
| 4 | **Service Note** | Configuration notes |
| 5 | **Action Priority** | Before (call 3rd party first → GL) or After (GL first → call 3rd party) |
| 6 | **Action Type** | Transaction creates cashcode / Integrate to 3rd party (Telco, Bill, Fund Transfer, Link Bank) / None |
| 7 | **Related** | Offer Roles: Subscriber, Agent, Merchant, Operator |
| 8 | **Channel** | Web / Mobile |
| 9 | **Status** | Active / Inactive |
| 10 | **Refund** | Is service refundable? Target service for refund |

### 6.3 Transaction Definition (GL Posting)
Each transaction is defined as a series of **double-entry GL posting steps**:

| # | Field | Details |
|---|---|---|
| 1 | **Debit** | Choose GL / Product pocket to debit |
| 2 | **Credit** | Choose GL / Product pocket to credit |
| 3 | **Amount** | Variable: TransAmount, TransOrigAmount, fee variables |
| 4 | **Description** | Step description |
| 5 | **Is Loop Step** | True = fee/discount calculation step |
| 6 | **Component Processed** | Fee or Discount |

**Key Transaction Variables:**
- `TransAmount` = TransOrigAmount + Debit fee
- `TransOrigAmount` = Original transaction amount
- Fee variables: `FeeGlTarget`, `FeeDebitValue`, `FeeCreditValue`, `TotalDebitFee`, `TotalCreditFee`
- Discount variables: `DiscountDebitValue`, `DiscountCreditValue`, `TotalDebitDiscount`, `TotalCreditDiscount`
- Distribution types: `OnBoardAgentDistribution`, `AgentDistribution`, `SystemDistribution`, `MerchantDistribution`, `AggregatorDistribution`, `SubscriberCashback`, `BeneficiaryCashback`

### 6.4 Transaction Validation ( Many Validation Function Base on service)
| Validation | Description |
|---|---|
| Can not access to service | User doesn't have access to this service |
| Sender is invalid | Invalid sender account |
| Currency is not valid | Currency mismatch |
| Amount too small | Below minimum transaction amount |
| Amount too big | Exceeds maximum transaction amount |
| Sender balance not sufficiency | Insufficient wallet balance |
| Amount exceeded daily limit | Daily limit reached |
| Amount exceeded monthly/weekly limit | Period limit reached |
| Transaction too frequently | Interval validation |
| Sender/Receiver balance exceed limit | Wallet balance cap |
| Sender/Receiver pocket locked | Account locked |

### 6.5 Transaction Fields ( Many Others Field Base kn Service)
Transaction fields are configured per service with:
- Field name, type, regex validation
- Min/max length
- Error code and error message
- Required flag
- How to get (user key-in, system query, dropdown)

### 6.6 Biller Configuration
| # | Field | Details |
|---|---|---|
| 1 | **Biller Code** | Unique code |
| 2 | **Biller Name** | Display name |
| 3 | **Phone** | Biller identifier |
| 4 | **Type** | Telco / Bank / Bill |
| 5 | **Biller URL** | Integration endpoint |
| 6 | **Request** | Request body template |
| 7 | **Settlement** | Prepaid (pre-fund) or Postpaid (settle later) |
| 8 | **Biller Fields** | Fields sent to biller |
| 9 | **Biller Validations** | Validation rules |

---

## VII. NOTIFICATION SYSTEM

### 7.1 Notification Template Fields
| # | Field | Details |
|---|---|---|
| 1 | **Name** | Display name in app |
| 2 | **Title Name** | Full system name |
| 3 | **Action** | Transaction (after txn) or Request (request notification) |
| 4 | **Need secured with** | Encrypted content in DB |
| 5 | **Channel** | SMS, Push Notification |
| 6 | **Content** | SMS text template with {variables} |
| 7 | **Full Content** | Push notification HTML template |

### 7.2 Notification Statuses
Each transaction service should define notifications for:
- **Processing** — Transaction in progress
- **Success** — Transaction completed
- **Fail** — Transaction failed
- **Reverse** — Transaction reversed

Template variables: `{Status}`, `{Service}`, `{Amount}`, `{Account}`, `{Timestamp}`, `{TxnRefId}`, `{BeneficiaryAccount}`, `{Currency}`


## VIII. OFFER & LIMITATIONS

### 8.1 Offer Factory Configuration
The **Offer** is the central mechanism to control what services/features a user type can access:
- Each **Offer Level** (Subscriber L2, Agent, Merchant, etc.) has its own configuration
- Per-offer settings: **Pocket limits**, **Service access**, **Transaction limits**, **Authentication**, **Fee**, **Discount**, **Notification**

### 8.2 Limitation Framework
| Limit Type | Scope | Example |
|---|---|---|
| **Per Transaction Min** | Single txn floor | 1,000 MMK |
| **Per Transaction Max** | Single txn ceiling | 10,000,000 MMK |
| **Daily Limit** | Max amount per day | 10,000,000 MMK |
| **Weekly Limit** | Max amount per week | Configurable |
| **Monthly Limit** | Max amount per month | Configurable |
| **Interval** | Min seconds between txns | Configurable |
| **Wallet Balance Limit** | Max wallet balance | Per offer level |
| **Pocket Lock** | Account frozen | System flag |

---

## IX. FEE, DISTRIBUTION & DISCOUNT

### 9.1 Fee Configuration
| Field | Details |
|---|---|
| **Name** | Fee name |
| **GL Target** | Target GL account |
| **Currency** | MMK |
| **Tier** | Multiple tiers with conditions (amount ranges) |
| **Conditions** | amount, totalDateAmount, totalDateTransaction, totalWeekAmount, totalMonthAmount, totalQuarterAmount, totalYearAmount |
| **Type** | **Standard** (Amount × % + fixed) or **Advanced** (variable-based formula) |

Special: MDR per merchant configured individually at Operations → Merchant.

### 9.2 Distribution
Fees collected are distributed among actors:
- Agent Commission (e.g., 80/20 split Agent/Master Agent)
- System Income
- Merchant Share
- Aggregator Share
- Cashback to subscriber/beneficiary

### 9.3 Discount
Same structure as Fee. Additional capability:
- Voucher from loyalty points
- 3rd-party discount verification
- Code-based promotions

---

## X. REPORTING

### 10.1 DW Portal Reports
| Report | Menu Location |
|---|---|
| Transaction 360 | Accounting menu |
| Transaction Detail | Report menu |
| Transaction Summary | Report menu |
| Agent's Daily Transaction | Report menu |
| Interbank Report | Report menu |
| CBM Report | Report menu (Bank link/unlink, Balance) |
| Onboarding Report | Report menu |
| Settlement Report | Accounting menu |

### 10.2 Billing Portal Reports
- Interbank Transfer Report
- Biller-specific settlement reports

### 10.3 Report Template Standard
Each service's BRD should define report columns to include in existing or new reports.

---

## XI. FLOWCHART / TRANSACTION LIFECYCLE

### 11.1 Payment Transaction Flow (Swimlane)
```
Customer           MoMoney Platform         Payment Processor      Finance Team
   │                     │                        │                    │
   ├─Select Payment──►   │                        │                    │
   │                 Create Order & Reserve Funds  │                    │
   │                 Validate Product/Order/Payment│                    │
   │                 Route to Processor──────────► │                    │
   │                     │                   Authorize Payment         │
   │                     │                   Deduct Funds              │
   │                     │◄──────────────── Return Response            │
   │                 Update Transaction State       │                    │
   │                 Log Accounting (GL) Entries     │                    │
   │                 Initiate Settlement             │                    │
   │◄──Notify────────────│                        │                    │
   │                     │                   Daily Settlement File──► │
   │                     │                        │           Reconcile │
```

### 11.2 Transaction State Machine
| State | Description | Next States | Trigger |
|---|---|---|---|
| **Request** | Initiated, funds checked | Processing, Expired, Failed | /payment/request |
| **Processing** | Active gateway interaction | Success, Failed, Timeout | Gateway API call |
| **Success** | Completed successfully | Settled, Refund | Gateway success response |
| **Failed** | Error occurred | Retry, Void, Closed | Gateway failure / system error |
| **Timeout** | No gateway response | Failed, Processing | Timer exceeded |
| **Expired** | Not completed in time | Retry, Closed | Inaction / timer |
| **Settled** | Merchant credited | Reconciled | Settlement process |
| **Reconciled** | Verified against external reports | Closed | Reconciliation match |
| **Closed** | Final immutable state | N/A | Terminal state |

### 11.3 Refund & Dispute Flow
```
Refund Request → Ops: Verify Original Txn → Valid? 
  → Yes → Create Refund Txn → Reverse Accounting → Call Refund API → Success? → Notify Customer
  → No → Reject & Notify

Dispute Received → Ops: Investigate → Genuine?
  → No → Submit Evidence → Processor Decision → Merchant Wins/Customer Wins
  → Yes → Initiate Forced Refund
```

---

## XII. CORE PRODUCT PORTFOLIO

| Product | Description | Key Features | Target |
|---|---|---|---|
| **Digital Wallet** | Stored-value account | P2P, Bill Pay, Cash In/Out | Consumers |
| **Biller Payments** | Utility payment gateway | Electricity, Water, Telecom, Internet | Consumers, Enterprises |
| **Gift Cards & Vouchers** | Digital gift cards | Corporate Gifting, Promotions | Retailers, Corporates |
| **QR Payments (MMQR)** | Scan-to-pay | Dynamic/Static QR, In-store | Merchants, Consumers |
| **Bank Linking** | Bank account integration | Cash In/Out, High-value transfers | Consumers, Agents |
| **BNPL** | Point-of-sale credit | Installment plans, Merchant financing | E-commerce, Retail |
| **EWA** | Earn Wage Access | Salary advance for corporates | Enterprises |
| **Loyalty** | Points & rewards | Tiers, campaigns, vouchers, cashback | All users |
| **Interbank Transfer** | Cross-bank transfers | Regular (ACH) and Faster (CCT013) | All users |
| **MoBiz/Corporate** | Corporate services | Payroll, bulk transfer, portal management | Enterprises |

---
****That is Important****

## XIII. USE CASE TEMPLATE (Standard BRD Format) *** 
**Template** https://github.com/mmtool/wallet/blob/main/brd_cr_template.md
Every new feature/CR should follow this use case structure:

| Field | Content |
|---|---|
| **Use Case ID** | e.g., DW_01 |
| **Use Case Name** | Short descriptive name |
| **Description** | Overall flow of the case |
| **Actors** | Subscriber, System, Merchant, MoBiz, Agent, 3rd Party, Operator, Aggregator, Biller, Bank |
| **Channel** | Which app/portal |
| **Offer** | Which offer levels apply |
| **Preconditions** | Required conditions before execution |
| **User Journey** | Step-by-step UI interaction detail |
| **Validation** | All business & technical validation rules |
| **Limitations** | Per Txn, Per Day, Per Month amounts |
| **Expectation** | Expected output |
| **GL Posting** | Double-entry Debit/Credit per step |
| **Fee** | Fee structure (Fix, %, Tier, Conditions) |
| **Distribution** | % distribution among actors |
| **Notification** | Per status: Type, Title, Content, Sample |
| **UI** | Figma link or screen reference |
| **Report Template** | Column list for reporting |
| **Error Messages** | Error code, English message, Burmese message |
| **Data Fields** | Field name, Rule/Format, Min/Max length, Validation, Required, How to get |


---

## XIV. USER JOURNEY — MOBILE APP (Subscriber Example: Faster Interbank)

| Step | Action | Screen |
|---|---|---|
| 1 | Log in to MoMoney App | Login Screen |
| 2 | Click "Send Money" | Home Screen |
| 3 | Click "Interbank Transfer" | Send Money Menu |
| 4 | Choose "Faster Interbank" | Transfer Type Selection |
| 5 | Choose or Search Bank Name | Bank List (dropdown/search) |
| 6 | Choose Branch | Branch dropdown |
| 7 | Key in Bank Account Number | Input field |
| 8 | Key in Account Holder Name | Input field |
| 9 | Key in Account Holder Phone | Input field |
| 10 | Key in Amount | Input field (with validation) |
| 11 | Enter Remark (optional) | Input field |
| 12 | Save Beneficiary checkbox | Toggle |
| 13 | Preview Transaction Detail | Preview screen (amount, fee, total) |
| 14 | Click "Confirm" | Confirmation button |
| 15 | Key in PIN | PIN entry screen |
| 16 | Transaction Status Screen | Success/Fail/Processing result |
| 17 | Push Notification received | System notification |


---

## XV. USER JOURNEY — PORTAL (MoBiz Portal: Maker/Checker)

| Step | Actor | Action |
|---|---|---|
| 1 | Maker | Login MoBiz Portal |
| 2 | Maker | Choose "Interbank Transfer" |
| 3 | Maker | Choose "New Item" → Select Bank → Click Next |
| 4 | Maker | Fill: Account Number, Holder Name, Phone, Amount, Remark |
| 5 | Maker | Preview → Submit (or Discard) |
| 6 | System | Notification sent to Maker and Checker |
| 7 | Checker | Receive notification → Home → My Tasks |
| 8 | Checker | Review → Approve or Reject |
| 9 | System | If Approved: Process transaction, notify Maker+Checker+Admin |
| 10 | System | If Rejected: Send rejection notification to all |

**Authentication:** Configurable per process (None, PIN, OTP, 2FA)

---

## XVI. SCOPE & WORKFLOW — FUNCTIONAL REQUIREMENTS BY CHANNEL

### 16.1 MoMoney Wallet App (Subscriber)
- Wallet management (balance, history, profile)
- P2P Transfer (wallet-to-wallet)
- Cash In/Out (via Agent, Bank Link)
- Bill Payments (Electricity, Water, Telecom, Internet)
- QR Payments (MMQR — OI Payment, RI Payment)
- Interbank Transfer (Regular ACH, Faster CCT013)
- Bank Linking (Shwe Bank, other banks)
- Loyalty (points, vouchers, tiers)
- Sub-Apps (FlyMya, Skynet DTH, Merchant promotions)
- Notifications (SMS + Push)

### 16.2 MoBiz App
- All Subscriber features for business users
- Corporate wallet management
- Interbank transfer with business limits
- EWA application

### 16.3 Agent App
- Cash-in/Cash-out services for customers
- Interbank transfers
- Commission tracking
- Customer onboarding

### 16.4 Merchant App
- Payment acceptance (QR, wallet)
- Interbank transfer
- Settlement tracking
- Bank linkage

### 16.5 MoBiz Portal (Web)
- Maker/Checker workflow
- Payroll upload and processing
- Bulk interbank transfers
- EWA management
- Bank linkage for corporate
- Reports and reconciliation

### 16.6 DW BackOffice Portal
- Service configuration (create/edit services, transaction design, fees, offers)
- User/Account management
- GL management
- Report generation
- Notification template management
- Biller management
- Settlement & reconciliation
- Batch adjustment

---

## XVII. SETTLEMENT & RECONCILIATION

| Process | Owner | Frequency | Description |
|---|---|---|---|
| **Instant Settlement** | System | Real-time (T+0) | Faster interbank via CCT013 — auto settle on success |
| **Daily Settlement** | Finance/Ops | T+1 | Batch settlement files from processors |
| **Reconciliation** | Finance + Tech | Daily | Match internal DB vs processor/bank statements |
| **MMQR Settlement** | Operations | T+1 | DPS balance clearance file via SMTP |
| **Dispute Handling** | Operations | As needed | Refunds, reversals, chargebacks |

**Key GL Accounts:**
- `L100000217` — Suspense GL (holding account during processing)
- `A100000201` — Bank Float Balance
- `I100000101` — Fee Income
- `E100000101` — Commission Expense
- `E100000103` — Discount Expense

---

## XVIII. ERROR HANDLING MATRIX

### Business Logic Errors
| Code | Scenario | User Message |
|---|---|---|
| BUS-001 | Insufficient Balance | "Insufficient balance. Please top up." |
| BUS-002 | Daily Limit Exceeded | "Daily limit exceeded. Try tomorrow." |
| BUS-003 | KYC Verification Required | "Additional verification required." |
| BUS-004 | Merchant Suspended | "Merchant unavailable." |

### Technical Errors
| Code | Scenario | Recovery |
|---|---|---|
| TECH-001 | Database Timeout | Retry with backoff |
| TECH-002 | Cache Unavailable | Fallback to database |
| TECH-003 | Internal API Timeout | Circuit breaker |

### Network Errors
| Code | Scenario | Strategy |
|---|---|---|
| NET-001 | Processor Timeout | Exponential backoff, switch to backup |
| NET-002 | Processor Unavailable | Circuit breaker, queue for later |
| NET-003 | SSL Handshake Failure | Fail immediately, log security alert |

---

## XIX. API REFERENCE

| Request Type | Endpoint | Purpose |
|---|---|---|
| Payment | /payment/request | Initiate payment |
| Retry | /payment/retry | Re-attempt failed payment |
| Refund | /payment/refund | Full/partial reversal |
| Void | /payment/void | Cancel before capture |
| Push Notify | /payment/push/status | Async status notification |
| Enquiry | /payment/check | Status check |
| Settlement | /settlement/process | Batch/real-time settlement |

**Payment Methods & Fees:**
| Method | Fee Type | MDR/Charges |
|---|---|---|
| Wallet | Percentage | 1.5% |
| Card (VISA/MPU) | % + Fixed | 2.0% + 100 MMK |
| Bank Transfer | Fixed | 300 MMK |
| QR Payment | Merchant Fee | 1.0% |
| Cash In/Out | Tier-based | Variable (e.g., 0.5%) |
| Interbank (Faster/CCT013) | % or Fixed | 0.01% (min 2,000) or 1,500 flat |

---

## XX. ACCOUNTING FLOW (Double-Entry)

| Transaction Type | Event | Debit | Credit | Amount |
|---|---|---|---|---|
| Successful Payment | Fund Transfer | Merchant Receivable | Customer Wallet Liability | Principal |
| | MDR Fee | MDR Expense | MDR Revenue | Fee |
| | Net Settlement | Merchant Wallet Liability | Bank Account | Principal - Fee |
| Refund | Reverse Principal | Customer Wallet Liability | Merchant Receivable | Principal |
| | Reverse MDR | MDR Revenue | MDR Expense Reversal | Fee |
| Interbank (Block) | Block | Customer Wallet | Suspense GL (L100000217) | Total |
| Interbank (Send) | Send to biller | Suspense GL | INTERBANKTRANSFER biller | Amount + Bank fees |
| Interbank (Fee) | System fee | Suspense GL | Fee Income (I100000101) | Fee |
| Settlement (Success) | Auto settle | INTERBANKTRANSFER biller → Suspense GL → Bank Float | | Amount |
| Reversal (Fail) | Auto reverse | Reverse all original entries | | All |

---

## XXI. RESPONSIBILITIES BY DEPARTMENT

| Team | Mandate | Responsibilities |
|---|---|---|
| **Technology** | System Reliability & Security | API design, integration, logging, error handling, uptime, data integrity |
| **Business/Product** | Market Growth & Profitability | Product definition, pricing, partnerships, BRDs, CRs |
| **Operations** | Process Execution & Support | Settlement, reconciliation, disputes, customer support |
| **Finance** | Fiduciary Oversight | Merchant payout, fee collection, reconciliation verification, compliance |
| **Risk** | Portfolio Health | Credit policies, fraud prevention, BNPL risk management |

---

## XXII. HOW TO USE THIS BRAIN FILE

### For AI Agents responding to queries:
1. **New Feature Request** → Reference Section XIII (Use Case Template), VI (Service Configuration), IX (Fees), VII (Notifications), XVI (Functional Requirements by Channel)
2. **Change Request (CR)** → Identify impacted channels (Section II), validate against current architecture (Section IV), check limitations (Section VIII), define GL postings (Section XX)
3. **BRD Creation** → Follow the template in Section XIII, populate all fields including user journey (XIV/XV), validation (VI.4), GL posting (XX), notifications (VII), reporting (X)
4. **Architecture Questions** → Section IV (Architecture), V (Portals)
5. **Transaction Flow Questions** → Sections XI (Flowchart), VI (Transaction Design), XVII (Settlement)
6. **Error/Validation Questions** → Sections XVIII (Errors), VI.4 (Transaction Validation)

### For Product Managers:
- Use this document to ensure all aspects of a new feature are covered
- Cross-reference channels, actors, offer levels, and GL postings
- Ensure notification templates cover all transaction statuses
- Define report columns for operational visibility
