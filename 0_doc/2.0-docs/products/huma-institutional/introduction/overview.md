# Overview

Huma Institutional is a permissioned protocol designed for institutional investors to access curated payment financing and RWA opportunities. This enables licensed financial institutions to scale responsibly while meeting the surging demand for flexible, compliant financial infrastructure. The list below highlights the key building blocks of the protocol:

- **Structured finance.** This includes tranches, first loss coverage, 30/360 calendar, and day boundary yield calculations.
- **Tokenization.** Allows real-world assets to be tokenized through SPV structures.
- **Transparency.** Clearly present the lifecycle of real-world receivables on-chain so that the investors can easily monitor the performance of these receivables.

Given the complexities of structured finance, we took a modular approach by defining critical abstractions and allowing additional modules to be added over time to enrich the protocol to suit the needs of various use cases. Below are some critical abstractions:

- **Tranche policy.** It defines the P&L rules between different tranches.
- **Calendar.** TradFi often uses 30/360 calendar, but more DeFi-native parties would like to take advantage of DeFi’s second-level yield calculation.
- **Yield manager.** It defines how yield is calculated. Some pools may charge various fees, ranging from front-loading and back-loading to subscription fees.
- **First loss cover.** First loss cover can be sourced from the borrower, insurance, or investors. A single pool might have multiple layers of first loss cover. The Huma protocol permits up to 16 layers of first loss cover, offering a flexible mechanism to configure both coverage and yield for these layers.
