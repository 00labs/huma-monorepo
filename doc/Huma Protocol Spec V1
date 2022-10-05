# Huma Protocol Spec V1

## 1.0 Introduction

## Overview

Smart contracts’ transparency and automatic execution played a critical role in DeFi’s success and will continue to do so. At the same time, the lack of two of the most critical inputs for all modern risk underwriting, income (cashflow) and credit history, DeFi had to rely solely on over-collateralization of a few digital assets. This substantially limited its reach, impact, and opportunities for sustainable high yield. As such limitation becomes more and more obvious to many in the industry, under-collateralization and lending for real world use cases naturally emerges as the next frontier. \
 \
In the next decade, tens of thousands of institutions and billions of people will onboard onto web3 ecosystems. They are unlikely to have rich crypto asset portfolios initially to collateralize against, however most of them are going to be creditworthy participants looking to enrich their income portfolios.

The DeFi infrastructure for serving such participants is mostly missing today. Huma Protocol is introducing these critical DeFi infra 3 innovations to enable it :

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

## 2.0 Income Portfolio Platform

Income Portfolio Platform (IPP) provides a comprehensive view of users’ on-chain and off-chain income. It is a general framework for the community to contribute to Huma’s vision. Developers can participate in the effort by building Income Portfolio Adapters (IPAs) for various income sources. Each IPA shall understand the amount, frequency, and other objective quantities that describe the income associated with a wallet. This can include information about predicted future income from that source. This can include information about predicted future income from that source. The API interface of an IPA is covered in the technical design doc.

### 2.1 Life Cycle of an IPA

1. Developers build the IPA, conforming to IPP API and documentation guidelines, and submit it to Huma DAO for review and approval
2. Once accepted by Huma DAO, the Adapter will be deployed on IPP.
3. All the accepted IPAs will be listed under the same directory, for the Evaluation Agents(EAs)to consume.
4. Some performance stats about each IPA and share as metadata. This will be valuable to the EA developers. It will also serve as an input when Huma DAO decides how to distribute IP rewards to different IPA providers.
5. Each IPA shall be maintained by the original developer, Huma DAODAO, or the community.

### 2.2 Developer Participation and Rewards

Developers can contribute to the initial development and ongoing maintenance of the IPAs.

To bootstrap the development of IPAs, Huma will offer bounty programs via gitcoin platform or hackathons. The IPA submissions will be reviewed, and once approved, the developers will be rewarded with the bounties.

Once the protocol goes live, a portion of the protocol revenue will be carved out to reward IPA developers, who can contribute by developing new IPAs or maintaining existing IPAs. Huma DAO will review the contributions and determine how to split the total IPA rewards to different IPA contributors.

### 2.3 V1 MVP

- Publish standard interface for IPAs
- Open source sample IPA (e.g. RN)
- Publish a developer guide
- Organize all IPAs in Github for easy discovery

The following features will not be in MVP:

- IP performance dashboard (v2)

## 3.0 Evaluation Agent (EA)

EA allows Developers to build and plug in their risk management modules in Huma Protocol. Each EA implements a standard interface to interact with Huma SDK and Huma contracts.

All the EAs are expected to run off-chain considering the computational complexity involved. We do not expect EAs to be open-sourced in the foreseeable future for anti-fraud reasons.

### 3.1 EA Listing and Hosting

In the early stage, we expect each pool to have its own EA. Once the platform becomes more mature, we envision some EAs will be generic or highly configurable, and thus can be shared by multiple pools. At that stage, we will provide a dashboard of the EAs to highlight their performances to the pool owners.

The EA developers will submit EAs to Huma DAO for review. Once approved, the EAs will be deployed to a hosting platform provided by Huma. The hosting platform will be open-sourced, but we will not require the EAs to open source the EA programs themselves.

We also considered the option for EA developers to host EAs by themselves. We call this option Private EA. We decided not to support it in v1 for several reasons:

1. Significant devops workload is needed to run an EA in production. It will be a burden for the EA developers.
2. Pool owners will unlikely use a private EA in the early days. Only after some EAs proved their performance and trustworthiness, will pool owners be open to use private EAs.
3. Huma’s hosting platform will be open sourced. It is merely a supporting infrastructure. Since it does not intervene with the credit underwriting decisions, the risk for it to be viewed as overly centralized is low.

In v2, we will look to make this EA-hosting platform more decentralized.

### 3.2 EA rewards and responsibilities

EA takes a percentage of the pool income. We will call it commissionRateInBpsForEA in the protocol. It can be configured for each pool and 2000bps can be a good starting point.

