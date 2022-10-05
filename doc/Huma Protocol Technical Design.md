# Huma Protocol Technical Design

Last updated: Oct. 1, 2022

## Overview

DeFi sparked the last crypto summer. Smart contracts’ transparency and automatic execution played a critical role in DeFi 2.0’s success. We expect the transparency and automatic execution will continue in DeFi 3.0. At the same time, because of a lack of support of income and credit history, two of the most critical inputs for all modern risk underwriting, DeFi has to rely heavily on over-collateralization. This substantially limited its reach and impact. As the limitation of over-collateralization becomes more and more obvious to many in the industry, under-collateralization naturally emerges as the next frontier. We expect the industry to emerge from the current crypto winter with key breakthroughs in this space.

Recognizing the reason that DeFi relies heavily on over-collateralization is because of a lack of essential infractures, in Huma, we focus on building these critical DeFi infrastructures through Huma Protocol and enable various lending products to be launched to serve millions of users. Let us first take a quick lookup at these critical building blocks and how Huma Protocol innovates on all of them.

### Our Belief:

We believe the future of DeFi is automated underwriting powered by signals about the borrowers’ AWC (Ability, Willingness, and Commitment) to pay.

- **Income**: Income is probably the most vital signal in most underwritings since it offers the best measure against <span style="text-decoration:underline;">one’s ability to pay</span>. The more comprehensive we can understand one’s income, the better we can underwrite.
- **Credit worthiness**: Credit worthiness is probably the best signal for <span style="text-decoration:underline;">one’s willingness to pay</span>. Web2’s credit score plays an important role, but it is more like a blackbox. The central agencies have way too much power. We need a decentralized credit system.
- **Receivables**: Receivables are proof of future income stream. Compared with collaterals, receivables are more accessible to most people. Not too many people have tons of crypto idling, but most people have receivables in the form of future paychecks, invoices, royalty, subscription income, etc. Receivables are the best signal for <span style="text-decoration:underline;">one’s commitment to pay</span>. Once someone transfers the ownership of their receivables to the lending platform, they are committed to pay. We actually think collaterals are just special forms of receivables. The only difference is that their cash value is available right now instead of at a future date. A good receivable platform should be able to embrace collaterals as well.
- **Automated risk underwriting** (ARU) - Most of Web2 credit applications are approved in an automated fashion. All the major DeFi protocols are built on AMM. We expect this to continue. However, it is a lot more complicated to support ARU in a risk-on world than a risk-off world. The ARUs are intelligent models. By nature, AI will find its role in the ARUs. At the same time, these ARUs will not be possible without additional data (e.g. income, credit scores). So please read on.

### Huma’s Technical Bets:

Figure 1 shows a high-level overview of Huma Protocol:

- Income Portfolio - It is a comprehensive view of users’ Web3 and Web2 income. Income Portfolio Adapters (IPA) can be developed to capture income from Web3 income sources such as on-chain payments, staking, mining, NFT royalty, Web3 payroll, to Web2 sources. The Income Portfolio Platform is built in such a way that any developers in the community can contribute and share the upside of the IPAs. Please refer to &lt;<IPA Developer Guide>> for more information.

