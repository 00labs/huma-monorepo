# FAQ

### What is Huma 2.0? What happens to the existing permissioned product?

Huma 2.0 democratizes access to decentralized finance with a permissionless model, allowing anyone to tap into institutional-grade PayFi yields—previously available only to professional investors. Huma 2.0 is the flagship product, branded simply as **Huma**.

The existing permissioned service continues under the **Huma Institutional** brand, serving institutional partners with tailored requirements.

The **Launch App** button on [huma.finance](https://huma.finance/) provides access to both:

- **Huma (permissionless)**: Launched in April 2025
- **Huma Institutional (permissioned)**: The original product prior to April 2025

---

### What are Huma Feathers? How are they related to Huma Points?

Huma Feathers are the evolution of our loyalty system to reward the community based on their engagement with the Huma Protocol, inspired by the mythical Huma bird—a symbol of prosperity and renewal. Feathers reflect the platform's agility and long-term vision.

All Huma Points have been rebranded as Feathers and converted at a 1:1 ratio. The points earned before the launch of Huma 2.0 can be accessed via the **Huma Institutional** DApp.

---

### On which chains are Huma and Huma Institutional available?

- **Huma 2.0**: Available only on **Solana**
- **Huma Institutional**: Available on **Solana**, **EVM**, and **Stellar**

---

### Who can participate as an LP in Huma 2.0?

Any user from a non-sanctioned or non-restricted country can participate, provided their wallet does not get flagged by **Chainalysis risk screening**.

---

### What is the minimum deposit amount?

1 USDC

---

### Is there a pool cap in Huma 2.0?

Yes. Huma has a **dynamic pool cap** based on real-world capital demand from PayFi partners to ensure high utilization rates. When the cap is reached:

- New deposits are paused.
- Deposits reopen only when new demand is added or existing LPs withdraw.

This protects yield quality for all participants and keeps capital highly efficient.

---

### What do users receive when they deposit?

Users receive a liquid LP token based on the mode they choose:

- **$PST** (Classic Mode)
- **$mPST** (Maxi Mode)

Users can switch the mode of their existing positions to swap between $PST and $mPST.

---

### What are Classic Mode and Maxi Mode?

Huma offers two modes to match different LP strategies. You can switch between them **anytime, as often as you like**.

- **Classic Mode** provides **stable yield** with **moderate Huma Feather rewards**. The current APY is **10.5%**, updated monthly based on market conditions. This mode is ideal for LPs who prioritize **consistent income**.
- **Maxi Mode** offers **maximum Feather rewards** by **trading away stable yield**. LPs in this mode earn only Huma Feathers, making it the go-to choice for **Feather-maximizing believers**—aka the Huma maxis.

---

### What are $PST and $mPST?

PST stands for PayFi Strategy Token

- **$PST**: LP token for Classic Mode (yield + rewards)
- **$mPST**: LP token for Maxi Mode (maximum rewards, no yield)

---

### What happens if I switch between Classic Mode and Maxi Mode?

When switching modes:

- Your current token (**$PST** or **$mPST**) is **burned**, and the corresponding token is **minted**.
- **Switching to Maxi**: Forgoes APY for higher amount of Huma Feathers.
- **Switching to Classic**: Captures APY with lower amount of Huma Feathers.

**Lockup status remains unchanged.**

You can switch at any time, as often as you'd like.

There is **currently no fee** for switching (gas fees apply), but this may change in the future.

---

### Can $PST be used in other DeFi protocols?

Yes. Huma integrates with major Solana protocols:

- **Jupiter** – PST swaps for instant liquidity
- **Meteora** – Underlying pool powering Jupiter
- **Kamino** – Borrow USDC against PST (looping may be supported)
- **RateX** – Trade the reward component of yield-bearing assets

---

### Can I transfer $PST or $mPST to another wallet?

Yes. Both tokens are standard SPL tokens and can be transferred to any supported wallet.

However, please note:

- **Transferred tokens lose their lockup status**
- The transferred position will be treated as **unlocked** in the receiving wallet.
- Any **extra Feathers earned from lockups** will be **reverted** in the original wallet.
- An exception applies only if the transfer is to protocols where Huma has officially stated that lockup status and rewards will be preserved (currently none).

---

### Why is the $mPST price above $1?

Although Maxi mode doesn’t generate a stable yield and the price is intended to remain at $1, we’ve discovered that some users accidentally burned their $mPST while leaving their USDC in the pool. This imbalance — more USDC held than $mPST outstanding — has driven the price above $1.

**Implications:**

- **Early depositors** (before any burning occurred) will receive slightly more USDC upon redemption than originally deposited.
- **Later depositors** (after the last burning incident) will now receive **fewer $mPST tokens** per USDC deposited, since $mPST is priced above $1. But when you redeem, you’ll still get back exactly the amount of USDC deposited.

**Warning:** Token burning is **irreversible**. Please double‑check before you proceed — **lost tokens cannot be recovered.**

---

### Why choose a lockup over no lockup?

Locking your position boosts your **Feather reward multiplier** while still giving you full access to your capital once the lockup ends.

Huma offers three lockup options:

- **No Lockup**: Redeem anytime. Earns **baseline Feather rewards**.
- **3-Month Lockup**: Redeem after 3 months. Earns **higher Feather rewards**.
- **6-Month Lockup**: Redeem after 6 months. Earns the **highest Feather rewards**.

💥 **Limited-Time Bonus**:

During the Huma 2.0 launch promotion, reward multipliers for 3-month and 6-month lockups are **boosted even further**. It's the perfect time to commit and maximize your earnings.

---

### What are the different ways to boost your reward multiplier?

You can stack multiple multipliers for even higher rewards:

- **Mode Multiplier** – Maxi Mode > Classic Mode
- **Lockup Multiplier** – Longer lockups = higher multiplier
- **OG LP Multiplier** – Lifetime bonus for pre-Huma 2.0 LPs who remained active
- **Loyal LP Multiplier** *(coming soon)* – For LPs with consistently retained positions
- **Community Boost Multiplier** – Temporary boost for users referred by partner communities

---

### How does redemption work?

- **No Lockup**: Redeem anytime.
- **Locked Positions**: Redeem after the lockup period ends.

Redemptions are processed on a **first-come, first-served** basis. Most are completed within **1 business day**, though some may take up to **7 days** .

---

### What if I need instant liquidity?

A **PST-USDC pool** on **Jupiter** (via Meteora) enables instant swaps.

Even if your position is locked, you can exit early by swapping on Jupiter. However, in that case

- The position is treated as **unlocked**.
- Any **extra Feathers** earned from the lockup will be **reverted**.

---

### How will the capital in the pool be used?

As the name **PayFi Strategy Token** suggests, most of the capital will be deployed into PayFi opportunities.  A portion of the pool will be allocated to **market-neutral liquid assets** to ensure liquidity for redemptions.

---

### Where does the yield come from?

Huma primarily generates yield from **PayFi**—real-world payment financing activities such as:

- Global settlement
- Card payments
- Trade finance

Businesses pay a **daily fee** to borrow capital (typically 1–5 days), allowing:

- **Capital recycling up to 100x/year**.
- **Compounding effect** that drives stable, double-digit returns.

Unlike DeFi yield, which relies on token incentives, PayFi yield is **rooted in the real economy**.

Huma also generates yield from **market-neutral digital asset deployments**.

---

### How does Huma ensure smart contract and system security?

Huma follows industry best practices for security:

- **Minimized Admin Rights** – All admin actions require multisig. Even if keys are compromised, contracts prevent LP fund theft.
- **Top-Tier Audits** – Audited by Spearbit, Halborn, and Certora. Huma 2.0 was audited by Halborn. [[View audit report here.](https://www.halborn.com/audits/huma-finance/solana-programs-060022)].
- **Infrastructure Security** – Penetration-tested backend, real-time malware monitoring, and employee security protections.

---

### What are the requirements for Huma Institutional?

Huma Institutional is available to **professional investors** who complete **KYC/KYB verification**.

This requirement is unchanged from the existing permissioned product.

---

### Are Huma Feathers transferable or tradable?

No. **Huma Feathers are non-transferable and non-tradable**.

They are **tied to your wallet** and reflect your individual participation and loyalty.

Feathers **cannot be sold, transferred, or shared**.

---

### Is there a cap on the rewards or Feathers I can earn?

There is **no hard cap**, but your rewards depend on:

- The **amount and duration** of your deposit
- Your **reward multipliers** (mode, lockup, OG status, etc.)
- The **reward allocation** available for the current season

Rewards are **performance-based**, not arbitrarily capped.

However, Huma **reserves the right to revoke rewards** if a wallet engages in **Sybil attacks or manipulation**.

---

### What are the risks of participating as a liquidity provider (LP)?

While Huma prioritizes safety, DeFi participation carries risks, including:

- **Smart Contract Risk**: Even with audits, vulnerabilities may exist.
- **Slippage / Impermanent Loss*: May occur when using $PST in external DeFi.
- **Liquidity Risk**: Redemptions may be delayed during peak activity.
- **Regulatory Risk**: Legal changes may affect your ability to participate.
- **Credit Risk**: While historically very low, PayFi borrowers may default.

Huma mitigates these through:

- Audited contracts
- Conservative protocol design
- Real-world yield generation
- Transparent governance
- Rigorous underwriting and risk management

**Disclaimer:** These FAQs are provided for user convenience. Accordingly, they do not fully describe the legal structure or operations of the issuer of $PST and $mPST, nor do they fully describe certain risk factors. Detailed information about the foregoing is set forth in the issuer's PayFi Strategy Memorandum (PSM), which will be provided to users as part of the deposit process.
