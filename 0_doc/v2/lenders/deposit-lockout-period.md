## Deposit and the Lockout Period

Deposits are accepted on a first-come, first-served basis until the pool liquidity cap is reached.

### Capital Deployment

Deposits are effective immediately upon acceptance, affecting the utilization rate for both senior and junior assets. In general, the amount of utilized capital attributed to each tranche corresponds to its proportion in the pool assets. For example, if a pool contains $80 in senior assets and $20 in junior assets, senior assets account for 80% of the total. If the borrower draws down $80, the protocol allocates $64 from the senior tranche and the remaining $16 from the junior tranche. If an additional $60 in junior capital is added to the pool, keeping the utilized capital at $80, the senior assets now represent 50% of the total pool. As a result, the protocol would allocate an equal deployment of $40 from each tranche.

### Lockout Period

A pool may establish a lockout period during which you must wait a certain number of days before you can redeem your deposits. The lockout period resets with each new deposit. For instance, if you make two deposits of $100 each on February 1st and March 1st, and the lockout period is 60 days, the lockout period resets to April 30th for the entire $200 following the second deposit.

### Minimum Deposit Amount

The protocol mandates each pool to set a minimum deposit amount. This threshold is enforced with every deposit. The protocol's absolute minimum is 10 units of the pool's underlying asset (for instance, 10 USDC for pools using USDC as the underlying asset). However, the Pool Owner has the discretion to set a higher threshold.
