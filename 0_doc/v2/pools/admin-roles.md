## Admin Roles
### Protocol Admin Roles

- **Protocol Owner:** The Protocol Owner (a multi-sig) is responsible for administering the entire protocol. This is the only account that can change various protocol configurations and perform administrative tasks, most notably, adding and removing pool owners and pausers, unpausing the protocol, and transferring protocol income from the pool wallet to the protocol treasury.
- **Protocol Owner Treasury:** The Protocol Owner Treasury account contains the protocol fees collected from pools. It is kept separate from the Protocol Owner account to avoid concentrating too much power in one account and to enhance security.
- **Pausers:** Pausers can pause the entire protocol. When the protocol is paused, no money moves out of the protocol. This is expected to happen in sporadic cases, where the safety and integrity of the protocol are threatened. There can be multiple pausers, including external security monitoring firms. After the protocol is paused, only the Protocol Owner can unpause it.

### Pool Admin Roles

- **Pool Owners:** Pool Owners are addresses approved by the Protocol Owner to create and manage pools. They set key parameters, choose the Evaluation Agent, and establish the fee structure through the Fee Manager. Additionally, they earn a portion of the pool income as a reward.
- **Pool Owner Treasury:** The Pool Owner Treasury account contains the pool owner fees collected from the pools owned by the pool owner. It is kept separate from the Pool Owner account to avoid concentrating too much power in one account and to enhance security.
- **Pool Operators:** Pool Operators act as operational staff supporting the Pool Owner. They review the results of KYC/KYB and accreditation, and they approve lenders. Pool Operator accounts do not need to be multi-sigs.
- **Evaluation Agents:** Evaluation Agents (EA) are responsible for approving or disapproving credit requests. Each pool is managed by a single EA. While we expect most EAs to operate automatically, the protocol also allows for human supervision. EAs earn a portion of the pool's income as a reward for their services.

To ensure accountability, EAs, like Pool Owners, must invest capital in the pools they oversee. A pool can only start accepting capital from other Lenders after both the Pool Owner and the EA have made the necessary deposits. Pool Owners may occasionally change the pool's EA. The incoming EA must fulfill the deposit requirements before the change is implemented. The outgoing EA is paid all accumulated rewards immediately after the change occurs.
