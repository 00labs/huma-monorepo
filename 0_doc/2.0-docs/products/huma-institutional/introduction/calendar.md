# Calendar

Businesses operate based on specific periods such as monthly, quarterly, or semi-annually. They prefer a fixed payment amount for each period, rather than one that fluctuates based on payment timing. Reducing the payment by a few cents due to earlier payment can create more complications than benefits.

One common approach is using the 30/360 day-count convention, which deviates from the regular monthly calendar. Here's how it works:

- Each year is divided into 12 equal months. This ensures that the yield generated each month is the same, regardless of whether the month has 31 or 28 days.
- To calculate the number of days that have passed in a month, we use the lesser of the days passed, or 30. For instance, on the 10th of a month, it's 10, but on the 31st of a month, it's 30.
- To figure out how many days remain in a month, we subtract the days passed from 30. For example, it's always 20 on the 10th of a month, whether it's February, March, or April. It drops to 0 on the 30th or 31st of the month.
- Each quarter is treated as three 30-day months.
- Each semi-annual period comprises six 30-day months.

In the Permissioned contracts, the 30/360 day-count convention is used for most time-related calculations, including yield, late fees, and due date calculations for borrowers, as well as yield calculations in the `FixedSeniorTranchesPolicy` for lenders. The exceptions to this rule are the "withdrawal lockup period" and "default grace period", which are both counted in actual calendar days.

All times are in UTC.
