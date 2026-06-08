
| **Version** | **Desc**                        | **Date** | **Creator** |
| ----------- | ------------------------------- | -------- | ----------- |
| 1.0         | User manual for Operation Guide | 1/7/2021 | Thuan Vu    |

# Preface

## Introduction

This user guide describes some the functionality offered by the Wallet Administrator website, including written instructions for each section and linked screenshots. It provides instructions on how to use the functions for the Operator team, excluding developer configuration.

## Audience

This manual is designed for the users from he Opos team, support team.

## Organization

This manual is organised into the following chapters:

| **Chapter No.** | **Description**                                                                                                                                                      |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                 | **Preface**: gives information about the purpose and scope of the document. It also defines the targeted audience and gives idea about the structure of this manual. |
|                 | **Overview of Wallet Admin**: provides an overview of Wallet Admin.                                                                                                  |
|                 | **User manual for Wallet Admin**: some basic instructions on how to administer and configure the website.                                                            |

# Overview of Wallet Admin

Wallet Admin system contains 3 mobile applications for iOS and Android devices: Subscriber App, Agent App and Merchant App. This system allows users to top up, online payment, bill payment, transfer money,...  
Wallet Admin system is designed to provide a wide range of payment technology between Customers and Agents, Merchants, Acquirers, Officers, Billers,... through both e-wallet & unwallet and linked bank account.   
Wallet Admin website is intended to help the user administer this payment system with specific sections as below:

| **No.** | **Functionalities** | **Section in the document** |
| ------- | ------------------- | --------------------------- |
|         | Login               | Section 1                   |
|         | Operations          | Section 2                   |
|         | Accounting          | Section 3                   |
|         | System History      | Section 4                   |
|         | Work Flow           | Section 5                   |
|         | Report              | Section 6                   |

# User manual for Wallet Admin

## Login

This is user guide new flow for login officer to admin portal. To increase security, officer need to authenticate with OTP on new devices. 

- In the Login form, officer enter User Name, Password, Captcha. 
    

- After click "Sign In', will show "OTP Verify" screen. And user need to enter Captcha, OTP with 6 degits to login. 
    

- To get OTP, access to registered email of officer.
    
- After that, enter OTP and login successfully, go to Dashboard screen.
    

## Dashboard

In this Module, overview of daily activities is performed.

- At the top of the page, it shows the increased number of Customers, Agents, Merchants and Billers over time.
    

- Next, all succeed transactions are indicated in Transaction Summary. This section can be viewed in 3 different ways: Tableview, Barchartview & Piechartview.
    
- Transactions which are cancelled or failed are recorded in the form of line graphs.
    

- Onboard List shows chart of onboarding Customers, Agents, Merchants & Billers in the system.
    

## Operations

### 2.1. Agents

Agent branches are built for the customers to top up their phone, cash in/out and send money, move money between Agent's wallet and linked bank account, or use for bill payment. But before the Agents can use any of those services, they should be registered first.

- The Agent account registration process can be done in following way:
    
- The admin user needs to log into the service provider web console. Then he/she needs to click on "Operations", available on the left menu.
    
- After clicking on "Operations", the user needs to click on "Agents".
    
- Then click on the "Create" or “Import” button. Import function support for upload excel file.
    
- From here, the user needs to fill up all the required parameters in the form, then click on "Save". The admin user successfully completes the registration process or cancels the process by choosing "Cancel".
    

- The admin can also view a list of Agent accounts with basic details, and search for Agents through their id, name, email, type, phone number, register name, activated date & status.
    

- The admin user is allowed to edit, lock, active or reset password of each Agent.
    

- By clicking on "Action", then "Detail", he/she can view and change all information of the Agent.
    

- At the bottom of this section, the admin gathers information about the activities summary of the Agents: Pocket Summary, Transactions, Customers, Commissions, Customer Activation and Transaction Summary over time. 
    

### 2.2 Customer

This section lists Customer's information.

- To add a new Customer, click on "Create".
    

  
Customers can be created in two ways:

- Quick Registration
    
- Full Registration with KYC
    

