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
