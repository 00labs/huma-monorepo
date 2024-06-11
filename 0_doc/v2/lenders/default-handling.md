## Default Handling

If a borrower fails to make payments on time, the Evaluation Agent (EA) may declare the credit as defaulted. However, if a pool has a default grace period, the default can only be declared after this period has passed. The grace period starts from the due date of the first missed payment. For example, if a payment is due on February 1 and isn't made on time, and the default grace period is 10 days, then the EA can declare a default on or after February 11.

### Overall Procedure

When a default occurs, the Pool Owner, Pool Operators, and EA will follow the below procedure:

1. The EA declares a default by calling the `triggerDefault()` function in the contract.
2. The Pool Owner or Pool Operators disable the pool.
3. The Pool Owner sets the liquidity cap on the pool and the maximum liquidity on each first loss cover to 0.
4. The Pool Owner enables the pool to allow borrowers to make repayments.

### P&L Distribution

When a default is declared, P&L distribution occurs as follows:

1. The unpaid yield and late fee due are first distributed as profit to tranches and first loss covers.
2. The unpaid principal, yield, and late fee are then distributed as losses to first loss covers and tranches.

Distributing profit first is to protect senior lenders' interest to the highest degree, even in a default event.

### Loss Recovery

If the borrower makes a payment after default, the pool enters the loss recovery process. In this process, senior lenders are compensated first, followed by junior lenders, and finally the first loss covers.

If the Pool Owner decides to return the pool to normal (e.g., after sufficient loss recovery), they will restore the pool liquidity cap and first loss cover max liquidity to their original values to allow new liquidity injection.

### Impact on Deposit and Withdrawal

Since the pool liquidity cap and first loss cover max liquidity are set to 0 when a default occurs, new deposits will only be accepted once these values are restored. There is no impact on your ability to withdraw, although you will realize the losses incurred on your principal if you choose to do so.