- The admin user can search for Customer through their id, name, phone, email, NRIC number,... or registered date, account balance, offer, status.
    
- The admin user is allowed to update detail, 360 View, approve/lock, reset password, change offer of Customer in "Action".
    

- Customer Detail includes 6 main parts:
    

First, the Detail Customer performs specific information as below: 

- At the bottom of the page contains Customer's summary of Pocket, Transactions History
    

- The admin user can also review Detail Transaction of Transaction Summary:
    

- Second part, Document stores photos of identification card. There also shows the level; status; created, approved & refused date of Customer, creator and the account that approved & refused this Customer.
    

- The third part, Device Managements shows all the device where customer logged in.  
    

- Part number four, in this tab the admin user can see the bank account information of the Customer.
    

- Next tab is Pocket Management
    

- The last part is Devices History.
    

### 2.3 Merchant

Merchants allow customers to move money between wallet and linked bank account or refund all transactions. This section lists all existing Merchant accounts in system.

- Add new Merchant by clicking on "Create", “Import”
    

  
Fill in all required fields, the admin user can also upload avatar or contract of new Merchant. Then select "Save" to create Merchant, or "Cancel" to return.  

- To search for a Merchant, enter data into search fields including id, name, email, phone, register name, activated  date and status.
    
- Type of Merchant are: Merchant or Thirdparty. Merchant is normal Merchant, Thirdparty use for Online Merchant
    
- The user is allowed to see/edit detail, active/lock or reset password, close account of Merchants. Officer can set up Fee for each Merchant.
    

- To edit Merchant's information, choose Detail in "Action", then click on "Edit".
    
- The user can change or update all fields as below. To keep updated information, select "Save", to return click on "Cancel".  
    In Detail, all Merchant's summary information like KYC Information, Account Information, Open Hours Information, Contract Information.
    
- Merchant Detail includes 6 main parts: Infor Details, Device Management, Bank Account, Poket Management, Sub-Merchant, Config Callback.
    
- The admin gathers information about the activities summary of the Agents: Pocket Summary, Transactions, and Transaction Summary over time. 
    

- Sub-Merchant : show all Employee of Merchant
    

### 2.4 Sub-Merchant

Sub-Merchant is Employee of Merchant. Sub-Merchant have 3 role: Owner, Admin, Sale. Each permission will have different access rights but it will have the main conditions as:

- Refund only transactions generated by themself
    
- Login to app by User ID of Merchant, phone of Sub-Merchant
    
- The amount will be transferred directly to the Owner Merchant after Sub-merchant do transaction successfully.
    

To have account, officer need register account for Sub-Merchant.

### 2.5 Officer

Officer is configured for employees working in bank.

- To add new Officer, click on "Create".
    

- Enter all needed information, upload Profile Picture if necessary, then choose "Save" to complete, or "Cancel" to return.
    

- The admin can search for Officers by entering data into the search fields, including id, name, group, phone, email, status.
    

- He/she can also edit details of created Officer by select Detail in "Action", and is also allowed to active/lock and reset password of officer account.
    

- In Detail, there are 2 main tabs. The first one is Detail Officer, admin user can view Officer information and can Edit or update information.  
    

- The second tab is Devices, in this tab the admin user can view the device where officer logged in. He/she can also remove of lock that device.
    

### 2.6 Merchant Categories

In Merchant Categories, the admin user can view all types of existing Merchants.

- To create a new type, click on "Add"
    
      
    Fill in all required fields, choose lock/active in Status, then click on "Save". Or select "Cancel" to return.
    

- To search for Merchant Type, insert data into the search field.
    

- The admin user is allowed to update detail, delete, lock/active each Merchant type in "Action".
    

### 2.7 Acquirer

This section shows list of Acquirers in Banking system.

- To add an Acquirer, click on "Create".
    

- Fill in needed information, then select "Create" to finish, or "Cancel" to return.  
    

- The user can find an Acquirer in search field.
    
- The admin user is allowed to update detail, delete, lock/active each Acquirer in "Action". 
    

### 2.8 ATM

This section shows a list of ATMs with specific information such as address, coordinates (latitude and longitude), status.