<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline drawings not supported directly from Docs. You may want to copy the inline drawing to a standalone drawing and export by reference. See <a href="https://github.com/evbacher/gd2md-html/wiki/Google-Drawings-by-reference">Google Drawings by reference</a> for details. The img URL below is a placeholder. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![drawing](https://docs.google.com/drawings/d/12345/export/png)

- Receivable Management - We have developed infrastructures to allow receivables to be captured in the form of NFTs, transferred, and used to secure credit borrowing.
- Evaluation Agent - This is an open platform for developers to contribute various risk underwriting models. Please refer to &lt;<Evaluation Agent Developer Guide>> for more information.
- Aura - This is a placeholder for capturing, reporting, and leveraging credit trustworthiness. This is not in scope for our v1 protocol. In v2, we will either compose a decentralized credit system or work with a consortium of innovators to define the new credit standard for Web3.
- Lending Protocol - This is a generic lending pool. It is designed to suit a broad range of use cases from receivable refactoring to general credit line. Please refer to &lt;<Huma Lending Protocol Technical Design>> for more information.

### Interaction between Components

Income Portfolio works relatively independently. Following the &lt;<IPA Developer Guide>>, developers can submit IPAs for approval. Once an IPA is approved by Huma DAO, it is available for Evaluation Agen developers to consume.

Auro works fairly independently as well. It acts on events emitted by Huma and other protocols and makes decisions on one’s credit worthiness.

Evaluation Agent (EA) makes underwriting decisions using signals from Income Portfolio and Auro. It leverages input from the Income Portfolio and Auro. It also factors in receivables that are available in different use cases in the models. Similar to the IPA platform, the EA platform is open to various entrepreneurs and developers. They can build powerful underwriting engines for specific use cases and launch with different liquidity pools.

Huma Lending Protocol interacts with the liquidity providers and the borrowers in a similar way as other DeFi protocols. The borrowers interact with Huma DApp or a partner’s DApp via Huma SDK to submit credit requests, drawdown, and payback. There are two differences from today’s common DeFi protocols. First, the borrowers will leverage many forms of receivables instead of the collaterals. Secondly, the DApp will talk to the Evaluation Agent to get the credit request approved instead of interacting with the contract directly. Since the Evaluation Agent is designed to make real-time decisions, there is very little difference to the end users.

## Huma Lending Protocol

Huma Lending Protocol offers a great level of flexibility as it strives to support a wide range of use cases, including credit line and receivable factoring (please refer to Appendix A for introduction about credit line and receivable factoring). In this section, we will first look at the overall contract architecture, then look at Fee Manager to examine how Huma is able to or be extended to support various use cases, followed by risk management, security, upgradability, gas, and contract size management.

### Contract Architecture

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image1.png "image_tooltip")

Huma Distribution Token (HDT) is used to track LPs’ deposits and ownership of the pool.

At the core of the protocol are the pool contracts:

- Interface IPool defines some pool administrative functions.
- Interface ILiquidityProvidrer defines functions for liquidity providers, from deposit to withdrawal.
- Interface ICredit defines the borrowing functions, from drawdown, payback, to default.
- Interface IReceivable defines the special functions related to receivables.
- BasePool is an abstract contract with all the functions related to token distribution, administration, and liquidity providers.
- BaseCreditPool is the core pool contract. It extends BasePool and implements ICredit. We expect most pools on Huma protocol to be running on BaseCreditPool.
- ReceivableFactoringPool is the special contract for receivable factoring. It extends BaseCreditPool and supports functions related to receivables.

BaseFeeManager, BasePoolConfig, HumaConfig and EvaluationAgentNFT are important supporting contracts.

- BaseFeeManager implements all the functions related to fee settings and calculations.
- BasePoolConfig manages all the configurations specific to a pool. Technically, all the functions can reside in BasePool as well. They are separated into this contract purely because the contract size for BaseCreditPool is getting close to Ethereum’s 24K contract size limit.
- HumaConfig manages all the configurations at the protocol level.
- EvaluationAgentNFT is a utility NFT that we have developed to manage the evaluation agents. Every evaluation agent is represented as an NFT in Huna Protocol.

The two storage contracts, HDTStorage, and BaseCreditPoolStorage are for upgradability. We will discuss in section x.

### Fee Calculation and Management

#### Extensible Fee Manager

Given that Huma would like to be a generic protocol, we would like to make the fee management as flexible as possible so that it can power a wide variety of credit products. Let us first examine a few common use cases:

1. In a typical credit line such as a credit card business, there is interest represented by APR, late payment fees, and optionally an annual fee. There is typically no fee to apply to cancel a card.
2. In an invoice factoring case, there is usually a factoring fee, charged at the beginning or when the invoice is fully paid. There is typically no interest charge.
3. In most cases, from a credit card to mortgage, in addition to the interest charges, it is required to pay a percentage of the principal in each pay cycle as well. At the same time, some business loans are interest-only. This is to make it easier for businesses to manage their cash flow.

From these use cases, we can see the following give commonly constructs in a bill:

