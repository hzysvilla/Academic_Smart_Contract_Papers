# 23_9_17
## sec23 | Your Exploit is Mine: Instantly Synthesizing Counterattack Smart Contract.
* Motivation: The author studies real-time defense against attacks on smart contracts on the blockchain, specifically, attacks initiated through vulnerabilities in contract implementation.
* Design: The author assumes that relevant attack transactions have been detected, so its main idea is how to identify attack contracts, generate countermeasure contracts, and then front run the attacker's malicious transactions.
* Challenge: How to identify the contract and remove the attacker's access control when generating a counter-contract.
* Approach: For the identification of attack contracts, the author finds the attack contracts by having short deployment time and data flow dependencies between attack transactions. Regarding the attacker's access control when generating the contract, the author bypassed it by replaying the attack transaction and finding the jump statements and transaction attribute parameters (msg.sender or tx.origin).
* Evaluation: The evaluation with 62 real-world recent exploits demonstrates approach's effectiveness, successfully countering 54 of the exploits. 

# 23_9_17
## sec23 | A Mixed-Methods Study of Security Practices of Smart Contract Developers.
* Motivation: The author investigates and analyzes current smart contract developers’ perceptions of security.
* Method: The author first conducted semi-structured interviews and code audit tests on 29 participants, and then conducted an online questionnaire survey on 171 participants.
* Observation1: Current developers do not pay attention to the security of smart contracts. The reasons include that they pay more attention to efficiency, the code is forked from well-known projects, and they rely on security audits.
* Obervation2: Developer awareness of security vulnerabilities is high, with less than half of the participants identifying security vulnerabilities in the audit tasks designed by the authors.
* Obervation3：Simply relying on existing measures such as documentation, reference implementations, and security tools is not enough to help junior developers identify contract security vulnerabilities.
* Insight1: The industry needs to invest more resources in helping developers learn and understand security vulnerabilities.

# 23_9_16
## ISSTA23 | Toward Automated Detecting Unanticipated Price Feed in Smart Contract.
* Motivation: This article focuses on the security issues of blockchain oracles, specifically how to defend against price manipulation problems caused by oracles in real time.
* Key Idea: The author uses formal modeling of the oracle, and then uses actual transactions to test the security of the oracle.
* Design: First, developers need to predefine the specifications of the price oracle and the corresponding verification rules themselves, and then use the transactions in the memory pool to perform symbolic execution in real time using the k framework, and detect whether there is price manipulation based on the amount of tokens in the fund pool.
* Implement: The author implemented their method into a tool VeriOracle.
* Evalution: VeriOracle is effcient in that its verifcation time (about 4s) is less than the block time of Ethereum (about 14s).

# 23_9_15
## ISSTA23 | Detecting State Inconsistency Bugs in DApps via On-Chain Transaction Replay and Fuzzing
* Motivation: The author focuses on state inconsistency vulnerabilities in smart contracts. Specifically, state inconsistency refers to state where the contract does not follow the expectations of developers or users. For example, front-running, reentrancy, and lack of access control are all such vulnerabilities.
* Prior work: Previous research using static analysis has extremely high false positives, while using dynamic analysis requires a sound oracle.
* Key Idea：The authors use historical transactions and their context (state, contract calling relationship) for fuzz testing users to discover such vulnerabilities. In order to avoid using oracles, the author uses the consistency of the state after each transaction sequence is executed to determine whether there are loopholes in the contract.
* Design and implement: The authors implemented their method into a tool IcyChecker. IcyChecker first collects transaction traces, then generates and mutates transaction sequences to fuzz test the Dapp contract, and determines whether there are vulnerabilities in the contract by looking at the state consistency before and after mutation.
* Evaluation：IcyChecker identifies a total number of 277 SI bugs with a precision of 87% on the top 100 popular DApps. nine of flaws have new attack patterns which are never disclosed by
prior research and are reported to corresponding authorities.

