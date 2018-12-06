# Glossary

__Distributed Ledger Technology (DLT):__ a type of data structure that exists across more then one computer device and is borderless in nature. DLT consists of a data model to capture the state of a ledger, language of transaction, and protocol.

__Blockchain:__ a specific form of distributed ledger technology that constructs a chronologic chain of different blocks.

__Smart Contracts:__ simple computer applications that execute a set of processes when certain conditions within the system are met.

__Aepps:__ Decentralized Applications that run on a blockchain via a smart contract.

__Consensus:__ A system that is dependent on peers agreeing with other peers about a certain decision or state of the blockchain.

__Cryptographic Hashes:__ Are timestamped and can reference the previous blocks. The hash once assigned to a block are immutable and record the transactions in the networks from the genesis block.

__Consensus Algorithms:__ designed to lead to all nodes sharing the duplicate data on the network by achieving agreements among peers on the network. These ensure that data on the ledger is the same for all of the participants, which ultimately, leads too the prevention of malicious actors from attempting to change data on chain.

__Block:__ set of transactions that are recorded. A block consists of metadata such as the previous blocks hashes, a nonce for proof of work, timestamp, and a Merkle tree root.

__Merkle Tree:__ A data structure that is also known as a binary hash tree. It is used to store different hashes of individual data in datasets. This allows for verification of datasets more efficient.

__Transaction:__ a verifiable, secure, ordered event that is packaged together in blocks.

__Cryptography:__ the study of the techniques that secure different data and communication between different parties. It provides immutability and authentication of data on chain.

__Permissioned Blockchain:__ private blockchain requires pre-authorization from participating parties to join and engage the peer-or-peer network.

__Permissionless Blockchain:__ public blockchains meaning any person can join and engage the peer-to-peer network.

__Peer-to-Peer Network (P2P):__ Computer systems which are directly connected to each other on a network without a central server.

__Peer:__ a node on a peer-to-peer network that contributes computing power and storage that is needed to maintain the network.

__Immutability:__ Characteristic or state that cannot be changed after it is created.

__Trustless:__ Trust in a centralized actor is not required it as the data and network is distributed amongst all peers in a system so that trust in any one centralized authority is removed.

__Blockchain Governance:__ A governance system must have incentives for peers to participate, and methods of coordination to come to an agreement on methods of change. As a blockchain lacks a central authority. There are multiple governance strategies that can be implemented such as a Benevolent Dictator, Open Governance, On-Chain Governance, and a Core Development Team.

__Decentralized Network:__ system operates without any central authority rather a system. The system depends on all peers on the network making decisions for themselves via consensus.

__Distributed System:__ A network whose components are located across different machines. The machines coordinate events by communicated with peers on the system.  

__Proof of Work (PoW):__ a consensus algorithm that involves peers solving a computational challenging puzzle so new blocks are created. Peers "Mine" blocks on the network and are incentivized to solve the computational problem with economic payoffs.

__Proof of Stake (PoS):__ A consensus algorithm that relies on Forgers to validate transactions to earn a set transaction fee. Peers are randomly selected on the network to validate blocks.

__Proof of Authority (PoA):__ a consensus algorithm which uses designated authorities whose job is to provide permissions to nodes so they can create new blocks. All major authorities must come to consensus for new blocks to be created.

__Proof of Capacity (PoC):__ A consensus algorithm that requires a user to show that they have a legitimate interest in a service (such as sending an email) by giving a amount of memory or disk space to solve a challenge presented by the host.

__Proof of Burn (PoB):__ A consensus algorithm peers sow that they 'burned coins". Burning coins means that they sent the coins to a verifiable address that does not let them spend the coin. Essentially, peers are willing to undergo a short-term loss for long-term economic gain.

__Proof of Elapsed Time (POET):__ a consensus algorithm follows a fair lottery system that is often found on permissioned blockchain networks the lottery decides block winners among peers by spreading the chances of winning fairly across the largest possible number of participants.

__Proof of location (PoL):__ a consensus algorithm requires peers to privately record and authenticate location data at set times that reveal their personal information at their discretion by presenting a location claim.

__Simplified Byzantine Fault Tolerance (SBFT):__ A set of characteristics (variables) that defines a system that can tolerate a class of failures that belong to the Byzantine Generals problem.