EAs are required to provide meaningful contributions to the liquidity pool so that they have enough skin in the game. The percentage of EA’s contribution is governed by a configuration parameter: liquidityRateInBpsByEA, which is determined by each Pool Owner.

### 3.3 V1 MVP

- Publish standard interface for EAs
- Publish a developer guide
- Deploy Invoice Factoring EA (Note: not open source)
- Host a descriptive page on Github or Gitbooks for each EA
- Launch the EA hosting and serving platform

The following features will not be in MVP:

- EA performance dashboard (v2)

## 4.0 Lending Protocol

On top of the Income Portfolio Platform and Evaluation Agent, Huma Lending Protocol intends to provide a credit line for every wallet. Different pools can be built to leverage different income streams and for various use cases, from credit card, receivable factoring, car loan, to many other forms of lending products. The protocol shall be designed in such a way that developers and business owners outside the Huma core team can develop and launch new products on the protocol.

### 4.1 Design Principles

#### 4.1.1 Transparency & Community Confidence

Transparency is critical to building community confidence. We will operate Huma Protocol at the highest level of transparency that we can.

Since the Protocol Owner wallet has a lot of power, it will be a multi-sig wallet with signees geographically distributed.

In addition, Timelock will be used so that the community has time to react to the proposed changes to the protocol. Openzeppelin timelock can apply different delays for different actions.

#### 4.1.2 Extensibility

Huma Protocol shall be designed as a true protocol, instead of just a lending product. It shall allow developers and businesses to support new use cases by leveraging its Income Access Protocol. As a result, it should allow different pools to apply different underwriting policies and fee schedules. For example, it shall be able to support interest-only, minimal monthly payment (e.g. credit card), or installments (e.g. car loan, mortgage).

### 4.2 User Roles

There are various user roles in the protocol. Some are at protocol-level. The others are at pool-level. Let us start by studying the list of user roles and their responsibilities.

#### 4.2.1 Protocol-level Admin Roles

<span style="text-decoration:underline;">Protocol Owner**: **</span>Protocol Owner is responsible for the administration of the entire protocol. It will be a multisig. After the initial deployment, the ownership will be transferred from the deployer to this multisig protocol owner. It has the following access rights:

- The only user who can change various

