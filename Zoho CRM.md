# Zoho CRM Integration

- Contact
- Account
- Deal
- Pipeline
- Stage

- Account
  - Store/Shop
  - New Account for all App Ids

- Contact
  - Merchant/Owner
  - Contact can have Multiple App Id


### Install
- Create Account 
- Link or Create Contact (Shop Owner Email is the link)
- Create Deal on MQL/Install in Sales Pipeline with default value

### Uninstall without Payment
- Move to Lost stage in Sales Pipeline

### Uninstall within Trial/Churn
- Move the deal to (UWT/CHURN) stage in Winback pipeline

### Pause Payment
- Move the deal to Paused stage in CS pipeline

### Uninstall after Pause Payment
- Move the deal to (UWT/CHURN) stage in Winback pipeline

### Re-Install (without Payment)
- Move to Re-Install stage in Sales Pipeline

### Reinstall (within Trial/Churn)
- Move to Re-Install stage in CS Pipeline

### Re Activation
- Move the deal to Re Activate stage in Winback pipeline

### Common
- Move Deal to Billing Activated Stage when Payment is done when in Sales Pipeline
  - Plan Details
  - Billing Frequency



### Open Questions?
- One deal for a account or multiple based on stages? One
- Contact can only be associated with a single Account?


### Brainstorm

Assumptions:
- New Account for all Installs
- Contact can be linked to multiple Account
- Each Account will have only one Deal, which is a long-lived Deal
- The Deal will be created only on App Install
- Except Install, the Deal will be updated with the event


Integration Flow:
  - On Install
    - Account will be created for each App
    - We will either link or create a Contact (Email address is the connection)
    - New Deal will be created
  - Other Events (Trial Activation, Uninstall, Reinstall, Pause, UWT, Churn & Re-Activation)
    - We will update the existing Deal


Deal Flow:
- On Install, we will create a Deal with property App/Store/Account Status. The property will hold the event name
- Except Install, we will update the Deal property App/Store/Account Status
- In Zoho CRM, we can set up automation to move Deal across Pipeline & Stage whenever the property App/Store/Account Status changes
- The above set-up will help us change Pipeline & Stage for the respective events in future without developer involvement


Open Questions:
- If we are creating only one Deal for an Account
  - Should we hold the App/Store/Account Status in Account level, instead of Deal?
  - Use Automation to create a Deal based on above property in the Account?
  - How do we restrict multiple Deal creation for an Account?
  - Should we have App Id as a unique identifier to prevent multiple Deal creation?


### Asks
- Demo Zoho Account
- Trial Days & all events as Timeline
- Invoiice, Refund
- Downgrade Upgrade

### Discussion with Sanjay & Vig

Assumptions:
- Account can have multiple Apps
- Each App wil have a single long-lived Deal
- App Id will act as the unique identifier in Deals
- Leads will only be created on App install
- Except Install, the Deal will be updated with the relevant details


Integration Flow:
  - On Install, Leads will be created with App Id, Email, Phone, Shop Name, Country & Any other needed details (Automated)
  - Leads will be converted to Deals, while conversion, Contact & Accounts will be linked or Created (Manually by Sales)
  - On Other Events (Trial Activation, Uninstall, Reinstall, Pause, UWT, Churn & Re-Activation)
    - We will update the existing Deal with relevant details & update metadata to Accounts when available. (Automated)


### Events in API

- Billing Activated
  - Activate Now from Dashboard

- Pause
  - Pause from Super Admin Dashboard

- Re Activate


### Questions
1. What happens to Sales Deal in UWT or CHURN?
2. Data requirement Excel Sheet?
3. Does Zoho CRM has events?


Merge Accounts in Zoho?


### Estimation

- Events
  - Install
  - Custom
  - Uninstall
  - Reinstall
  - Shopify Billing Pause
  - Shopify Billing Resume
  - Billing Cancelled Internally
  - Billing Reactivated
  - Billing Activated
  - Subscription Realised


#### Efforts
- Service Setup - 2h
- Zoho API Helpers - 4h
- Firebase Helpers - 2h
- Shopify API Helpers - 4h
- Vajro -> Zoho Events - 31h
  - Install - 3h
  - Uninstall - 4h
  - Reinstall - 4h
  - Shopify Billing Pause - 3h
  - Shopify Billing Resume  - 3h
  - Billing Cancelled Internally  - 3h
  - Billing Reactivated - 4h
  - Billing Activated - 4h
  - Subscription Realised - 3h
- Zoho -> Events - 3h
  - Discount Code on Tagging - 3h


### Next Steps
- Account, Contact & Deals Fields list
- Parent - Child Account linking clarification
- Feasibility of Zoho Automation Workflow to Create/Update Deal


- Pipedrive <-> Zoho CRM - API
- Pipedrive deal unique value - AppId
- Cleanup Zoho CRM - Yes
- Pipedrive - Vig
- Shopify Partners - Vig

- Pipedrive  
  - Notes, Activities & Attachments


- If deal exists in CS & Onboarding pipeline, create deal in zoho with deal details from CS pipleine
- If deal exist only in Onboarding pipleine, create deal in zoho with deal details from Onboarding pipleine