---
description: Transparency principles and key addresses
---

# Multisig and Timelock Addresses

## Transparency Principles

Huma Protocol strives to operate at the highest level of transparency. We commit to abide by the following principles:

* The ownership of Protocol Contracts, Huma Config, and Pool Contracts to be a timelock.
* Timelocks to be operated by a majority vote of multisig wallets of minimum of 3 signees.
* Timelock delay is at least 24 hours.
* All the key addresses (timelock address, multisig address, and multisig signees) for the protocol and all active pools are published on this page.

## Polygon

### Key Addresses for Huma Protocol Administration

**HumaConfig contract address:** `0x03D80E259E34354B552fE5d152D7484192535393`

**timelock address:** `0x4730Ba92780b6783Ce97bD5f7AaD75337d6D180A`

**multisig address:** `0x7E13931931d59f2199fE0b499534412FCD28b7Ed`

#### multisig signees:

Note: As a general rule, for security considerations, we do not allow private keys from different individuals to be stored in the same location.\
\
During the Beta launch, all multisig signees are the founding team members of the Huma Protocol. Once the DAO is formed, more signees from the community will be added.

* [Richard](https://twitter.com/wisdant): `0xb6768AF8279CeeaeE4dB323396b1F185b0559439`
* [Ji](https://twitter.com/P1ayJ0k3r): `0x079a31ADA15D9F90c82600D14Cf77b384ea8b2c7`
* [Erbil](https://twitter.com/0xErbil): `0x1DC412E9273786F2C02c40cc8140dB598871d64d`

### Key Addresses for Active Pools

During the Beta launch, two pools are active on Polygon with the majority of pool funds bootstrapped by the Huma Protocol founding team.

A timelock owns each pool contract with a multisig as the only proposer. This timelock only governs the upgrade of the contract.

All the configurations of a pool are managed through BasePoolConfig and BaseFeeManager. Both contracts are owned by a separate timelock with the same multisig as the only proposer.

#### Credit Line Pool - Polygon

**PoolProxy contract address:** `0xAb3dc5221F373Dd879BEc070058c775A0f6Af759`

**PoolProxy upgrade timelock address:** `0x6fE57952F3Ce61f6B6d348e1BB52943C8531e99B`

**PoolConfig contract address:** `0x39f7D6040EC30B62c508723e2EDb822413837527`

**FeeManager contract address:** `0x65C5535735581039c5711A9d7c223cff9384334F`

**Timelock (for PoolConfig and FeeManager) address:** `0x48065723605D1367bC4256B747293e281F5aD37b`

**multisig address:** `0xD252073bF424bb13B474004bf9F52195d54aEDb6`

**multisig signees:**

* [Richard](https://twitter.com/wisdant): `0x76C89c2d8cDB9299EE32673026faB8a2A177dCa4`
* [Ji](https://twitter.com/P1ayJ0k3r): `0xEC5c04192A251f6ffD42a48ad3Ee8250F7757D08`
* [Erbil](https://twitter.com/0xErbil) : `0x1BACF76592Be393610cA422D7DDED282330CaED8`

#### Receivable Factoring Pool - Polygon

**PoolProxy contract address:** `0x58AAF1f9cB10F335111A2129273056bbED251B61`

**PoolProxy upgrade timelock address:** `0x1691090fb0cFd3bd9b59128b57490eA882A09573`

**PoolConfig contract address:** `0x98f41d57C06b302AFf999f3F58f4ae7a3F884590`

**FeeManager contract address:** `0x5B7841b94a3C7246662ef514745b034A6ceaAB15`

**Timelock (for PoolConfig and FeeManager) address:**

`0x0562e6287dd69E76771E046f7E24ADC608c837b6`

**multisig address:** `0xD252073bF424bb13B474004bf9F52195d54aEDb6`

**multisig signees:**

* [Richard](https://twitter.com/wisdant): `0x76C89c2d8cDB9299EE32673026faB8a2A177dCa4`
* [Ji](https://twitter.com/P1ayJ0k3r): `0xEC5c04192A251f6ffD42a48ad3Ee8250F7757D08`
* [Erbil](https://twitter.com/0xErbil): `0x1BACF76592Be393610cA422D7DDED282330CaED8`

``

## `Ethereum Mainnet`

### Key Addresses for Huma Protocol Administration

**HumaConfig contract address:** `0x03D80E259E34354B552fE5d152D7484192535393`

**timelock address:** `0x4730Ba92780b6783Ce97bD5f7AaD75337d6D180A`

**multisig address:** `0x1eCD14504885ADfF674842F6b805e202c7C05B75`

#### multisig signees:

Note: As a general rule, for security considerations, we do not allow private keys from different individuals to be stored in the same location.\
\
During the Beta launch, all multisig signees are the founding team members of the Huma Protocol. Once the DAO is formed, more signees from the community will be added.

* [Richard](https://twitter.com/wisdant): `0xb6768AF8279CeeaeE4dB323396b1F185b0559439`
* [Ji](https://twitter.com/P1ayJ0k3r): `0x079a31ADA15D9F90c82600D14Cf77b384ea8b2c7`
* [Erbil](https://twitter.com/0xErbil): `0x1DC412E9273786F2C02c40cc8140dB598871d64d`

### Key Addresses for Active Pools

During the Beta launch, two pools are active on Ethereum mainnet with the majority of pool funds bootstrapped by the Huma Protocol founding team.

A timelock owns each pool contract with a multisig as the only proposer. This timelock only governs the upgrade of the contract.

All the configurations of a pool are managed through BasePoolConfig and BaseFeeManager. Both contracts are owned by a separate timelock with the same multisig as the only proposer.

#### Credit Line Pool - Ethereum Mainnet

**PoolProxy contract address:** `0x58AAF1f9cB10F335111A2129273056bbED251B61`

**PoolProxy upgrade timelock address:** `0x1691090fb0cFd3bd9b59128b57490eA882A09573`

**PoolConfig contract address:** `0x98f41d57C06b302AFf999f3F58f4ae7a3F884590`

**FeeManager contract address:** `0x5B7841b94a3C7246662ef514745b034A6ceaAB15`

**Timelock (for PoolConfig and FeeManager) address:** `0x0562e6287dd69E76771E046f7E24ADC608c837b6`

**multisig address:** `0x608c2DEA3C90849b0182DBD0F1008240881f3C90`

**multisig signees:**

* [Richard](https://twitter.com/wisdant): `0x76C89c2d8cDB9299EE32673026faB8a2A177dCa4`
* [Ji](https://twitter.com/P1ayJ0k3r): `0xEC5c04192A251f6ffD42a48ad3Ee8250F7757D08`
* [Erbil](https://twitter.com/0xErbil) : `0x1BACF76592Be393610cA422D7DDED282330CaED8`

#### Receivable Factoring Pool - Ethereum Mainnet

**PoolProxy contract address:** `0xC902e744916B88BF3a2F0465b651C9AC525A25aC`

**PoolProxy upgrade timelock address:** `0x3b1b39C039cB25701fc708cC8984DC49b0dEc55b`

**PoolConfig contract address:** `0x112dBd143fC64c0e31a706142e711b530fDDF5cd`

**FeeManager contract address:** `0x0140ABA3E70eba261E31eDaef77a5898DDe84bC1`

**Timelock (for PoolConfig and FeeManager) address:** `0xAb3dc5221F373Dd879BEc070058c775A0f6Af759`

**multisig address:** `0x608c2DEA3C90849b0182DBD0F1008240881f3C90`

**multisig signees:**

* [Richard](https://twitter.com/wisdant): `0x76C89c2d8cDB9299EE32673026faB8a2A177dCa4`
* [Ji](https://twitter.com/P1ayJ0k3r): `0xEC5c04192A251f6ffD42a48ad3Ee8250F7757D08`
* [Erbil](https://twitter.com/0xErbil): `0x1BACF76592Be393610cA422D7DDED282330CaED8`