# 23_9_14
## ICSE23 | AChecker: Statically Detecting Smart Contract Access Control Vulnerabilities
* Motivation: The author mainly focuses on the access control issue of smart contracts, that is, accessing key variables and codes, and whether the contract implements reasonable access control.
* Key Idea: The author associates the user role of the contract with related state variables to restore the implementation of state access.
* Design：The author first uses backward data flow analysis and heuristic rules to obtain the state variables and specific implementation of access control, and then uses symbolic execution and taint analysis to see whether the state variables can be bypassed to access sensitive code or variables.
* Implement: The authors implemented their method based on eTainter and named it AChecker.
* Evalution: The author verified the effectiveness of AChecker on three data sets: CVE, Smartbug, and Popular contract. AChecker can flag vulnerabilities in 21 frequently-used contracts on Ethereum blockchain with 90% precision.

# 23_9_11
## ISSTA23 | SmartState: Detecting State-Reverting Vulnerabilities in Smart Contracts via Fine-Grained State-Dependency Analysis.
* Motivation: The author focuses on the identification of a type of vulnerability in smart contracts, State-reverting Vulnerability (SRV).
* Key Idea：The author constructed a new state dependency graph (SDG) based on state reading and writing and control flow relationships, and used historical transaction data to help complete the construction of the graph, and then performed SRVs detection based on the graph.
* Design: The author first relies on the read-write relationship of state variables to build SDG in the function, then builds the SDG edges between functions based on control flow and data flow, and then builds some edges that cannot be found by static analysis based on historical transaction guidance. Finally, the author determines whether sensitive state variables lack access control and have uncertain state dependencies on the graph to determine whether there is SRV.
* Implemention: The author built a tool SmartTest to implement the method it proposed.
* Evaluatin：SmartTest achieves a precision of 87.23% and a recall of 89.13% and and detect 11 SRVs on the real contracts.
  
# 23_9_10
## WWW23 | Know Your Transactions: Real-time and Generic Transaction Semantic Representation on Blockchain & Web3 Ecosystem.
* Motivation: The author focuses on how to identify the high-level semantics of blockchain transactions, such as token exchange and liquidity addition.
* Key Idea：The author uses the graph analysis method (network motifs) to first define some basic patterns, and then use these basic patterns to mine token transaction flows.
* Design and Implemention: The author first reconstructs the RPC API of the blockchain client into a parallel design in order to improve efficiency; then extracts transaction flow information from the blockchain, including contract creation, token transfer, eth transfer and other information, to form a semantic graph. Finally, 16 basic patterns were defined, and then advanced semantic mining and inference were performed on the semantic graph.
* Evaluatin：The method proposed by the author can extract nine categories of high-level semantics, which can then be applied in transaction classification and account classification.

# 23_9_9
## FSE23 | DeepInfer: Deep Type Inference from Smart Contract Bytecode.
* Motivation: The author is mainly concerned about the problem of functional interface recovery of closed source contracts. Specifically, the author hopes to recover the type and number of parameters and return values from the contract bytecode.
* Key idea: The author uses static analysis for feature extraction, and then uses machine learning techniques to perform type analysis.
* Challenge: Nested complex types have no fixed rules and are difficult to infer, and the return value requires the entire function to be inferred.
* Method: The author uses multiple neural networks to play different roles at different stages to solve the above Challenges.
* Designt and Implemention: In the first step, the author uses Gigahorse to upgrade bytecode to SSA's IR, then extracts type features (constants, RD relationships) on the IR, and finally builds a CFG on the IR; in the second part, the author first uses the Word2Vec model to restore simple types and complex types Classification of nested types; in the third step, the author uses the sequence generation model to dynamically restore complex nested types; in the fourth step, the author uses the GAT network to learn the return value type from CFG.
* Evaluation: The system designed by the author is superior to existing systems in terms of accuracy and precision, and can adapt to different compiler versions.

