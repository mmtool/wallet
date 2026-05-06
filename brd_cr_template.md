# BRD / CR Template — Complete AI Agent Instruction Guide

> **Purpose:** This document instructs an AI Agent to generate a complete BRD (Business Requirement Document) or CR (Change Request) following the exact template structure. Every section includes its purpose, field-by-field instructions, formatting rules, and a filled sample/example.

---

## Determining Document Type

Before starting, the AI Agent must determine:
- **BRD** — Used for **new features or projects** being built from scratch. Contains full use cases, diagrams, GL posting, fees, distribution, etc.
- **CR (Change Request)** — Used for **changes to existing features/flows**. Highlights what is changing from current behavior. Contains Change Request detail tables with enhancement areas, workflow/process changes, and acceptance criteria.

---

## I. OVERVIEW

### 1.1. Document Information

**Purpose:** Provides the metadata identity of the document for traceability, ownership, and versioning.

**Format:** A 2-column table (Field | Value)

| Field | Instruction | Example (BRD) | Example (CR) |
|---|---|---|---|
| **Document name** | The full descriptive name of the feature/project. Use the official product or project name. | `Cash Out BRD` | `Change Request: Displaying Specific Error Message for KYC mismatch in bank linkage process` |
| **Type** | Must be exactly `BRD` or `CR` | `BRD` | `CR` |
| **Status** | Use Confluence status macros. Values: `Initial`, `Draft`, `In Review`, `Final`. Use GREEN for Final, default for others. | `Final` (green) | `Initial` (default) |
| **Code** | Internal project/module code (e.g., `MO_01`). Leave blank if not assigned yet. | `MO_01` | *(blank or a code)* |
| **Author** | The person who created this document. Use @mention (Confluence user link). | `@Kaung Htet Min` | `@kyawzin.thant` |
| **Ref BRD/docs** | *(CR only)* — Link to the original BRD or related Jira ticket this CR modifies. Use `-` if none. | *(not applicable for BRD)* | `-` or `https://jira.momoney.com.mm/browse/CS-435` |
| **Version** | Semantic version number. Start at `1.0`. Increment on significant revisions. | `1.0` | `1.0` |
| **Created date** | Date of initial creation in `DD/MM/YYYY` format. | `09/05/2023` | `27/02/2024` |

---

### 1.2. Document Revisions

**Purpose:** Tracks every change made to the document so stakeholders know the document's evolution.

**Format:** 5-column table

| Revision | Date | Document Change | Changed By | Revised By |
|---|---|---|---|---|
| `1.0` | `08/09/2025` | `Initial Draft` | `Kaung Htet Min` | *(blank)* |
| `1.1` | `15/09/2025` | `Added GL Posting and Fee sections` | `Kaung Htet Min` | `Nang Tom Kham` |
| `2.0` | `01/10/2025` | `Final document after review` | `Kaung Htet Min` | `Su Wut Yee` |

**Instructions:**
- **Revision**: Increment minor version for small changes (1.0 → 1.1), major version for significant rewrites (1.x → 2.0)
- **Date**: Use `DD/MM/YYYY` format
- **Document Change**: Brief description of what was modified (e.g., "Init document", "Updated fee structure", "Added error messages")
- **Changed By**: Person who made the change
- **Revised By**: Person who reviewed/approved the change (can be blank for initial drafts)

---

### 1.3. Document Approvals *(CR documents)*

**Purpose:** Records formal sign-off from stakeholders. Required for CRs to ensure authorization.

| Revision | Date | Approver Name | Project Role | Signature/Electronic Approval/Email |
|---|---|---|---|---|
| `1` | `27/02/2024` | `Nang Tom Kham` | `Product Owner` | `nang.tom@company.com` |
| `2` | `05/03/2024` | `Tech Lead Name` | `Technical Lead` | *(approved via Confluence)* |

