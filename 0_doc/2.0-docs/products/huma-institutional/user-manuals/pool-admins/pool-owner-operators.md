## Pool Owner and Pool Operators

Pool Owners are participants authorized by the Protocol Owner to create and manage pools. As a Pool Owner, you have the ability to set key parameters, select the Evaluation Agent, and define the fee structure through the Fee Manager. You may delegate some administrative tasks to chosen Pool Operators, such as approving and removing lenders or disabling the pool.

### Pool Configuration

A significant aspect of the Pool Owner’s role is setting the various parameters of a pool before its launch and updating configurations as necessary when the pool evolves. You can find the complete list of pool parameters in the `PoolConfig` contract here (a link to the code will be provided upon the publication of the repo). The protocol provides default values for some parameters, but you must supply values for others before enabling the pool.

**Pool Settings**

- `maxCreditLine`: This refers to the maximum credit line for a borrower, which is measured in terms of pool tokens.
- `minDepositAmount`: This is the minimum amount a lender or First Loss Cover provider must supply each time they deposit. It is also the absolute minimum balance the pool owner needs to maintain in tranches to prevent inflation attacks.
- `payPeriodDuration`: This parameter refers to the number of months in a single payment period.
- `latePaymentGracePeriodInDays`: This refers to the grace period, in days, before a late fee can be charged.
- `defaultGracePeriodInDays`: This is the grace period, in days, before a default can be triggered. It can be 0.
- `advanceRateInBps`: This specifies the maximum credit line as a percentage (in basis points) of the receivable amount. For example, for a receivable of $100 with an advance rate of 9000 basis points, the credit line can be up to $90.
- `receivableAutoApproval`: This parameter indicates whether receivables should be automatically approved during the initial drawdown. If set to `false`, then receivables must be approved before the first drawdown.

**AdminRnR Settings**

These settings outline the responsibilities and rewards for pool administrators:

- `rewardRateInBpsForEA`: The percentage of pool income allocated to EA.
- `rewardRateInBpsForPoolOwner`: The percentage of pool income allocated to the Pool Owner.
- `liquidityRateInBpsByEA`: The percentage of the `liquidityCap` contributed by the EA in the junior tranche.
- `liquidityRateInBpsByPoolOwner`: The percentage of the `liquidityCap` contributed by the Pool Owner in the junior tranche.

**Front Loading Fee Structures**

- `frontLoadingFeeFlat`: This is a part of the platform fee, charged as a flat amount when borrowing occurs.
- `frontLoadingFeeBps`: This is also a part of the platform fee, but it's charged as a percentage of the amount borrowed.

**Fee Structures**

- `yieldInBps`: This represents the expected blended yield for the entire pool in basis points. Please note that individual credits in the pool may have different yield rates, as approved by the Evaluation Agent.
- `minPrincipalRateInBps`: This is the minimum percentage of the outstanding principal to be paid in each statement period.
- `lateFeeBps`: This is the late fee rate, expressed in basis points. The late fee is an additional charge applied when a payment is late. It's calculated as a percentage of the total outstanding balance.

**Tranche Configuration**

The following configurations govern the tranches in a pool:

- `liquidityCap`: This is the maximum amount of liquidity that can be deposited into the pool. The pool value may exceed this cap due to yield income. However, LPs cannot deposit more into the pool once the liquidity cap has been reached.
- `maxSeniorJuniorRatio`: This is the maximum senior-to-junior asset ratio allowed. The senior assets cannot be more than the product of the junior assets and this ratio. A ratio of zero suggests a uni-tranche setup where only the junior tranche is enabled.
- `fixedSeniorYieldInBps`: This is the fixed yield rate for the senior tranche. Pools using the `FixedSeniorYieldTranchesPolicy` must set this value and leave the risk adjustment rate setting at 0.
- `tranchesRiskAdjustmentInBps`: This rate dictates how much profit will be shifted from the senior tranche to the junior tranche. Pools using the `RiskAdjustedTranchesPolicy` must set this value and leave the fixed senior yield rate setting at 0.
- `withdrawalLockoutPeriodInDays`: This is the lockup period for lender withdrawal. Lenders cannot withdraw until this lockup period has passed after their most recent deposit.