# 23_9_8
## issta23 | Beyond “Protected” and “Private”: An Empirical Security Analysis of Custom Function Modifiers in Smart Contracts.
* Motivation: The author investigates and detects the security of modifiers in solidity smart contracts. The modifiers refer to some key conditions at the entrance of the contract function, similar to assert() in C language.
* Challenges: The data dependencies of complex contract state variables and the calling relationships between functions.
* Key Idea: The author constructed a modifiers dependency graph (MDG), abstracted the modifiers into a function, and then used the dependency relationship before the variables and the calling relationship of the function to connect the modifiers with the global state variables and functions into edges, and then in Solve security issues on MDG.
* Design and Implemention: Step 1, the author first uses Slighter to convert the source code into IR, builds MDG on Slighter's IR, and then iteratively constructs new edges (some edges require multiple constructions to obtain) until a fixed point is reached. Step 2, the author uses Z3 to solve on MDG and detects whether any modifiers can be bypassed. Step 3: The author uses NLP technology to cluster the names of decorators and then classify the current decorators.
* Evaluation: The system analyzes a large dataset of 62,464 contracts, over 400 of which were identified with bypassable modifiers.

# 23_9_7
## sec23 | Token Spammers, Rug Pulls, and Sniper Bots: An Analysis of the Ecosystem of Tokens in Ethereum and in the Binance Smart Chain (BNB).
* Motivation: The author mainly focuses on the ecology of tokens in the liquidity pools of Ethereum and Binance Chain, including: token life cycle, token spammers, token trading bots.
* Method: The author ran the full nodes of Ethereum and Binance Chain to collect transaction data, and then collected token information based on the token interface and token events; collected token transaction pair information based on Dex events.
* Insight1：About 60% of tokens are active for less than one day, and 1% of addresses create an anomalous number of tokens (between 20% and 25%).
* Insight2: The author discovered a new scam called a 1-day rug pull, which is a rug pull that occurs in one day. This scam generates $240 million in profits
* Insight3: The author found that some token trading robots in the market are becoming victims of rug pull because they buy tokens without restriction.

# 23_9_6
## ASE23 | DeFiWarder: Protecting DeFi Apps from Token Leaking Vulnerabilities.
* Motivation: The author studies the problem of Token Leaking vulnerability, specifically, the problem that users can withdraw more tokens from DApp abnormally.
* Key Idea: The author analyzes the token transaction flow based on on-chain transactions and calculates the ratio of the user's deposit amount and withdrawal amount to detect Token Leaking vulnerability.
* Implement：The author first extracts the contract call tree in the transaction. The edges are the call relationships of the contracts, and the nodes are the logs of the token contracts. The tree is then heuristically pruned to exclude irrelevant data. Finally, the author merges the token transaction flow from the tree and determines the existence of Token Leaking Vulnerabilities based on the ratio (i.e., withdrawal amount / deposit amount).
* Expriments: The system proposed by author successfully reveals 25 Token Leaking vulnerabilities from 30 Defi apps.

# 23_9_5
## sec23 | Automated Inference on Financial Security of Ethereum Smart Contracts.
* Motivation: The author focuses on how to universally detect vulnerabilities in token contracts.
* Existing work： The program static analysis technology is limited to fixed pattern matching and is not universal; while automatic reasoning technology only intelligently detects a single vulnerability and does not have scalability.
* Key Idea: The author abstracts the relevant variables of the token, and uses automatic reasoning technology to detect the rationality of these abstract variables, and has achieved the purpose of multi-vulnerability detection.
* Implement：The author first uses the K framework to abstract the source code of the token contract, then divides the variables of the token contract into invariant properties (e.g., the total amount of balance) and equivalence property (e.g., the balance of each account), then uses Tamarin prover for automatic reasoning, and finally Use z3 to check whether the relevant variables meet the corresponding constraints.
* Expriments: The system proposed by author can detect transaction order dependency (TOD), timestamp dependency(TD), Reentrancy, gasless send, overflow/underflow, transferMint and the accuracy to identify token contracts is higher than 98%.

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

  
