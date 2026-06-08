|   |   |
|---|---|
|Title|MoMoney Portal Configuration Guide|
|Type|Internal guide|
|Code|MoMoney_PC_001|
|Author|Hoang ND|
|Version|1.0|
|Create date|9.12.2021|

## **Overview**

|**#**|**Step**|**Detail**|
|---|---|---|
|1|Create biller|Purpose: Declare new biller and some related information such s: middleware/ Bill URL, the body of the request,...<br><br>Notes: Declare for only transactions that need to integrate to 3rd parties, with internal transactions, skip this step.|
|2|Create Service|Purpose: Declare new services such as Transfer to Wallet, Transfer to Mobile,...|
|3|Create Transaction Design|Purpose: to confi,g the Transaction Flow, Transaction Validation a d Transaction Filed.|
|4|Create Fee/ Distribution/ Discount||
|5|Create notification notification thethe is|Notification to send to party of transaction|
|6|Add new service to offer||

## **Detailed steps**

### 1. Create Biller

**Link: Operations/ Biller ( Biller Management)/ Create**

_Notes:  This is a step only for transactions that need to integrate to 3rd party, with internal transactions, please skip this step._

|   |   |   |
|---|---|---|
|#|Filed Name|Details|
|1|Biller Code (*)|Unique code for each biller|
|2|Biller Name (*)|Biller Name|
|3|Phone (the *)|ID of biller to make transaction|
|4|Type (*)|There are 3 types:<br><br>- Telco: for all Mobile Topup service<br>    <br>- Bank: Move Money/ Fund transfer service<br>    <br>- Bill: Other billers|
|5|Biller URL (*)|Link to biller or middleware|
|6|Request (*)|Body of request|
|7|Settlement|2 Types:<br><br>- Prepaid: as 2C2P, MoMoney will pay for 2C2P first, then settle from Biller Pocket to Operation Account<br>    <br>- Postpaid: MoMoney settle to 3rd partner later (after transaction done). In this case, we can set up a bank account to settle.|
|8|Biller Fields|Declare all field to send to Biller URL|
|9|Biller Validations|add validation rule.|

### 2. Create Service.

**Link: Product Management/ Service/ Add New**

|   |   |   |
|---|---|---|
|#|Filed Name|Details|
|1|Code (*)|Unique code for each service|
|2|Name (*)|Service Name ( tthe his name will be shown in transactionfields)|
|3|Full Name|Service Full Name|
|4|Service Note|config|
|5|Action priority (*)|This ca onfig is to handle kina d of service call to 3rd party.<br><br>There are 2 types:<br><br>- Before: Call to 3rd party first then Post to GL<br>    <br>- After: Post to GL first then call to 3rd party|
|6|Action Type (*)|There are 3 main types:<br><br>- **Transaction creates cashcode**<br>    <br><br>There are some sub configs: <br><br>Cashcodecash code Expiry: Expire time of cashout ( minute)<br><br>Format Cash code: currently, we are using format 000000 ( 6 digits)<br><br>- **Integrate to 3rd party** ( 4 subtypes: Telco, Bill Payment, Fund Transfer and, Link Bank Account)<br>    <br><br>Biller Connecting: Config the biller of service<br><br>- **None**<br>    <br><br>Left transactions as Transfer to Wallet, Pay Merchant, Cash in/ out at Agent,...|
|7|Related|Add Offer Roles related to this service as  Subscriber, Agent, Merchant, Operator|
|8|Channel|2 types: Web and Mobile|
|9|Status|Active or Inactive|
|10|Refund|Declare type of this service are refunded?<br><br>If yes, need to choose service targe|
|11|Description||

### 3. Transaction Design

**Link: Product Management/ Transaction Design**

In Transaction Design, there are some main features:

#### 3.1. Transaction Definition

This step to config step by step of GL Posting. We can choose Dr or Cr to GL or user pocket via GL Level and PProduct-Level Otherside, we also can use the mapping fee/ discount.

|   |   |   |
|---|---|---|
|#|Filed Name|Details|
|1|Debit|Choose GL/ Product want to debit|
|2|Credit|Choose GL/ Product want to credit|
|3|Amount|Add variable|
|4|Des|Description of step|
|5|Is Loop Step|True: Set True in step get fee/ discount value<br><br>False: without fee/ discount step|
|6|Component processed|2 Types: Fee/ Discount|

|||
|---|---|
|TransAmount|= TransOrigAmount + Debit fee|
|TransOrigAmount||
|||
|distribution of a fee||
|- OnBoardAgentDistribution<br>    <br>- OnBoardRedeemAgentDistribution<br>    <br>- AgentDistribution<br>    <br>- RedeemAgentDistribution<br>    <br>- SystemDistribution<br>    <br>- MerchantDistribution<br>    <br>- AggregatorDistribution<br>    <br>- DistributorDistribution<br>    <br>- SubscriberCashback<br>    <br>- BeneficiaryCashback||
|- //fee  <br>    <br>- FeeGlTarget<br>    <br>- FeeDebitValue: // debit value of a fee<br>    <br>- FeeCreditValue // credit value of a fee<br>    <br>- TotalDebitFee // sum debit fee ( multi fee)<br>    <br>- TotalCreditFee||
|- DiscountDebitValue: 0, //debit discount amount of each discount item<br>    <br>- DiscountCreditValue: 0, // credit discount amount of each discount item<br>    <br>- TotalDebitDiscount: 0, // total debit discount amount of whole transaction<br>    <br>- TotalCreditDiscount: 0, // total credit discount amount of whole transaction||
|//discount<br><br>BillerDiscountAmount //biller, telco discount|= amount - system commission|

