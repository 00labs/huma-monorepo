## Autotasks
The Huma protocol employs OpenZepplin’s Autotasks to perform certain routine processes. There are four types of Autotasks, with each of them supporting a different aspect of the pool operation:

### AutoPay Autotask
- Fetch all credits with a due date in the next 2 days and the credit state is in `GoodStanding` or `Delayed`.
- For each credit, if the borrower has enough funds in their wallet to cover the payment amount (`nextDue + totalPastDue`), and has approved enough allowance to the pool, call `makePayment` on behalf of the borrower to pay back the pool.

### Close Epoch Autotask
- Fetch all pools where the current epoch `endTime` is in the past.
- Call `processYieldForLenders` on the junior and senior tranche.
- Call `closeEpoch` on the epoch manager contract.
- Call `investFeesInFirstLossCover` on the pool fee manager contract.
- Call `payoutYield` on all first loss cover contracts of the pool.

### Refresh Credit Autotask
- Fetch all credit lines where `nextBillRefreshDate` is in the past and credit state is in `GoodStanding` or `Delayed`.
- Call `refreshCredit` on the credit manager contract for that borrower.

### Start Committed Credit Autotask
- Fetch all credit lines where credit state is `Approved`, committed amount is greater than 0, and the designated credit start date is in the past.
- Call `startCommittedCredit` on the credit manager contract for that credit.

Unless otherwise noted, all Autotasks run every 5 minutes. For access control, Autotasks will call contracts using the sentinel service account wallet.
