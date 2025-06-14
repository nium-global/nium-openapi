## May 13, 2025

### Core

##### Updated beneficiary validations

- We've updated the validations when creating beneficiaries to align with the validations in place for creating payouts. You'll see a decrease in rejections due to typos or special characters. For more information, see [Add Beneficiary V2](/api#tag/beneficiary/POST/api/v2/client/{clientHashId}/customer/{customerHashId}/beneficiaries).

##### Ongoing Due Diligence

Corporate customers approved more than one year ago are subject to our **Ongoing Due Diligence (ODD)**.

ODD is a periodic review process that applies to active customers based on their risk profile and transaction history. During this review, a compliance officer may issue one or more **Requests for Information (RFIs)**. You are expected to respond promptly to any RFIs to help complete the review.

Failure to respond may result in temporary account suspension. For more information, see [Corporate Customers](/docs/overview-corporate-customer).

---

## April 29, 2025

### Payouts and Payins

##### Local Funding Now Available in Brazilian Real

You can now fund in **Brazilian Real (BRL)** locally through Nium using Brazil’s most widely used payment systems: **PIX** (Instant Payment Platform) and **TED** (Electronic Funds Transfer).

This update helps clients with a presence in Brazil move money faster and reduce cross-border friction.

For more information, see [Fund a Wallet](/docs/fund-wallet#brazil).

---

## April 15, 2025

### Core Platform

##### Settlement Report Now Available

We’ve launched a daily **Settlement Report** to support your reconciliation efforts. The report includes all settled transactions across payins, payouts, P2P transfers, and fees.

You can download the report via the Nium Portal or receive it securely via SFTP.

For more information, see [Settlement Report](/docs/settlement-report).

#### Enhancements

##### Find Transactions Faster with Improved Filters

We’ve enhanced the **Transactions** page in Nium Portal to help you locate the data you need—faster:

- Search by **External ID**
- View transactions across **all platform customers**
- Filter by **date and time** with access to full transaction history

For more information, see [Nium Portal](/docs/portal-reports#transactions-reports).

---

## April 1, 2025

### Core Platform

##### New `clientTransactionId` included in reconciliation labels

`clientTransactionId` is now included as a label in the following transaction types:

- `Wallet_Credit_Mode_Offline`
- `Wallet_Credit_Mode_Offline_Third_Party`

`clientTransactionId` is provided by clients in the [Fund Wallet](/api#tag/customer-funding/POST/api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/fund) request, helping you track transactions for reconciliation purposes.

For more information, see [Transaction Response Labels](/docs/transaction-response-labels).

### Issuance and Cards

##### Convert virtual cards to physical cards

Empower your customers with more choice. With the new [Convert Card](/api#tag/lifecycle/POST/api/v1/client/{clientHashId}/customer/{customerHashId}/wallet/{walletHashId}/card/{cardHashId}/convert) request, you can upgrade an active virtual card to a physical one. This supports fast virtual issuance while still meeting customer demand for in-store or ATM access.

For more information, see [Manage Cards](/docs/card-management).

##### New Flutter SDK guides for Apple Pay and Google Pay

Integrate digital wallet provisioning into your Flutter apps more easily. Our new guides walk you through implementing Apple Pay and Google Pay Push Provisioning using Nium’s SDKs, including platform channel setup, native code examples, and troubleshooting tips.

Whether building for iOS or Android, get cards into wallets faster and streamline the in-app payment experience.

For more information, see:

- [Apple Pay - Flutter SDK](/docs/apple-flutter)
- [Google Pay - Flutter SDK](/docs/google-flutter)

### Payouts and Payins

##### Improved bank account verification with Nium Verify

Recent upgrades to **Nium Verify** improve visibility, clarity, and developer experience:

- **Simplified integration:** You no longer need to pass the `customerId` in your requests.
- **Track verification history:** Use the new [List Verifications](/api#tag/nium-verify/GET/api/v1/client/{clientHashId}/verifications) request to fetch all verifications sent to Nium.

We've also refined our response data to help you act with confidence:

- **Valid accounts:** New `derivedAccountDetails` object includes the account holder’s name from bank records—and local language name, where applicable.
- **Invalid accounts:** New `failureCode` explains why verification failed (e.g., incorrect name, inactive account).
- **Unsupported accounts:** Responses now provide more specific reasons, such as unsupported banks or currency-country mismatches.

These changes deliver a smoother onboarding experience and reduce verification delays.

Learn more in the updated [Nium Verify](/docs/account-verification).

---

## March 18, 2025

### Core Platform

#### Enhancements

#### New `rfiHashId` for Easier RFI Tracking

A new parameter, `rfiHashId`, is now available in the following requests:

- [Fetch Corporate Customer RFI Details​](/api#tag/customer-account---corporate/GET/api/v1/client/{clientHashId}/corporate/rfi)
- [Respond to RFI for Corporate Customer](/api#tag/customer-account---corporate/POST/api/v1/client/{clientHashId}/corporate/rfi)

You can now store and use an `rfiHashId` to uniquely identify and respond to Requests for Information (RFIs), helping ensure accurate tracking and preventing mix-ups.

While `templateId` remains available, we strongly recommend migrating to `rfiHashId` for improved accuracy and future compatibility.

For more details, see [Requests for Information (RFIs)](/docs/rfi-process-for-corporate-customers). If you have any questions, please contact your Nium account manager or [Nium Support](mailto:support@nium.com).

### Payouts and Payins

### New Features

#### Nium Playbook Changelog

We’ve launched a changelog for the **Nium Playbook**, making it easier to track updates to our transaction capabilities all in one place.

Explore the changelog and stay up to date: [Nium Playbook](https://playbook.nium.com/)

#### Failure Codes Guide

We’ve published a new [Failure Codes](https://docs.nium.com/docs/failure-codes) guide outlining why transactions may fail and the standardized ISO codes that are returned. These codes help you by providing a:

- **Simplified integration**: Standardized failure codes reduce the need to interpret multiple financial messages.
- **Faster resolution**: Recommended actions are provided for each failure, helping you quickly identify and resolve issues.

---

## March 4, 2025

### Core Platform

#### Enhancements

##### Updates to Virtual Account Assignment
Virtual accounts can now only be assigned when a customer’s compliance `status` is **CLEAR**. If the status is **PENDING**, the request will return an error.

This change helps ensure virtual accounts are only assigned to valid customers. For more information, see [Virtual Account Number](https://docs.nium.com/apis/docs/virtual-account-number).

Use the [Assign Payment ID](https://docs.nium.com/apis/reference/assignpaymentid) request to assign virtual accounts. This change ensures virtual accounts are only assigned to eligible customers.

---

## February 18, 2025

### Core Platform

#### Enhancements

##### Wallet-to-Wallet Transfers Now Support External ID
You can now include a `senderExternalId` in wallet-to-wallet transfer requests. Additionally, you can fetch wallet-to-wallet transfers using the `externalId` assigned when creating the customer.

This enhancement simplifies transaction tracking and reconciliation. For more information, see [Wallet to Wallet Transfer](https://docs.nium.com/apis/reference/wallet-to-wallet-transfers).

### Payouts and Payins

#### New Features

##### Fetch Transaction Lifecycles with External ID
You can now fetch the lifecycle of a transaction and status changes it goes through using the `externalID` from our [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) request. This change helps make transaction tracking and reconciliation even simpler.

- **Search using your External IDs**: Retrieve the lifecycle of a transaction using `externalID` as a parameter.
- **Easier Reconciliation**: Track transactions using your own reference IDs.
- **No Breaking Changes**: You can still fetch the lifecycle of transactions using the `systemReferenceNumber`.

For more information, see [Transaction Lifecycle](https://docs.nium.com/apis/reference/transactionlifecycle).

---

## February 4, 2025

### Core Platform

#### Deprecation Notices

##### P2P Transfer Between Wallets Webhook Deprecation
The [P2P Transfer Between Wallets](https://docs.nium.com/apis/reference/p2p-transfer-between-wallets) webhook event will be deprecated in March 2025.

- This event was sent for `transfers` that have **Customer_Wallet_Credit_Fund_Transfer** as the `transactionType`.
- The [Fund Transfer Between Wallets](https://docs.nium.com/apis/reference/fund-transfer-between-wallets) event will be sent instead for `transfers` that have `Customer_Wallet_Credit_Fund_Transfer` as the `transactionType`.

### Issuance and Cards

#### Enhancements

##### New `childCustomerHashId` Field in Assign Card Request
The [Assign Card](https://docs.nium.com/apis/reference/assigncard) request now includes a `childCustomerHashId` field. This change helps you keep track of customers under a corporate client account and their activity for accurate record-keeping and oversight.

### Payouts and Payins

#### New Features

##### Send Payments and Add Beneficiaries in One Step
We’ve made it easier to send payments through Nium! Previously, creating a beneficiary using our [Beneficiary endpoint](https://docs.nium.com/apis/reference/beneficiary) was required before initiating a `transfer`. With this latest change, you now have the flexibility to send payments without pre-creating a `beneficiary`.

Specifically, customers can now send payments using the Transfer Money request by either:

- Including **beneficiary details** directly within the request, along with the account details.
- Including a `beneficiaryId` (similar to today’s behavior).

This update simplifies payment processing and offers greater flexibility. See the [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) guide. Start creating beneficiaries and payments today for a smoother payout experience! 🚀

#### Enhancements

##### Faster Transaction Processing with Document Upload
We’ve enhanced our [Upload Transaction Receipt](https://docs.nium.com/apis/reference/uploadtransactionreceipt) request to streamline payment processing and minimize delays caused by RFIs.

Customers can now upload supporting documentation linked to a payment, allowing us to process transactions faster. Specifically, after using the [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) request to initiate a transaction, retrieve the system reference number from the response.

Then use the [Upload Transaction Receipt](https://docs.nium.com/apis/reference/uploadtransactionreceipt) request to upload documentation; include the system reference number as the `transactionId` in the path parameter.

For more information, see the following requests:

- [Transfer Money](https://docs.nium.com/apis/reference/transfermoney)
- [Upload Transaction Receipt](https://docs.nium.com/apis/reference/uploadtransactionreceipt)

---

## December 10, 2024

### Core Platform

#### New Features

##### Nium Portal In-line Payouts

In-line Payouts enables any user to create payouts directly in Nium Portal—no coding or integrations needed. Select a beneficiary, set payout details, and you're done! For more information, see [Payouts](https://docs.nium.com/apis/docs/batch-payouts).

#### API Breaking Changes

##### Transactions `complianceStatus` Changes

The `complianceStatus` returned in the [Transactions](https://docs.nium.com/apis/reference/transactions) API response will only return **RFI_REQUESTED** and **RFI_RESPONDED** beginning January 15th, 2025. For compliance purposes, the remaining values won’t be supported. If you have any questions, please contact your Nium account manager or [Nium Support](mailto:support@nium.com).

---

### Payouts and Payins

#### Enhancements

##### Nium Verify now available in India and the European Union

Nium Verify is live in the European Union and India! You can now verify corporate bank accounts in Belgium, France, Italy, Netherlands, and Poland and retrieve the account holder name. For a consolidated list of all Nium Verify’s coverage, see [Nium Verify](https://docs.nium.com/apis/docs/account-verification).

##### New `externalID` Field

We have introduced a new field, **externalID**, in the Transfer Money request to allow customers to include their custom reference ID for transactions. This enhancement simplifies reconciliation for clients.

- The **externalID** field is a string that accepts user-defined reference numbers.
- It supports idempotency by rejecting transactions with duplicate reference numbers, thereby preventing duplicates.
- Customers can filter transactions using **externalID** via the Transactions API and Fetch Remittance Lifecycle API.
- Additionally, this field is included in all payout webhooks to facilitate seamless reconciliation.

For more info, see [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) in our API Reference.

#### API Breaking Changes

##### Fetch Supported Corridor V2 Deprecation

The [Fetch Supported Corridor V2](https://docs.nium.com/apis/reference/fetchsupportedcorridorsv2) request will be deprecated and unavailable as of **April 1, 2025**. We’ve launched an updated version, [Fetch Supported Corridors V3](https://docs.nium.com/apis/reference/fetchsupportedcorridorsv3), which offers enhanced details on supported remittance corridors.

Please integrate with Fetch Supported Corridor V3 by **April 1, 2025** to avoid any disruptions. For more information, contact your Nium account manager or [reach out to Nium Support](mailto:support@nium.com).

## November 26, 2024

### Issuance and Cards

#### New Features

##### Multiple Wallets for Card Issuance Clients
Multiple Wallets now supports card issuance, enabling users to issue cards from additional wallets. This helps manage funds across multiple wallets within card spend accounts, enabling flexible expense allocation and greater control over spending.

**Card UI Updates:**

- **Add Card UI:** Added a `walletHashId` dropdown to enable wallet selection during card setup for customer-level association.
- **Card List UI:** `walletHashId` is now displayed, showing wallet associations for each card.
- **Assign Physical Card UI:** Added `walletHashId` and `customerHashId` fields for assigning physical cards to specific wallets and customers.

Multiple Wallets and Card Issuance is currently available in:

- Australia
- Canada
- Hong Kong
- Singapore
- United Kingdom

For more information on Multiple Wallets, see [Wallets - Overview](https://docs.nium.com/apis/docs/wallet-overview#multiple-wallets).

If you’re interested in Multiple Wallets, please reach out to your Nium account manager or contact [Nium Support](mailto:support@nium.com).

### Payouts and Payins

#### New Features

##### Payins Playbook
We’ve launched an [online playbook](https://playbook.nium.com/payins) for pay-in network capabilities. Use it as a guide to receive money on the Nium network.

For more information, see the [Payins User Guide](https://playbook.nium.com/payins/user-guide).

#### Enhancements

##### Nium Verify now available in the United States
Nium Verify is now live in the United States! You can verify bank accounts in the U.S.

For a full list of regions Nium Verify is available in, see [Nium Verify](https://docs.nium.com/apis/docs/account-verification).

##### Paper check payouts now available in the United States
We’ve enhanced our U.S. payout capabilities to support paper checks for beneficiaries.

For more information, see [Paper Checks](https://docs.nium.com/apis/docs/paper-checks).

## November 12, 2024

### Core Platform

#### New Features

##### Test Nium with our new Simulation requests
Nium has introduced enhanced Simulation APIs to help developers test various services and refine their integrations confidently. This suite allows you to simulate different scenarios across onboarding, payouts, and compliance transitions. By leveraging these simulations, clients can ensure their implementation meets real-world demands without impacting actual operations. Available tests include:

- **Onboarding Simulations**: Test the compliance statuses for individual and corporate accounts, ensuring readiness before live operation.
- **Payout Simulations**: Validate transaction flows, including error handling and response to different compliance requirements.
- **Flexible Status Transitions**: Move transactions through various lifecycle statuses, such as `RFI_REQUESTED`, `PAID`, or `ERROR`, to verify end-to-end processes.

For step-by-step guides and API details, see [Testing Nium](https://docs.nium.com/apis/docs/testing).

##### Nium Verify
Ensure accurate bank details and reduce payment failures with real-time account verification. For more information, see [Nium Verify](https://docs.nium.com/apis/docs/account-verification).

#### Enhancements

##### Multiple Wallets - Account Statement
Clients can now generate account statements for a specific wallet using the [Fetch Wallet Statement](https://docs.nium.com/apis/reference/walletstatement) request. This change helps you better reconcile and manage the different wallets you create.

For more information, see [Customer Account Statement](https://docs.nium.com/apis/docs/customer-account-statement).

#### API Breaking Changes

##### Biometric Authentication Requirement
Nium will begin updating authentication requirements for online card transactions in line with the latest requirements from card issuers. These changes aim to enhance transaction security and improve the cardholder’s experience by implementing more robust authentication measures.

By **April 1st, 2025**, all NIUM clients must enable biometric authentication for online transactions made on devices that support biometric verification (e.g., fingerprint or facial recognition). Clients will need to integrate with Nium’s Out-of-Band (OOB) authentication flow to support this functionality. For more information about implementing, see [OOB Authentication Flow](https://docs.nium.com/apis/docs/oob-authentication-flow).

By integrating biometric authentication for online payments, Nium clients can provide their customers with a more convenient and secure method for verifying transactions. Biometric authentication helps increase the success rate of authentication while reducing fraud in high-risk scenarios.

- Higher authentication success rates
- Increased transaction approval rates
- Reduced fraud on high-risk transactions
- Improved security for step-up authentication when biometrics are used

##### `complianceStatus` changes
The [`complianceStatus`](https://docs.nium.com/apis/reference/transactions) returned in the API response will only return **RFI_REQUESTED** and **RFI_RESPONDED** beginning January 15th, 2025. For compliance purposes, the remaining values won’t be supported. If you have any questions, please contact your Nium account manager or Nium Support.

### Payouts and Payins

#### New Features

##### New `beneficiaryIntermediaryBankCode` field
We’ve added a new `beneficiaryIntermediaryBankCode` to the [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) request to help capture the correspondent’s (also called the intermediary’s) bank code. This new field helps reduce transaction rejections where SWIFT payouts to specific corridors require additional information about the intermediary bank.

## October 29, 2024

### Core Platform

#### New Features

##### Test Nium with our new Simulation requests
Nium has introduced enhanced Simulation APIs to help developers test various services and refine their integrations confidently. This suite allows you to simulate different scenarios across onboarding, payouts, and compliance transitions. By leveraging these simulations, clients can ensure their implementation meets real-world demands without impacting actual operations. Available tests include:

- **Onboarding Simulations**: Test the compliance statuses for individual and corporate accounts, ensuring readiness before live operation.
- **Payout Simulations**: Validate transaction flows, including error handling and response to different compliance requirements.
- **Flexible Status Transitions**: Move transactions through various lifecycle statuses, such as `RFI_REQUESTED`, `PAID`, or `ERROR`, to verify end-to-end processes.

For step-by-step guides and API details, see [Testing Nium](https://docs.nium.com/apis/docs/testing).

##### Nium Verify
Ensure accurate bank details and reduce payment failures with real-time account verification. For more information, see [Nium Verify](https://docs.nium.com/apis/docs/account-verification).

#### Enhancements

##### Multiple Wallets - Account Statement
Clients can now generate account statements for a specific wallet using the [Fetch Wallet Statement](https://docs.nium.com/apis/reference/walletstatement) request. This change helps you better reconcile and manage the different wallets you create.

For more information, see [Customer Account Statement](https://docs.nium.com/apis/docs/customer-account-statement).

#### API Breaking Changes

##### Biometric Authentication Requirement
Nium will begin updating authentication requirements for online card transactions in line with the latest requirements from card issuers. These changes aim to enhance transaction security and improve the cardholder’s experience by implementing more robust authentication measures.

By **April 1st, 2025**, all NIUM clients must enable biometric authentication for online transactions made on devices that support biometric verification (e.g., fingerprint or facial recognition). Clients will need to integrate with Nium’s Out-of-Band (OOB) authentication flow to support this functionality. For more information about implementing, see [OOB Authentication Flow](https://docs.nium.com/apis/docs/oob-authentication-flow).

By integrating biometric authentication for online payments, Nium clients can provide their customers with a more convenient and secure method for verifying transactions. Biometric authentication helps increase the success rate of authentication while reducing fraud in high-risk scenarios.

- Higher authentication success rates
- Increased transaction approval rates
- Reduced fraud on high-risk transactions
- Improved security for step-up authentication when biometrics are used

##### `complianceStatus` changes
The [`complianceStatus`](https://docs.nium.com/apis/reference/transactions) returned in the API response will only return **RFI_REQUESTED** and **RFI_RESPONDED** beginning January 15th, 2025. For compliance purposes, the remaining values won’t be supported. If you have any questions, please contact your Nium account manager or Nium Support.

### Payouts and Payins

#### New Features

##### New `beneficiaryIntermediaryBankCode` field
We’ve added a new `beneficiaryIntermediaryBankCode` to the [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) request to help capture the correspondent’s (also called the intermediary’s) bank code. This new field helps reduce transaction rejections where SWIFT payouts to specific corridors require additional information about the intermediary bank.

## October 15, 2024

### New Features

**Bulk Card Issuance**

Nium now supports issuing cards in bulk. Bulk card issuance refers to the process where many prepaid or debit cards are produced at the same time.

Bulk issuance is an efficient way to generate and distribute large quantities of cards and helps in saving card delivery costs.

Nium supports both personalized and generic card issuance. Cards can be personalized (Name on Card) or generic (no Name on Card), and can be shipped in one single shipment.

Bulk card issuance is often used for corporate programs, gift cards, payroll, or disbursement programs. Please contact your Nium account manager or Nium support if you’re interested in issuing cards in bulk.

For more information, see [Card Overview](https://docs.nium.com/apis/docs/card-overview).

## October 1, 2024

### New Features

**Multiple Wallets**

Corporate customers can now have multiple wallets on the Nium platform. Multiple Wallets offers more choice and convenience to clients and helps ledger management with single or multiple currencies.

- Currently, whenever a customer is onboarded on to Nium, a default wallet is created and linked with the customer. All transactions are credited and debited from that single wallet.
- With this change, customers can now hold balances and transfer funds between multiple wallets based on their business needs.
- The assignment of virtual accounts to any wallet is supported by the [Assign Payment ID](https://docs.nium.com/apis/reference/assignpaymentid) request.
- We’ve introduced three new APIs to support this feature:
  - [Add Wallet](https://docs.nium.com/apis/reference/addwallet)
  - [Update Wallet](https://docs.nium.com/apis/reference/updatewallet)
  - [Fetch Wallet](https://docs.nium.com/apis/reference/getwallet)
- We're actively working on bringing card issuance and card-based transactions for additional wallets.
- Currently, card issuance and card-based transactions only support the default wallet that was created and linked with the customer after completing onboarding.
- Multiple wallets are currently only available in select regions. The regions Multiple Wallets are available include:
  - Australia (AU)
  - Canada (CA)
  - Hong Kong (HK)
  - Singapore (SU)
  - United Kingdom (UK)
  - United States (US)

Please contact your Nium account manager or Nium support to evaluate your business use case and configure wallets for you.

### Enhancements

**Stay Informed with Our New Status Page**

Monitor the real-time status of Nium services with our new Status Page. Stay updated on service performance and incidents, and subscribe to notifications for timely alerts on any service changes or issues. See our [guide for more information](https://docs.nium.com/apis/docs/status-page).

**Virtual Account related information**

The account type returned in the API response of [Virtual Account Details V2](https://docs.nium.com/apis/reference/virtualaccountdetailsv2) and the [Client Details](https://docs.nium.com/apis/reference/clientdetails) request for `GMO_JP` bank has been changed from **SAVINGS** to **LOCAL** to make it standardized across all banking partners.

## September 17, 2024

### Enhancements

**Intermediary Bank Code for Virtual Accounts from JPMC SG**

The virtual account detail returned by the **Virtual Account Details V2 API** will now include the intermediary bank SWIFT BIC for virtual accounts issued for non-SGD currencies. This will be available in the `routingCodeValue2` field and should be used for fund transfers through virtual accounts issued by JPMC SG.

**Virtual Account Numbers**

You can now create virtual account numbers directly in the Nium Portal on the Customer Balances page. This caters to users who prefer the portal over our API. For more information, see [Virtual Account Numbers](https://docs.nium.com/apis/docs/portal#virtual-accounts).

**GPI Details for SWIFT Transactions**

Global Payments Innovation (GPI) details for SWIFT transactions are now included in transaction reports, providing end-to-end visibility into transaction statuses. For more information, see [GPI details](https://docs.nium.com/apis/docs/portal-reports#gpi-details).

**Payout Return Reasons**

Transaction reports now display reasons for returned payout transactions, helping you identify and prevent issues. For more information, see [Transaction reports](https://docs.nium.com/apis/docs/portal-reports#transactions-reports).

**New Financial Institutions Use-Case Guide**

We’ve released a new use-case guide tailored for Financial Institutions (FIs). It provides detailed integration steps, fund flow examples, and an overview of key Nium features. For more information, see [Financial Institutions](https://docs.nium.com/apis/docs/financial-institutions).

**Customer-Named Virtual Accounts Now Available for Hong Kong Payins**

We’re enhancing payin capabilities in Hong Kong! You can now collect funds into customer-named virtual accounts in HKD via local methods, and in USD, EUR, GBP, AUD, CAD, and CNY via wires. For more information, see [Virtual Account Number](https://docs.nium.com/apis/docs/virtual-account-number#customer-named-virtual-accounts).

**Enhanced Reference Info for Nepal Payments**

Beneficiaries in Nepal can now see the sender's name in Rupee payouts, improving transaction tracking. This adds transparency and security to every transaction.

**Enhancements to the Proof of Payments API**

The ultimate remitter’s name will now appear on the Proof of Payment PDF for on-behalf payouts, helping Financial Institutions manage third-party payout use cases more effectively. For more information, see the [Get Proof of Payment](https://docs.nium.com/apis/reference/pop) request.

## August 20, 2024

### Enhancements

**Apple SDK**

Our Apple Pay SDK has been enhanced to display the client's name when adding a card to an Apple Wallet. This helps you better manage cards in your Apple Wallet.

- SDK Version: 2.0.2
- Run `pod update` or `pod repo update` to get the latest version.

If you have any questions about our Apple SDK, please contact [Nium Support](https://nium.com/).

**Card Webhook Update**

The `walletProvider` field in the **VTS Token** webhook is now restricted to `applePay` and `googlePay`.

This corrects an issue where some response returned `APPLE` or `GOOGLE`. For more information, see [VTS Token](https://docs.nium.com/apis/reference/vts-token).

## August 6, 2024

### Enhancements

**Nium Portal - Redesigned Customer Balances Page**

We've redesigned the Customer Balances page to enhance usability:

- Review, at a glance, what features are enabled for each currency. This change helps you better understand what capabilities are available when managing those funds.
- Create Virtual Accounts for Payin-enabled currencies. Non-developers can now create Virtual Accounts in Nium Portal without directly using Nium’s API.

For more details, see the [Nium Portal - Customer Balances](https://docs.nium.com/apis/docs/portal#customer-balances).

## July 23, 2024

### New Feature

**Account Verification**

We’ve released a new [Account Verification](https://docs.nium.com/apis/docs/account-verification) request that helps you verify payee details while [creating beneficiaries](https://docs.nium.com/apis/reference/addbeneficiaryv2). This change helps you simplify your integration, removing the need for a separate integration dedicated to verifying account details.

For more information, see [Account Verification](https://docs.nium.com/apis/docs/account-verification).

### Enhancements

**Updates to the Fetch Supported Corridors V3 Request**

We’ve made the following changes to the [Fetch Supported Corridors V3](https://docs.nium.com/apis/reference/fetchsupportedcorridorsv3) request:

- `payoutMethodCategory` query parameter: Helps you separate supported payout methods by corridor - for more information and a detailed breakdown, see the [Nium playbook](https://playbook.nium.com/).
- The query parameters `beneficiaryAccountType`, `customerType`, and `payoutMethod` have been made enums.

For more information, see the [Fetch Supported Corridors V3](https://docs.nium.com/apis/reference/fetchsupportedcorridorsv3) request.

**New `isOffMarket` Parameter**

We’ve introduced a new `isOffMarket` field to help you understand when off-market fees get applied to `Conversion` and `Quote` requests.

- The `isOffMarket` field is returned in the response to the following requests:
  - [Create Quote](https://docs.nium.com/apis/reference/createquote)
  - [Fetch Quote by ID](https://docs.nium.com/apis/reference/fetchquote)
  - [Create Conversion](https://docs.nium.com/apis/reference/createconversion)
  - [Fetch Conversion By Id](https://docs.nium.com/apis/reference/fetchconversion)
- Please note that this field isn't returned unless off-market requests have been enabled by Nium.

For more information, see [FX - Overview](https://docs.nium.com/apis/docs/fx-overview#off-market-rates).

---

## July 9, 2024

### Enhancement

A new query parameter status has been released for the [Virtual Account Details V2](https://docs.nium.com/apis/reference/virtualaccountdetailsv2) request. With this new parameter, the active/inactive virtual accounts can be filtered by Clients.

---

## June 25, 2024

### New Feature

Reports are now available in Nium Portal. Reports enhance your financial management experience by providing detailed insights into your transactions. You can now track, analyze, and manage your financial activities with ease. For more information, see [Reports](https://docs.nium.com/apis/docs/portal-reports).

### Breaking API Changes

Starting October 1st, 2024, changes in Nium’s compliance policy will require additional documents and parameters to onboard corporate customers using the Onboard Corporate API. Please update your integration accordingly to avoid disruptions. If you have any questions, please contact your Nium account manager or Nium Support.

- **Current State:** These documents and parameters are optional.
- **Future Requirement:** From October 1st, 2024, these fields and parameters will be mandatory.
- **Changes to Nium:** If the required documents and parameters are not included, the API will return an error indicating the missing documents and/or parameters.

### Changes to the Onboard Corporate API include:

- **Device Information:** IP address and device name is now required for all regions when onboarding corporate customers. See the `deviceDetails` object in our API Reference for more information about the changes in each country:
  - [Australia (AU)](https://docs.nium.com/apis/docs/cc-au-required-parameters#devicedetails-object)
  - [Canada (CA)](https://docs.nium.com/apis/docs/cc-ca-required-parameters#devicedetails-object)
  - [Europe (EU)](https://docs.nium.com/apis/docs/cc-eu-required-parameters#devicedetails-object)
  - [Hong Kong (HK)](https://docs.nium.com/apis/docs/cc-hk-required-parameters#devicedetails-object)
  - [Singapore (SG)](https://docs.nium.com/apis/docs/cc-sg-required-parameters#devicedetails-object)
  - [United Kingdom (UK)](https://docs.nium.com/apis/docs/cc-uk-required-parameters#devicedetails-object)
  - [United States (US)](https://docs.nium.com/apis/docs/cc-us-required-parameters#devicedetails-object)
- **Europe (EU):** Additional information and documents are now required for both eKYB and manual KYB when onboarding corporate customers in Europe (EU). For more details, see:
  - [EU Required Documents](https://docs.nium.com/apis/docs/cc-eu-required-documents)
  - [Stakeholder KYC](https://docs.nium.com/apis/docs/cc-eu-onboarding#stakeholder-kyc)
  - [Expected Account Usage](https://developersandbox.nium.com/apis/docs/cc-eu-required-parameters#expectedaccountusage-object)
- **Singapore (SG):** Proof of Identity and Proof of address documents are now required for stakeholders for both eKYB and Manual KYB when onboarding corporate customers in Singapore (SG). For more information, see [SG Onboarding](https://docs.nium.com/apis/docs/cc-sg-onboarding#stakeholder-kyc).

---

## May 28, 2024

### New Features

* **Direct Debit** is now available for Singaporean (SG) customers. Direct Debit enables SG-based businesses to fund their Nium wallets using their Singaporean (SG) bank account in real time.
  * The transaction type for Direct Debit transactions is `WALLET_CREDIT_MODE_DIRECT_DEBIT`.
  * Reach out to your Nium account manager for details on how to activate Direct Debit.
  * For more information, see [Direct Debit SG](https://docs.nium.com/apis/docs/direct-debit-sg).

### Enhancements

* Maximum limit for INR Proxy (UPI) transactions has been increased to INR 200,000 from INR 100,000. For more information, see the [Nium - India Playbook](https://playbook.nium.com/country/india?pm_relation=payout_methods).

* **Fetch Card Details V2**: Fetching details using the Card Details V2 endpoint now returns the `demographics` object. The `demographics` object only gets returned if the card is assigned to an employee but issued within a corporate customer's wallet.
  * Details that get returned in the `demographics` object include:
    * `firstName`
    * `middleName`
    * `lastName`
    * `nameOnCard`
    * `email`
    * `mobile`
  * For more information, see [Card Details V2](https://docs.nium.com/apis/reference/carddetailsv2).

---

## April 30, 2024

### Enhancements

* We’ve introduced three new reasons you can include when permanently blocking a customer:
  * **UNRESPONSIVE_CUSTOMER**
  * **DORMANCY**
  * **OTHER**
* Moving forward, when **PERMANENT_BLOCK** is used, the customer's account will be considered closed, and they can no longer process any further activity.
* Applications rejected due to high risk or non-compliance will now be blocked from being resubmitted. Previously, such applications could be resubmitted but were rejected by our compliance team after review. With this change, applications that have been previously rejected will automatically be rejected without any wait.
  * Resubmission is still allowed for reasons unrelated to compliance, such as incomplete applications, typos, or incorrect addresses.
  * For individual customers, see [Individual Customer Onboarding - Overview](https://developersandbox.nium.com/apis/docs/overview-individual-customer).
  * For corporate customers, see [Corporate Customer Onboarding - Overview](https://docs.nium.com/apis/docs/overview-corporate-customer).

* We’ve released two new webhook events to help you manage cards:
  * `Card Details Updated`: This event is triggered to notify the client or cardholder when any card details are updated. For more details, see [Card Details Updated](https://docs.nium.com/apis/reference/card-details-updated).
  * `Card Expiry Alert`: This event is triggered when a card is approaching its expiration date. For more details, see [Card Expiry Alert](https://docs.nium.com/apis/reference/card-expiry-alert).

---

## April 16, 2024

### Enhancements

*   Our eKYC Onboarding APIs are now available for individual customers in Canada. For more details, see [CA onboarding](https://developersandbox.nium.com/apis/docs/ca-onboarding-individual).
        
*   Our OpenAPI spec is now available on GitHub. You can download and review our OpenAPI spec to help you build your integration with Nium. For more details, see our [Nium OpenAPI](https://github.com/nium-global/nium-openapi/) repo.

*   We've added [▶ Run in Postman](https://www.postman.com/nium-api/workspace/nium/collection/31522218-58e10ab7-1db6-4ec0-8146-80529969db98) buttons to several guides. These buttons give you quick access to our Postman collection and enable you to see how requests run in real-time. For an example, see [Individual Customer Onboarding](https://docs.nium.com/apis/docs/overview-individual-customer/).
    
*   We've added additional fields to the `remitter` object used in the [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) request to provide more details about the payout sender. Fields added include:
    
    *   `idExpiryDate`
    *   `idIssueDate`
    *   `originatingFICity`
    *   `originatingFICountry`
    
    For more details, see [Transfer Money](https://docs.nium.com/apis/reference/transfermoney).
---
## Mar 5, 2024

### New Features

*   Clients can now manually execute FX conversions. With this change, you're given greater control and flexibility over how funds get converted in customer wallets and the associated settlement timeframes.
    
    *   Pass the new `ExecutionType` field when making requests to the `/Quote` API to indicate a manual scheduled FX conversion. This field defaults to `at_conversion_time` if nothing is passed.
        *   FX conversions with the field `ExecutionType` set to `at_conversion_time` [settle at standard time, 5 PM local time](https://docs.nium.com/apis/docs/fx-overview#settlement-cut-off-time).
    *   Manual scheduled FX conversions must be executed using the `/Execute` endpoint (within the `ExpiryTime` to transfer funds from the source currency to the destination currency within the wallet.
        *   New fields:
            *   `ExecutionType`: Set to `at_conversion_time` for timed conversions and `manual` for manual FX conversions.
            *   `ExpiryTime`: This is a timestamp that indicates when the FX conversion expires. Manual conversions must be executed before this time.
    *   We've also updated the following APIs:
        *   [Create Quote](https://docs.nium.com/apis/reference/createquote)
        *   [Fetch Quote by ID](https://docs.nium.com/apis/reference/fetchquote)
        *   [Create Conversion](https://docs.nium.com/apis/reference/createconversion)
        *   [Fetch Conversion By ID](https://docs.nium.com/apis/reference/fetchconversion)

### Enhancements

*   We've added a new `compliancestatus` query parameter to the `Transactions` endpoint. For more information, see:
    
    *   [Client Transactions](https://docs.nium.com/apis/reference/clienttransactions)
    *   [Customer Wallet Transactions](https://docs.nium.com/apis/reference/transactions-1)
    
*   Our manual KYB Onboarding APIs are now available for corporate customers in Canada. For more details, see [CA Onboarding](https://docs.nium.com/apis/docs/ca-onboarding).

*   We've released a new version of our Fetch Supported Corridors API. This new version provides greater details about the corridor being used. Changes include:
    
    *   Adding a `mandatoryDataRequirements` and `supportingDocuments` field.
    *   Adding specifics around the transaction's limitations and turnaround time.
    
    For more information, see [Fetch Supported Corridors V3](https://docs.nium.com/apis/reference/fetchsupportedcorridorsv3).
    
*   We've added the following query parameters to the [Beneficiary List V2](https://docs.nium.com/apis/reference/beneficiarylistv2) endpoint.
    
    *   `beneficiaryName`
    *   `beneficiaryAccountNumber`
    *   `destinationCurrency`
    *   `payoutMethod`
    

### Deprecation Notices

*   We'll be deprecating [Fetch Supported Corridors V2](https://docs.nium.com/apis/reference/fetchsupportedcorridorsv2) within the next six months. As we prepare to do so, we'll surface more details. If you have any questions, reach out to the [Nium Support team](mailto:support@nium.com) at anytime.

---

### Feb 20, 2024

### Enhancements
    
*   We've added a new `complianceStatus` query parameter to the following endpoints.
    
    *   [Transactions](https://docs.nium.com/apis/reference/transactions-1)
    *   [Client Transactions](https://docs.nium.com/apis/reference/clienttransactions)
    
*   You can now use PGP keys (also called RSA security) to transmit sensitive data.
    
    For more details, see [PGP Prerequisites.](https://docs.nium.com/apis/docs/pgp-prerequisites)
    
### API Breaking Changes
    
*   We've removed the **BEN** enum from the `payout#swiftFeeType` field in the [Transfer Money](https://docs.nium.com/apis/reference/transfermoney#:~:text=This%20object%20accepts%20the%20payout%20details.) request.

---

## Feb 6, 2024

### New Features

*   We have introduced a new feature to Nium Portal called **Batch Payouts**. With batch payouts, you can now effortlessly process multiple transactions in one go while ensuring all your payouts are handled seamlessly. Learn more about batch payouts from our [blog](https://www.nium.com/resources/batch-payouts-in-the-nium-portal).
    
    For details on how to create batch payouts, see [Batch Payouts](https://docs.nium.com/apis/docs/batch-payouts).
    
*   We've released a Postman collection for all Nium APIs. Use the collection to build your integration.
    
    For more information, see [Postman collection](https://docs.nium.com/apis/docs/postman-collection)
    
### New Feature

*   We've released several new APIs related to Card Security and 3DS authentication. These new APIs enable you to send and receive data in more secure manner (e.g RSA encrypted). For more information, see the following from our API reference:

    *   [Show Security Details Encrypted](https://docs.nium.com/apis/reference/showsecuritydetailsencrypted)
    *   [Set/Reset PIN V2](https://docs.nium.com/apis/reference/setresetpinv2)
    *   [Fetch ATM PIN V2](https://docs.nium.com/apis/reference/fetchatmpinv2)
    *   [Add Or Update Passcode](https://docs.nium.com/apis/reference/setpasscode)

### Enhancements

*   We've made some improvments and fixes to our Google Pay Push Provisioning SDK to support EU and UK address verification. For details on our Google Pay Push Provisioning SDK, see [Google Pay Push Provisioning.](https://docs.nium.com/apis/docs/google-pay-push-provisioning-1)

---
## Jan 23, 2024

### New Feature

*   We have introduced a new Webhook event type called `CUSTOMER_COMPLIANCE_STATUS` applicable for individual customers. This event is triggered when there is a change to the individual customer's compliance status. For more information, see the [Customer compliance status](//docs.nium.com/apis/reference/customer-compliance-status) event in our API reference.

    Prior to this change you had to configure a separate URL to receive the customer compliance status from Nium. The new event update will improve the developer experience by simplifying the number of integration steps. You can now use the same URL configured to receive all Webhook events and subscribe to the new event.

    You can also subscribe to the event type `CARD_CLIENT_KYB_STATUS_WEBHOOK` to receive the compliance status of corporate customers. The [Callback to receive customer compliance status](https://docs.nium.com/apis/reference/callback-to-receive-customer-compliance-status) will continue to be supported.

### Enhancement

*   We have introduced two new fields - `ClientMarkupRate` and `MarkupRate` - to help you apply FX markup rates to your customers.

    *   The `ClientMarkupRate` is the markup rate you negotiated with Nium.
    *   The `MarkupRate` field details the FX markup fees configured for your customer.
    *   If there are no fees configured for your customer, the `MarkupRate` will default to the `ClientMarkupRate`.

    Both fields can be found in the response body of the following APIs:

    *   [Create Quote](https://docs.nium.com/apis/reference/createquote)
    *   [Fetch Quote by ID](https://docs.nium.com/apis/reference/fetchquote)
    *   [Create Conversion](https://docs.nium.com/apis/reference/createconversion)
    *   [Fetch Conversion By Id](https://docs.nium.com/apis/reference/fetchconversion)

    Having these fields readily available offers a convenient way to charge FX markup fees to your customers and helps you further monetize your FX services for revenue generation.

### Other Changes

Enabled local Nigerian Naira (NGN) payouts to Nigeria for person-to-person (P2P) and business-to-person (B2P) use cases.

---
## Dec 19, 2023

### New Feature

*   Introduced a new payment option `FASTER_DIRECT_DEBIT`is now available as a `fundingChannel` in the [Fund Wallet](https://docs.nium.com/apis/reference/fundwallet) API. This option is available for eligible clients to choose between Faster Direct Debit and Standard Direct Debit in US.

### Enhancements

*   For AUD currency transactions additional details will now be visible to the beneficiary. The enhancement will provide remitter name and other narrative information to the beneficiary leading to better transparency of each transaction benefitting both the sender and the beneficiary.

### Other

*   The minimum supported value for VND local transactions is updated to 2000 VND due to the restrictions put in place by Nium's bank partner.

---
## Dec 5, 2023

### New Feature

*   Introduced Card Widget which provides embeddable html that shows Payment Card Industry Data Security Standard (PCI DSS) data in end user applications. The Nium hosted url for the embeddable html can be retrieved using the new [Get card details widget](https://docs.nium.com/apis/reference/getcardwidget) API. This API is secured by JWT token authentication which is encrypted by AES RSA encryption algorithm.

### Enhancements

*   Updated the [Remittance lifecycle](https://docs.nium.com/apis/docs/remittance-lifecycle#testing-remittance-transaction-statuses-in-sandbox) user guide under the Transfer Money category with simulation account details that will allow you to create transactions in sandbox environment. With these instructions, you will now be able to replicate `PAID`, `SENT TO BANK`, and `RETURN` statuses and their state transitions.
    
*   Introduced [a new user guide on GPI tracking](https://docs.nium.com/apis/docs/gpi-tracking-for-wires) that offers insights into improved tracking for SWIFT wire transactions.
    

### Other

*   Local ZAR currency payouts for P2P use cases have been temporarily deactivated due to a technical issue with our payment partner. Nium continues to support payouts for other use cases such as B2P and B2B. We are working closely with our partner to resolve this issue at the earliest.

---
## Nov 21, 2023

### New Features

*   Introduced a new [Proof of Payment (POP)](https://docs.nium.com/apis/reference/pop) API to generate proof for the transactions that are in PAID status. You can use this API to download the proof of payment.
    
    *   Proof of payment is a pdf generated by Nium to provide the necessary details of the transaction such as sender details, beneficiary details, transaction date & time, paid amount, fees, and FX rate.
    *   You can provide POP documents to your customers or suppliers for enhancing transparency. Your customers typically use this document, also known as transaction receipt, for reconciliatiion, and for tax verification purpose.
    
*   Introduced collections capability in Japan. To support this capability, a new data object, `InvoiceDetails`, is added to the request body of the [Fund Wallet](https://docs.nium.com/apis/reference/fundwallet) API.
    
    You will now be able to receive funds locally from individuals and businesses in JPY currency in real time and hold the funds in the customer wallets in JPY currency. You can also issue JPY virtual accounts to your customer wallets using the [Assign Payment ID](https://docs.nium.com/apis/reference/assignpaymentid) API. Contact your Nium representative to learn more about this feature.
    
*   Introduced the Direct Debit capability for your corporate customers in Australia (AU). AU based businesses can now fund from their AU bank account into their Nium-issued wallets using Direct Debit. For this feature, the `transactionType` is shown as `WALLET_CREDIT_MODE_DIRECT_DEBIT` in the response body of [Wallet Transactions](https://docs.nium.com/apis/reference/transactions-1) API. Contact your Nium representative to activate this capability.
    
    Refer to the [Direct Debit AU](https://docs.nium.com/apis/docs/direct-debit-au) user guide for more details on this feature.

---
### Nov 7, 2023

### Enhancement

*   Introduced a new field called `referenceCode` in the [Cards 3DS OTP](https://docs.nium.com/apis/reference/3ds-otp) Webhook.

    `referenceCode` is a unique value generated with each new OTP value. In the instance where the consumer can receive multiple OTPs for the same transaction, this can be leveraged to show the consumer which OTP is expected to be entered. This value should be sent in the SMS or Email along with the OTP and then displayed on the consumer screen.

### Enhancement

*   We have added two new parameters in the `gpi` object to enhance the gpi details shared with you in [Fetch Remittance Life Cycle Status](https://docs.nium.com/apis/reference/fetchremittancelifecyclestatus) API and [Remit Transaction Sent to Bank](https://docs.nium.com/apis/reference/remit-transaction-sent-to-bank) webhook.

    *   `forwardBankCode`: Bank identification code (BIC) of the next participant bank to which the payment has been forwarded.
    *   `remarks`: Detailed description of the `reasonCode`. This interpretation is provided by Nium.

---
## Oct 24, 2023

### New Features

*   We have added several new features to the Nium portal in sandbox environment including, global wallets view, reports for payout transactions, configure webhook events, invite new users to your sandbox, and transparency with chronometer in the transaction details. Read the [announcement blog](https://www.nium.com/resources/nium-portal-faster-time-to-market) for more details.

*   If you are using the delegated model, we have improved the settlement report file to offer more comprehensive information for transaction matching. The new settlement file includes additional fields and is formatted with the pipe symbol as a delimiter, making it simpler to parse and handle. We're delivering the updated V2 version of the file to the same SFTP location where V1 was previously shared. Clients can take advantage of this enhanced file to improve their settlement processing. Detailed information on the format of the file is available in the [Client settlement report](https://docs.nium.com/apis/docs/client-settlement-report-v2) guide.

*   Introduced a new API to retreive Account Ownership Certificate (AOC) for your customers. To download the account ownership certificate you can call the [Account Ownership Certificate](https://docs.nium.com/apis/reference/accountownershipcertificate) API.
    *   Account Ownership certificate is a pdf generated by Nium to provide the details of the virtual account(s) assigned to the name of the underlying customer.
    *   AOC are usually required by online market places or payment gateways for registration.
    *   AOC document can be used by your underlying customers for providing account details for collections across different payment platforms.
    *   Additionally, AOC are required for loan applications or when dealing with government agencies.

### API Breaking Changes

*   **Document details are required when onboarding in EU**
    
    Nium must report the "documentNumber" associated with the individual stakeholder positions of corporate customers to regulatory authorities through various reports. Until now, clients were not obligated to provide `stakeholderDetails.documentDetails` in the eKYB process. However, starting January 1, 2024, `stakeholderDetails.documentDetails` will become a mandatory field for both the eKYB and Manual KYB procedures when the position corresponds to UBO, TRUSTEE, or PARTNER.
    
    Additionally, `stakeholderDetails.kycMode`, and `stakeholderDetails.documentDetails.document` will continue to be optional in the eKYB process when a `searchID` is provided, but they will be required fields when `searchID` is not provided for the manual KYB flow.
    
    See [EU required Parameters](https://docs.nium.com/apis/docs/cc-eu-required-parameters) and [EU required documents](https://docs.nium.com/apis/docs/cc-eu-required-documents) for more details.

### Enhancements

*   Ability to update name on card for corporate cards. We have enhanced [Update Card Details V2](https://docs.nium.com/apis/reference/updatecarddetailsv2) API which will allow customers or cardholders to update card data at individual card level including the name on card.
*   We have included new delivery options for EU & UK. In [Add Card V2](https://docs.nium.com/apis/reference/addcardv2) API the `issuanceMode` field has two new options `international_delivery_track`, and `international_delivery_track_sign`.
*   Added transparency about timing of the interbank FX rate. In order to ensure that you know the exact time at which we obtained the last traded interbank FX rate being used in an FX quote, a new field called `rateCaptureTime` was added in the API response for creating a quote and fetching an existing quote. The `rateCaptureTime` field has the timestamp at which we got it from our rate service provider.


---
## Oct 10, 2023

### Enhancements
    
*   Corporate customer onboarding enhancements
    *   Added a new `status` field in [Client KYB Status](https://docs.nium.com/apis/reference/client-kyb-status) webhook to enhance corporate customer onboarding.  
        At present, the Client KYB Status webhook only provides access to the `complianceStatus` parameter, and you proceed with the transaction upon receiving a `complianceStatus` value of `COMPLETED`. Although infrequent, certain transactions may not succeed because transactions are only allowed when the `status` is `Clear`
        
        To address this issue and prevent transaction failures, we have now included the `status` field in the webhook, which is already available in the Customer Details API. We strongly recommend that clients utilize both `complianceStatus` and `status` to ensure the successful execution of transactions.
        
        Note that the `complianceStatus` being `COMPLETED` does not signify a terminal state, as there is still a possibility of receiving Requests for Information (RFIs) even after this webhook has been received. In rare instances, RFIs may still be raised even after the `status` has reached `Clear` due to post-approval due diligence. However, transactions will not be blocked in such situations.
        
    *   Amendment to attestation for US Clients.  
        For US clients, it is necessary to update the applicant declaration or attestation in your onboarding process to incorporate the UBO (Ultimate Beneficial Owner) declaration. Use the following amended attestation:
        
        _“I certify that I am the authorized representative of the customer; all information provided and documents submitted are complete and correct. I confirm that I have provided all the UBOs present. I have read and accepted the Nium Terms and Conditions.“_
        
*   Individual customer onboarding enhancements
    *   Enhancement in [Unified Add Customer](https://docs.nium.com/apis/reference/unifiedaddcustomer) API by adding a new optional field `isTncAccepted` to support both onboarding and the terms and conditions (T&C) acceptance in a single API call.
        
        `isTncAccepted` is a boolean field and the default value is `false`. With this change, customer's initial consent to the T&Cs can be recorded during the onboarding flow.
        
    *   Introduced shortened enum values for `intendedUseOfAccount` and `estimatedMonthlyFunding` fields in [Unified Add Customer](https://docs.nium.com/apis/reference/unifiedaddcustomer) API. The shortened values and their corresponding descriptions are available in the [enum values description guide](https://developersandbox.nium.com/apis/docs/unified-add-customer-api-example#enum-values). This enhancement will make the API easier to use and reduce the chance of getting validation errors.
        
    *   [Regenerate KYC URL](https://docs.nium.com/apis/reference/regeneratekycurl) API now supports individual customers in addition to corporate customers.

*   Extended [Get Card Widget](https://docs.nium.com/apis/reference/customergetcardwidget) API to support UnionPay.  
    This improvement expands the Nium card widget's support to include UnionPay China cards alongside the currently supported Visa Cards. This update will facilitate payments to UnionPay cardholders in China for those who do not meet Payment Card Industry Data Security Standard (PCI DSS) compliance requirements.
    
    If you are not compliant with PCI DSS, you need to integrate with Get Card Widget API to get the recipient’s encrypted card token number. You then pass the token number in the field encryptedBeneficiaryCardToken when you add a beneficiary to make a payout to a card.
    
    [Steps to make payouts](https://docs.nium.com/apis/docs/get-a-card-widget) to UnionPay Cards will remain same as existing Visa card payouts.
    
*   GPI Details for SWIFT Wires SWIFT GPI (Gpi stands Global Payments Innovation) was developed in 2017 to improve the experience of making a payment via the SWIFT network.
    
    With this enhancement, we are utilizing the information received from our SWIFT partner banks to offer end-to-end visibility into the status of a transaction, starting from the moment it's initiated to the moment it's deposited to the beneficiary account. In essence, we're enabling the tracking of SWIFT wire transactions.
    
    The GPI details can be obtained using the [Fetch Remittance Life Cycle Status](https://docs.nium.com/apis/reference/fetchremittancelifecyclestatus) API which now includes a new object `gpi` with four parameters in the API response:
    
    *   `reasonCode`: GPI code shared by the SWIFT partner bank
    *   `statusDescription`: Description of the GPI reason code
    *   `timestamp`: Date and time of the last status change
    *   `forwardBankName`: Name of the next participant bank to which the payment has been forwarded
    
    [Remit Transaction Sent to Bank Webhook](https://docs.nium.com/apis/reference/remit-transaction-sent-to-bank) will have the following enhancements:
    
    *   The `gpi` object with the above described four parameters will also be available in the webhook response.
    *   We will send a new event notification whenever there is a change in `reasonCode` or `forwardBankName`.

---
## Sep 26, 2023

### New Feature

*   Introduced the new [Fetch Aggregated Exchange Rates](https://docs.nium.com/apis/reference/aggregatedexchangerates) endpoint that allows you to track and monitor historic market trends for any currency pair.

    After you specify the required `sourceCurrencyCode` and `destinationCurrencyCode` fields, this API returns the aggregated daily FX data for the past ninety days.

    You can also specify the following optional fields:

    *   `start` and `end` dates that need to be within the the last ninety days.
    *   `window` to specify whether the results should be grouped by hour or day.

*   For both the hourly and daily window views, the following are displayed for the specified currency pair during the selected time window:

    *   `min` - The minimum FX rate captured.
    *   `max` - The maximum FX rate captured.
    *   `average` - The average FX rate calculated.
    *   `time` - The starting timestamp of the FX rate aggregation.

    For additional information, refer to the [FX overview guide](https://docs.nium.com/apis/docs/fx-overview#rate).

---
## Sep 12, 2023

*   Added a new RFI template called `otherData` for corporate onboarding.
    
    Currently the RFIs requiring additional data are limited to `businessName`, `transactionCountries`, and `intendedUseOfAccount`. Prior to this change, when additional information was required, an RFI was raised using an email or with the `otherDocument` RFI template. Since the `otherData` RFI handles non-document requests, any type of information can now be collected without the need to add any new RFI templates in the future.
    
    The `otherData` RFI is available in preprod for testing now and will be available in production starting **October 10, 2023**.
    
    The request body for [Respond to RFI](https://docs.nium.com/apis/reference/respondtorfiforcorporatecustomer) API accepts `businessInfo.additionalInfo.otherData` object as an item in the `rfiResponseRequest` array object.
    
    **Examples for usage of `otherData`:**
    
    *   [Template in the response of the Fetch RFI Details API](https://docs.nium.com/apis/docs/cc-rfi-examples#otherdata-template-in-the-response-of-the-fetch-rfi-details-api)
    *   [Request body for the Respond to RFI API](https://docs.nium.com/apis/docs/cc-rfi-examples#otherdata-request-body-for-the-respond-to-rfi-api)

---
## Aug 29, 2023

### Enhancements

*   For security and to inform customers of any account takeover, notifications are sent in two ways.

    * Notification by Email

        *   The new email template `CUSTOMER_UPDATE_EMAIL` has been introduced to send email notifications to the customers whenever there is any update in the email address or mobile number of the customer.
        *   For any change in the email address, notifications are sent to both the previous and updated email address.
        *   For any change in the mobile number, the notification is sent to the current email address.
        *   Currently, this is applicable only for individual customers whose `kycStatus` is `Clear`.

    *  Notification by Webhook

        *   To send the contact information of the customer prior to the update, three new key-value pairs have been included in the `fields` parameter:
            *   `previousCountryCode`
            *   `previousMobile`
            *   `previousEmail`
        *   The `CARD_CUSTOMER_UPDATE_WEBHOOK` parameter notifies about the customer’s previous and newly updated contact information to you.
        *   Example of the updated field in the request body of the webkook template:  
            `"fields": {`  
            `"countryCode": "SG",`  
            `"mobile": "67543800",`  
            `"email": "john@xyzmail.com",`  
            **`"previousCountryCode": "US",`  
            `"previousMobile": "123456789",`  
            `"previousEmail": "jack@xyzmail.com"},`**

### New Feature

*   The new [OOB Callback v2](https://docs.nium.com/apis/reference/processoobcallbackv2) API simplifies the request payload for providing Nium with the result of 3DS out-of-band authentication.

    *   After you perform authentication using Biometrics or other means, you can provide the success or failure to Nium against the Transaction ID.
    *   [OOB Callback v1](https://docs.nium.com/apis/reference/processoobcallback) API will be deprecated and becomes unsupported on **March 31, 2024**.

---
## Aug 15, 2023

### Enhancements

*   EU Corporate Customer Onboarding allows an application to be submitted without the collection of the `REGISTER_OF_DIRECTORS` and `REGISTER_OF_SHAREHOLDERS` documents for Public and Private companies when not required.
    
    *   Starting **August 14**, `businessDetails.additionalInfo.businessExtractCoveredStakeholder` is no longer validated, allowing an application to be submitted without these two documents.
    *   There are no longer any notes related to these documents in the `remarks` field in the response object of the [Onboard Corporate Customer](https://docs.nium.com/apis/reference/onboardcorporatecustomer) API.
    *   An RFI will be raised if either of these documents is required. Typically, when the `BUSINESS_REGISTRATION_DOC` does not contain the details of directors and shareholders based on customer input.
    
    [See here for the complete list of required business documents for EU corporate customers.](https://docs.nium.com/apis/docs/cc-eu-required-documents#business-details)
    
*   EU, SG, and UK Individual Customer Onboarding has three additional parameters in the KYC redirect URL to help you better understand the status of a customer’s verification: `errorCode`, `errorMessage`, and `isSuccess`.
    
    *   This is applicable for the eDocument verification flow in EU, UK, and SG and applicable for the eKYC flow in SG.
    *   The `isSuccess` field is returned as true or false depending on the customer’s completion status of the verification flow with the vendor.
    *   The `errorCode` and `errorMessage` fields are populated whenever `isSuccess` is false.
    
*   All _new_ US corporate customers registered in Delaware and New Jersey require a `CERTIFICATE_OF_GOOD_STANDING` document. If not provided, this document appears in the `remarks` field in the response of the Onboard Corporate Customer API as shown below and the application stays in the `IN_PROGRESS` status until the document is provided.
    
         {
            "clientId": "NIM1691559286485",
            "caseId": "e4f6f7be-8e75-4cbc-9db4-5032a8b0da9c",
            "status": "IN_PROGRESS",
            "remarks": "BUSINESS -> Certificate of Good Standing is expected for business entity Soylent Corporation6s3323, Please upload expected document.|KYC : SCREENING COMPLETED, ALIAS_KYC : SCREENING COMPLETED|VERIFIED",
            "customerHashId": "d08c856a-9dcf-46bb-be24-125d352459ba",
            "walletHashId": "337ffc84-dc5d-48fb-8471-2bd7cac3fd94",
            "redirectUrl": "",
            "errors": []
        }  
    
    **Impact:**
    
    *   The enum value `CERTIFICATE_OF_GOOD_STANDING` has been added to the enum list of the `businessDetails.documentDetails.documentType` field in the [Onboard Corporate Customer](https://docs.nium.com/apis/reference/onboardcorporatecustomer) API.
    *   The `CERTIFICATE_OF_GOOD_STANDING` is a required document when the `address.registeredAddress.state` field is `DE` or `NJ`, and the application stays in the IN\_PROGRESS state until submitted.
    
    [See here for the complete list of required documents for US corporate customers.](https://docs.nium.com/apis/docs/cc-us-required-documents)
    
    **Items available for testing in the sandbox environment:**
    
    *   The enums list added `CERTIFICATE_OF_GOOD_STANDING`, and the `remarks` field is available for missing documents for both eKYB and Manual KYB clients.
    *   By **August 22**, Manual KYB clients can use the remarks field for `CERTIFICATE_OF_GOOD_STANDING` documents.

---
## Aug 1, 2023

### New Features

*   You can now use a new method to link a bank account for [Debit ACH US through a micro-deposit](https://docs.nium.com/apis/docs/direct-debit-us#option-2-link-bank-account-via-micro-deposit-verification). This option is especially beneficial in cases where instant verification _is not_ supported. Your customer now has the flexibility to choose between two verification options: [instant](https://docs.nium.com/apis/docs/direct-debit-us#option-1-link-bank-account-via-instant-verification) or [micro-deposit](https://docs.nium.com/apis/docs/direct-debit-us#option-2-link-bank-account-via-micro-deposit-verification). To support the micro-deposit option, you need to implement the [Confirm Funding Instrument API](https://docs.nium.com/apis/reference/confirmfundinginstrumentid). Once the micro-deposit is successfully delivered, a new webhook, [DIRECT\_DEBIT\_MICRODEPOSIT\_SUCCESSFUL](https://docs.nium.com/apis/reference/direct-debit-micro-deposit-successful) is sent by Nium to notify you of the successful transaction. These enhancements aim to provide you and your customers with broader coverage and improved options for bank account verification.
        
*   Philippine peso(PHP) currency support is now enabled for collections and funding. You now have the option to call the [Assign Payment ID](https://docs.nium.com/apis/reference/assignpaymentid) API with the parameter `bankName` set as `NETBANK_PH_PHP` and the `currencyCode` set as PHP. This configuration allows your customers to generate a PHP virtual account, facilitating expanded payment processing and management.

*   Introduced a new feature, [Wallet to Wallet Transfers](https://docs.nium.com/apis/docs/wallet-to-wallet-transfers-1) that enables fund transfers between Nium customers' wallets using the new [Wallet to Wallet Transfer](https://docs.nium.com/apis/reference/wallettransfer) API. With this functionality, customers can easily transfer funds to another Nium onboarded customer. The sender and receiver of the funds can belong to the same client setup or different client setups onboarded with Nium, depending on their geographic presence.

    *   This enhancement benefits global clients with multiple client setups on the platform. It allows customers across these client setups to conduct wallet-to-wallet transfers seamlessly, enhancing the overall user experience and facilitating smoother financial transactions.
    *   Transferring funds between customers of the same client setup does not require any configuration changes within the client setup. However, for funds transfer between customers of different client setups, you need to contact your Nium representative. They can help you enable this feature, allowing your customers to utilize it seamlessly.

### Enhancement

 *   Added a new enum value called **"Travel related spending"** in the parameter `intendedUseOfAccount` within the [Unified Add Customer](https://docs.nium.com/apis/reference/unifiedaddcustomer) API. The new value will support individual customers' travel-related use cases. This addition better supports and accommodates various financial transactions related to travel expenses for our customers.

### Deprecation Notices

*   In the Client Details API, the `multiCurrencySupported` field is being removed from the API's response object as it is an unused field and is set to false by default. This field was giving misleading information that the client does not have support for multiple currencies. Clients will see the currencies enabled for their setup in the `currencies` field of the response.
*   In the [Unified Add Customer](https://docs.nium.com/apis/reference/unifiedaddcustomer), [Customer Details V2](https://docs.nium.com/apis/reference/customerdetailsv2), and [Customer List V3 APIs](https://docs.nium.com/apis/reference/customerlistv3), the `preferredName` field has been changed from required to optional, meaning it is no longer required for customer onboarding purposes. You now have the flexibility to provide this information if needed, but it is not required when using the API for customer registration.
*   The [P2P Transfer](https://docs.nium.com/apis/reference/p2ptransfer) API is deprecated and becomes unsupported on January 31, 2023.

---
## July 19, 2023

### New Features

*   Introduced a new Transaction Prescreening capability for scheduled transactions. This functionality enables payroll clients to send transactions to Nium for compliance or risk-related checks before the scheduled date of the transactions. It’s recommended to initiate a scheduled payout five to seven days in advance if the client wants to prescreen the transaction. A new `preScreening` boolean field, with a value as true/false, is introduced in the payout object of the [Transfer Money](https://docs.nium.com/apis/reference/transfermoney) API. New transaction types are introduced for prescreening transactions `Remittance_Debit_External_Prescreening` and `Remittance_Debit_Prescreening` (self-payment).
        
*   Note: The reverted FX conversion feature is improved by changing the URL names of the Conversion APIs listed below to clearly distinguish between a conversion within a customer’s wallet and a transfer from one customer’s wallet to another customer’s wallet.
        
    Introduced the capability to perform FX conversions within a customer’s wallet using locked FX rates as well as scheduled settlement. This service helps you convert your funds from any of the supported Nium payin currencies into any of the Nium payout currencies at transparent and guaranteed FX rates. The converted amount can then be used to send payouts or spend through a card.
    
    *   You can choose from a range of lock periods (up to 24 hours) for the FX quote so that you have time to confirm the rate with your customers or internal users and initiate the FX conversion.
    *   You can also choose from a range of conversion schedules (up to two business days) so that you get the necessary time to fund with the source amount required for the FX conversion.
    
    Refer to the [FX Overview](https://docs.nium.com/apis/docs/fx-overview) guide for more information on this capability.  
    The following new APIs are introduced to support this capability:
    
    *   [Create Quote](https://docs.nium.com/apis/reference/createquote) API: Creates an FX quote for a pair of currencies based on a lock period and conversion schedule.
    *   [Fetch Quote by ID](https://docs.nium.com/apis/reference/fetchquote) API: Fetches the details of an FX quote using the quoteId.
    *   [Create Conversion](https://docs.nium.com/apis/reference/createconversion) API: Converts funds within a customer's wallet from a source currency to a destination currency at either a market FX rate or a locked FX rate obtained using the Create Quote API.
    *   [Fetch Conversion by Id](https://docs.nium.com/apis/reference/fetchconversion) API: Fetches the details of an FX conversion using the conversionId.
    *   [Cancel Conversion](https://docs.nium.com/apis/reference/cancelconversion) API: Cancels an FX conversion that’s yet to be settled.
    
*   We have introduced a new [Unblock PIN](https://docs.nium.com/apis/reference/unblockcardpin) API that allows you to unblock a card’s personal identification number (PIN) when an invalid PIN number is entered more than four times. You can query the PIN status using the [Fetch PIN Status](https://docs.nium.com/apis/reference/fetchpinstatus) API. This API is applicable for Physical cards only and available for clients in the APAC region.

### Enhancements

*   **Direct Debit**
    
    1\. Introduced an option for faster settlement time for Direct Debit ACH in the US. Reach out to your Nium sales representative for more information.
    
    2\. Introduced additional webhooks when there’s a change in the status of your funding instrument:
    
    *   `DIRECT_DEBIT_FUNDING_INSTRUMENT_APPROVED` — when the status of your fundingInstrument changes from Pending to Approved. After this, you can call the [Fund Wallet](https://docs.nium.com/apis/reference/fundwallet) API to initiate a debit from your bank account.
    *   `DIRECT_DEBIT_FUNDING_INSTRUMENT_FAILED` — when the status of your fundingInstrument changes from Pending to Failed. After this, you can call the [Get Funding Instrument Details](https://docs.nium.com/apis/reference/getfundinginstrumentdetails) API to know the reason for the failure and act accordingly.
    *   `DIRECT_DEBIT_FUNDING_INSTRUMENT_CANCELLED` — when the status of your fundingInstrument status changes from Approved to Cancelled. You receive this as an acknowledgement that the customer has cancelled the mandate via their bank.
    
*   Enhanced the ability for a client to embed the card widget within the client’s domain. A new `clientDomain` field is introduced in the request body of the [Get Card Widget](https://docs.nium.com/apis/reference/customergetcardwidget) API. This field contains the domain name where the widget needs to be embedded.

---
## July 5, 2023

### API Breaking Changes

*   We've identified that the [previously announced](https://docs.nium.com/apis/changelog/jun-20-2023) FX conversions APIs require a few critical improvements. As a result, we're reverting the feature effective immediately and plan to relaunch the revised APIs shortly. Stay tuned for an updated announcement.

### New Features

*   *   We've introduced a beta version of AI-powered docs. OpenAI now backs our docs to provide human-like interaction with the **Ask a question** search field. You can find this feature in the header section of all documentation pages.

### Enhancements

*   We've made enhancements to the daily downloadable [Client Account Fees Report](https://docs.nium.com/apis/docs/daily-client-account-fees-report) by adding the following new fields:

    *   Fee Source: This field indicates the source of the fee levied by the system, the default fee setup or the client charge fee API.
    *   Fee Type: This field applies only to fees levied by the system and indicates whether the fee was set up as a percentage or a flat fee.
    *   Fee Value: This field applies only to fees levied by the system and contains the defined value of the fee in the client setup.
    *   Fee Value Currency: This field applies only to flat fee types and indicates the currency in which the fee value was defined.
    *   Additional Fee Type: This field applies only to fees where clients have opted for additional fees as part of the payout request. It shows the fee type chosen by the client, either fixed or percentage.
    *   Additional Fee Value: This field applies only to fees where clients have opted for additional fees as part of the payout request. It contains the amount value that was added to the fee.

### Deprecation notice

*   The `designation` parameter in [Unified Add Customer](https://docs.nium.com/apis/reference/unifiedaddcustomer), [Customer List V3](https://docs.nium.com/apis/reference/customerlistv3), and [Customer Details V2](https://docs.nium.com/apis/reference/customerdetailsv2) APIs, is deprecated and becomes unsupported on December 16, 2023.

---
## Jun 20, 2023

### New Features

*   We have identified that a few critical improvements are required to the below announced FX conversions APIs. As a result, we have reverted the feature effective immediately and will be re-launching the revised APIs shortly. Stay tuned for an updated announcement.

    We are introducing the capability to perform FX conversions within a customer’s wallet using locked FX rates as well as scheduled settlement. This service helps you convert your funds from any of the supported Nium payin currencies into any of the Nium payout currencies at transparent and guaranteed FX rates. The converted amount can then be used to send payouts or spend through a card.

    *   You can choose from a range of lock periods (up to 24 hours) for the FX Quote so that you have time to confirm the rate with your customers or internal users and initiate the FX conversion.
    *   You can also choose from a range of conversion schedules (up to two business days) so that you get the necessary time to fund with source amount required for the FX conversion.

    Refer to the FX Overview guide for more details on this capability.

    The following new APIs are being introduced to support this capability:

    *   Create Quote API: Create an FX quote for a pair of currencies based on a lock period and conversion schedule.
    *   Fetch Quote by id API: Fetch the details of an FX Quote using the quoteId.
    *   Create Transfer API: Convert funds within a customer's wallet from a source currency to a destination currency at either a market FX rate or a locked FX rate obtained using the Create Quote API.
    *   Fetch Transfer by id API: Fetch the details of an FX Transfer using the transferId.
    *   Cancel Transfer API: Cancel an FX Transfer that is yet to be settled.
    
### Enhancements
    
*   `cardProductId` parameter, that is required request body parameter in the Add Card V2 API, has been changed from a 3-digit number to UUID format. This change is only applicable to new clients. Clients that are setup previously with a 3-digit `cardProductId` can continue to use it.
*   `addressLine1` and `addressLine2` parameters in the Address object of all card lifecycle APIs, Add Card V1 & V2, Update Card Details V2, Block and Replace Card, and Renew Card, have additional validation. As per the new validation rules, only chars in the below regex pattern are allowed: `Regex: [a-zA-Z0-9.'-#@%&,:/ ]+`
*   Revised posting logic on transaction settlements for all Wallet based Clients. Previously, A separate transaction was posted for `Settlement Debit` and `Settlement Credit` depending on if the fluctuation was higher or lower respectively. In the revised logic, fluctuations are accounted for by reversing the original transaction including relevant fees that were charged and posting a new transaction as `Settlement Direct Debit` for the new amount (higher or lower) and recalculate all relevant fees and markups.     
    There is no impact to wallet clients as the amount being debited or credited has not changed, only the methodology has been updated.  
    This change is not applicable to clients on Delegated Mode (RHA).
    
    Following are example scenarios where this change is applicable:
    
    *   FX Rates have fluctuated in the time period between authorization and settlement.  
        Example: The FX rates have fluctuated between SGD (billing Currency) and USD (authorization currency i.e., the receiving wallet).  
        Fluctuated higher-
        
        *   FX rate between SGD and USD was 1.33510 at the time of authorization.  
            FX rate between SGD and USD has become 1.34100 at the time of clearing.
        
        Fluctuated lower-
        *   FX rate between SGD and USD was 1.33510 at the time of authorization.  
            FX rate between SGD and USD has become 1.33100 at the time of clearing.
    *   FX Rates have fluctuated between the transaction currency and the billing currency in the time period between authorization and settlement.  
        Example: The transaction was performed in PHP (Philippine Peso) and the billing currency is SGD (Singapore Dollar).  
        Fluctuated higher-
        
        *   FX Rate between PHP and SGD was 0.02410 at the time of authorization.  
            FX Rate between PHP and SGD has become 0.02490 at the time of clearing.
        
        Fluctuated lower-
        *   FX Rate between PHP and SGD was 0.02410 at the time of authorization.  
            FX Rate between PHP and SGD has become 0.02380 at the time of clearing.
    *   There has been a change in the transaction amount between authorization and clearing.  
        Example: The cardholder has left a tip in a restaurant due to which the transaction amount during clearing is higher than the transaction amount at the time of authorization.

---
## Jun 6, 2023

### Enhancement
    
*   The responses for the [Confirm Funding Instrument](https://docs.nium.com/apis/reference/confirmfundinginstrumentid) API, the [Get Funding Instrument List](https://docs.nium.com/apis/reference/getfundinginstrumentlist) API, and the [Get Funding Instrument Details](https://docs.nium.com/apis/reference/getfundinginstrumentdetails) API responses are enhanced to include the new `bankName` field in the funding instrument linked for direct debit.
    
### API Breaking Change
    
*   This is a reminder notice about the breaking changes to beneficiary APIs that are enhanced with two new fields, `beneficiaryContactName` and `beneficiaryEntityType`. The fields are required to make a local payout to a business in South Africa with the South African rand (ZAR) currency. Details on the changes are available in an earlier communication in the [May 9, 2023 changelog](https://docs.nium.com/apis/changelog/may-9-2023). The changes will become effective on **June 15, 2023**.
    
### New Feature

*   [Activate Card V2](https://docs.nium.com/apis/reference/activatecard) API is a new operation that features the concept of an activation code to help cardholders activate their cards using it. The activation code is provided in the card kit cardholders receive with the physical copy of the card.

    *   The platform generates an activation code for all PHY-type cards using the [Add Card V2](https://docs.nium.com/apis/reference/addcardv2) API only. This feature is not available if the [Add Card V1](https://docs.nium.com/apis/reference/addcard) API is used when creating cards. The activation code is sent in the embossing file to the personalization vendor and printed on the letter accompanying the card.
        
    *   The API structure mirrors the structure of all other Card V2 APIs with logical tags. The API includes the activation code as a required field to activate the physical card. This prevents cards from being activated immediately upon creation.
        
    
### Deprecation notice
    
*   [Activate Card V1](https://docs.nium.com/apis/reference/activatecard_1) API is deprecated and becomes unsupported on December 31, 2023. [Activate Card V2](https://docs.nium.com/apis/reference/activatecard) is the latest version of this API.
    
### Enhancement
    
*   Search and filter transactions in the Transaction Report of the [client portal](https://spend.nium.com/cards-ui/authenticate/login), with additional filter options using a card hash ID, transaction status, or settlement status. The transaction status and settlement status now support searching with multiple values.
---
## May 23, 2023

### New Features

*   [**Link a corporate customer to an individual customer**](https://docs.nium.com/apis/docs/parent-child-hierarchy) is a new feature for Spend Management and Payroll Management use cases. You can now link an individual customer, or employee, to their corporate customer and create that hierarchy in the system.
    
    **Note**: For details on how to link a corporate customer to an individual customer or the Spend and Payroll Management feature, refer to the **Platform** tab.
    
    *   [**Spend Management**](https://docs.nium.com/apis/docs/parent-child-hierarchy#add-a-card-to-an-employee-linked-to-a-corporate-account): assigns a card to an employee linked to a corporate account. You can issue cards using the [Add Card V2](https://docs.nium.com/apis/reference/addcardv2) API to provide the customer details as mentioned below:
        
        *   `customerHashId`: the `customerHashId` of the corporate customer
        *   `walletHashId`: the unique `walletHashId` of the corporate customer
        *   `childCustomerHashId`: the `customerHashId` of the individual customer
        
        The card is issued to a corporate customer and is linked to an individual customer.
        
        You can fetch the `childCustomerHashId` with the [Card Details V2](https://docs.nium.com/apis/reference/carddetailsv2) and [Card List](https://docs.nium.com/apis/reference/cardlist) APIs. The query parameters are enhanced to include the clientHashId, customerHashId, walletHashId, and childCustomerHashId to help filter the results.
        
    *   [**Payroll Management**](https://docs.nium.com/apis/docs/parent-child-hierarchy#assign-a-card-to-an-employee-linked-to-their-account): assigns a card to an employee for their own account. You can issue cards using the [Add Card V2](https://docs.nium.com/apis/reference/addcardv2) API to provide the customer details as mentioned below:
        
        *   `customerHashId`: the `customerHashId` of the corporate customer
        *   `walletHashId`: the unique `walletHashId` of the corporate customer
        *   `childCustomerHashId`: `NULL`
        
        The card is issued to an individual customer.
        
*   [**Card List V2**](https://docs.nium.com/apis/reference/cardlist) API retrieves a list of all cards issued to a wallet using the `walletHashId` and the `customerHashId` path parameters.
    
    *   The API structure mirrors the structure of all other Card V2 APIs with logical tags.
    *   The API shows the delivery address on file, the address where the card is delivered, and its embossing details.
    *   **Card List V1** API is deprecated and becomes unsupported on December 31, 2023.
    
*   A transaction is declined if the Know Your Customer (KYC) verification process is in the **pending** status. This change is in accordance with compliance regulations. All cards associated with the customer and their wallet are also temporarily blocked until the status changes to verified.
*   [**Spend and Payroll management**](https://docs.nium.com/apis/docs/parent-child-hierarchy):
    *   **Link a corporate customer to an individual customer** is a new feature for Spend Management and Payroll Management use cases. You can now link an individual customer, or employee, to their corporate customer and create that hierarchy in the system. Only an individual customer can be linked to a corporate customer. The opposite isn’t true.
        
        To establish a connection or relationship between the individual customer and the corporate customer, you need to configure the relationship with the `childMustHaveParent` parameter set to `true`. If this flag is `false`, you have the option to establish the connection, but the hierarchy is not enforced by the system.
        
        *   Spend Management clients need to be configured with the `billingAddressAsCorporate` parameter set to `true`. This parameter allows the billing address of an Individual customer to be the same as the business address of a corporate customer.
        *   Payroll Management clients need to be configured with the `billingAddressAsCorporate` parameter set to `false`.
        
        To setup the hierarchy, you need to [onboard the corporate customer](https://docs.nium.com/apis/reference/onboardcorporatecustomer) first and then onboard the individual customer using the [Unified Add Customer](https://docs.nium.com/apis/reference/unifiedaddcustomer) API. The fields below have been impacted:
        
        *   `parentCustomerHashId`: A new required parameter has been added if the `childMustHaveParent` flag is set to `true`.
        *   `kycMode`: accepts MANUAL\_KYC value if the `billingAddressAsCorporate` parameter is set to `true`.
        *   `billingAddress`: details are optional if the `billingAddressAsCorporate` parameter is set to `true`.
        
        You can fetch the parentCustomerHashId for an individual customer with the following enhanced APIs:
        
        *   [**Customer List V3**](https://docs.nium.com/apis/reference/customerlistv3) API: allows all individual customers to have the `parentCustomerHashId` parameter value available. You can fetch all the Individual customers linked to a corporate customer by providing the `parentCustomerHashId` parameter as a part of the query parameter.
        *   [**Customer Details V2**](https://docs.nium.com/apis/reference/customerdetailsv2) API: the `parentCustomerHashId` parameter, in the individual customer details section, provides the `customerHashId` of a corporate customer to which the individual customer is linked.
        
    *   [**Transaction management**](https://docs.nium.com/apis/docs/parent-child-hierarchy#transaction-management) is enhanced with the update of the following APIs to include the transactions that individual customers make on the cards issued to corporate accounts:
        
        *   [**Transactions**](https://docs.nium.com/apis/reference/transactions-1) API: The `childCustomerHashId` parameter is added for all the transactions. The value includes the `customerHashId` of the individual customer for the applicable transactions. The `childCustomerHashId` can be used as a query parameter in this API.
        *   [**Client Transactions**](https://docs.nium.com/apis/reference/clienttransactions) API: The childCustomerHashId parameter is added for all the transactions. The value includes the customerHashIdof the individual customer for the applicable transactions. The `childCustomerHashId` can be used as a query parameter in this API.
        
*   **Electronic document verification**, or `E_DOC_VERIFY`, is now available as an option in `kycMode` for Know Your Customer (KYC) applicants in all regions. Corporate customers in Australia (AU), Singapore (SG), and the United States (US) previously completed the applicant KYC verification process via `MANUAL_KYC`, which delays the approval process. Using `E_DOC_VERIFY`, customers can now complete the KYC verification process for non-resident applicants following the redirect URL of Nium's KYC vendor and uploading documents on the vendors' UI resulting in real-time approvals. `E_DOC_VERIFY` is also available for Electronic Know Your Business (eKYB) and manual KYB. `E_DOC_VERIFY` is also available for European Union (EU) and United Kingdom (UK) applicants.
    
    Enable `E_DOC_VERIFY` by passing the `businessDetails.applicantDetails.kycMode=E_DOC_VERIFY` object in the [**Onboard Corporate Customer**](https://docs.nium.com/apis/reference/onboardcorporatecustomer) API. Refer to [**Region-specific KYB requirements**](https://docs.nium.com/apis/docs/overview-corporate-customer#region-specific-kyb-requirements) to see the available applicant and stakeholder KYC modes. Refer to the applicant KYC information on the following pages to learn how to integrate: [**AU**](https://docs.nium.com/apis/docs/au-onboarding), [**SG**](https://docs.nium.com/apis/docs/sg-onboarding), [**US**](https://docs.nium.com/apis/docs/us-onboarding)
    
*   **Customer account statement** generates a statement that gives a list of all transactions your customer makes on the platform, including deposits, withdrawals, spending, fees, payments, and refunds. You can give your customers an account statement periodically or based on their specific requests to help them keep the information for their records or to reconcile their transactions. You can now generate an account statement for your customers via the [**Account Statement**](https://docs.nium.com/apis/reference/accountstatement) API as a PDF or a CSV document. Contact your Nium representative to use this feature.

### Enhancements

*   **Search and filter cards** in the [**client portal**](https://spend.nium.com/cards-ui/authenticate/login) using a new **Search** and **Filter** feature entering a card number, a card hash ID, and a card proxy number, on the customer details screen. The functions help find a card among multiple ones attached to a wallet.
*   **Card Details** [V1](https://docs.nium.com/apis/reference/carddetails) and [V2](https://docs.nium.com/apis/reference/carddetailsv2), and **Card List** [V1](https://docs.nium.com/apis/reference/cardlist) and [V2](https://docs.nium.com/apis/reference/cardlistv2) APIs provide device details for Mastercard. Before, device details were only available for Visa cards.

*   [**Customer List V3**](https://docs.nium.com/apis/reference/customerlistv3) API features a new query parameter, named `customerType`, so you can fetch your customer list based on your customer type. The accepted values are `INDIVIDUAL` or `CORPORATE`.
    
*   [**Unified Add Customer**](https://docs.nium.com/apis/reference/unifiedaddcustomer) API makes the new customer onboarding delivery address parameters listed below optional. You can now choose to use the fields but they’re not required.
    
    *   `deliveryAddress`
    *   `deliveryAddress2`
    *   `deliveryCity`
    *   `deliveryCountry`
    *   `deliveryLandmark`
    *   `deliveryState`
    *   `deliveryZipCode`


---
## May 9, 2023

### New Features
    
*   Introduced the **Direct Debit** capability on Nium's payments network for UK and EU customers. The capability provides convenience to UK-based and EU-based businesses to fund from their UK and EU bank account respectively into their Nium-issued wallets using Direct Debit. To support this feature, new APIs have been added and the existing APIs have been modified as mentioned below. The transaction type for this payment method in Nium's system is `WALLET_CREDIT_MODE_DIRECT_DEBIT`. Contact your Nium representative to activate this feature.
    
    Refer to the [Direct Debit](https://docs.nium.com/apis/docs/direct-debit) user guide for more details on this feature.
    
    *   [`addFundingInstrument`](https://docs.nium.com/apis/reference/addfundinginstrument) API — Links the customer’s bank account to their Nium wallet. Additional data elements have been added to receive bank account details in setting up Direct Debit for UK and EU customers.
    *   [`confirmFundingInstrument`](https://docs.nium.com/apis/reference/confirmfundinginstrumentid) API — Receives the one-time password (OTP) entered by the customer for validation by Nium against the OTP generated by Nium before setting up a Direct Debit mandate. This is a new API.
    *   [`getFundingInstrumentDetail`](https://docs.nium.com/apis/reference/getfundinginstrumentdetails) API — Provides the details of the account that's linked.
    *   [`getFundingInstrumentList`](https://docs.nium.com/apis/reference/getfundinginstrumentlist) API — Provides the list of accounts that are linked.
    *   [`fundWallet`](https://docs.nium.com/apis/reference/fundwallet) API — Initiates the payment instruction to pull the funds.
    
    In the previous year, we implemented restrictions on card issuance to countries that were approved in the Payment Instruction File (PIF) submitted to the card schemes. However, following additional feedback from the schemes, we have updated our approach and now restrict card issuance based on card type: physical or virtual.
    
    With this new approach, you have the flexibility to configure the countries where you want to issue virtual cards (pending approval from the schemes), even if physical card issuance to those countries is not permitted.
    
    For example, VISA has granted approval for virtual card issuance in Vietnam for a client based in Singapore, but physical cards are still prohibited.

*   In the previous year, we implemented restrictions on card issuance to countries that were approved in the Payment Instruction File (PIF) submitted to the card schemes. However, following additional feedback from the schemes, we have updated our approach and now restrict card issuance based on card type: physical or virtual.
    
    With this new approach, you have the flexibility to configure the countries where you want to issue virtual cards (pending approval from the schemes), even if physical card issuance to those countries is not permitted.
    
    For example, VISA has granted approval for virtual card issuance in Vietnam for a client based in Singapore, but physical cards are still prohibited.

*   **Fetch Corporate Constants API**
    
    [Fetch Corporate Constants API](https://docs.nium.com/apis/reference/fetchcorporateconstantsusingget) is now available for you to look up the enum values related to the onboarding of your corporate customers. This API returns acceptable values of various fields that need to be passed via the Onboard Corporate Customer API.
    
    There are many fields in Onboard Corporate Customer API which are of type enum and some of these fields have values that change often, such as `intendedUseOfAccount` and `IndustrySector`. Integrating this API helps you handle these changes without the need of any further development on your end when values are updated.
    
    Keeping enum values updated is beneficial to customers as it improves the approval rates and reduces the approval turnaround time.
    
    You need to integrate the Fetch Corporate Constants API and display the output to customers as a dropdown list while they complete your onboarding form. Use this API for all possible fields such as `businessType`, `documentType`, `annualTurnover`, `intendedUseOfAccount`, etc. For further details, see the [Fetch Corporate Constants](https://docs.nium.com/apis/docs/fetch-corporate-constants-api) user guide.
        
*   **Regenerate KYC URL API for Onboarding Corporate Customers**
    
    The KYC URL returned in the response of Onboard Corporate Customer has an expiration time; and once expired, the link cannot be used to complete the applicant KYC.
    
    Use the [Regenerate KYC URL](https://docs.nium.com/apis/reference/regeneratekycurl) API to generate a new KYC URL with a renewed expiration time.
    
    This API can be used for all regions if `applicantDetails.kycMode='E_DOC_VERIFY'` and in Singapore for both `E_DOC_VERIFY` and `E_KYC`.

### Enhancements
    
*   Introduced the new field `statementNarrative` in the Fund Wallet API to allow you to pass information that you would like to display in the payer's account statement for every debit transaction done via Direct Debit. The information that you can pass has a maximum length of 10 characters for the US and UK and a maximum length of 140 characters for EU.

*   In the previous release notes, we announced that `ADD_ON` type additional cards will no longer be supported from Sep 30th, 2023. With this release, ADD\_ON cards will not be renewable via the Card Renewal API.

### API Breaking Changes
    
*   Introduced two new fields in both V1 and V2 of beneficiary APIs. These fields are required for making a local payout to a business in South Africa with South African rand (ZAR) currency.
    
    The updated APIs that include the new fields are `addBeneficiary`, `updateBeneficiary`, `beneficiaryDetail`, and `beneficiaryList`.
    
    *   `beneficiaryContactName` (`beneficiary_contact_name` in v1) - This field requires the name of the contact person of the business.
    *   `beneficiaryEntityType` (`beneficiary_entity_type` in v1) - This field requires a beneficiary entity type and needs to be one of the following lowercase values:  
        \[`sole_propriatorship`, `partnership`, `privately_owned_company`, `publicly_owned_company`, `government_owned_company`, `go`, `financial_institution`\]
        
    
    The changes are effective **June 15, 2023.**
    
*   Removed the `maskedCardNumber` field from the response object of Add Card API v2. If needed, you can use Card Details API (v1 or v2) to get the `maskedCardNumber` field. The maskedCardNumber field still exists in Add Card API v1.

*   Introducing a new validation on `businessRegistrationNumber`. The change is applicable to Nium clients in all geographies that are onboarding corporate customers in the US. Going forward, you are expected to send only 9 digit numerals in this field. Any other format will result in a validation error. The change is effective **July 1, 2023**.

### Deprecation Notices
    
*   Add-on Cards are no longer issued after **September 30, 2023**.
    
    *   Add Card API v1 will return an error if the card being created is an 'Add-On’ card after **Sep 30th, 2023**. Clients must make the change to either switch to Add Card API v2 or ensure that `cardIssuanceAction` field in Add Card API v1 is passed as 'NEW' to indicate creation of the primary card.
    *   All existing Add-On cards are going to continue to work.
    
    Refer to the [Deprecated APIs](https://docs.nium.com/apis/docs/deprecated-apis) page for the complete list.
    
*   Starting **Sep 1, 2023** many of the enum values for the below listed fields will be removed or updated to support a newer version of our risk scoring model. Make use of the new [Fetch Corporate Constants](https://docs.nium.com/apis/reference/fetchcorporateconstantsusingget) API to get the latest values that are supported for these fields.
    
    Going forward integrate this API instead of hardcoding the new enum values for the associated fields.
    
    Once your integration is completed, please reach out to Nium support to get your template configured for the latest risk model.
    
    A few values are deprecated in the following fields of the Onboard Corporate Customer API:
    
    *   riskAssessmentInfo.industrySector
    *   riskAssessmentInfo.annualTurnover
    *   riskAssessmentInfo.intendedUseOfAccount
    *   riskAssessmentInfo.totalEmployees
    
    Refer to the [Deprecated APIs](https://docs.nium.com/apis/docs/deprecated-apis) page for the complete list.

---
## Apr 25, 2023

### New Features
    
*   Updated [Fetch Remittance Life Cycle Status](https://docs.nium.com/apis/reference/fetchremittancelifecyclestatus) API with additional remittance statuses in its response. The new statuses provide granular information about each state of the transaction. The new statuses are:
    
    *   `INITIATED` — This status indicates that the transaction is accepted for processing.
    *   `IN_PROGRESS` — This status indicates that the transaction is undergoing compliance review.
    *   `RFI_REQUESTED` — This status indicates that Nium's compliance has raised a request for information (RFI).
    *   `RFI_RESPONDED` — This status indicates that the customer has responded to the RFI.
    *   `COMPLIANCE_COMPLETED` — This status indicates that Nium’s compliance has completed its review and that the transaction is going to be sent to the beneficiary’s bank.
    *   `REJECTED` — This status indicates that the transaction is rejected due to compliance reasons.
    *   `SCHEDULED` — This status indicates that the transaction is scheduled and is going to be processed on the set date.
    
    The description of the new statuses is available in the `statusDetails` field of this API.

*   Added the Saudi riyal (`SAR`) currency for the Payin use case of collections and funding through an international wire transfer.

*   Electronic Know Your Business (eKYB) identification processs for onboarding US corporate customers. The eKYB check is now available for onboarding US corporate customers for clients in all countries where Nium operates. Using eKYB, corporate customers can get approved soon after submitting their application. Applicants aren't required to upload documents, making this an automated process. See the [US](https://docs.nium.com/apis/docs/us-onboarding#ekyb-flow) Corporate Customer Onboarding guide for more information about the implementation instructions of the eKYB process. Contact Nium customer support to get your template configured for eKYB to use this feature.
        
### Enhancements
    
*   The response body of the [Card Transaction Reversal](https://docs.nium.com/apis/docs/transaction-reversal) webhook event type is updated to include the notification of additional transaction reversal scenarios. We now support _transaction aging_ scenarios in addition to the _merchant reversals_.
    
*   Updates to the _Customer List_ report that can be downloaded from the UI portal
    
    *   The following fields are added to the report:
        *   Billing Country
        *   Case Id
        *   Client Hash Id
        *   Client Id
        *   Client Name
        *   Compliance Region
        *   Registered Date
        *   Segment
        *   Wallet Compliance Level
    *   The following fields are removed from the report:
        *   Compliance Profile
        *   Designation
        *   KYC Status
        *   Preferred Name
    
### API Breaking Changes
    
*   We've introduced two additional required fields for onboarding corporate customers in the US.
    
    *   `businessDetails.applicantDetails.additionalInfo.applicantDeclaration`
    *   `businessDetails.description`
    
    The required fields apply to Nium clients in all countries. Applications missing any of the required fields result in a validation error.
    
    The changes are effective **July 1, 2023**. Clients are required to collect a declaration from the applicant during the time of corporate customer onboarding for the eKYB and manual KYB processes. This update only applies to corporate customers in the US. Clients are required to show the following text to the applicant and collect a click-to-accept agreement for the declaration.
    
    _"I certify that I am the authorized representative of the customer and all information provided and documents submitted are complete and correct. I have read and accept the Nium Terms and Conditions."_
    
    After the applicant accepts the declaration, they send a `Yes` value for the below field in the [Onboard Corporate Customer](https://docs.nium.com/apis/reference/onboardcorporatecustomer) API.
    
        
          businessDetails.applicantDetails.additionalInfo.applicantDeclaration