__Byzantine Generals Problem:__ The problem is to find a reliable computer system that can handle multiple malfunctioning components that give conflicting information
to different parts of a system. The common abstract thought game that was originally provided in the 1982 SRI international paper Titled ["The Byzantine Generals Problem"](https://people.eecs.berkeley.edu/~luca/cs174/byzantine.pdf) a group of
generals in the Byzantine army along with their troops have an enemy city surrounded. The Generals can only communicate via messenger, the generals (peers) need too agree upon a common battle plan to win. The generals know that one or more of the generals may be traitors who will try to confuse the loyal generals by misinforming the others about their plans. In order to solve the problem an algorithm needs to be constructed that ensures only the loyal generals will reach an agreement about the tactics they use to attack the city.

__State Channels:__ Events and processes that could occur on the Main Blockchain that instead occur in off chain channels without increasing any risk to users of the blockchain leading too increased speed and scalability paired with decreased costs.

__Scalability:__ the ability of a network to handle a growing amount of users and therefore work.

__Oracles:__ A third-party information source that provide increased functionality to smart contracts by providing a method of communication outside of a blockchain network.

__AENames:__

__Time-to-Live (TTL):__ The time that data can exist on a network before being removed.






```
__æternity:__
æternity is a decentralized, public blockchain that uses the GHOST consensus protocol, with Proof-of-Work (PoW) for security and Proof-of-Stake (PoS) for governance. æternity is an account-based system, like Ethereum, and does not use Bitcoin-style unspent transaction outputs (UTXO).

Real-world data can interface with smart contracts through decentralized “oracles”. Scalability and trustless Turing-complete state channels set æternity apart from other Blockchain 2.0 projects.

Source

__æternity token:__
The æternity token (AE) is used as payment for any resources that users consume on the platform, e.g. sending payments, using oracles, etc. The distribution of AE in the genesis block will be determined by a smart contract hosted on Ethereum. More AE will be created via mining.

__Application-specific integrated circuit (ASIC):__
An application-specific integrated circuit (ASIC) /ˈeɪsɪk/, is an integrated circuit (IC) customized for a particular use, rather than intended for general-purpose use. For example, a chip designed to run in a digital voice recorder or a high-efficiency Bitcoin miner is an ASIC. Application-specific standard products (ASSPs) are intermediate between ASICs and industry standard integrated circuits like the 7400 series or the 4000 series.

Source

__Blockchain:__
A block chain is a transaction database shared by all nodes participating in a system based on the Bitcoin protocol. A full copy of a currency’s block chain contains every transaction ever executed in the currency. With this information, one can find out how much value belonged to each address at any point in history.

This ledger of past transactions is called the block chain as it is a chain of blocks. The block chain serves to confirm transactions to the rest of the network as having taken place.

Source Source

__Cuckoo Cycle:__
æternity uses Cuckoo Cycle as the ASIC-resistant mining algorithm to avoid centralizing mining power in the hands of a few large mining pools.

Cuckoo Cycle is the first graph-theoretic proof-of-work, and the most memory bound, yet with instant verification.

From this point of view, Cuckoo Cycle is a very simple PoW, requiring hardly any code, time, or memory to verify.

Finding a 42-cycle, on the other hand, is far from trivial, requiring considerable resources, and some luck (for a given header, the odds of its graph having a L-cycle are about 1 in L).

Its large memory requirements make single-chip ASICs economically infeasable for Cuckoo Cycle.

__GHOST consensus protocol:__
GHOST is short for the Greedy Heaviest Observed Subtree chain selection rule which was a proposed modification for the Bitcoin blockchain.

GHOST orignally was a protocol modification, a chain selection rule, that makes use of blocks that are off the main chain to obtain a more secure and scalable system.

With that modification, it is possible to speed up the blockchain to a velocity of up to 1 block per second. The result is a general higher possible transaction rate without compromising the blockchain consensus and security.

[Source](https://ethereum.stackexchange.com/questions/314/what-is-ghost-and-what-is-its-relationship-to-frontier-and-casper

__Consensus:__
When several nodes (usually most nodes on the network) all have the same blocks in their locally-validated best block chain.

__Faucet (cryptocurrency):__
Bitcoin faucets are a reward system, in the form of a website or app, that dispenses rewards in the form of a satoshi, which is a hundredth of a millionth BTC, for visitors to claim in exchange for completing a captcha or task as described by the website. There are also faucets that dispense alternative cryptocurrencies.

__Genesis block:__
A genesis block is the first block of a block chain. Modern versions of Bitcoin number it as block 0, though very early versions counted it as block 1. The genesis block is almost always hardcoded into the software of the applications that utilize its block chain. It is a special case in that it does not reference a previous block, and for Bitcoin and almost all of its derivatives, it produces an unspendable subsidy.

Source

__Hashcash PoW:__
Hashcash is a proof-of-work algorithm that requires a selectable amount of work to compute, but the proof can be verified efficiently. For email uses, a textual encoding of a hashcash stamp is added to the header of an email to prove the sender has expended a modest amount of CPU time calculating the stamp prior to sending the email. In other words, as the sender has taken a certain amount of time to generate the stamp and send the email, it is unlikely that they are a spammer. The receiver can, at negligible computational cost, verify that the stamp is valid. However, the only known way to find a header with the necessary properties is brute force, trying random values until the answer is found; though testing an individual string is easy, if satisfactory answers are rare enough it will require a substantial number of tries to find the answer.

__Merkle tree (hash tree):__
In cryptography and computer science, a hash tree or Merkle tree is a tree in which every leaf node is labelled with the hash of a data block and every non-leaf node is labelled with the cryptographic hash of the labels of its child nodes. Hash trees allow efficient and secure verification of the contents of large data structures. Hash trees are a generalization of hash lists and hash chains.

Hash trees can be used to verify any kind of data stored, handled and transferred in and between computers. They can help ensure that data blocks received from other peers in a peer-to-peer network are received undamaged and unaltered, and even to check that the other peers do not lie and send fake blocks.

__Mining:__
In cryptocurrency networks, mining is a validation of transactions. For this effort, successful miners obtain new cryptocurrency as a reward. The reward decreases transaction fees by creating a complementary incentive to contribute to the processing power of the network. The rate of generating hashes, which validate any transaction, has been increased by the use of specialized machines such as FPGAs and ASICs running complex hashing algorithms like SHA-256 and Scrypt. This arms race for cheaper-yet-efficient machines has been on since the day the first cryptocurrency, bitcoin, was introduced in 2009. However, with more people venturing into the world of virtual currency, generating hashes for this validation has become far more complex over the years, with miners having to invest large sums of money on employing multiple high performance ASICs. Thus the value of the currency obtained for finding a hash often does not justify the amount of money spent on setting up the machines, the cooling facilities to overcome the enormous amount of heat they produce, and the electricity required to run them.

Bitcoin mining is intentionally designed to be resource-intensive and difficult so that the number of blocks found each day by miners remains steady. Individual blocks must contain a proof of work to be considered valid. This proof of work is verified by other Bitcoin nodes each time they receive a block. Bitcoin uses the hashcash proof-of-work function.

Source Source

__Nonce (cryptography):__
In cryptography, a nonce is an arbitrary number that can only be used once. It is similar in spirit to a nonce word, hence the name. It is often a random or pseudo-random number issued in an authentication protocol to ensure that old communications cannot be reused in replay attacks. They can also be useful as initialization vectors and in cryptographic hash functions.

Nonces are used in proof-of-work systems to vary the input to a cryptographic hash function so as to obtain a hash for a certain input that fulfills certain arbitrary conditions. In doing so, it becomes far more difficult to create a “desirable” hash than to verify it, shifting the burden of work onto one side of a transaction or system. For example, proof of work, using hash functions, was considered as a means to combat email spam by forcing email senders to find a hash value for the email (which included a timestamp to prevent pre-computation of useful hashes for later use) that had an arbitrary number of leading zeroes, by hashing the same input with a large number of nonce values until a “desirable” hash was obtained.

Source

__Oracle:__
Oracles are trusted entities signing claims about the state of the world - RPCs, gateways to input/output with the physical realm.

They form the ability to refer to values from real-world data.

An oracle is a mechanism that tells the blockchain facts about the real-world we live in (e.g. the weather, the closing price of Apple shares on a particular date, sports events, or human deaths). æternity’s oracle system(21) uses the same governance mechanism as the æternity blockchain itself, it does not require a separate governance layer on top of the æternity main-net (22) (as with Augur on top of Ethereum).

Typed oracles as primitives on the blockchain provide a well-defined way for smart contracts to interface with data from the outside world. Data-feeds from individuals or institutions can directly interface with the blockchain and provide data for smart contracts.

Source Source

__Proof-of-stake (PoS):__
Proof of stake (PoS) is a type of algorithm by which a cryptocurrency blockchain network aims to achieve distributed consensus. In PoS-based cryptocurrencies, the creator of the next block is chosen via various combinations of random selection and wealth or age (i.e., the stake). In contrast, the algorithm of proof-of-work-based cryptocurrencies such as bitcoin uses mining; that is, the solving of computationally intensive puzzles to validate transactions and create new blocks.

Proof-of-stake currencies can be more energy efficient than currencies based on proof-of-work algorithms.

Source

__Proof-of-work system (PoW):__
A proof-of-work (PoW) system (or protocol, or function) is an economic measure to deter denial of service attacks and other service abuses such as spam on a network by requiring some work from the service requester, usually meaning processing time by a computer.

A key feature of these schemes is their asymmetry: the work must be moderately hard (but feasible) on the requester side but easy to check for the service provider. This idea is also known as a CPU cost function, client puzzle, computational puzzle or CPU pricing function. It is distinct from a CAPTCHA, which is intended for a human to solve quickly, rather than a computer.

ReasonML
Reason lets you write simple, fast and quality type safe code while leveraging both the JavaScript & OCaml ecosystems.

__Smart Contract:__
A smart contract is a computer protocol intended to digitally facilitate, verify, or enforce the negotiation or performance of a contract. Smart contracts allow the performance of credible transactions without third parties. These transactions are trackable and irreversible.

The aim of smart contracts is to provide security that is superior to traditional contract law and to reduce other transaction costs associated with contracting. Various cryptocurrencies have implemented types of smart contracts.

With the present implementations, based on blockchains, “smart contract” is mostly used more specifically in the sense of general purpose computation that takes place on a blockchain or distributed ledger. In this interpretation, used for example by the Ethereum Foundation or IBM, a smart contract is not necessarily related to the classical concept of a contract, but can be any kind of computer program.

A major limitation of smart contracts is that they are unable to communicate with resources external to the blockchain they are secured on. In practice, this means that smart contracts are not able to trigger based on real-life events. This is known as “the oracle problem”, after test oracles. Oracles provide external data and trigger smart contract executions when pre-defined conditions are met, providing connectivity to the outside world.

The overreaching functional goal of Æternity smart contracts is to be able to execute code on the chain. That is, code execution that is verified by a miner and which can alter the state of the chain. A contract runs on a virtual machine. A smart contract is associated with a virtual machine for the execution of that contract. The AEternity blockchain supports four virtual machines.

Further reading (here)(https://en.wikipedia.org/wiki/Smart_contract ) and (here)(https://github.com/aeternity/protocol/blob/master/contracts/contracts.md)

__Solution-verification PoW:__
Solution-verification protocols do not assume such a link: as a result the problem must be self-imposed before a solution is sought by the requester, and the provider must check both the problem choice and the found solution. Most such schemes are unbounded probabilistic iterative procedures such as Hashcash.

__State channel:__ State channels enable highly scalable, trustless transactions of value and purely functional, easily verifiable Turing-complete smart contracts.

State channels offer a way to scale “off-chain” by only storing channel opening and closing information on the blockchain. Two parties deposit tokens into a channel when they open it and the sum of two deposits is the only amount of tokens that can be used within that channel. The state of the channel is the current balance of each party, co-signed by both parties. There can be multiple exchanges of state between the parties but only the last undisputed state becomes the final closing state of the channel. Each message in the channel carries an ever-increasing counter and the message with the highest counter value is considered to be the last state.

State channels come from the realization that, for most purposes, only the actors involved in a smart contract are required to know about it. Two or more actors lock a state and a contract on the blockchain and then perform signed transactions between themselves, off of the public network (or off-chain). The final state is then written to the blockchain. If the end result is disputed, the series of signed off-chain transactions can be uploaded to the blockchain for verification or dispute resolution

[Source](https://github.com/aeternity/aeternity-reimagined/blob/master/state-channels.md
[Source](https://en.wikipedia.org/wiki/%C3%86ternity#State_channels

__Solidity:__
Solidity is a contract-oriented, high-level language for implementing smart contracts. It was influenced by C++, Python and JavaScript and is designed to target the Ethereum Virtual Machine (EVM).


__Sophia (programming language):__
An AEternity BlockChain Language - Sophia is a dialect of ReasonML.

Sophia is customized for smart contracts, which can be published to a blockchain (the AEternity BlockChain). Thus some unnecessary features of Reason (and OCaml - since Reason is closely related to OCaml) have been removed, and some blockchain specific primitives, constructions and types have been added.

The Functional Typed Warded Virtual Machine is used to efficiently and safely execute contracts written in the Sophia language.

__Virtual Machine:__
A virtual machine is a computer program which provides the services usually provided by a computer, but which runs on another computer, which may be of the same type, but as easily may not. Blockchains provide virtual machines in order to enable programs to be run on the blockchain.

The Ethereum Virtual Machine focuses on providing security and executing untrusted code by computers all over the world. To be more specific, this project focuses on preventing Denial-of-service attacks, which have become somewhat common in the cryptocurrency world. Moreover, the EVM ensures programs do not have access to each other’s state, ensuring communication can be established without any potential interference.

To put this into a language everyone can understand, the Ethereum Virtual Machine is designed to serve as a runtime environment for smart contracts based on Ethereum. As most cryptocurrency enthusiasts are well aware of, smart contracts are very popular these days. This technology can be used to automatically conduct transactions or perform specific actions on the Ethereum blockchain. Many people predict smart contracts will help revolutionize finance and other industries over the coming years.

The AEternity blockchain supports four virtual machines.

HLM - A high level machine for executing logical formulas and blockchain operations.
FTWVM - A Functional Typed Warded Virtual Machine
AEVM - A version of the Ethereum VM
FAEVM - A fast version of the Ethereum VM
```
