# Payment Defaulting Service

## Need

When a payment has been due longer than its grace period, a default action must be triggered that liquidates the existing principal.

## Proposal

A daemonized node.js service similar to [Superfluid's Sentinel](https://github.com/superfluid-finance/superfluid-sentinel) that periodically syncs with all of a pool’s active loans and attempts to call **triggerDefault** when a loan is predicted to exceed its grace period.

Every X minutes, the PDS service will perform its upkeep function. The first step in the upkeep persists all of the active loans in a **BaseCreditPool** (fetched from a subgraph) to a local database for easy lookup and filtering. Using an event emitted from **drawdownWithReceivable **calls, our service will fetch all borrower addresses and check **_creditMapping() **to retrieve all the loan states.

Next the upkeep will check for all outstanding loans that must be liquidated. Each of these loans will be liquidated with an asynchronous **triggerDefault** call. Because this service is openly distributed, anyone can run their own service and a loan may or may not actually need to be liquidated; it is the pool contract’s responsibility to be the final check that a loan should be marked defaulted.

~~Lastly, PDS hosts need to be compensated for performing pool upkeep. In **triggerDefault**, a **loanDefaultRewardBps** percentage of the paid principal will also be written off as a loss and given to the liquidator. ~~

### Contract Changes

* **_creditRecordMapping **must be made public for service querying
* **drawdownWithReceivable **needs to emit an event with the borrower address
* ~~Introduce **loanDefaultRewardBps** variable, and add loss calculation and reward distribution logic to pool~~

## Notes

* Centrally host this for now