<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "protocol configurations"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[protocol configurations](#heading=h.x6h4nfz0ebnv)

- The only user who can add and remove Pool Owners.
- The only user who can add and remove Pausers.
- One of the users who can pause the entire protocol.
- The only user who can unpause the protocol after it is paused by one of the pausers.
- The only user other than the pool owner who can perform admin tasks on a pool.
- The only user who can transfer protocol income from pool wallet to protocol treasury.

<span style="text-decoration:underline;">Pausers</span>: Pausers can call a pause function to pause the entire protocol. When the protocol is paused, no money moves in or out of the protocol. This is expected to happen in very rare cases, such as major security attacks, or serious security issues discovered. It is expected for the protocol to have multiple pausers, possibly including an external security monitoring firm. The only thing that a pauser can do is to pause the protocol, nothing else. After the protocol is paused, only the Protocol Owner can unpause it.

<span style="text-decoration:underline;">Protocol Treasury**:**</span> This is technically not a user. It is the wallet to hold treasury for the protocol.

#### 4.2.2 Pool-level User Roles

<span style="text-decoration:underline;">Pool Owners</span>: Pool owners are a list of addresses that are approved by the ProtocolProtocol Owner to create and manage pools. They have the following access rights:

- The only user who can set Evaluation Agent for the pool.
- The only user who can set Fee Manager to be used by the pool and configure the Fee Manager.
- The only user who can change various

<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "pool configurations"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[pool configurations](#heading=h.kpxs0t2ztpy).

- The only user who can transfer the Pool Owner’s income from the pool.

<span style="text-decoration:underline;">Evaluation Agent**: **</span>The Evaluation Agent makes underwriting decisions for a pool. Each pool can only have one Evaluation Agent. They have the following access rights:

- The only user who can approve credit requests to the pool.
- The only user who can post a pre-approved credit line to the pool contract.
- The only user who can post off-contract payments received and trigger subsequent actions by the contract.
- The only user who can transfer the EA’s income from the pool.

After the pool owner has set the evaluation agent for the pool, the EA has to deposit the required capital before the pool owner to enable the pool.

Pool owner can choose to change the evaluate agent for the pool. When this happens, all the accrued EA rewards are paid to the old EA immediately. The EA needs to have made the required deposits.

<span style="text-decoration:underline;">Liquidity Providers</span>: Liquidity Providers (a.k.a. Lenders) provide capital to the pool and expect financial returns for their investment. The only actions that they can do are depositing and withdrawing capital from the pool.

<span style="text-decoration:underline;">Borrowers**: **</span>Borrowers are the party who initiates a credit line with the pool and drawdown against the credit line. They are responsible for paying interest and minimal principal payment per pay period.

### 4.3 Protocol Administration

<span style="text-decoration:underline;">Pause Protocol</span>: At critical time, any of the pausers can pause the protocol. After a protocol is paused, it does not accept any actions that involve money flow in or out, i.e., no deposits, no withdrawals, no drawdowns, no repayments.

<span style="text-decoration:underline;">Unpause Protocol</span>: Resume the protocol operations. Only the Protocol Owner can unpause the protocol.

<span style="text-decoration:underline;">Add / Remove liquidity assets allowed</span>:This is the list of assets to be allowed as the underlying assets for pools in the protocol. We will only support stablecoins in the foreseeable future, starting with USDC.

<span style="text-decoration:underline;">Change Protocol-level Grace Period for Defaults</span>: Protocol offers the default value for the grace period for defaults. Each pool can overwrite this default value.

<span style="text-decoration:underline;">Change Protocol Treasury</span>: This is the wallet address for the protocol treasury. Only pool owner can change this address.

<span style="text-decoration:underline;">Change Protocol Fee</span>: Since Huma is a risk-on protocol, it is fair for the protocol to take a share of all the fees and interest generated in the protocol. To keep it simple, the protocol fee will simply be a percentage of all the fees and interest generated in the protocol. Initially, this Protocol Fee percentage will be configured by the protocol owner, later on, Huma DAO will take over the responsibility.

<span style="text-decoration:underline;">Add or remove pool owners</span>: Add or remove a pool owner.

<span style="text-decoration:underline;">Add or remove pausers</span>: Add or remove a pauser.

### 4.4 Pool Administration

Under Huma protocol, many pools can be created for specific business opportunities. They will attract different sets of lenders and borrowers to serve different purposes.

#### 4.4.1 Pool Initialization

When a pool is initialized, the following information shall we specified:

- Pool name: the name of the pool
- Pool token: the token that is used to track LP’s contribution to the pool. The current value of the pool token reflects the performance of the pool so far. We expect each pool to have a unique token. At the point of time, Huma view these tokens as utility tokens and does not have plan to support the trading of these tokens through DEX or other secondary market. LPs mint new tokens when they contribute capital to the pool, and burn tokens when they withdraw.
- Huma Config: Huma Config hosts all the global configurations.
- Fee Manager: A FeeManager implements all the core functions around fee calculation. Every pool can have its own FeeManager implementation.

**Question: **Who can initiate a pool? Is it the protocol owner to initiate on behalf of the pool owner or the pool owner? One thing to watch out for is the uniqueness of the pool name. Due to gas fee considerations, it is not advisable to enforce the uniqueness on-chain. It is better checked off-chain before initiating the pool on-chain. The protocol owner will be in a better position to do so. If that is the case, we may need the ability for the protocol owner to initiate the pool on behalf of the pool owner and transfer to the pool owner immediately after the initialization.

Both Pool Owner and Evaluation Agent commit to provide a certain percentage of the pool liquidity. Once the pool is initiated, once after the Pool Owner and Evaluation Agent deposit the required liquidity, the pool can be enabled by the Pool Owner to accept additional deposits from the lenders and borrowing by the borrowers.

#### 4.4.2 Pool Configurations

<span style="text-decoration:underline;">Pool Name**: **</span>Each pool needs to have a name. This name will be listed on the Huma website. We will define an off-chain workflow to make sure of the uniqueness of the pool names.

<span style="text-decoration:underline;">Underlying Token</span>: This is the asset to be used for lending and borrowing in the pool. In v1, we will support USDC only.

<span style="text-decoration:underline;">Liquidity Cap**:**</span> the cap of liquidity for the pool in the unit of underlying token. Pool owners can set and change it.

<span style="text-decoration:underline;">Pool Owner Commitment Rate**: **</span>the portion of the pool liquidity to be deposited by the pool owner. It will be represented in basis points.

<span style="text-decoration:underline;">Evaluation Agent Commitment Rate</span>: the portion of the pool liquidity to be deposited by the Evaluation Agent. It will be represented in basis points.

~~<span style="text-decoration:underline;">Min Borrow Amount</span>: The min amount that one can borrow in each borrowing transaction. This does not add much value, thus has been deleted. ~~

<span style="text-decoration:underline;">Max Credit Line</span>: The max credit line allowed by the pool. If the credit limit approved by EA is above this line, the request will be rejected.

<span style="text-decoration:underline;">Pool APR</span>: Interest rate for the pool. It is represented in basis points.

<span style="text-decoration:underline;">Origination Fee</span>: a fee to be charged when the user completes a drawdown. It can be a fixed fee or a percentage of the drawdown amount or a combination of both. In reality, we expect most pools to use a percentage. The percentage will be represented in basis points. What the borrower gets is the net of the drawdown amount and this fee.

<span style="text-decoration:underline;">Late Payment Fee</span>: a fee to be charged when the borrower is late for a payment or the payment is lower than the required due amount. The late fee can be a fixed fee or a percentage of the total outstanding balance or a combination of both. Please note when a percentage is used to calculate the late fee, the percentage is applied to the entire balance instead of the amount due. For example, if the outstanding balance is $5000 and the amount due for this cycle is $500, if the late fee rate is 1% per period, the late fee will be $50 instead of $5. If the user is late for several periods in a row. the late fee will be charged each period.

**Question: **We do not have a grace period for late fees. Shall we add? (it is kind of tricky to support it, I prefer we not to do it. In real life, there is no grace period to late fees in most cases.)

<span style="text-decoration:underline;">Membership Fee</span>: a fixed fee per pay period.

<span style="text-decoration:underline;">Required receivable rate**:**</span> The ratio between the value of the receivables and the credit limit. The ratio will be represented in basis points. There must be enough receivables deposited or making the pool the beneficiary of the receivable before the borrowers can draw down using the approved credit line.

<span style="text-decoration:underline;">withdrawalLockoutPeriod</span>: this is the period that the lender is prevented from withdrawing since its last deposit to the pool. This will be represented in seconds. The protocol will ensure it is longer than 30 days to guard pool admin from careless mistakes.

<span style="text-decoration:underline;">poolDefaultGracePeriod</span>: the grace period between the due date and the moment that a default can be triggered. Late fees will apply during the default grace period.

<span style="text-decoration:underline;">Pay Period Duration</span>: The duration for each pay period. This can be configured in days. Every borrower follows the pay period duration to calculate its next due.

<span style="text-decoration:underline;">minPrincipalRateInBps</span>: Min percentage of the principal due at each pay period. This will be represented in basis points.

#### 4.4.3 Pool Administration

<span style="text-decoration:underline;">Enable and Disable Pool</span>: Pools can be enabled when the essential configurations are setup and the required minimal liquidity has been deposited by the admins.

<span style="text-decoration:underline;">Set Evaluation Agent</span>: Set the evaluation agent

Set and update the configurations outlined in

<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: undefined internal link (link text: "the section above"). Did you generate a TOC? </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>

[the section above](#heading=h.kpxs0t2ztpy).

### 4.5 LP Participations

#### 4.5.1 Qualification

LP needs to pass KYC to participate in the pool. The process can be managed off-chain in v1. As a result, the pool owner will add LP to the pool. Only after that, the LP can deposit and withdraw.

#### 4.5.2 Deposits

LP can contribute capitals to the pool as long as it has not reached the liquidity cap set by the pool owner. There is no max or min requirement for each deposit. After each deposit, the withdrawalLockupPeriod is reset, i.e., the LP has to wait for the period defined by withdrawalLockupPeriod before withdrawal.

#### 4.5.3 Withdraw

Once the withdrawalLockupPeriod is passed, the LP can choose to withdraw from the pool. The LP can choose to withdraw a portion or the entire withdrawable amount.

**Questions: **

1. TruFi uses cooldown. The lender can propose a withdrawal. Then the counter of cooldown starts. Only after the cooldown period is over, can the lender withdraw. TruFi also implemented an exit fee concept. The exit fee varies depending on the liquidity in the pool. When there is lots of liquidity, the exit fee is low. When liquidity is tight, the exit fee is hiked. Which one is better? withdrawalLockupPeriod better or cooldown + exit fee? I think withdrawalLockupPeriod might be better than cooldown since it provides better certainty to the protocol on the lender’s commitment. I also think exit fees are a great concept from a pool stability perspective, but not very friendly to the lenders. I recommend we launch with withdrawalLockupPeriod only. We can add a variation of exit fee in v2.

#### 4.5.4 Income and Losses

Please see section xxx for more detail.

### 4.6 Borrowing

#### 4.6.1 Credit Line

What Huma offers to the borrowers are credit lines. Based on the information that the Evaluation Agent can gather about the account, it approves a credit line with a credit limit. After the approval, the borrower can drawdown or payback at any time that they want as long as the total outstanding balance is below the credit limit.

EA can update the terms of the credit line for various reasons. Some sample reasons are massive changes to the external environment, or changes to the borrower’s financial situation, or algorithm enhancements.

In Web3, it is preferred for the users to initiate any actions rather than the protocol. We want to give EA the power to change the terms of the credit line before a new drawdown, at the same time, it suits Web3 pattern better if this process is triggered by the users. Instead of having EAs periodically update the terms of the credit lines, we can allow the users to get the latest terms of their credit line before requesting a new drawdown. This will prompt the EA to run its algorithm and update the contract with the latest terms.

#### 4.6.2 Interest Rate

Each credit line has its personalized interest rate. The Evaluation Agent will consider each account’s credit history and income stability to determine the interest rate.

This rate can be changed by the Evaluation Agent. Since it is a credit line, the new interest rate will apply to both the existing balance and new drawdowns. The rate change will take effect starting from the next pay period, thus, there is no change to the due amount to the current pay period.

**Question: **Do we want to put a timeline for the user to initiate the first drawdown? Once past this timeline, withdrawals will be rejected

#### 4.6.3 Payments Per Cycle

The amount due for each pay period is calculated using the following formula:

Amount Due = Late Fee + Interest Fee + Principal Due

Late fee will be charged if the full amount due from the last pay period is not paid in full by the end of the pay period. First, the remaining amount due is added to the outstanding balance. Then the following formula is used to calculate the late fee.

Late Fee = Flat Rate + Percentage Rate \* Total Outstanding Balance.

Interest Fee is computed using the following formula. The corrections are introduced to reflect additional drawdown or principal payment during the middle of the pay period. For example, if there is a drawdown in the middle of the cycle, the Total Outstanding Balance at the end of the pay period is higher than the actual balance in part of the pay cycle, thus the interest fee will be overly charged, thus a negative correction shall be applied. Similarly, when there is a payment towards principal, the Total Outstanding Balance at the end of the cycle gets lower, the interest fee is thus under accounted for, thus a positive correction amount.

Interest Fee = Total Outstanding Balance _ APR _ Seconds in a Pay Period / Seconds in a year + Corrections

Principal Due is the product of Total Outstanding Balance and the min principal payment rate.

Please note in solidity, all divisions round to zero. We will round Late Fee, Interest Fee, and Principal Due separately. For example, if Late Fee is 3.3, Interest Fee is 2.9, Principle Due is 4.9, the Amount Due is 9, instead of 11.

### 4.7 Risk Management

#### 4.7.1 Underwriting Decision

EA takes the borrowers’ income portfolio, credit history, and other factors to decide if to approve a credit line, the credit limit to be approved and the interest rate for the credit line.

In v2, the performance of each EA, including approval rate and risk loss rate, will be available for the Pool Owner to review.

#### 4.7.2 Default flow

Each pool can define a default grace period, which is a multiple of the pay periods. Once the grace period has passed, if the borrower still has not paid the amount due yet, the default process will be triggered. The entire balance including principal, interest, and fees, including the fees and interest accrued during the grace period, will be written off as losses. The losses will be distributed to the LPs per their shares of the liquidity pool.

To be explicit, the protocol, pool owner, and EA themselves do not share the losses, however, since Pool Owner and EA have contributed as a LP, they will share the losses in the same way as any other LPs.

Once the default is triggered, the balance is written off and the accounting should follow accordingly.

At the same time, the borrowing record will still be open and the borrower still has a chance to make payment towards the balance due. This is unlikely to happen, all the payments will be considered as income to the pool and follow the income distribution process.

### 4.8 Income and Loss Distribution

The protocol defines a percentage of all pool income that goes to the protocol treasury. Huma DAO will then decide how to distribute the income. We know a portion of it will go to the IPA

developers.

For any pool income, it will allocate the portion for the protocol first, and distribute the remainder to the pool. For the portion allocated to the pool, it will first distribute the commission to the EA. The remainder will be distributed to all the LPs per their share of ownership of the liquidity pool.

For the amount allocated for the protocol, to avoid unnecessary gas waste, it will not be moved to the protocol treasury immediately. it will be kept in the pool wallet but with a clear record. The protocol owner can trigger the withdrawal any time and resulting in an immediate transfer.

The same process applies to the commission fee for the EAs. It will be kept in the pool wallet with a clear record and the EA can trigger a transfer at its sole discretion.

### 4.9 Upgradability

We expect the core contracts continue to evolve, thus upgradability is critical for key contracts.