**Instructions:**
- List every person who must formally approve this document
- **Project Role** examples: `Product Owner`, `Technical Lead`, `Business Analyst`, `QA Lead`, `Operations Manager`
- Include email or note how approval was given

---

### 1.4. Overview

**Purpose:** A high-level summary of what this document covers and how it will be used across teams.

**Instructions:** Write 1-2 paragraphs that:
1. State what the document defines (the feature/change name in **bold**)
2. List the standard activities this document supports

**Template Text (always include these bullet points):**

> This document defines the high-level requirements of **[Feature/Project Name]**. It will be used as the basis for the following activities:
> - Creating solution designs
> - Developing test plans, test scripts, and test cases
> - Determining project completion
> - Assessing project success

**Then add — Business Benefits/Purpose:**

Describe the overall project goals and all business benefits. Cover:
- What problem does this solve?
- Who benefits and how?
- What is the expected business outcome?

**Example:**
> This document defines the high-level requirements of **Mo Payment Cash Out**. It will be used as the basis for the following activities:
> - Creating solution designs
> - Developing test plans, test scripts, and test cases
> - Determining project completion
> - Assessing project success
>
> **Business Benefits/Purpose**
> The Cash Out feature enables MoMoney wallet users to withdraw cash from their digital wallet via authorized agents. This reduces dependency on traditional banking channels, increases financial inclusion for unbanked populations, and generates transaction fee revenue for the company and agent network.

---

### 1.5. Term and Glossary

**Purpose:** Defines domain-specific terms, abbreviations, and acronyms used in this document so all readers (Business, Tech, QA, Operations) share the same understanding.

| Term | Glossary |
|---|---|
| `KYC` | `Know Your Customer — identity verification process required for financial services` |
| `NRC` | `National Registration Card — Myanmar national ID document` |
| `GL` | `General Ledger — the main accounting record` |
| `MoBiz` | `Mobile Business — the business user application channel` |
| `L2 Subscriber` | `Level 2 verified wallet user with full KYC completion` |

**Instructions:** List every abbreviation, technical term, or business-specific term mentioned in the document. If in doubt, include it.

---

### 1.6. Business Benefit/Motivation

**Purpose:** Maps each actor/stakeholder to the specific benefit they receive from this feature/change. Ensures every stakeholder's value is documented.

| No | Actor | Benefit/Motivation |
|---|---|---|
| `1` | `Subscriber (Wallet User)` | `Enables convenient cash withdrawal from digital wallet without visiting a bank branch, saving time and travel costs` |
| `2` | `Agent` | `Earns commission on each cash out transaction, increasing agent revenue and incentivizing agent network participation` |
| `3` | `MoMoney (System)` | `Generates transaction fee revenue and increases platform engagement. Supports financial inclusion KPIs` |
| `4` | `Operations Team` | `Reduces manual intervention in cash-out processes through automated GL posting and reconciliation` |

**Instructions:** Consider ALL actors: Subscriber, Merchant, Agent, MoBiz user, System/Platform, Operations, 3rd Party, Bank, Regulator, etc.

---

### 1.7. Action

**Purpose:** Defines WHO does WHAT on WHICH system. Maps each feature to its responsible actor and the action performed. Ensures Business, Operations, and Tech perspectives are all covered.

| Feature | Actor | Action |
|---|---|---|
| `Cash Out Request` | `Subscriber` | `Initiates cash out from wallet app by entering amount and selecting agent` |
| `Cash Out Approval` | `Agent` | `Confirms the cash out request, verifies subscriber identity, and dispenses cash` |
| `Transaction Processing` | `System (Backend)` | `Validates balance, applies fee, debits subscriber wallet, credits agent wallet, posts GL entries` |
| `Transaction Monitoring` | `Operations Officer` | `Monitors suspicious transactions via BackOffice Portal, can flag/reverse if needed` |

**Instructions:**
- *"Change features will be done by who, which system?"*
- *"What will be performed based on that feature?"*
- Add more columns for details to clearly cover Business, Operation, and Tech perspectives
- Include sub-features if applicable