#### 3.2 Transaction Validation

This Step adds validations for the transaction, we also can configure the error code and error message for each in the portal. Some popular validations for the transaction:

- Validate Amount ( Min, Max, Limit Per Day, Per week, Per month)
    
- Validate interval ( interval time for each transaction)
    
- Validate is Balance sufficiency
    
- Validate account 
    

|**Popular Validation**|||
|---|---|---|
|Can not access to service|||
|Sender is invalid|||
|Currency is not valid|||
|Amount too small|||
|Amount too big|||
|Sender balance not sufficiency|||
|Amount exceeded daily limit|||
|Amount exceeded monthly limit|||
|Amount exceeded weekly limit|||
|Transaction too frequently|||
|Sender balance exceed limit|||
|Receiver balance exceed limit|||
|Sender pocket locked|||
|Receiver pocket locked|||

#### **3.3 Transaction Fields**

To add all fields of the transaction. We can define field name, type, regex, min/ max length and error code for each field if, the client sends the wrong format. we also can configure error messages for each in the portal.

#### **3.4 Input Building**

This is an advanced function, designed for developer use only. 

This step is to query some fields from DB, like Cashout by Cash code. We can query other information in DB to add in transactions. Clients don’t need to add those fields to request.

### 4. Add Fee/ Distribution/Discount

#### 4.1 Add fee

**Link:  Product Management/ Fee**

|     |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| --- | --------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| #   | Filed Name      | Details                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| 1   | Name            | Fee Name                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 2   | GL Target       | Choose GL target of this fee.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 3   | Currency        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 4   | Descriptiotiers |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 5   | Tier            | Can add many tier, each tier can config different condition and fee<br><br>Eg. Amount < 100,000 fee is 100<br><br>Amount < 200,000 Fee is 200                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 6   | Conditions      | To add condition of each tier <br><br>amount: Transaction Amount<br><br>totalDateAmount: The total amount of transactions per day of 1 service,<br><br>totalDateTransaction: The total number of transactions per day of 1 service,<br><br>totalWeekAmount: The total amount of transactions per week of 1 service,,<br><br>totalWeekTransaction: The total number of transactions per week of 1 service,<br><br>totalMonthAmount: The total amount of transactions per month of 1 service<br><br>totalMonthTransaction: The total number of transactions per month of 1 service<br><br>totalQuarterAmount: The total amount of transactions per quarter of 1 service<br><br>totalQuarterTransaction: The total number of transactions per quarter of 1 service<br><br>totalYearAmount: The total amount of transactions per year of 1 service<br><br>totalYearTransaction:The total number of transactions per year of 1 service |
| 7   | Type            | 2 types:<br><br>- Standard: fee = Amount x percentage + amount<br>    <br>- Advance: can config fee with variables of transaction                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

With some special types as MDR for each Merchant, need to config individual fee in Operation/ Merchant

#### 4.2 Add Distribution

**Link:  Product Management/ Distribution/ Create**

#### **4.3 Add Discount**

**Link:  Product Management/ Discount/ Create**  

Almost config in Discount is the same as Fee. 

Discount has 1 more case: get a discount from a 3rd party and apply the voucher from Point. This config allows us to call a 3rd party to verify the voucher.

#### **4.4 Notifications**

**Link: Notifications/ Notification Template/ Create**

We can configure the notification to send to subscriber/ agent/ merchant after a transaction is done successfully.

|   |   |   |
|---|---|---|
|#|Filed Name|Details|
|1|Name|Name will show in app|
|2|Title Name|Full name in system|
|3|Action|Transaction: this type for sending notification after transaction done<br><br>Request: this type for sending Request notificanotification with|
|4|Need secured with|With all information is encrypted in DB|
|5|Need hidden||
|6|Channel|SMS, Push notification|
|7|Content|This type to send via SMS|
|8|Full Content|This type to push notification ( HTML format)|

### 5. Add service to offer

In Offer, we can add a new Role ( subscriber, agent, merchant, biller, operator).

Can change limit pocket, add service, config limit transaction, authentication, fee, discount, and notification.

#### **5.1 Config the Pocket limitation**

**Link: Offer/ Offer Factory/ Choose offer**  

#### **5.2 Add and configure new service**

Step 1: Choose Add or Remove, then choose the service want to add to the offer

Step 2: Config the transaction limitation, Fee, Discount, Authentication, and Notification