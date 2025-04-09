# Lockup

When depositing into the Huma pool, LPs have the option to **lock up their funds** for a fixed period in exchange for **enhanced Huma Feathers rewards**. During the lockup period, the position cannot be redeemed; however, once the lockup ends, the position becomes **unlocked** and can be withdrawn at any time.

When you deposit, you can choose **no lockup**, a **3-month lockup**, or a **6-month lockup**. You can **always move forward**:

- From no lockup → 3 months or 6 months
- From 3 months → extend to 6 months

However, you **cannot go backward**. For example, if you're already at 6 months, you can't shorten it.

This design gives you **flexibility and control,** allowing you to ease into longer commitments and boost your rewards over time without locking yourself in from day one.

Lockups are a meaningful way to demonstrate long-term alignment with the protocol. In return, LPs are rewarded with **higher Feathers multipliers**—the longer the commitment, the greater the rewards.

The table below outlines the available lockup durations and their corresponding reward multipliers:

| Lockup | Redemption | Rewards Multiplier |
| --- | --- | --- |
| No Lockup | Redeem anytime | 1x |
| 3-month | After 3 months | 2x* |
| 6-month | After 6 months | 3x* |

* During the **promotional period** of the Huma 2.0 launch, these multipliers are elevated to **3x for 3-month** lockups and **5x for 6-month** lockups.

You can earn the lockup multiples only if you use Huma DApp or any other DeFi protocols that have been officially supported by Huma.

## **Restrictions**

Positions with a lockup come with limitations on redemption and transfers:

- **No early redemption**: Locked positions cannot be redeemed through the Huma DApp. Any attempt to bypass this via direct smart contract calls will be rejected. If redemption somehow occurs despite restrictions, **all Feathers earned from that position will be forfeited**.
- **Bonus rewards will be forfeited upon locked token transfer**: If locked tokens are transferred—including actions like swapping on Jupiter or depositing into platforms like Kamino or RateX—the transferred portion will be treated as **unlocked**. This means **any bonus Feathers earned from the lockup will be reverted**.

**Example**

Suppose an LP deposits $1,000 in Classic mode with a 3-month lockup during a promotional period offering a **3x Feather multiplier**. This yields **3,000 Feathers per month**.

After one month, if the LP swaps **$700** of the position on Jupiter for USDC, that portion will be treated as **unlocked from the start**. The revised Feather reward would be:

- $700 × 1x = 700 Feathers
- $300 × 3x = 900 Feathers
- **Total = 1,600 Feathers**

Since the LP had originally earned 3,000 Feathers, the **extra 1,400 Feathers** gained due to the lockup will be **revoked**.