- To create a new one, click on "Create".
    

- Fill in all needed fields and select "Save". Or choose "Cancel" to return.  
    

- The admin user can search for ATMs by entering one of their information into search field.
    
- The user can also edit or active/lock ATMs in "Action".
    

-   
    To update an ATM's information, select "Edit" in "Action". After editing, click on "Update" to finish, or "Back" to return.
    

### 2.9 Approve Documents

This section summarizes all the documents that need to approve.

- The admin user can search for name, phone, approved account, NRC number to find a Document.
    

- Select Detail to review, approve/refuse a Document.
    

### 2.10 Approve Locations

This section summarizes client locations that need to be approved. Agent or Merchant will request update location from application.

- The admin user can filter the search by date, client type, or status.   
    
- To review, approve/refuse Location, select “Detail”.
    
- After the review, select “Approve”, “Refuse” or “Back”.
    

### 2.11 Branch

This section shows all WALLET Bank Branches. 

- To add a new Branch in Admin page, click on “Create”.
    
- Fill in all fields then select “Create”, or “Back” to return.
    

- The user can search for Branches by using the search field.
    
- The admin user is allowed to edit detail, lock or delete a Branch by clicking on “Action”.
    
- To update a Branch’s detail, select Edit in “Action”.
    

### 2.12 Township

Township is used to register new townships and assign township name, code, and city/province.

- Township registration process can be done in following way:
    
- The admin user needs to log into the service provider web console. Then he/she needs to click on “Operations”, available on the left menu.
    
- After clicking on "Operations", the user needs to click on “Township”.
    
- Then click on the "Create" button.
    

- From here, the user needs to fill up all required parameters in the form, then click on "Save”. The admin user successfully completes the registration process or cancels the process by choosing “Cancel”.
    

- The admin user can also view township details and search for Township through their code, name, and city/province.
    
- The admin user is allowed to edit and delete each Township.
    
- By clicking on "Action", then "Edit", the user can view and change all information of the Township.
    

### 2.13 Province

Province is used to register new province, choose province type, and assign province code.

- Province registration process can be done in following way:
    
- The admin user needs to log into the service provider web console. Then he/she needs to click on “Operations”, available on the left menu.
    
- After clicking on "Operations", the user needs to click on “Province”.
    
- Then click on the "Create" button.
    

- From here, the user needs to fill up all required parameters in the form, then click on "Save”. The admin user successfully completes the registration process or cancels the process by choosing “Cancel”.
    
- The admin user can also view township details and search for Township through their code, name, and city/province.
    

- The admin user is allowed to update and delete each Province.
    
- By clicking on "Action", then "Update", the user can view and change all information of the Province.
    

### 2.14 Agent Categories

In Agent Categories, the admin user can view all types of existing Agents.

- To create a new type, click on "Add"
    
- Fill in all required fields, choose lock/active in Status, then click on "Save". Or select "Cancel" to return.
    
- To search for Merchant Type, insert data into the search field.
    
- The admin user is allowed to update detail, delete, lock/active each Merchant type in "Action".
    

### 2.15 Corporate

Corporate used to register a Wallet account to login to Corporate portal wallet:

- Click “Create” to register account
    
- enter full information and complete after 4 step:
    

- The admin can also view a list of Corporate accounts with basic details, and search for Customers throught their id, name, email, phone number, NRIC number, state, offer, channel, date, and status. 
    

- The admin user is allowed to edit, have 360 view, lock, or reset password, change offer, close of each Corporate.
    
- By clicking on "Action", then "Detail", he/she can view and change all information of the Corporate.
    

## Accounting

### 3.1 Transaction 360

In this section, the admin user is allowed to review Transactions history with all types of services as below:

- To search for a Transaction, the user needs to fill in fields, include: id, name, phone, date duration, type and status of Transaction.
    

- The admin is not allow to edit a Transaction, but he/she can view Transaction detail in "Action".
    

- This screen contains 3 main part:
    
- In the left, it shows the detail information of Transaction.
    
- In the middle is Transaction stages from start to end.
    
