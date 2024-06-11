## Yield, Fees, and Principal Payment

### Day-Based Calculation

The Huma protocol employs a day-based calculation approach when determining yield, fees, and principal due. This is different from V1, where a second-based approach was used. This means it counts the total number of days elapsed since the last due amounts were computed. An important aspect of this method is that it always rounds up to the start of the next day, regardless of when in the current day the calculation occurs.

### Late Payment Grace Period

Each pool can set a late payment grace period, typically 5 days. Payments made within the grace period after the due date are considered on time. This setting is referred to as `latePaymentGracePeriod` in the `poolConfig`. During this period, further drawdowns are not permitted.

### No Refunds for Early Payment

In V1, if part of the principal was paid before the due date, the yield related to the unused days for the repaid principal portion was refunded to the borrower. This is because the capital was not employed during those days. However, this is not desirable for business lending as the capital will be idle in the pool. Therefore, the V2 protocol will not provide a refund if the borrower makes early repayment.

### Simplified Yield Calculation

V1 used a compound yield calculation. If an account was late, all due amounts were added to the principal, and the updated principal was used to compute the due for the next period. This added complexity. In V2, we use a simpler yield calculation, more common in business lending. If an account is late, we simply apply the late payment fee, do not adjust the principal, and use the existing principal to calculate the yield for the next period.

### Principal Payment Only

Usually, when a payment is made, it is first applied to late fees and yield due before being applied to the principal. In special cases, the borrower may wish to pay towards the principal first to demonstrate their ability to make more frequent payments than the typical monthly basis. While this is not common in today's business, in the RWA world, some borrowers want to show that their receivables are indeed short-duration as claimed and opt to make principal payments before the due date.

### Making Principal Payment and Drawdown in One Transaction

Similar to the above, the borrower may wish to make a payment to show they have the necessary capital and then borrow again for a new transaction. To save time and gas fees for the borrower, these two actions can be combined into one transaction.

### Late Fee Calculation

If an account is late (after the late payment grace period), a late payment fee will be charged. This fee is in addition to the regular interest due for all the outstanding principal. The additional charge is calculated using:

$$\frac{Principal \times LateFeeInBps \times NumberOfDaysBeingLate}{360}$$

For instance, if an account with an outstanding principal of $10,000 and an APR of 12% has a `lateFeeInBps` of 18%, the actual charge on the borrower is an annualized 30% for the days when the account is late. It is charged daily to encourage the borrower to pay back as soon as possible.

### Front-Loading Fee Calculation

At the origination of a loan, the borrower may be charged a front-loading fee, also known as an origination fee. This fee is usually a combination of a percentage of the principal amount and a fixed fee. The `frontLoadingFeeFlat` parameter defines the fixed fee, and the `frontLoadingFeeBps` parameter defines the percentage of the principal to be charged. For example, if `frontLoadingFeeFlat = $2,000`, and `frontLoadingFeeBps = 100`. For a loan of $100K, the front-loading fee will be:

$$\$2,000 + \$100K \times 100/10,000 = \$2,000 + \$1,000 = \$3,000$$
