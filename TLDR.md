# issta22_SPCon 
## issta22 | Finding permission bugs in smart contracts with role mining.
* Motivation：This research focuses on verifying whether the access control policy design of smart contracts is reasonable.
* Key Idea：The author mines the corresponding role permission structure from historical transactions, and conducts a conformance testing on these role permissions to see if there are flaw.、
* Technical challenge: The role and permission information provided by historical transactions is incomplete.
* Solution：The author abstracts the process of recovering from a partial role permission model to a complete model as an optimization problem, and adopts genetic algorithm to obtain the optimal solution.
* Implements and evaluation: The author implements SPCon and evaluate it on the sampled 50 smart contracts within the role mining benchmark. The results show that SPCon can largely reduce the number of mined with better accuracy.

# sp23_WeRLman
## sp23 | WeRLman: To Tackle Whale (Transactions), Go Deep (RL).
* Motivation: This research mainly studies the security impact of the abnormal miner reward brought by MEV on the Proof-of-Work (POW) mechanism.
* Previous Work: Previous work did not consider miner rewards for MEV anomalies, and modeled them with constant rewards.
* Key Idea：The author adopts deep Reinforcement Learning (RL) to build a POW reward model to evaluate possible security issues in the POW mechanism, especially the collapse of the POW reward mechanism caused by MEV.
* Technical challenge：The high reward (i.e., the amount) for miners by MEV will cause the state space that needs to be simulated to become very large.
* Solution: The author obtains a simplified model by simplifying the behavior of miners. The model is two orders of magnitude smaller than the full model and can be solved by dynamic programming.
* Evalution and conlusion：The authors analyzed the historical records of Bitcoin and reveal that the security threshold of Bitcoin (the proportion of computing power required to attack the network) is declining sharply through their proposed model.

# sp23_CF
## sp23 | Clockwork Finance: Automated Analysis of Economic Security in Smart Contracts.
* Motivation: Detect and identify financial security issues of DeFi smart contracts.
* Previous work: Existing works can only detect known and limited DeFi smart contract vulnerabilities.
* Key Idea: The author uses formal verification techniques to automatically reason about and quantify the financial security problems that contracts may encounter.
* Implements：The author instantiate Clockwork Finance Framework (CFF) in the K framework for mechanized proofs.
* Insight: CFF uncovers on average an expected $56 million of EV per month in the recent past.

# ccs22_vrust
## ccs22 | VRust: Automated Vulnerability Detection for Solana Smart Contracts.
* Motivation：Detect security issues with smart contracts on the solana chain.
* Background: Solana is a stateless blockchain, which requires callers to provide the data they need in the parameters of the interface of the contract, which leads to a new attack surface.
* Key Idea：The author developed a static contract verification tool VRust, after converting the contract into the form of MIR, and then comparing the eight fixed vulnerability patterns proposed by the author to detect security issues.
* Evalution： VRust has been evaluated on over a hundred of Solana projects, and it has revealed 12 previously unknown vulnerabilities, including 3 critical vulnerabilities in the official Solana Programming Library confirmed by core developers

# 23_8_27
## sp23 | Three Birds with One Stone: Efficient Partitioning Attacks on Interdependent Cryptocurrency Networks.
* Motivation：This study explores the threat to the security of the blockchain itself if the autonomous systems (ASes) of the blockchain network is not independent.
* Background：ASes own a series of IPs, usually telecom operators or cloud service providers.
* Key Idea: The author exploits characteristics of different blockchains sharing the same ASes, and further partitions Bitcoin and Ethereum by launching a partition attack on the Ripple blockchain first.
* Technical challenge：Blockchain networks are often overlapping and thus it is not easy to mine topological data.
* Solution: Ripple's network information is publicly disclosed, so attacks are launched through Ripple.
* Evalution: 9.4K blockchain nodes can be attacked by partitions.

  