---

### 1.8. Impact Feature

**Purpose:** Lists all EXISTING features that will be affected by this new feature or change. Prevents regression and ensures QA tests impacted areas.

| Channel | Feature |
|---|---|
| `MoMoney Wallet App` | `Wallet Balance Display — must update in real-time after cash out` |
| `Agent App` | `Agent Float Balance — must reflect incoming funds from cash out commission` |
| `BackOffice Portal` | `Transaction Report — must include new cash out transaction type in reports` |
| `DW Biller Portal` | `No impact` |

**Instructions:**
- List every channel and identify which existing features are impacted
- If no impact on a channel, explicitly state "No impact"
- Note any further investigation needed for downstream effects

---

## II. SCOPE OF WORK

**Purpose:** Defines the boundaries of what IS and IS NOT included in this BRD/CR. Lists all channels and features to be developed. This is the contract between Product and Development.

**Instructions:**
- *"Express all detail requirements — functional, non-functional, and operational"*
- Add more columns to describe details (Description, Sub Features if applicable)
- Developers must be able to clearly identify the full scope area — services, features, etc.
- Include suggested scope items

| # | Channel | Feature | Sub Feature *(if needed)* |
|---|---|---|---|
| `1` | `MoMoney Wallet App` | `Cash Out to Agent` | `Amount entry, Agent selection, PIN confirmation, Receipt` |
| `2` | `Agent App` | `Cash Out Fulfillment` | `Request notification, Subscriber verification, Cash dispensing confirmation` |
| `3` | `BackOffice Portal` | `Cash Out Transaction Report` | `Filter by date/agent/status, Export to CSV, Real-time dashboard` |
| `4` | `System/Backend` | `Cash Out API & Processing` | `Balance validation, Fee calculation, GL posting, Notification triggers` |

---

## III. USE CASE

### 3.1. Diagram

**Purpose:** Visual representation of the end-to-end process flow. Must include ALL parties and systems involved.

**Instructions:**
Provide three types of diagrams (use Draw.io/Miro or describe in text):

1. **Activities Process Flow Diagram** — Step-by-step activity flow showing decisions and actions
2. **Business Flow Diagram** — Shows business actors and their interactions
3. **Tech Flow Diagram** — Shows system components, API calls, and data flow

Below the diagram, include a **Step Description Table:**

| Step | Description |
|---|---|
| `1` | `Subscriber opens MoMoney Wallet App and selects "Cash Out"` |
| `2` | `Subscriber enters cash out amount and selects a nearby agent` |
| `3` | `System validates subscriber balance, daily limits, and agent float availability` |
| `4` | `System generates a one-time Cash Out code and sends it to the subscriber via SMS/push notification` |
| `5` | `Subscriber provides Cash Out code to Agent` |
| `6` | `Agent enters the code in the Agent App and confirms the transaction` |
| `7` | `System debits subscriber wallet, credits agent commission, posts GL entries, sends notifications to both parties` |

---

### 3.2. Use Case List

**Purpose:** Master index of ALL use cases covered in this document. Serves as a quick navigation table.

**Instructions:**
- Consider ALL perceptions: Success, Alternative, Fail, Happy path, Edge cases
- *"Make sure all cases are listed out — which helps Development and QA test case reference"*
- Include normal cases, strange/edge cases, and additional cases

| Use Case ID | Use Case Name |
|---|---|
| `UC_01` | `Successful Cash Out via Agent (Happy Path)` |
| `UC_02` | `Cash Out Failed — Insufficient Balance` |
| `UC_03` | `Cash Out Failed — Daily Limit Exceeded` |
| `UC_04` | `Cash Out Failed — Agent Float Insufficient` |
| `UC_05` | `Cash Out Reversal — Transaction timeout` |
| `UC_06` | `Cash Out with Promotional Fee Waiver` |

---

### 3.3. Use Case Detail