1. Interest charge: It is often measured by an APR.
2. Front-loading fee (a.k.a. origination fee): It is charged when the borrower makes a drawdown after the credit approval.
3. Late fee: It can be a flat fee, which happens more often in consumer use cases such as credit cards, or a percentage of the outstanding balance, which happens more often in business borrowings since a $29 flat fee may not mean much for a businesses who borrow millions of dollars.
4. Membership fee: a monthly or annual fee.
5. Principal payments: This can be a percentage of the outstanding principal balance.

To meet our needs to be flexible with various fee and payment options, we allow each pool to have its own FeeManager. A BaseFeeManager is provided with build-in support for all 5 types of payments listed above. If this is still insufficient to meet the needs of a pool, a new fee manager can be developed to extend BaseFeeManager and add additional functions. For example, installments are not currently supported by BaseFeeManager, it is relatively straightforward to build one, which we plan to add when such a use case emerges.

#### Bill Triggering

With Web3, we prefer users to trigger transactions if we can. So for most cases, we wait for the user to trigger the bill. Only when the user is late, we use Sentinel, a service that monitors account activities through events, to refresh the account. When the account is so late that it has passed the grace period for account default, Sentinel can trigger default as well. More details on Sentinel can be found in section x. This means the bill may not be computed exactly at the anniversary of the pay cycle. It is possible the bill is not refreshed for multiple months if there were no activities on the account.

#### Bill Calculation

The billing anniversary is set when the first drawdown happens. The bill is computed from the beginning of each pay period whenever the bill is triggered. This means the user might be over-paying interest if the payment is made before the end of the pay period. We introduced a correction concept to capture this kind of adjustment. When a payback happens before the due date, the user has paid more than the actual interest cost, there will be a negative correction. Similarly, when the user makes an additional drawdown during the middle of the cycle, we compute a positive correction. Both positive and negative corrections will be applied in the next bill. Please refer to Appendix B for the algorithm for computing amount due for each pay period is Appendix B.

### Credit Line State Management

We introduced the following states for a credit line. The diagram below is the state transition diagram.

###

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image2.png "image_tooltip")

- Requested
- Approved
- GoodStanding
- Delayed
- Defaulted
- Deleted

The credit line is in Requested state once created. After approval, it transitions to the Approved state. A credit line can be created in two ways. One way is for the borrower to submit a request, and approved by the Evaluation Agent by calling the approveCredit() function in the pool contract. This flow is easier when there is no need to evaluate the value of a collateral. The other way is for the borrower to submit a credit request to the Evaluation Agent via a DApp. The Evaluation Agent approves the request and calls the pool contract’s postApprovedCredit() directly. This path is used when receivables are involved so that the Evaluation Agent can decide the credit line by considering income, credit worthiness, and receivables.

Once the borrower finishes the first drawdown, the credit line will be transitioned to GoodStanding state. If the borrower continues to pay on time, it will stay in GoodStanding state until the credit line reaches its maturity, when the credit line is transitioned to Deleted state after the balance is paid off.

When a credit line is late for payments, it is moved to Delayed state. Once the due amount is paid, it will be moved back to GoodStanding again. If there is not enough payment for the entire duration of a default grace period, the account can be defaulted. If default is triggered by the pool owner, it will be transitioned to Defaulted state. At that moment, the contract will automatically write off all the outstanding balances including principal, interest and fees. The borrower can still make payment even after the account is defaulted. Once the entire due amount is paid, the account can be brought back to GoodStanding.

One special case is that the Evaluation Agent can decide to stop the credit line by changing the credit limit to 0 at any time. If there is no outstanding balance, the credit line will be moved to Deleted state. If there are outstanding balances, the credit line will be changed to 0 and the borrower will not be able to draw down anymore, but they can still pay back.

There are several special cases in the state transitions, either due to the limitation of Solidity or business requirements.

### Sentinel Service

With our design so far, we update the user account whenever users take actions on the account. There are several needs that the contract needs to be triggered.

- Refresh the account when the user is late. This is necessary so that we can bookkeeping the balances for the LPs correctly.
- Trigger default when the account has passed the default grace period.
- Let the contract know a payment related to a collateral has been received.

Sentinel Service monitors our own subgraph and partners’ subgraphs, calls the contracts when any of the conditions are met.

