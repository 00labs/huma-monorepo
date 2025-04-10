## Evaluation Agent

The Evaluation Agent plays the role of the underwriter for the pool, performing several crucial credit-related tasks. These include:

- Reviewing and approving credit requests
- Declaring default when the borrower fails to repay
- Restructuring credits by updating the APY, credit limit, waiving late fees, etc.

### Credit Approval

As the Evaluation Agent of a pool, your responsibilities include reviewing credit requests submitted by borrowers and determining their eligibility to borrow from the pool. If deemed eligible, you must decide on the exact terms of the credit, which includes:

- **Credit limit**: This is the maximum borrowing amount. The credit limit cannot exceed 4 billion of the underlying asset (stablecoin) of the pool.
- **Duration**: This is the loan duration, given in payment periods. Duration can be monthly, quarterly, or semi-annually.
- **Yield APR**: This is the annualized percentage rate of the credit. It determines the yield due for each payment period.
- **Late fee APR**: This is the pool-level setting that decides the amount of the late fee. If a payment is late, this fee is charged in addition to the regular yield charge. Like yield, it's an annualized rate.
- **Minimum principal rate**: This pool-level setting determines the amount of principal payment due each payment period. It's a per-payment-period rate. For example, a 10% minimum principal rate means 10% of the principal must be repaid at the end of each payment period.
- **Committed loan amount**: This is the amount the borrower pledges to borrow. Yield will be charged on this amount if the outstanding principal balance is below it.
- **Designated start date**: This marks the commencement of the credit term. Borrowing is disallowed before this date and interest starts accumulating from this point forward.
- **Revolving**: This indicates whether the borrower can reuse the credit after repaying a portion of the principal. For instance, if the approved credit is $1,000, the borrower has taken out $500, and $400 is repaid, the remaining credit will be $500 for non-revolving credit and $900 for revolving credit.

If you are the EA for a Receivable-backed Credit Line or Receivable Factoring Credit pool, you will also be responsible for evaluating the quality of receivables submitted by the borrower. This evaluation determines whether the receivables can be used for drawdown.

### Default Trigger

If it becomes apparent that the borrower will not be able to repay their obligations in full within a reasonable timeframe after a late payment, you have the authority to declare a default on the credit. This action will realize losses and initiate the loss distribution process. If the pool has established a default grace period, you can only declare default after this grace period, which begins after the due date of the borrower's first missed payment.

### Restructuring Credit

There are a few actions available for restructuring credit:

- **Updating the yield APY**: You have the option to update the yield APY of an active credit. However, the update will not be immediate. It will take effect either at the start of a new pay period when the credit is refreshed or when the borrower makes another drawdown, whichever occurs first.
- **Updating the credit limit and/or committed amount**: You can also adjust the credit limit and/or committed amount of an active credit. If you need to prevent the borrower from making further drawdowns due to unfulfilled obligations, set the credit limit to 0. This update will also not be immediate and will take effect in the same manner as updating the yield APY. Note that changes may affect the yield due for the borrower if the relationship between the outstanding principal and the committed amount changes after the update.
- **Extending the number of remaining periods**: You can lengthen the number of remaining periods for a credit in good standing. If the credit is in its final period where all principal is due, the borrower remains responsible for the full principal payment.
- **Waiving late fees**: You have the ability to waive late fees on a credit. If the waived amount exceeds the late fees accrued on the credit, only the actual amount will be waived.

### Credit Closure

A borrower’s credit will automatically be closed once it's paid off and has passed its maturity date. You also have the ability to close a credit early, before its maturity date, provided the following conditions are met:

- The outstanding balance on the credit has been paid off. This includes the amount due next, any past due amounts, and the outstanding principal.
- There is no committed amount on a credit that has already started. You can also close a credit that's been approved but not started and has an outstanding commitment.

### First Loss Cover and Tranche Liquidity Requirements

Like the Pool Owner, the EA is also subject to liquidity requirements, but they are generally less stringent:

- The Pool Owner and EA must collectively deposit at least the amount specified by the `minLiquidity` parameter of the admin's first loss cover.
- The EA must deposit at least the amount specified by the `liquidityRateInBpsByEA` parameter into the junior tranche.