**Purpose:** The most critical section. Each use case must be described in complete detail with a 16-row specification table.

#### 3.3.1. Use Case Detail Table

For each Use Case, create a numbered table with these exact rows:

| # | Field | Instruction | Example |
|---|---|---|---|
| 1 | **Use case ID** | Unique identifier matching the Use Case List (e.g., `UC_01`, `DW_01`) | `UC_01` |
| 2 | **Use case Name** | Short, descriptive name | `Successful Cash Out via Agent` |
| 3 | **Description** | Overall flow description covering the whole case end-to-end | `Subscriber initiates a cash out from their MoMoney wallet at an authorized agent location. The system validates the request, processes the transaction, and both parties receive confirmation.` |
| 4 | **Actors** | All parties involved. Choose from: `Subscriber, System, Merchant, MoBiz Business User, Agent, 3rd Party, Operator, Officer, Aggregator, Biller, Bank` | `Subscriber, Agent, System` |
| 5 | **Channel** | All applicable platforms. Choose from: `MoMoney Wallet App, Mobiz App, Mobiz Portal, Agent App, Merchant App, Merchant Portal, DW BackOffice Portal, DW Biller Portal, DW Loyalty Portal, AMS Portal, DSE App` | `MoMoney Wallet App, Agent App` |
| 6 | **Offer** | Which user types/tiers can access this feature. List all applicable: Subscriber (L1/L2/L3/Employee/Mo Employee), Merchant (Online/Offline), Agent (Agent/Master Agent), MoBiz (Individual/Business/Corporate Class A Portal User) | `Subscriber L2, Subscriber Employee L1, Subscriber Employee L3` |
| 7 | **Preconditions** | Conditions that MUST be true before this use case can execute | `1. Subscriber has active L2 wallet account. 2. Subscriber balance ≥ cash out amount + fee. 3. Agent is within service hours and has sufficient float. 4. Subscriber has not exceeded daily cash out limit.` |
| 8 | **User journey** | Step-by-step UI interaction steps. Focus on what the user sees and does on each screen. End-to-end. | `1. User opens app → taps "Cash Out". 2. Enters amount → System shows fee and total deduction. 3. Selects Agent from map/list. 4. Reviews confirmation screen → Enters PIN. 5. Receives Cash Out code on success screen. 6. Shows code to Agent. 7. Receives push notification of successful transaction.` |
| 9 | **Validation** | ALL business and technical validation rules. Include: Limitations (Daily, Per Txn, User Account, Wallet, Balance, Service, Offer), Alternative scenarios, System validations | `1. Amount must be ≥ 1,000 MMK and ≤ 5,000,000 MMK per transaction. 2. Daily limit: 10,000,000 MMK. 3. Monthly limit: 50,000,000 MMK. 4. PIN must match. 5. Agent must be active and not suspended. 6. Agent float must be ≥ cash out amount.` |
| 10 | **Limitations** | Max/Min amounts per transaction, per day, per month | `Min per txn: 1,000 MMK. Max per txn: 5,000,000 MMK. Max per day: 10,000,000 MMK. Max per month: 50,000,000 MMK. Max transactions per day: 10` |
| 11 | **Expectation** | Expected output/result of this use case | `Transaction completed successfully. Subscriber balance reduced by amount + fee. Agent balance increased by amount + commission. Both parties receive success notification. Transaction visible in history.` |
| 12 | **GL Posting** | Double entry accounting (Debit/Credit). List each flow with a title. | *(see GL Posting example below)* |
| 13 | **Fee** | Fee structure for this transaction. Specify: Fix/Percentage/Tier-based, conditions, who is charged | `Fee: 0.5% of transaction amount, minimum 500 MMK, maximum 5,000 MMK. Charged from: Subscriber. Fee type: Percentage with min/max cap.` |
| 14 | **Distribution** | How the fee is distributed among parties. Must total 100% | `Total Fee = 100%. MoMoney System: 60%. Agent: 30%. Master Agent: 10%.` |
| 15 | **Notification** | Notification details per status (see Section 4 for full template) | `Status: Success. Type: Push + SMS. Title: "Cash Out Successful". Content: "You have cashed out {Amount} MMK. Fee: {Fee} MMK. Txn ID: {TxnID}. Date: {Date}"` |
| 16 | **UI** | Screens and visual elements the user sees during this journey | `Screen 1: Cash Out Amount Entry. Screen 2: Agent Selection (Map + List view). Screen 3: Confirmation (shows amount, fee, agent name). Screen 4: PIN Entry. Screen 5: Success Screen (shows Cash Out Code, Txn ID, amount). Screen 6: Transaction Receipt (downloadable/shareable).` |
| 17 | **Report Template** | Column list for any reports generated from this use case | `Columns: Txn ID, Date/Time, Subscriber Phone, Agent Code, Amount, Fee, Net Amount, Status, Channel` |

