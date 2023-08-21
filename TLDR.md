# issta22_SPCon 
## issta22 | Finding permission bugs in smart contracts with role mining
* Motivation：This research focuses on verifying whether the access control policy design of smart contracts is reasonable.
* Key Idea：The author mines the corresponding role permission structure from historical transactions, and conducts a conformance testing on these role permissions to see if there are flaw.、
* Technical challenge: The role and permission information provided by historical transactions is incomplete.
* Solution：The author abstracts the process of recovering from a partial role permission model to a complete model as an optimization problem, and adopts genetic algorithm to obtain the optimal solution.
* Implements and evaluation: The author implements SPCon and evaluate it on the sampled 50 smart contracts within the role mining benchmark. The results show that SPCon can largely reduce the number of mined with better accuracy.
