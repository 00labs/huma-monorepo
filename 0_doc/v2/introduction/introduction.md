# Introduction

Huma V1 is an income-backed lending protocol. It allows businesses and individuals to borrow against their future income by connecting them with global investors on-chain. The protocol not only comes with common credit facilities such as revolving credit lines and receivable factoring but also includes Decentralized Signal Processors and Evaluation Agents, which are critical infrastructures to integrate with income sources for credit underwriting and ongoing risk management. This lending protocol with built-in risk management was well received when launched at ETHDenver 2023. With more than 20 projects built on Huma, it was one of the developers’ favorites in the world’s largest Ethereum developer conference.

The Huma V2 protocol builds upon the foundation of the V1 protocol. In addition to the revolving credit line and receivable factoring, it added the support of receivable-backed credit lines. The primary goal of V2 is to support institutional investors with a rich set of features:

- **Structured finance.** This includes tranches, first loss coverage, 30/360 calendar, and day boundary yield calculations.
- **Tokenization.** Allows real-world assets to be tokenized through SPV structures.
- **Transparency.** Clearly present the lifecycle of real-world receivables on-chain so that the investors can easily monitor the performance of these receivables.

Given the complexities of structured finance, we took a modular approach by defining critical abstractions and allowing additional modules to be added over time to enrich the protocol to suit the needs of various use cases. Below are some critical abstractions:

- **Tranche Policy.** It defines the P&L rules between different tranches.
- **Calendar.** TradFi often uses 30/360 calendar, but more DeFi-native parties would like to take advantage of DeFi’s second-level yield calculation.
- **Yield Manager.** It defines how yield is calculated. Some pools may charge various fees, ranging from front-loading and back-loading to subscription fees.
- **First loss cover.** First loss cover can be sourced from the borrower, insurance, or investors. A single pool might have multiple layers of first loss cover. The Huma protocol permits up to 16 layers of first loss cover, offering a flexible mechanism to configure both coverage and yield for these layers.