**GL Posting Example (Row 12):**
> 1. **Cash Out — Subscriber Debit**
>    - Debit: Amount + Fee from Subscriber Wallet GL
>    - Credit: Amount + Fee to Suspense GL
>
> 2. **Cash Out — Agent Credit**
>    - Debit: Amount from Suspense GL
>    - Credit: Amount to Agent Float GL
>
> 3. **Cash Out — Fee Distribution**
>    - Debit: Fee from Suspense GL
>    - Credit: 60% to MoMoney Revenue GL
>    - Credit: 30% to Agent Commission GL
>    - Credit: 10% to Master Agent Commission GL

---

#### 3.3.2. Data Field Table

**Purpose:** Defines EVERY input/output field with validation rules. Developers use this for API design. QA uses this for test case boundaries.

| # | Field Name | Rule/Format | Min/Max Length | Validation | Required? | How to Get |
|---|---|---|---|---|---|---|
| 1 | `Phone` | `number` | `9-11` | `Start with "09", 9-11 digits only, no special characters` | `YES` | `User keyin` |
| 2 | `Amount` | `numeric` | `4-10` | `Min 1,000 MMK, Max 5,000,000 MMK. No decimal. Daily/monthly limit check` | `YES` | `User keyin` |
| 3 | `Agent Code` | `alphanumeric` | `6-10` | `Must be a valid, active agent code in the system` | `YES` | `User selection from list/map` |
| 4 | `PIN` | `number` | `6` | `Exactly 6 digits, must match stored PIN, max 3 attempts` | `YES` | `User keyin` |
| 5 | `Cash Out Code` | `number` | `6` | `System-generated OTP, valid for 15 minutes, single use` | `YES` | `System generated` |
| 6 | `Remarks` | `string` | `0-200` | `Optional free text, no script injection` | `NO` | `User keyin` |
| 7 | `Transaction ID` | `alphanumeric` | `16` | `System-generated unique identifier` | `YES` | `System generated` |

---

#### 3.3.3. Error Message Table

**Purpose:** Lists ALL error scenarios with bilingual messages (English + Burmese). Developers implement these exact strings. QA verifies these exact messages.