**First Loss Cover Configuration**

The following configurations are supported for each layer of first loss cover:

- `coverRatePerLossInBps`: This indicates the percentage of the defaulted asset covered by the first loss cover.
- `coverCapPerLoss`: This is the maximum amount the first loss cover provides when a loss occurs.
- `maxLiquidity`: This is the maximum amount for this first loss cover. Once this value is reached, no more coverage can be deposited into this layer of first loss cover.
- `minLiquidity`: This is the minimum amount for this first loss cover. The pool cannot be enabled until this coverage is met.
- `riskYieldMultiplierInBps`: This parameter is a weighting factor that helps establish the yield for the first loss cover. All layers of first loss covers share the yield with the junior tranche. The liquidity in each layer is multiplied by this risk yield multiplier, and the results are added together (the multiplier for the junior tranche is 10,000), resulting in the total capital participation in yield distribution. Keep in mind that the value of this parameter can either be higher or lower than 10,000, and in certain cases, it can be 0. For example, the borrower's cash collateral does not participate in the yield distribution, so the risk yield multiplier for this layer of first loss cover is set at 0.

### First Loss Cover and Tranche Liquidity Requirements

Before a pool can be enabled, the Pool Owner must meet certain liquidity requirements in the tranches and the admin's first loss cover. More specifically:

- Both the Pool Owner and Evaluation Agent must together deposit at least the amount outlined by the "min liquidity" parameter of the admin's first loss cover.
- The Pool Owner is required to deposit at least the amount indicated by the "liquidity rate by pool owner" parameter into the junior tranche.
- For a multi-tranche pool, the Pool Owner must also deposit at least the amount specified by the "min deposit amount" parameter, as a prevention measure against inflation attacks.

### Enabling and Disabling A Pool

The Pool Owner can enable a pool once all required parameters are set, and liquidity and first loss cover requirements are fulfilled. The pool is considered live and begins to accept lender deposits once enabled.

Either the Pool Owner or Pool Operators can disable a pool. A pool may be disabled in the event of extraordinary circumstances, such as a default. Most contract functions will be disabled when the pool is disabled. For instance, the borrower can no longer draw down or make payments, and lenders cannot deposit or request redemptions.

### Lender Eligibility Management

The eligibility of lenders to participate in the pool is managed by the Pool Operators as follows:

- Adding lenders: Pool Operators review the KYC/KYB and accreditation results, as well as the legal documents signed by potential lenders. They can then add these individuals as approved lenders in the contract. During this process, Pool Operators decide whether the lender will receive automatic yield distributions or reinvest their yield back into the pool.
- Removing lenders: Pool Operators also have the ability to remove lenders from a pool, preventing them from making additional deposits.
- Setting the "reinvest yield" option: Pool Operators can adjust the "reinvest yield" setting for approved lenders.

### Pool Fee Management

The Pool Owner, the Evaluation Agent, and the Protocol Owner all earn a portion of the pool yield as their income. The Pool Owner and Evaluation Agent's incomes are determined by the `rewardRateInBpsForPoolOwner` and `rewardRateInBpsForEA` parameters in `PoolConfig`, respectively, and can be controlled by the Pool Owner. The Protocol Owner's income is defined by the `protocolFeeInBps` parameter in `HumaConfig` and can only be set by the Huma protocol owner.

### Closing A Pool

The Pool Owner is responsible for closing the pool after its maturity, allowing lenders and first loss cover providers to withdraw their funds without needing to submit redemption requests. This can be done by calling the `closePool()` function on the `Pool` contract. Before closing the pool, ensure that the yield is distributed to lenders by executing the `processYieldForLenders()` function in each `TrancheVault` contract.