- And in the right, it performs each stage's details.
    

- The admin can see details of each stage by clicking on it.  
    In "Start", the user is allowed to view input information of a Transaction, includes user id, client, service id, sender id, sender phone, sender client, money amount, currency, device id.  
     
    

- In "Stage 1", it shows all requests sent to the system when a Transaction started. This includes related fields which are needed to validate a Transaction.  
    First, the system will validate all input information, such as sender id, sender phone number, receiver client, currency, money amount,…
    

- If these fields match the right data format, the system will calculate fees that the sender and the receiver has to pay.   
    Next, the system will determine the total amount that the sender must pay and check if the sender's account is sufficient to pay this amount, or the limits of this account can meet the payment conditions or not.  
     
    

- If a third party is involved in this Transaction, such as biller, the system will validate all biller fields.  
       
    After requesting, a Transaction needs to be confirmed. In "Stage 2" the admin can see the transaction authentication, includes PIN, OTP or 2FA and sender phone, client information.  
     
    

- In "Stage 3", it shows details information when the transaction authentication in stage 2 is completed. The admin can see if PIN/OTP/2FA is verified or not, and also review all service actions have occurred in system.
    
- Click to “GL Posting” tab to view GL Flow of each transaction
    

- Cash flows will be recorded into both system's GI accounts and the sender's account.   
    In "End", it shows all details information of transaction and transaction results. Transaction history will be recorded after this step is completed.
    

- The admin user is allowed to view all of these steps if they are validated. For example, if the authentication method is incorrectly entered, he/she can only see the start and request stage.
    

### 3.2 Jouanal Entry

In this section, the admin user is allowed to review step by step GL history with all types of services offered:

- Officer can export or search to reconcile
    

### 3.3 Transaction

In this section, the admin user is allowed to review Transactions history with all types of services offered:

- The user can search for a Transaction by filling out Reference code, Reference ID, Channel, Transaction Status, Cash Code Status, Service Name, Phone Number, and Date.
    
- The admin is not allowed to edit a Transaction, but he/she can view Transaction detail in “Detail”.
    

### 3.4 Biller Settlement

In this section, the accountant or administrator can make accounting adjustments of all billers accounts. 

- The admin user can search by Reference ID, Biller, Date Creator Name, and Status. 
    
- The admin user can download account data in “Export”, or add new account by clicking on “Create”.
    

- To create account, the admin user needs to fill in all needed information, then click on “Next”.
    

- Enter PIN to validate adjustment, then select “Next” to complete, or “Previous” to return. If this PIN is confirmed, adjustment will be recorded in “Success”.
    

- The admin user can view settlement detail in “Action”.
    

### 3.5 Cashin Agent

In this section, the admin user can cash in money for agent.

- The admin user is allowed to create Cash-in, export Cash-in data by clicking on “Create” or “Export”.
    
- The admin user can select Cash-In Agent by entering Agent Phone, Agent Name, Date, Creator, and Status. 
    

- To cash in for agent, enter agent’s phone number, money amount, remarks (if needed) and choose currency. If the user fills in correct phone number, the agent's name will appear with a green tick mark.
    

- After clicking on “Next”, the admin can preview entered information in the last screen. If all fields are correct, continue clicking on “Next”.
    
- Then, enter PIN and select “Next”.
    
- If the PIN code is correctly entered, the system will record this Cash-in in “Success”
    

## System Config

### 4.1 User Role

This section shows all Developer Role options. The admin can assign limit access for specific developer users in Admin portal.

- To add a new Developer Role, click on “Create”.
    

- Fill in needed fields and choose “Create” to add a new Role, of “Cancel” to return.
    

- The admin user can also edit an existing role in this section:
    
- Select the Developer Role that the admin wants to edit and click on “Edit”
    

- Change needed fields then click on “Update”, or “Cancel” to return.
    
- Choose Developer Role options. The admin user can click on the name of the option to see access rights. After that, click on “Save” to complete.
    

### 4.2 Menu

This section allows the user to design and assign action permissions for each section in the Menu on the left side.

- To add a new section in Menu, click on “Create”.
    

