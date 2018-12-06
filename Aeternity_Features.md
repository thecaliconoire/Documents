# *__Aeternity Features__*

## __Oracles__
An __oracle__ is an entity on the blockchain. It lives in the oracle state tree as a full node. Oracles are third-party information providers. They allow users to broadcast an oracle on the blockchain, and for other users to query the broadcasted oracle for the desired information.  
An __oracle operator__ creates an oracle by creating a __oracle register transaction__ on the chain. Then the oracle can be queried about the transaction creating a __oracle query object__ in a state tree. The oracle then can scan the transactions on the blockchain. The __oracle operator__ responds to the query by posting an __oracle response transaction__. The oracle response transaction leads to the oracle response modifying the oracle query object on the chain after the response is added, the oracle query object is closed and is now immutable.
For further information and examples on aeternity oracles please check the [Oracle Protocol](https://github.com/aeternity/protocol/blob/master/oracles/oracles.md).

# __Aeternity Naming System (AEN)__
The __aeternity naming system (AEN)__ is designed too create user friendly human readable names for account addresses. A common practice in blockchain systems is to represent account addresses in a hex or base64/base58 notation. This makes it harder and more confusing for users to use the system. The AEN system is similar too the concept of Domain Name Systems (DNS) that allows for human readable names to represent an IP address. However, instead of representing an IP address AENs represent your account address. For more information regarding the AEN systems please read the [AEN protocol](https://github.com/aeternity/protocol/blob/master/AENS.md).

## __Smart Contracts__
A __smart contract__ is a program on the blockchain that resides in a contract state tree as a full node. The contracts themselves run on a virtual machine and are created when an owner creates the contract and broadcasts it to the chain. An aeternity contract when deployed on the blockchain, will be verified by a node before execution. After the execution of the contract the chain will be changed.
A contracts execution should be safe, efficient, scalable, cheap and should be able to migrate from Ethereum smart contracts.

### __Sophia language__
Sophia is the first smart contract language for the aeternity blockchain. It is apart of the Meta language (ML) family. Sophia's closest relation is to [ReasonML](https://reasonml.github.io/). Similar to ReasonML, Sophia is strongly typed, meaning that type errors are always detected and the language allows for identification of misused variables that result in type errors. The language has a restricted mutable state in other words, it has a limited form of state associated with each contract. The language itself is written for smart contract functionality, and therefore does not allow for certain functions such as floating point arithmetic. It is highly recommended too read over the [Sophia Protocol](https://github.com/aeternity/protocol/blob/master/contracts/sophia.md) to gain a fundamental understanding of how to write a smart contract on the Aeternity Blockchain.

## __State Channels__
__State Channels__ are off chain channels that allow entities on the aeternity blockchain to communicate with each other. The channels allow for smart contracts to be executed off chain. The benefits of state channels include an increase in privacy, speed and scalability.

_Privacy_ is increased due to the parties being able to hide their nature and identity and they can communicate to one another in their shared state channel. In comparison the main chain, makes no effort to hide the nature of parties or the parties identity. _Security_ on a state channel is the exact same as on the main channels. It has the same liveness features and remains trustless.

The _Speed_ of operations is increased once a state channel is established between the parties. However, when the channel is first established the normal on chain latency will occur.

The creation of a state channels require a minimum of two transactions. One to open the channel and one to close it. However, once the channel is open no other transactions are required until the channel is closed. The use of a state channel outside of opening or closing the state channel are up to the users discretion. For more details read the [state channel protocol](https://github.com/aeternity/protocol/blob/master/channels/README.md#goals).

For a more in depth understanding of other features that the aeternity blockchain provides please read the protocol document that covers the features above as well as aeternity's Epoch, and governance system. For more general information please read our [General](https://blog.aeternity.com/%C3%A6ternity-frequently-asked-questions-faq-9cb0e34e0740), [Technical](https://blog.aeternity.com/frequently-asked-questions-faq-general-tech-questions-f61e1353a6ca) and [Mainnet](https://blog.aeternity.com/frequently-asked-questions-faq-mainnet-launch-9ec87ad850a7) FAQ sheets.