| Error | Error Message in English | Error Message in Burmese |
|---|---|---|
| `Insufficient Balance` | `Your wallet balance is insufficient to complete this transaction.` | `သင့်ပိုက်ဆံအိတ်လက်ကျန်ငွေ မလုံလောက်ပါ။` |
| `Daily Limit Exceeded` | `You have reached your daily cash out limit. Please try again tomorrow.` | `သင်၏နေ့စဥ်ငွေထုတ်ကန့်သတ်ချက် ပြည့်သွားပါပြီ။ မနက်ဖြန်ထပ်ကြိုးစားပါ။` |
| `Agent Float Insufficient` | `The selected agent does not have sufficient float. Please select another agent.` | `ရွေးချယ်ထားသောအေးဂျင့်တွင် လက်ကျန်ငွေ မလုံလောက်ပါ။ အခြားအေးဂျင့်ကို ရွေးချယ်ပါ။` |
| `Invalid PIN` | `The PIN you entered is incorrect. You have {remaining_attempts} attempts remaining.` | `သင်ထည့်သွင်းသော PIN မှားယွင်းပါသည်။ {remaining_attempts} ကြိမ် ကျန်ပါသေးသည်။` |
| `Cash Out Code Expired` | `Your Cash Out code has expired. Please initiate a new transaction.` | `သင်၏ငွေထုတ်ကုဒ် သက်တမ်းကုန်သွားပါပြီ။ ငွေလွှဲမှုအသစ် ပြုလုပ်ပါ။` |
| `Service Unavailable` | `Cash Out service is temporarily unavailable. Please try again later.` | `ငွေထုတ်ဝန်ဆောင်မှုကို ယာယီရပ်ဆိုင်းထားပါသည်။ နောက်မှထပ်ကြိုးစားပါ။` |

**Instructions:** 
- Must provide BOTH English and Burmese for every error
- Use `{variables}` for dynamic values (e.g., `{remaining_attempts}`, `{Amount}`)
- Cover all validation failures from the Data Field table and Use Case validations

---

## IV. NOTIFICATIONS TEMPLATE

**Purpose:** Defines all notification messages sent to users/actors during and after the transaction. This is critical for development (state machine mapping) and operations (audit trail).

**Formatting Rules (Strict):**
- Use a bulleted list for each status
- Each status must include: **Status**, **Trigger**, **Sender/Receiver**, and **Channel**
- Below these fields, include a **Template** section with:
  - **Title** (on its own line)
  - **Content** (on its own line)

**Statuses to cover:** Processing, Success, Fail, Reverse, and others based on requirements.

**Example:**

**• Processing**
- **Status:** Processing
- **Trigger:** When the cash out request is submitted and backend processing begins
- **Sender/Receiver:** System → Subscriber
- **Channel:** Push Notification
- **Template:**
  - **Title:** Cash Out Processing
  - **Content:** Your cash out of {Amount} MMK is being processed. Transaction ID: {TxnID}.

**• Success**
- **Status:** Success
- **Trigger:** When GL posting is completed and agent confirms cash dispensed
- **Sender/Receiver:** System → Subscriber AND System → Agent
- **Channel:** Push Notification + SMS
- **Template (Subscriber):**
  - **Title:** Cash Out Successful
  - **Content:** You have successfully cashed out {Amount} MMK. Fee: {Fee} MMK. Cash Out Code: {Code}. Agent: {AgentName}. Date: {DateTime}. Txn ID: {TxnID}.
- **Template (Agent):**
  - **Title:** Cash Out Fulfilled
  - **Content:** Cash out of {Amount} MMK for {SubscriberPhone} completed. Commission: {Commission} MMK. Txn ID: {TxnID}.

**• Fail**
- **Status:** Fail
- **Trigger:** When any validation fails or system error occurs
- **Sender/Receiver:** System → Subscriber
- **Channel:** Push Notification
- **Template:**
  - **Title:** Cash Out Failed
  - **Content:** Your cash out of {Amount} MMK could not be processed. Reason: {ErrorMessage}. Please try again or contact MO call center.

**• Reverse**
- **Status:** Reverse
- **Trigger:** When a completed transaction is reversed by Operations due to dispute/fraud
- **Sender/Receiver:** System → Subscriber AND System → Agent
- **Channel:** Push Notification + SMS
- **Template:**
  - **Title:** Cash Out Reversed
  - **Content:** Your cash out transaction {TxnID} of {Amount} MMK has been reversed. {Amount} MMK has been credited back to your wallet. For inquiries, contact MO call center.