- Fill in all required fields, choose “Parent”, “Ctg” and “Permission”, “Status”, and “Icon”, then select “Create” to complete or “Cancel” to return.
    

- The admin user can view and edit menu structure by clicking on “View Structure”.
    
- Click on “Save” to update and save menu structure. Click on “Back” to return.
    

- The admin user can find needed information in the search field.
    
- To edit or delete a section in the Menu, click on “Edit” or “Delete”.
    

## System History

### 5.1 Authentication History

Description: **Authentication History** will show lock event, lock type by “_Device, Account, Account on Device_”.

- Locked cases will happen when user enter wrong pin or otp number too many times, need team support to unlock account or device
    

#### 5.1.1 Set permission for user role

Go to user-role and select permission :

#### 5.1.2 Logout Device

- Step 1: Enter “_phone_” and “_device name_” and select “_Channel_: customer or agent or merchant “ or more information in search box to find account is locked.
    

- Step 2: After found correct device, continue find "_locked event_"and "_type_" locked that user reported. After that click to “Device Detail”.
    

- Step 3: View information again and check “Locked Until” time. If it more than current time then click “Logout”.
    

- Step 4: Enter remark and click sure
    

- After logout, the previous "Lock events" of the same type will switch status to “expired”. And user can continue use this event.
    

_Note: You can click “Search” again to reload page._

### 5.2 Device History

Description: This page will show device history and lock event, lock type by “_Device_”.

- Locked cases will happen when user enter wrong pin or otp number too many times, need team support to unlock device
    

#### 5.2.1 Set permission for user role

Go to user-role and select permission :

#### 5.2.2 Logout Device

- Step 1: Enter “_phone_” and “_device name_” and select “_Channel_: customer or agent or merchant “ or more information in search box to find account is locked.
    

- Step 2: After found correct device, check “Locked Until”, if it more than current time then click “Logout” to logout device.
    

- Step 3: Enter remark and click “Logout”
    
- After logout success, status will change to “Pending” and user can continue use this event in application.
    

### 5.3 Authentication

Description: Authentication will show lock events, lock type by “_Account, Account on Device_”.

- Locked cases will happen when user enter wrong pin or otp number too many times, need team support to unlock account or device
    

#### 5.3.1 Set permission for user role

Go to user-role and select permission :

#### 5.3.2 Unlock

- Step 1: Enter “_phone_” and select “_Channel_: customer or agent or merchant “ or more information in search box to find account is locked.
    

- Step 2: After found correct device, check “Locked Until”, if it more than current time then click “Auth Detail”
    
- Step 3: View infomation and click “_Unlock All_” to logout device
    
- Step 4: Enter remark and click “Unlock All”
    

- After logout success, user can continue use this event in application.
    

## Reversal Workflow

A reversal transaction happens when a client wants to recover the amount of money that he/she has made in the original transaction.

- Each transaction is reversed one time only.
    

### 6.1 Maker

#### **6.1.1 Create request**

- **Step 1**: The client creates a new request for Reversal transaction by clicking ‘New request’ in the Workflow module.
    

The client fills in the Transaction Reference ID on the search bar and checks the basic information of that Transaction as below. The Maker can add a message, and attach a file by clicking “Select file”.

- Select file: Most of the transactions need to attach file (.doc, .xlsx, .png etc) for reconciliation
    

- **Step 2**: The client clicks ‘Next’ to proceed to the second step (**Assignee**). This step will decide who will be the Checker for this Reversal Transaction. Then the Maker will choose the Expired date. 
    

- **Step 3**: After selecting the Assignee and choosing the Expired date, the Maker will move on to the next step, which is **Preview**. In this stage, the Maker will preview information of the transaction as shown below.
    

**Step 4:** The maker need to verify to complete reversal request: PIN or OTP or 2FA

**Step 5:** the request for Reversal Transaction will be sent successfully. 

- After successfully create a request for Reversal Transaction. The newly-made request will appear in My request with according status.
    

Once the request is approved/rejected, the maker will receive notification via email and can see the request updated status in My request.

  

#### **6.1.2. Cancel request**

