# 23_9_4
## sec23 | Smart Learning to Find Dumb Contracts.
* Motivation: The author studies the problem of smart contract vulnerability detection, specifically, how to extend the source code level analysis capabilities of existing formal detection tools to bytecode.
* Key Idea: The author uses static analysis tools to perform supervised learning at the source code level, then compiles the source code into bytecode, and then performs machine learning by matching the source code-level vulnerability results with the bytecode.
* Implement：The system proposed by the author first uses slither to analyze the contract source code, then compiles the source code into bytecode, and then associates the bytecode with slither's detection results.
* Challenge: For close source contracts, the author will perform similarity analysis twice, the first time It is used to filter out those bytecodes with vulnerabilities that are similar to those that have been detected, and the second test is for vulnerability detection.
*  Expriments: The system proposed by author leads the pack with a 100% Completion Rate, 99.7% Accuracy, and 0.2 second average contract analysis time, i.e., 10-1,000x faster than competitors. Besides, the True Positive Rate is 98.7% and False Positive Rate is 0.6%.

# 23_9_3
## sec23 | Snapping Snap Sync: Practical Attacks on Go Ethereum Synchronising Nodes.
* Motivation: This research focuses on the security issue of the synchronization mechanism of the Ethereum client (i.e., go-ethereum), that is, by interfering with the synchronization mechanism of Ethereum to achieve the purpose of forking the blockchain.
* Key Idea: The author uses some defects in the synchronization mechanism of the Ethereum client (geth), such as the chain import mechanism, the state pruning mechanism, and the segmented block verification mechanism, to construct three types of different attack schemes.
* Scope: geth in Ethereum mainnet before PoS fork, Ethereum Classic, Ethereum PoW.
* Implementation: The first Attack method uses the block import mechanism and state pruning mechanism to invalidate the legal chain; the second attack method uses the characteristics of the client to randomly verify blocks, constructs false blocks, and attacks consensus; third attack method is a combination of the first two.
* Cost: The optimal cost of this attack only requires one millionth of the mining computing power to achieve the purpose of forking the blockchain.


# 23_9_2
## ccs22 | Towards Automated Safety Vetting of Smart Contracts in Decentralized Applications
* Motivation: The author mainly studies the inconsistency between the front-end UI of the DApps and the back-end contract of the DApps, and then does some risk research on the DApps.
* Prior Study: Previous work mainly used heuristic rules to detect Dapp vulnerabilities, which is not universal.
* Approach: The author first uses static analysis to extract the program semantic graph from the DApp's contract code, then extracts the business logic of the contract from the DApp's UI, and then conducts consistency detection and risk verification.
* Innovation：The author uses the UI info to obtain the business logic of the Dapp (i.e., the specifications in formal analysis).
* Evalution: The author discovers 19 new safety risks in the wild, such as expired lottery tickets and double voting.

# 23_9_1
## raid22 | Penny Wise and Pound Foolish: Quantifying the Risk of Unlimited Approval of ERC20 Tokens on Ethereum
* Motivation: The author studies the status quo, risks, and security issues of unlimited approvals in ERC20 tokens, and proposes a best practice for user-initiated approvals.
* Background：The approval mechanism is used to delegate the privilege of spending users’ tokens to DApps. However, current Dapps usually allow users to grant unlimited approval quotas without the user's knowledge, which exposes users' assets to risk.
* Approach: The author first analyzes the transaction history of Ethereum and defines some indicators (such as amount) to quantify the severity of the current unlimited approvals. Then, for some well-known wallets and exchanges, check their approval process and evaluate the current industry's emphasis on unlimited approval. Finally, the authors propose a set of best practice approval processes for users.
* Insight1：The research reveals that 60% of collected approval transactions belong to unlimited approval transactions, and a majority of unique users (2.9m/4.9m) have participated in unlimited approval transactions.
* Insight2：Only 10% of DApps and wallets provide explanatory information for the approval mechanism, and only 16% of UIs enable users to adjust approval amounts.
* Insight3：The evaluation result suggests that only 0.2% (2,475/1,496,886) of investigated users mitigate risk by following best practices.


# 23_8_31
## ndss23 | Smarter Contracts: Detecting Vulnerabilities in Smart Contracts with Deep Transfer Learning
* Motivation: How to efficiently, fine-grained and scalable detect vulnerabilities in smart contracts.
* Prior work: Non-machine learning methods, such as program analysis, are inefficient and not scalable; machine learning-based methods rely on source code and intelligently perform binary classification.
* Approach: The author utilizes transfer learning to quickly and lightweightly train a network containing new vulnerabilities while ensuring multi-classification of vulnerabilities.
* Implement：The author first obtains the contract bytecode from the blockchain, then uses the existing vulnerability detection tools (e.g., Oyente, Mythril, Vandal, Maian) to label the contract, and finally sends it to the neural network for training.
* Evaluation：The tool from this study can detect 11 vulnerability classes in 0.15s per smart contract on average and yields an average F1 score of 97% across all evaluated classes.

# 23_8_30
## ndss23 | Double and Nothing: Understanding and Detecting Cryptocurrency Giveaway Scams.
* Motivation: The authors measure and investigate the current state of attackers using websites to phish victims with high cryptocurrency rebates.
* Approach: The author used the certificate information to obtain a large number of phishing websites of attackers, and then conducted a lot of analysis on the information of these websites. In addition, the author also analyzed the relevant transactions of the attacker's wallet account to assess the loss.
* Observation1: During the six months the authors studied, a total of 10,079 phishing sites were observed, an average of 55.7 phishing sites per day.
* Observation2: During the six months the authors studied, attackers have stolen the equivalent of tens of millions of dollars.
* Observation3: The author extracts the transactions corresponding to 2,266 wallets belonging to scammers.

# 23_8_29
## sec23 | A Large Scale Study of the Ethereum Arbitrage Ecosystem
* Motivation: How will the current large-scale arbitrage affect the blockchain ecology.
* Background: Arbitrage is defined as the simultaneous purchase and sale of the same asset in two different markets for advantageously different prices.
* Key idea1：The author proposes a method based on graph analysis to identify arbitrage behavior. First, the author identifies token behavior, then constructs a token transaction graph, then finds whether there is a cycle in the graph, and finally extracts arbitrage information.
* Key idea2：The author replays historical transactions to identify arbitrage opportunities that have existed in the past.
* Observation 1: The income generated by current arbitrage may be enough to make miners evil, because it far exceeds the income generated by consensus mining.
* Observation 2: The current arbitrage benefits may make oracle price manipulation attacks easier to implement.


# 23_8_28
## sp22 | Quantifying Blockchain Extractable Value: How dark is the forest?
* Motivation：Quantify and expand the profits of current blockchain extractable value (BEV) and analyze the harm of BEV to the current blockchain consensus.
* Measurement：The author quantifies the profits brought by miner arbitrage, sandwich attacks, and  liquidation.
* Key Idea: The author proposes an algorithm for replayed transactions to estimate the profits that are not calculated by BEV.
* Contribution: The author formalizes the BEV relay concept as an extension of the P2P transaction fee auction model.
* Conclusion: BEV relay not only did not alleviate the network load, but jeopardized the consensus of the blockchain. The algorithm from author extends the total captured BEV by 35.18M USD.



# issta22_SPCon 
## issta22 | Finding permission bugs in smart contracts with role mining.
* Motivation：This research focuses on verifying whether the access control policy design of smart contracts is reasonable.
* Key Idea：The author mines the corresponding role permission structure from historical transactions, and conducts a conformance testing on these role permissions to see if there are flaw.
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

  