[design doc](https://docs.google.com/document/d/1nxzVGVjMzk_LnsSznc5GRt80pgZNuIcKaHuoHZShasY/edit#heading=h.d0lh7ix9lw8v)

### Error Handling

We use Solidity’s _custom error_ pattern in the entire code base. Errors.sol defines all the errors. In the contracts, whenever an error condition is met, it is reverted with the right error. This pattern enabled us from using a commonly used require approach. The error text in the _require_ statement will meaningfully increase the contract size.

```
contract Errors {
   error creditExpiredDueToFirstDrawdownTooLate();
}
…
contract BaseCreditPool {
    if (cr.dueDate > 0 && block.timestamp > cr.dueDate)
        revert Errors.creditExpiredDueToFirstDrawdownTooLate();
}
```

The above code snippet shows the power of custom error. The error name can be as descriptive as you want, but it only takes 4 bytes since internally it will be compiled as a function selector. This allows us to achieve the same goal in a much more contract size efficient way. In addition, it offers the benefit of having a clear list of all errors in the contracts.

### Upgradability

We choose to support upgradability. After evaluating different upgrade patterns, we have decided to use the transparent proxies pattern for its simplicity and relatively small impact on gas and contract size. [UUPS](https://blog.logrocket.com/using-uups-proxy-pattern-upgrade-smart-contracts/) offers ultimate removal of upgradability, but it is a lot more complicated and has a bigger impact on contract size.

We have decided to make BasePool and HDT upgradable. Since all the other contracts such as HumaConfig, BasePoolConfig, and BaseFeeManager are composed into BasePool, if it is essential to upgrade these contracts, we can deploy an updated version and reset to have the pool to use these new contracts, following the community transparency policy that is covered in Section x.

### Testing

The tech stack use Hardhat, Ethers, and Web3py. We require 95%+ testing coverage for the smart contracts.

### Security and Risk Considerations

#### Contract Audit

We plan to have two audits. The first audit happens before our Beta launch with liquidity provided by Huma and its equity investors. After running the protocol in Beta mode for at least 3 months, we will engage with a second auditor. Only after then, we will open the protocol to public pool owners and liquidity providers.

#### Protocol Multisig and Timelock

The protocol owner account must be a multisig with at least 3 signatures. Any actions with protocol changes except pausing at emergency will be governed by Timelock so that the community has the full transparency on any changes to the protocol in advance.

#### Pool Owner Multisig

Each pool owner is required to be a multisig. Initially, Huma will hold one of the signatures. Once the platform becomes more stable, the pool owners themselves can own all the signatures.

#### Security for Service Accounts

The protocol uses two service accounts:

- eaServiceAccount: For security consideration, Huma will host the EAs initially. This means all the approvals will be initiated from a service account.
- pdsServiceAccount: Sentinel uses this service account to interact
- AWS Key Manager will be leveraged to store the

#### Capital Commitment by Pool Owner and Evaluation Agent

Each pool requires the Pool Owner and Evaluation Agent to deposit enough capital to the pool with a percentage of the pool’s liquidity cap before the pool can be enabled to accept investment from other LPs. When the Pool Owner or Evaluation Agent withdraws from the pool, the contract enforces them to meet the capital commitment, otherwise, the withdrawal will be reverted. As a result, the Pool Owner and Evaluation Agent will be the last two parties to exit the pool.

#### Security Bug Bounty

We will work with Security Bug Bounty programs to get help from the community.

#### Credit Risk

The Evaluation Agent manages the credit risk. We will have a separate chapter for this topic.

## Invoice Factoring Service

### Architecture

For a receivable factoring to work in Web3, we need to tokenize the receivable and NFT is a natural choice. We are working with partners to tokenize the receivables. The users are presented with the option to get paid now. Once the user selects to do so, the Evaluation Agent will determine the credit line that the receivable factoring pool on Huma can offer to the user. If the user is happy to proceed with the factoring, they can choose to draw down partial or the entire approved amount. Huma smart contract will accept the transfer of the NFT and fund the user. Once the receivable is paid, the receivable processor will direct the payment to the NFT owner, in this case, the receivable factoring pool on Huma. Sentinel monitors the subgraph of the receivable processor and notifies the contract about the received payment. The contract will then disperse the remainder of the fund to the user.

The sequence diagram below shows the flow. Step 10-90 shows the request and approval process. Step 210-240 shows the actual factoring and funding process. Step 300-340 illustrates the payment flow. Step 400 shows the default flow when a payment is not received by the end of default grace period. Step 500-530 (not included in v1) shows how Huma protocol interacts with Aura on credit reporting.

​​

<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image3.png "image_tooltip")

### SDK

To enable more partner sites to take advantage of Huma’s Get Paid Now capabilities, Huma has provided a SDK for the partners’ DApp to use. Core functions in the SDK include:

- Call read-only functions of the contracts to provide interest and fees to the user
- Interact with Evaluation Agent to submit factoring requests and seek approval
- Interact with the contracts to enable NFT transfer and funding for the factoring.

## Income Portfolio

Please refer to &lt;<IPA Developer Guide>>

## Evaluation Agent

Evaluation Agent (EA) is a process that evaluates each credit line request using signals from IPAs, receivables, and Aura. A typical EA is an underwriting strategy in the form of rule-based engines or Machine Learning(ML) models. Huma pool owners select EA for their pools. The selected EA must make the required liquidity contribution to the pool.

### EA description

Each agent has the following properties:

- Id (will be a path to trigger evaluation)
- Name
- Description: Owner’s description of the EA
- Owner wallet address: To receive rewards
- Style: Automatic/manual
- Authorized EA wallet
- Performance
  - Historical performance in pools
  - Backtesting performance
  - Expected performance
- Stats
  - Usage
  - Last updated
  - Voting stats
- IP inputs

### EA experiences

#### EA experience for developers

1. Checkout EA GitHub repo, which has a template for building an EA
2. Develop their own EA
3. Register their EA with their own wallet address
4. Collaborate with Huma DAO to get EA approved
5. Launch the EA in Huma infrastructure
6. Get selected by pool admins
7. Get rewards

<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image4.png "image_tooltip")

