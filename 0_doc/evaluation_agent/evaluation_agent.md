# Evaluation Agent

The Evaluation Agent (EA) is the risk management layer in the Huma Protocol. They are responsible for the underwriting decisions for the lending pools they are associated with. The goal for the EA platform is to build a secured, community-driven system to support accurate underwriting decisions at scale.

Each EA implements a standard interface to interact with Huma SDK and Huma contracts. They also have borrower authenticated read access to relevant signals in the DSP for their models.

## EA Hosting

Each lending pool selects an EA from the HUMA EA registry to delegate its underwriting. EAs can further specialize to serve the use cases of a specific pool, or stay more generic to support more pools.

The EAs are fully decentralized. Each EA is a microservice with a shared interface. For anti-fraud considerations, Huma does not require the EAs to open-source their models. Both Huma and the Pool Owner will inspect and validate the EA before selecting it to underwrite for a pool.

The EA hosting platform is open-sourced (as in this repo). It is centralized at this moment due to the need for the complexity of computations and to support faster iteration in the early stage. As decentralized execution engines become more powerful, we will transition the EA hosting platform to a decentralized execution platform as well.

## Creating a new EA

To create a new EA. Developers submit their models, EAs, to Huma DAO for review. Once approved, the EAs are deployed in a secure container provided by Huma.

See a [sample Evaluation [Agent](https://github.com/00labs/huma-underwriter-eth-txns) that underwrites loans using simple rules based on wallet transaction history.

An NFT is minted to represent each EA. Although any developer can mint an EA NFT, only Huma DAO can update the relevant metadata (e.g. status, performance) for each EA NFT and creates an entry in the EA Registry so that it is discoverable by pool owners.

We invite developers to contribute to the initial development and ongoing maintenance of EAs and the hosting platform. As a way to kickstart development, Huma offers bounty programs and a portion of the protocol revenue will be allocated to reward Signal Adapter developers and maintainers. The Huma DAO will review all contributions and determine how to distribute the reward pool among different contributors. Join us and be a part of building the future of decentralized finance!
