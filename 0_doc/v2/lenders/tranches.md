## Tranches

Tranche support is vital for institutions participating in the Huma protocol.  As mentioned before. there are two types of tranches: senior and junior. The senior tranche is generally seen as a lower-risk investment. It offers a modest yield but carries less risk. If there's a default, senior tranche lenders receive payment first. The junior tranche, on the other hand, assumes a higher risk and earns a higher yield when things go smoothly. If there's a default, junior tranche lenders are paid after those in the senior tranche.

### Yield Distribution Policies

In V2, we introduce two yield distribution policies: fixed yield and risk-adjusted yield.

- In fixed yield mode, the senior tranche yield remains constant as long as risk loss doesn't prevent this.
- In risk-adjusted yield mode, the yield is first determined by the senior-junior asset ratio, and then a portion of the return is transferred from the senior to the junior tranche. For instance, a 20% adjustment means shifting 20% of the return from the senior to the junior tranche.

### Protection From Losses

To guarantee adequate protection for the senior tranche, a maximum leverage ratio is set between the senior and junior tranches for each pool. A 4:1 ratio means that a minimum of 20% of the pool should be junior tranches and a maximum of 80% can be senior tranches. As long as no more than 20% of the pool defaults, the principal of the senior tranche remains secure.