#### Pool admin experience

1. Browse EA descriptions
2. Select an EA for the pool
3. Config pool with EAID and authorize EA

<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image5.png "image_tooltip")

### Design

<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image6.png "image_tooltip")

#### Huma hosted EA

To simplify developers’ efforts and enhance secret management, Huma runs EA infrastructure to host all EAs. Developers can submit their EA code to Huma DAO for approval to create new EAs. Huma’s wallet signs transactions between EA and Huma pool.

For reasons such as confidentiality of evaluation strategy, anti-fraud, etc. Only EA developers and Huma have access to EA source code.

#### Manual EA

For some use cases, the EA could be manual-reviewed based, e.g. business lending, our protocol also supports manual EAs to enable these use cases.

For manual EAs, borrowers request manual reviews and the manual EAs (authorized by the pool admins by their wallet address) post approval results to the pool contract.

#### EA registry

A contract that maps an EAID to its corresponding descrition data. When an EA developer registers a new EA, they need to interact with the contract to sign, so their wallet address is verified.

### EA Serving Flow

When a credit approval request comes from Huma SDK, EA reacts by fulling the following tasks:

- Take context(including pool address) from SDK
- Retrieve pool info (including EAID) from the pool
- Trigger the corresponding EA for approval
- If approved, call functions in the pool to record approved credit
- Return results to SDK

<p id="gdcalert8" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert9">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

![alt_text](images/image7.png "image_tooltip")

### Interaction with the smart contracts

We will create an NFT contract to represent the collection of EAs. Each EA will be an NFT.

EA NFT can be minted by TBD (protocol owner vs. end user). Each EA NFT will have a status (Developer vs. Production) that will be displayed. We will disable all functions related to the transfer so that people cannot obtain EA status through transfers.

The wallet address of the EA NFT owner will be the only wallet that can receive EA rewards. The EA NFT tokenid will be the EA identifier used in our system.

When pool owner decides which EA to use, BasePool.setEvaluationAgent(address eaAddress, uint256 tokenId) will be called to register EA wallet and EA tokenid.

