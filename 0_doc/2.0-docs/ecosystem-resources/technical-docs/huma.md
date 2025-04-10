# Huma (2.0)

Huma is powered by a robust blend of on-chain and off-chain components that work seamlessly to deliver a secure, efficient experience:

- **Solana Program**

  The core engine driving our permissionless liquidity pools and executing all essential business logic.

- **Decentralized App (dApp) Frontend**

  Your primary interface for interacting with Huma.

- **Web2 Services**

  Auxiliary systems that support Huma Feathers allocation and account management.

- **Price Oracle**

  A dedicated service that tracks the price of $PST in real time.

- **Off-chain Autotasks**

  Automated tasks that manage various operational functions within the pools.


**Price Oracle**

The Price Oracle continuously monitors and tracks the price of $PST, ensuring accurate and up-to-date data for all protocol operations.

**Autotasks**

Two primary autotasks power our pool operations:

- **Redemption Request Processing Job**

    This job is responsible for:
    
    - Canceling redemption requests that violate lockup requirements.
      - Processing redemption requests in an all-or-nothing manner—if the pool lacks sufficient funds to cover a request in full, processing will pause until enough funds are available.

- **Price Oracle Refresh Job**

    Regularly updates the Price Oracle to ensure the data remains current.

Together, these components form the backbone of the Huma protocol, delivering a secure, efficient, and user-friendly experience.
