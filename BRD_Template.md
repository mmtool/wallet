# I. Overview:

## 1.1. Document information:

| **Name**          | Description |
| ----------------- | ----------- |
| **Document Name** |             |
| **Type**          |             |
| **Status**        |             |
| **Code**          |             |
| **Author**        |             |
| **Create Date**   |             |


## 1.2. Document revisions:

|**Revision**|**Date**|**Document Change**|**Changed By**|**Revised By**|
|---|---|---|---|---|
|1.0|08/09/2025|Final document|Kaung Htet Min||

## 1.3. Overview

This document defines the high-level requirements of **Mo Payment BRD.** It will be used as the basis for the following activities:

- Creating solution designs
    
- Developing test plans, test scripts, and test cases
    
- Determining project completion
    
- Assessing project success
    

**Business Benefits/Purpose**

Add description details if available whole project goals

All Business Benefits,

## 1.4 Action

_Change features will be done by who, which system?_

_what will be performed base on that feature ?_

Note Add more columnfor details to Clear seen from all business, Operation, Tech Perspective.

|**Feature**|**Actor**|**Action**|
|---|---|---|
||||
||||
||||
||||

## 1.7. Impact Feature

_Existimg Features Impact , Impact Area, Note for Further Impact_

|**Channel**|**Feature**|
|---|---|
|||
|||
|||

# II. Scope of work

_Enhanced features details_

Express All Details Requirements Function or non or operation

Boundaries and Add more Column to Describe Details, Developer, can know clearly for full scope area like service, features etc . 

You can add more like Description, Sub Features if applicable,
and can add some details with scope , retry , error handling etc.

Mentioned Suggestion of scope should include

| **Channel** | **Feature** | Remark |
| ----------- | ----------- | ------ |
|             |             |        |
|             |             |        |
|             |             |        |

# III. Use Case

## 3.1. Diagram

Notes: End to end process

Activities Process Flow Diagram,
Business Flow Diagram ,
Process Flow
Tech Flow Diagram ,
BPMN Diagram,

|**Step**|**Description**|
|---|---|
|1||
|2||
|3||
|4||
|5||

## 3.2. Use case List

Consider All Use Case from All Perception Success, Alternative, Fail , Happy, etc.

Make Sure all List Out Of all Case which Help to Development and QA Test Case can Reference, and Can Know the case which Strange case , Additional Case , Normal case , etc.

|**Use case ID**|**Use case Name**|
|---|---|
|||
|||

## 3.3. Use case

### 3.3.1. Use case Detail

Format Rule Strictly, Each Use Case in Usecase Detail Table . Make sure Each Cell can be included different type eg . list, bullet list , Number list, etc put in cell of Table. advoid seperate or break to out side of usecase details table template.

There will be 2 Column at use case table , Column 1 is the title of template and Column 2 is fill value of the use case Details. 

| **Use case ID**     | DW_01                                                                                                                                                                                                                                                                                                                                                 |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Use case Name**   | Name Short                                                                                                                                                                                                                                                                                                                                            |
| **Description**     | Overall Flow Whole Case                                                                                                                                                                                                                                                                                                                               |
| **Actors**          | Subscriber,System, Merchant,MoBiz Business User, Agent, 3rd Party , Operator,Officer, Aggregator, Biller, Bank etc                                                                                                                                                                                                                                    |
| **Channel**         | MoMoney Wallet App, Mobiz App, Mobiz Portal, Agent, Merchant App, Merchant Portal, DW BackOffice Portal,DW Biller Portal, DW Loyalty Portal, AMS Portal, DSE App                                                                                                                                                                                      |
| Offer               | if MoMoney Wallet User<br><br>- Subscriber L2,<br>    <br>- Employee L1 ,<br>    <br>- Employee L3,<br>    <br>- Mo Employee<br>    <br><br>Merchant<br><br>- Online Merchant,<br>    <br>- Offline Merchant<br>    <br><br>Agent<br><br>- Agent, Master Agent<br>    <br><br>MoBiz<br><br>- Individual , Business, Corporate Class A ( Portal User ) |
| **Preconditions**   | Precondition of use case to execute                                                                                                                                                                                                                                                                                                                   |
| **User journey**    | Step By Step Of Focus on UI - Interface Steps<br><br>Whole of Case End to End Steps UI interaction and detail that described as user steps                                                                                                                                                                                                            |
| **Validation**      | All Validation related with system, features, rule , policy that help developers not missing with validation <br> included all Technical, Business, Others like, Alternative, System,                                                                                                                                                                 |
| **Limitations**     | Max Min Amount Per Txn,<br><br>Per Day, Per Month                                                                                                                                                                                                                                                                                                     |
| **Expectation**     | Expected Output                                                                                                                                                                                                                                                                                                                                       |
| **GL Posting**      | Double Entry Debit Credit<br><br>1. Title of Flow<br>    <br><br>- Debit Amount from --<br>    <br>- Credit Amount to Suspense GL<br>    <br><br>1. Title of flow<br>    <br><br>- Debit Amount from Suspense GL<br>    <br>- Credit Amount to<br>    <br><br>3.4.5 .<br><br>.                                                                        |
| **Fee**             | fee of txn service<br><br>Fix , Percentage ,<br><br>Tier base Conditions?<br><br>Charge from ?                                                                                                                                                                                                                                                        |
| **Distribution**    | distribution base on Fees<br><br>% of Total Fee , base on 100%<br><br>Distribution can be Agent, System, Merchant etc                                                                                                                                                                                                                                 |
| **Notification**    | Status :<br><br>Type :<br><br>Title :<br><br>Content :<br><br>Sample                                                                                                                                                                                                                                                                                  |
| **UI**              | Journey View list data                                                                                                                                                                                                                                                                                                                                |
| **Report Template** | Column List                                                                                                                                                                                                                                                                                                                                           |

**Note: Information will be different based on Use Case**

### 3.3.2. Data Field

|**Field name**|**Rule/ Format**|**Min length/ Max length**|**Validation**|**Required?**|**How to get**|
|---|---|---|---|---|---|
|Phone|number|9-11|- Start with “09”<br>    <br>- Have 9-11 characters|YES|- User keyin|
|Amount|numeric||- Daily/weekly/monthly limit<br>    <br>- Min/max amount|YES|- User keyin|
|Remarks|string|||NO|- User keyin|

### 3.3.3. Error Message

|**Error**|**Error Message in English**|**Error Message in Burmese**|
|---|---|---|
||||
||||
||||
||||
||||

@status

## **4. Notfications Template**

​**Formatting Rules (Strict):**

- ​Use a bulleted list for each status.
    
- ​Each status must include these fields: **Status**, **Trigger**, **Sender/Receiver**, and **Channel**.
    
- ​Below these fields, include a **Template** section with two specific sub-bullets:
    
    - ​Title (on its own line)
        
    - ​Content (on its own line)
        

​Statuses to cover: Processing, Success, Fail, and Reverse and Others base on required

###   
**Why these instructions matter**

- ​**Status Mapping:** By defining specific statuses like Processing or Reverse, you ensure the developers map these directly to the **State Machine** in the backend code.
    
- ​**Trigger Precision:** The "Trigger" field tells the technical team exactly which API response or database change (e.g., a webhook from the bank) should fire the notification.
    
- ​**Audit & Variable Readiness:** By specifying "Title" and "Content" on separate lines with {Variables}, developers can build the template mapping directly into the code using fields from the **Data Table** and othersfrom db (e.g., {Status} txn, Your {Account} {Amount}...etc).