Because we only support hosted EA, a Huma service account _eaServiceAccount_ will be used to call the pool contracts to approve credit lines. \_eaServiceAccount \_and the EA NFT contract address will be stored in HumaConfig. BasePool.getPoolSummary() will also be updated to return the EA ID for the pool as well.

We debated whether to use the same service account for Payment Detection Service. We decided to use two accounts. One of the key considerations is if we use the same service account, if it is compromised, the hacker can approve the credit line and mark it as paid to make everything look very normal and more difficult to discover. The service account for Payment Detection Service will be called _pdsServiceAccount_, which will be stored in HumaConfig as well.

## Appendix A: Intro to Credit Line and Receivable Factoring

### Introduction to Credit Line

A [credit line](https://www.investopedia.com/terms/l/lineofcredit.asp) is a preset borrowing limit that can be tapped into at any time. Credit line comes with a lot of built-in flexibility. The borrower can borrow, payback, and borrow again as needed. Credit line can be secured (e.g. backed by receivables) or unsecured (e.g. credit card). Credit lines can be resolving and non-revolving. In a revolving credit line, the borrower can

### Introduction to Receivable Factoring

Invoice factoring is a way for businesses to fund cash flow by selling their invoices to a third party (a factor, or factoring company) at a discount. Typically, the invoice owner will get paid 80% of the value of the invoice. When the invoice is paid, the invoice owner will be paid for the remainder of the invoice. There is a 3-5% factoring fee, charged either at the beginning of the factoring or when the invoice is paid.

## Appendix B: List of Events

<table>
  <tr>
   <td>Contract Name
   </td>
   <td>Events
   </td>
  </tr>
  <tr>
   <td>BaseCreditPool
   </td>
   <td>BillRefreshed(address indexed borrower, uint256 newDueDate, address by)
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>DrawdownMade(
<p>
        address indexed borrower,
<p>
        uint256 amount,
<p>
        address by,
<p>
        address receivableAddress,
<p>
        uint256 receivableParam
<p>
    )
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>PaymentMade(address indexed borrower, uint256 amount, address by)
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>DefaultTriggered(address indexed borrower, uint256 losses, address by)
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>CreditApproved(address indexed borrower, address by)
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>CreditInitiated(
<p>
        address indexed borrower,
<p>
        uint256 creditLimit,
<p>
        uint256 aprInBps,
<p>
        uint256 payPeriodInDays,
<p>
        uint256 remainingPeriods,
<p>
        bool approved
<p>
    )
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>CreditLineClosed(address indexed borrower, address by)
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>CreditLineChanged(
<p>
        address indexed borrower,
<p>
        uint256 oldCreditLimit,
<p>
        uint256 newCreditLimit
<p>
    )
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>CreditLineExtended(
<p>
        address indexed borrower,
<p>
        uint256 numOfPeriods,
<p>
        uint256 remainingPeriods,
<p>
        address by
<p>
    )
   </td>
  </tr>
  <tr>
   <td>ReceivableFactoringPool
   </td>
   <td>ExtraFundsDispersed(address indexed receiver, uint256 amount);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>ReceivedPaymentProcessed(
<p>
        address indexed sender,
<p>
        address indexed borrower,
<p>
        uint256 amount,
<p>
        bytes32 paymentId
<p>
    );
   </td>
  </tr>
  <tr>
   <td>BasePool
   </td>
   <td>event LiquidityDeposited(address indexed account, uint256 assetAmount, uint256 shareAmount);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>event LiquidityWithdrawn(address indexed account, uint256 assetAmount, uint256 shareAmount);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>event PoolInitialized(address _poolAddress);
<p>
    event PoolCoreDataChanged(
<p>
        address indexed sender,
<p>
        address underlyingToken,
<p>
        address poolToken,
<p>
        address humaConfig,
<p>
        address feeManager
<p>
    );
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>PoolConfigChanged(address indexed sender, address newPoolConfig);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>PoolDisabled(address by);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>PoolEnabled(address by);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>AddApprovedLender(address lender, address by);    
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>RemoveApprovedLender(address lender, address by);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>IncomeDistributed(address indexed by, uint256 fundsDistributed);
   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td>LossesDistributed(address indexed by, uint256 lossesDistributed);
   </td>
  </tr>
</table>
