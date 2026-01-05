# FAQ

# General

## What is Huma 2.0? What happens to the existing permissioned product?

Huma 2.0 democratizes access to decentralized finance with a permissionless model, allowing anyone to tap into institutional-grade PayFi yields—previously available only to professional investors. Huma 2.0 is the flagship product, branded simply as **Huma**.

The existing permissioned service continues under the **Huma Institutional** brand, serving institutional partners with tailored requirements.

The **Launch App** button on [huma.finance](https://huma.finance/) provides access to both:

- **Huma (permissionless)**: Launched in April 2025
- **Huma Institutional (permissioned)**: The original product prior to April 2025


## On which chains are Huma and Huma Institutional available?

- **Huma 2.0**: Available only on **Solana**
- **Huma Institutional**: Available on **Solana**, **EVM**, and **Stellar**


## What are the requirements for Huma Institutional?

Huma Institutional is available to **professional investors** who complete **KYC/KYB verification**. This requirement is unchanged from the existing permissioned product.


## Who can participate as an LP in Huma 2.0?

Any user who is not from a [sanctioned or restricted region](https://app.huma.finance/restricted-countries) can participate, provided their wallet does not get flagged by **Chainalysis risk screening**.


## What is the minimum deposit amount?

1 USDC


## Is there a pool cap in Huma 2.0?

Yes. Huma has a **dynamic pool cap** based on real-world capital demand from PayFi partners to ensure high utilization rates. When the cap is reached:

- New deposits are paused.
- Deposits reopen only when new demand is added or existing LPs withdraw.

This protects yield quality for all participants and keeps capital highly efficient.


## What do users receive when they deposit?

Users receive a liquid LP token based on the mode they choose:

- **$PST** (Classic Mode)
- **$mPST** (Maxi Mode)

With Prime, users receive a transferrable NFT that holds information about their position.

**Critical**: Burning any of these tokens will lead to a total loss of the user's deposit. Be extremely careful using incinerators!


## Why choose a lockup over no lockup?

Locking your position boosts your **Huma reward multiplier** while still giving you full access to your capital once the lockup ends.

Huma offers three lockup options:

- **No Lockup**: Redeem anytime. Earns **baseline Huma rewards**.
- **3-Month Lockup**: Redeem after 3 months. Earns **higher Huma rewards**.
- **6-Month Lockup**: Redeem after 6 months. Earns the **highest Huma rewards**.


## How does redemption work?

- **No Lockup**: Redeem anytime.
- **Locked Positions**: Redeem after the lockup period ends.

Redemptions are processed on a **first-come, first-served** basis. Most are completed within **2 business days**, though some may take up to **7 days** per SLA.


## What if I need instant liquidity?

Users could swap on Jupiter leveraging the PST-USDC pool and mPST-USDC pool (via Orca) at secondary market price. Even if your position is locked, you can exit early by swapping on Jupiter. However, in that case:

- The position is treated as **unlocked**.
- Any **extra $HUMA token rewards** earned from the lockup will be **reverted**.
- You may face slippage.


## How will the capital in the pool be used?

As the name **PayFi Strategy Token** suggests, most of the capital will be deployed into PayFi opportunities. A portion of the pool will be allocated to **market-neutral liquid assets** to ensure liquidity for redemptions. We aim to maintain a long-term ratio of 85% PayFi assets and 15% liquid assets.


## Where does the yield come from?

Huma primarily generates yield from **PayFi**—real-world payment financing activities such as:

- Global settlement
- Card payments
- Trade finance

Businesses pay a **daily fee** to borrow capital (typically 1–5 days), allowing:

- **Capital recycling up to 100x/year**.
- **Compounding effect** that drives stable, attractive returns.

Unlike DeFi yield, which relies on token incentives, PayFi yield is **rooted in the real economy**.

Huma also generates yield from **market-neutral digital asset deployments**.


## What are the risks of participating as a liquidity provider (LP)?

While Huma prioritizes safety, DeFi participation carries risks, including:

- **Smart Contract Risk**: Even with audits, vulnerabilities may exist.
- **Slippage / Impermanent Loss**: May occur when using $PST in external DeFi.
- **Liquidity Risk**: Redemptions may be delayed during peak activity.
- **Regulatory Risk**: Legal changes may affect your ability to participate.
- **Credit Risk**: While historically very low, PayFi borrowers may default.

Huma mitigates these through:

- Audited contracts
- Conservative protocol design
- Real-world yield generation
- Transparent governance
- Rigorous underwriting and risk management


## How does Huma ensure smart contract and system security?

Huma follows industry best practices for security:

- **Minimized Admin Rights** – All admin actions require multisig. Even if keys are compromised, contracts prevent LP fund theft.
- **Top-Tier Audits** – Audited by Spearbit, Halborn, and Certora. Huma 2.0 was audited by Halborn. [[View audit report here.](https://www.halborn.com/audits/huma-finance/solana-programs-060022)].
- **Infrastructure Security** – Penetration-tested backend, real-time malware monitoring, and employee security protections.


# Classic & Maxi

## What are Classic Mode and Maxi Mode?

Huma offers two modes to match different LP strategies. You can switch between them **anytime, as often as you like**.

- **Classic Mode** provides **stable yield** with **moderate $HUMA token rewards**. The current base APY is visible through the Huma App, updated monthly based on market conditions. This mode is ideal for LPs who prioritize **consistent returns**.
- **Maxi Mode** offers **maximum $HUMA token rewards** by **trading away stable yield**. LPs in this mode earn only $HUMA tokens, making it the go-to choice for **token-maximizing believers**—aka the Huma maxis.


## What are $PST and $mPST?

PST stands for PayFi Strategy Token

- **$PST**: LP token for Classic Mode (base yield + Huma rewards)
- **$mPST**: LP token for Maxi Mode (maximum Huma rewards, no base yield)


## What happens if I switch between Classic Mode and Maxi Mode?

When switching modes:

- Your current token (**$PST** or **$mPST**) is **burned**, and the corresponding token is **minted**.
- **Switching to Maxi**: Forgoes base APY for a higher amount of Huma rewards.
- **Switching to Classic**: Captures base APY with a lower amount of Huma rewards.

**Lockup status remains unchanged.** You can switch at any time, as often as you'd like. There is **currently no fee** for switching (gas fees apply), but this may change in the future.


## Can I transfer $PST or $mPST to another wallet?

Yes. Both tokens are standard SPL tokens and can be transferred to any supported wallet. However, please note:

- **Transferred tokens lose their lockup status**
- The transferred position will be treated as **unlocked** in the receiving wallet.
- Any **extra Huma rewards earned from lockups** or **badges** will be **reverted** in the original wallet.
- An exception applies only if the transfer is to protocols where Huma has officially stated that lockup status and rewards will be preserved (currently none).


## Why is the $mPST price above $1?

Although Maxi mode doesn't generate a stable yield and the price is intended to remain at $1, we've discovered that some users accidentally burned their $mPST while leaving their USDC in the pool. This imbalance — more USDC held than $mPST outstanding — has driven the price above $1.

**Implications:**

- **Early depositors** (before any burning occurred) will receive slightly more USDC upon redemption than originally deposited.
- **Later depositors** (after the last burning incident) will now receive **fewer $mPST tokens** per USDC deposited, since $mPST is priced above $1. But when you redeem, you'll still get back exactly the amount of USDC deposited.

**Warning:** Token burning is **irreversible**. Please double‑check before you proceed — **lost tokens cannot be recovered.**



# Prime

## What is Huma Prime? How does it work?
Huma Prime is an innovative looping strategy vault, leveraging the yield from $PST (Huma Classic). It's built on Huma's Defensive Looping technology.

### What is Defensive Looping?

Defensive Looping is a protected leverage strategy designed to augment yields on yield-bearing assets while mitigating the "death spiral" risks inherent in conventional looping in DeFi. It combines recursive borrowing with three primary layers of protection: automated leverage or deleverage based on supply and borrow rates, primary-market redemptions to substantially reduce liquidations driven by potential depegs in secondary markets, and isolated reserve mechanisms (coming soon) to buffer against asset impairments.

### How is Defensive Looping different from conventional looping?

Conventional DeFi looping allows users to boost returns by repeatedly depositing collateral and borrowing against it. This is great for capital efficiency and a substantial advantage over TradFi.

However, this creates three critical vulnerabilities that Defensive Looping is engineered to solve:

- **Interest rate reversal (negative carry):** If borrowing costs in a lending pool surge above the yield generated by the asset (common during market volatility), the user enters a "leveraged loss" state where they lose money every hour the position is open.

- **Cascade risk of secondary market:** Conventional looping relies on secondary market price oracles. If a market "depegs" due to low liquidity or manipulation, it triggers forced sales on the open market. This selling pressure pushes prices lower, causing a "liquidation death spiral."

- **Underlying asset impairment:** In traditional DeFi, if the collateral asset gets impaired, the token price collapses, leading to a total loss for the looper.

### The defensive solution

Defensive Looping transforms leverage into a controlled strategy by integrating these specific architectural layers:

**1. Automated yield-based deleveraging**

The protocol continuously monitors the spread between the Borrowing Cost and Asset Yield. If the cost of debt threatens to exceed the yield, the system automatically triggers a deleveraging event. This "fail-safe" protects the user's principal before a leveraged loss can occur.

**2. Primary market pricing**

Instead of force-selling assets on secondary markets first, Defensive Looping routes liquidations through the primary market (direct minting/redemption with the issuer). By redeeming assets at their face value, the protocol removes dependency on volatile oracles and ensures that a single liquidation event does not impact the market price for other users.

**3. Isolated reserve layer (coming soon)**

Positions are protected by a dedicated Reserve Layer. Because PayFi and RWA tokens are backed by real-world assets and cash flows, these reserves can be mathematically modeled to absorb impairments, providing a level of security that purely synthetic DeFi protocols cannot offer.

## Who can participate in Huma Prime? Are there caps for deposits?

Anyone can participate in Huma Prime. Due to high demand, priority might be given to OG and Vanguard badge users. Similar to Classic and Maxi, deposits are subject to caps to democratize institutional grade yield. Total deposit capacity is limited by borrowing limits in lending markets that the vault borrows from.

## Can I move existing Classic or Maxi deposits into Huma Prime? What if they are locked?

Existing Classic deposits, locked or unlocked, can be moved into Huma Prime by simply switching modes on the Portfolio page.

Maxi positions, locked or unlocked, need to be switched to Classic first, before they can be moved into Prime.

Due to the way lockups work differently between Prime and Classic/Maxi, users should pay attention to the new maturity date when moving their locked positions:

- If the original position is locked for 6 months and has more than 3 months until maturity, the Prime position has to be locked for 6 months.
- If the original position is locked for 6 months and has less than 3 months until maturity, the Prime position can be locked for 3 months or 6 months.
- If the original position is locked for 3 months, the Prime position has to be locked for 3 months.
- If the original position is unlocked, the Prime position can be unlocked or locked for 3 months or 6 months.

## What's the purpose of the NFT I get after depositing into Huma Prime? Can they be used in other DeFi protocols? 

Those NFTs are receipt tokens for the user's deposit position in Huma Prime.

**Critical: Burning that NFT will lead to a total loss of the user's deposit position. Never burn your Huma Prime deposit NFT, and be extremely careful using incinerators!**

Currently, there is no DEX liquidity or DeFi integration for the NFT. However, the NFTs can be transferred. When such a transfer happens, the underlying investment follows the NFT to the new NFT owner. A transfer does not change the lockup and maturity date.

## Do lockups in Huma Prime work in the same way as Classic and Maxi? 

While users can choose between no lockup, 3 months or 6 months across all modes, lockups work differently for Huma Prime. 

### No secondary market for Huma Prime
Both $PST and $mPST can be bought or sold on DEXes, regardless of their lockup. When locked positions are sold, they lose Huma rewards associated with them. 

For Huma Prime, there is no secondary DEX market, and vault positions keep their locked status until maturity even when the receipt NFT is transferred. That means, no early withdrawal mechanism is available for locked Huma Prime positions.  

## Why should I deposit into Huma Prime instead of looping $PST through Jup Lend or Kamino directly? 

Huma Prime is an automated yield-optimizing vault built on top of Huma's Defensive Looping technology. While $PST looping on Jup Lend and Kamino could provide greater leverage and control to sophisticated DeFi users, it's not for users or institutions looking for sustainable yield strategies. Huma Prime was created as a deposit-and-forget solution for long-term LPs, addressing the most critical risk scenarios that exist in conventional DeFi looping, while benefiting from the yield boost that comes from looping. 


# DeFi integrations

## Can $PST be used in other DeFi protocols?

Yes. Huma integrates with major Solana DeFi protocols:

- **Jupiter** – PST-USDC swaps for instant liquidity
- **Orca** - mPST-USDC swaps, underlying pool powering Jupiter
- **Kamino** – Provide liquidity to the PST-USDC and mPST-USDC liquidity vault or engage in the Huma Market in the following ways:
  - Supplying USDC or USDS.
  - Depositing PST.
  - Borrowing USDC or USDS against their deposited PST.
  - **Note:** Each wallet can either supply or borrow, but cannot do both. 
- **RateX** – Enables Huma LPs to transform their $PST into structured DeFi positions (PT/YT), enabling leverage, hedging, and more tailored yield strategies.


## Why are my swap transactions on Jupiter not appearing in my portfolio?

It might take a while to synchronize the actions you have taken outside Huma. If you had a successful transaction on Jupiter, your portfolio will eventually reflect that.


## What do I earn in the Huma market and liquidity products on Kamino? 
Huma rewards are rewarded hourly, though there may be a delay before they appear in your portfolio. This is the only way for these specific tokens to earn Huma rewards—they will not earn additional Huma rewards from other areas of the Huma ecosystem.

If the PST/mPST you deposit is currently under a lockup period, any extra Huma rewards you previously earned from that lockup will be deducted. Make sure you only deposit unlocked tokens.


# Rewards & badges

## What are Huma rewards? How are they related to Huma Feathers?

Starting October 2025, to provide greater certainty and clarity on HUMA token rewards, the system will **continuously allocate token rewards** to the community and distribute them at the end of each airdrop season.

While the reward mechanism remains powered by Huma Feathers, users will now see their accrued $HUMA token rewards directly, and the impact on APY will be reflected in the Huma App. The estimated rewards APY will be calculated based on Huma's tokenomics and the 7-day average price of $HUMA token.

Feathers are converted to $HUMA tokens based on a Feather-to-$HUMA ratio, which can be adjusted periodically to keep rewards attractive to the community. 
The historical Feather-to-$HUMA ratios are:

- Season 0: 8.3
- Season 1: 23.5
- Season 2: 30 (subject to adjustment if needed)

**Huma rewards and Feathers are non-transferable and non-tradable.** They are **tied to your wallet** and reflect your individual participation and loyalty. **Neither can be sold, transferred, or shared.**

## Is there a cap on the Huma rewards I can earn?

There is **no hard cap**, but your rewards depend on:

- The **amount and duration** of your deposit
- Your **reward multipliers** (mode, lockup, OG status, etc.)
- The **reward allocation** available for the current season

Rewards are **performance-based**, not arbitrarily capped.

However, Huma **reserves the right to revoke rewards** if a wallet engages in **Sybil attacks or manipulation**.


## What are the different ways to boost your reward multiplier?

You can stack multiple multipliers for even higher rewards:

- **Mode Multiplier** – Maxi Mode > Classic Mode.
- **Lockup Multiplier** – Longer lockups = higher multiplier.
- **OG LP Multiplier** – Lifetime bonus for pre-Huma 2.0 LPs who remained active.
- **Staking Multiplier** – $HUMA Stakers currently earn 10% APY with a 14-day unstaking cooldown. 
- **Vanguard Multiplier** – A lifetime bonus to reward long-term stakers of the $HUMA token.
- **Community Boost Multiplier** – Temporary boost for users referred by partner communities.



## How do I earn badges?
### OG LP badge 
Designed to reward early believers of Huma and PayFi's vision.

If you provided liquidity to the Huma protocol before Apr. 2025, you would have earned the OG LP badge. As long as you continue to provide at least 100 USDC liquidity, you keep the OG LP badge and enjoy the benefits. 
### Vanguard badge 
Designed to encourage and reward long-term $HUMA stakers.

You can earn a Vanguard badge by staking $HUMA. Users must meet qualification criteria following ONE of the two paths, airdrop and non-airdrop, while **maintaining their staking position for at least 6 months**.

#### Airdrop route
- **< 100,000 $HUMA** → Stake **100%**
- **100,000–200,000 $HUMA** → Stake **100,000 $HUMA**
- **> 200,000 $HUMA** → Stake **50%**

*Notes:*
- *Staking the required amount across **2 seasons** within a **6-month** window qualifies you for **Vanguard**.*
- *Includes **$HUMA presale** for **Huma OGs** and **Jup** stakers.*

#### Non-airdrop route
- If you did not receive an airdrop, qualify by staking **at least 100,000 $HUMA**.
- *Includes **Kaito**.*

For both routes, the badge will be awarded after you have staked for six months, and you can maintain it thereafter by continuing to stake at least 10,000 $HUMA.
### Anchor badge 
Designed for LPs to gain the ability to contribute more capital.

To qualify: An LP must deposit at least 1,000 USDC with a six-month lockup into any Huma product. Once the deposit matures, they will have three months to redeposit for another six-month lockup. The new deposit limit will be the greater of 2x the original deposit or the per-wallet cap, and as long as the final deposit amount is at least 1,000 USDC, the LP will earn the Anchor badge.

---

**Disclaimer:** These FAQs are provided for user convenience. Accordingly, they do not fully describe the legal structure or operations of the issuer of $PST and $mPST, nor do they fully describe certain risk factors. Detailed information about the foregoing is set forth in the issuer's PayFi Strategy Memorandum (PSM), which will be provided to users as part of the deposit process.


# Staking

## What are the benefits of staking $HUMA? 

**Staking Rewards**: Stakers earn rewards directly, without needing to be LPs.

**Boosted LP Rewards**: Stakers receive enhanced rewards on their LP positions.

**Priority Access to Ecosystem Incentive Programs**: Stakers enjoy exclusive or early access to various protocol-driven and partner-based incentives. Examples include:
- Early access to deposit into Huma when capacity is limited
- Eligibility for Huma Yapper rewards 
- Eligible for promotions and airdrops from ecosystem partners


## What is the staking policy? 

Stakers can request to unstake at any time, and can withdraw after a 14-day cooldown. Staking Factor plays a critical role in determining the staking reward. The initial promotional value of the Staking Factor is 10x. Staking rewards are distributed in the form of Huma rewards, similar to LP rewards.

Those who staked before June 30th, 2025 can keep their 0-day unstaking cooldown. Starting Aug 26, 2025 they will stop earning Huma rewards unless they opt into the new policy: est. 10% APY with a 14-day cooldown in the Huma App. 

The staking reward applies retroactively to those who have staked before the staking rewards launch on June 30th, 2025.
