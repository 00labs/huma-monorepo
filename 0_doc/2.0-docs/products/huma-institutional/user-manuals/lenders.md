# Lenders

On Huma, lenders earn a part of the pool's profit by providing liquidity. The Huma Insitutional protocol defines two tranche types for lenders: senior and junior. A pool might either have a two-tranche structure with both tranches active or a uni-tranche structure with only the junior tranche enabled. If you want to participate in both tranches in a pool where both are active, you must obtain separate approvals.

## Lender Approval and Removal

Since all pools on the Huma protocol are permissioned, all lenders must get approval to join a pool. Here are the steps involved:

1. Pass the Know Your Customer (KYC)/Know Your Business (KYB) checks. This step is handled by Securitize.
2. Secure investor accreditation/qualification if required in your country/region of residence. This step is also handled by Securitize.
3. Sign legal documents specified by the Pool Owner, like the investor questionnaire and lender agreement. The exact documents you need to sign can vary based on the pool you're joining.
4. Get approval from the Pool Owner or Pool Operators.

Pool Operators have the discretion to remove a lender. If removed, the lender can no longer supply additional liquidity to the pool. However, the lender’s existing funds will stay in the pool, continuing to generate yield, and can be requested to redeem at any time.

For a detailed walkthrough of the process, refer to the [Step-by-step Guides](https://www.notion.so/Invoice-Financing-by-Request-Huma-72adb4cca5b042128395230b28dab668?pvs=21) section.

## Pool Closure

Once a pool matures, the Pool Owner will close it, allowing you to withdraw your liquidity. Any pending redemption requests submitted prior to the pool's closure will be processed when the pool is shut down, regardless of the epoch schedule. The redeemed funds will then be available for withdrawal.

You can use the DApp to withdraw all funds, which includes the redeemed amount and any remaining amounts in the pool not requested for redemption. If you're familiar with interacting with the contract directly, you can also invoke the `withdrawAfterPoolClosure()` function on `TrancheVault` contracts to withdraw all your funds.