Maker can cancel request that he/she just created. This action only applies for the request with “Pending” status and has not been reversed.

- **Step 1**: Maker clicks on the module “My request” in Workflow, then clicks on “Detail” of the pending request that needs to be cancelled.
    

- **Step 2**: Maker can view the request detail on the screen as well as summary of the status. Then the maker can click on the red button in the upper right corner “Cancel request”. 
    

- **Step 3**: The maker needs to enter PIN and OTP (this verification step will be based on the configuration). 
    

- **Step 4**: After canceled successfully, the status of the request will be updated in My request
    

- Maker will receive notification on admin portal as well as via email.
    

### **6.2 Checker**

- The checker will receive notification of a new reversal request via email with a link to view the details about the transaction.
    

**Step 1**: The checker goes to the Admin Portal and clicks the module **‘My task’** to see pending Requests. Click the button “Action” then “Detail” to decide which action will be done to that Request.

  

**Step 2:** After viewing the details of the Transaction, the Checker will either choose “Approve” or “Reject” for the request.

  

**Step 3:** After the Checker select “Approve” or “Reject”, he/she will move on to the next step. This step will be based on the configuration flow. There are 4 cases according to the configuration: No need verify, verify by OTP, PIN, 2FA

**Case 1**: The Checker does not have to go through the Verification step, he/she just needs to add a comment then click “Confirm Approve/Reject”.

**Case 2**: The Checker needs to verify password and OTP. In this case, the Checker type in Password, OTP in the email, and add Comment then click “Confirm Approve/Reject”. 

**Case 3**: The Checker needs to verify password. In this case, the Checker type in Password and add Comment then click “Confirm Approve/Reject”.

**Case 4**: The Checker only needs to verify OTP. In this case, the Checker type in OTP that was sent to their email and add Comment then click “Confirm Approve/Reject”.

**Step 4**: The request will be approved/rejected successfully soon after that. 

- The maker will also receive notification via email and can see the request updated status in My task.
    

The status of the request will also be updated in “My task”.

  
**6.3 Report**

In this ‘Report’ module, you can search by:

- Name: Reference Transaction ID
    
- Checker’s name
    
- Maker’s name
    
- Choose type: single or multiple
    
- Choose status:
    
- Init
    
- Pending
    
- Approved/Rejected
    
- Done
    
- Canceled
    
- Date: From/TYou can view all the Request for Reversal Transaction and each request’s name, type, flow, maker, checker, created at, status, current step, and action.o
    

View detail each request by clicking Action -> Detail.

### **6.4 Flow config**

In this module, you can configure the flow for Reversal Transaction

- Limit: Config the limit for some criteria as shown below.(cannot use now)
    

- Choose Permission for Checker and Maker
    

- Authorization for Checker and Maker: 
    

Checker and Maker can authorize the request by PIN/OTP/2FA 

- Notification for Checker and Maker
    

###   
**6.5 Workflow Definition**

This section will show you how to add a service, and allow that service to go through the workflow.

- Click to menu Workflow Definitions → Choose a workflow: View Detail
    

- In tab “Input Building”: Add “serviceId” of service that allow it to go through the workflow to Source of config “listService”
    

_Note: Before you add service, you have to go to Transaction Design to get Service_

- Also go to “Form Buider” tab: add service in Params.
    

- After done, click to Publish and reload page.
    

### **6.6 Corporate Information Update by Batches**

This section will show you how to update corporate information.

- Click to menu Operation → Corporate → Import → Update Existing Records → Download the sample file to update.
    

- Sample file will export as xlsx file format then prepare your file and update corporate information to update.
    

- Click choose file and import your file to update.
    

- Correct, Incorrect and basic information will display.
    

- Once you imported successfully, can see in detail after imported.
    

The lists what you can update by batches are.

1. Name
    
2. Offer
    
3. Email
    
4. Gender
    
5. DOB
    
6. Address
    
7. Country
    
8. Region
    
9. District
    
10. Township
    
11. Portrait
    
12. Business License
    
13. Proof of existence
    
14. Clean background
    
15. NRC front and Back