**Why these instructions matter:**
- **Status Mapping:** Defined statuses map directly to the **State Machine** in backend code
- **Trigger Precision:** The "Trigger" field tells the technical team exactly which API response or database change fires the notification
- **Audit & Variable Readiness:** Specifying "Title" and "Content" with `{Variables}` enables developers to build template mapping directly using fields from the Data Table (e.g., `{Status}`, `{Account}`, `{Amount}`)

---

## FOR CR (CHANGE REQUEST) DOCUMENTS — Additional Section

### III. Details — Change Request Table

**Purpose:** When the document type is CR, replace the "Use Case Detail" table with a "Change Request Detail" table that specifically highlights WHAT IS CHANGING from the current behavior.

| # | Field | Instruction | Example |
|---|---|---|---|
| 1 | **Change Request ID** | Unique CR identifier | `CR_01` |
| 2 | **Change Request Name** | Descriptive name of the change | `Displaying Specific Error Message for KYC mismatch in bank linkage process` |
| 3 | **Channel** | All channels where this change applies | `Subscriber App (all offers), Agent App (all offers), Merchant App (all offers), Mobiz App (all offers), MoBiz Portal (all offers)` |
| 4 | **Actor** | Who is affected by this change | `MO users (Subscriber/Agent/Merchant/Mobiz/Mobiz Portal)` |
| 5 | **Workflow/Process** | Step-by-step current + changed flow. Highlight changed steps in **red** | `Step 1: Log in. Step 2: Navigate to "Link Bank". Step 3: Enter bank account number. Step 4: Click Submit. Step 5: If KYC matches → Success screen. Step 6: If KYC mismatches → **Show SPECIFIC error message** (changed from generic message)` |
| 6 | **Overview** | What data/logic is involved in the change | `KYC data that must match: Name, Phone Number, NRC, DOB. Note: "Gender" excluded from matching.` |
| 7 | **Enhancement Area** | Specific area being enhanced | `Displaying Specific Error Message for KYC Mismatch in Bank Linkage Process` |
| 8 | **Description** | Current behavior + what's wrong with it. Include screenshots if applicable | `Currently, a general error message "Bank Information mismatch" is displayed. Users don't know WHICH KYC field mismatched.` |
| 9 | **Change Request** | The NEW behavior. List every scenario with exact error messages in English AND Burmese. Use color coding: red for scenario labels, green for messages | *(See scenario examples in the CR sample — list each mismatch field combination with exact bilingual messages)* |
| 10 | **Acceptance Criteria** | Conditions for the CR to be considered complete. Must be testable. | `1. Language-specific messages display correctly. 2. Bank linkage succeeds only when ALL KYC data matches. 3. Move Money functions work after successful linkage. 4. Change applies to ALL channels.` |

---

## QUICK REFERENCE: AI Agent Checklist

When generating a BRD/CR, the AI Agent must verify:

- [ ] Document type correctly identified (BRD vs CR)
- [ ] All document info fields are filled
- [ ] Revision history has at least one entry
- [ ] Approvals table included (for CR)
- [ ] Overview paragraph follows the exact template text
- [ ] Terms and Glossary covers ALL abbreviations
- [ ] Business Benefits lists ALL actors with specific benefits
- [ ] Action table covers Business, Operations, AND Tech perspectives
- [ ] Impact Feature lists ALL channels (even those with "No impact")
- [ ] Scope of Work table includes channel + feature + sub-feature
- [ ] Use Case List covers Happy, Alternative, Fail, Edge, and Reverse cases
- [ ] Each Use Case Detail has ALL 16-17 rows filled
- [ ] Data Fields have validation rules, min/max, and how-to-get
- [ ] Error Messages are provided in BOTH English and Burmese
- [ ] GL Posting shows complete double-entry with titled flows
- [ ] Fee structure specifies type (Fix/Percentage/Tier), min/max, and who pays
- [ ] Distribution adds up to 100%
- [ ] Notifications cover Processing, Success, Fail, and Reverse statuses
- [ ] All `{Variables}` in notifications map to fields in the Data Field table

---

