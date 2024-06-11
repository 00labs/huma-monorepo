## Pool Closure

Once a pool matures, the Pool Owner will close it, allowing you to withdraw your liquidity. Any pending redemption requests submitted prior to the pool's closure will be processed when the pool is shut down, regardless of the epoch schedule. The redeemed funds will then be available for withdrawal.

You can use the DApp to withdraw all funds, which includes the redeemed amount and any remaining amounts in the pool not requested for redemption. If you're familiar with interacting with the contract directly, you can also invoke the `withdrawAfterPoolClosure()` function on `TrancheVault` contracts to withdraw all your funds.
