---
description: >-
  This guide briefly describes the ways to study the network for different cases
  of its use as a developer.
cover: ../.gitbook/assets/Developer Guide (2).png
coverY: 0
---

# 👉 Developer Guide

## Overview

Before reading the material below, it is advisable to be familiar with the basic description of the network, which can be read [**here**.](../about/introduction.md)

### Foreword

Everscale has an incredibly wide range of potential opportunities, taking into account all the known bottlenecks of popular blockchains, and that is why Everscale is significantly different from other networks, but in essence it is extremely logical in architecture.

### Let's start!

We believe you have already read the Everscale Overview section and have a basic understanding of the principles of the network and its ideology. Below we will take a closer look at the constituent elements of the network.

Let us clarify that this guide will be useful both for those who want to write or scale their protocol from scratch from other networks, and for those who want to partially use Everscale in their projects.

Before you start interacting with the network, you need to study each of its several basic elements in order to take into account possible controversial points and pitfalls in the process of writing code.

### Data presentation

The fundamental basis for understanding how the network works is the understanding of the fact that TVM (Ton Virtual Machine, about it a little later) represents all data in the form of a set or package of so-called cells. In turn, each cell can contain up to 1023 bits of data, as well as up to four link references to other cells. The cells are organized among themselves in the form of a tree, or rather a directed acyclic graph (GAQ).

We recommend that you read more about the cells in the section \[1.1, 4, 3.1] of [**Everscale White Paper**](https://everscale.network/docs/everscale-whitepaper.pdf)****

### Blockchain structure. Dynamic sharding.

The Everscale blockchain is a collection of blockchains (even a collection of blockchains of blockchains) as a single blockchain is not capable of reaching the processing speed of millions of transactions per second. Detailed structure of the blockchain architecture: A unique masterchain containing general information about the protocol and the current values ​​of parameters: a set of validators and their stakes, many currently active workchains and their "shards", and most importantly, a set of hashes of the latest blocks of all workchains and shardchains.

Several working blockchains - workchains, which are "workhorses" and contain transfers and transactions of the main part of smart contracts. Different workchains can have different "rules", that is, different account address formats, different transaction formats, different virtual machines for smart contracts, different main cryptocurrencies, and so on.

Each workchain, in turn, divides up to 2 ^ 60 shardchains, which have the same rules and block format as the workchain itself, but are responsible only for a dynamically determined subset of accounts, depending on the first few (most significant) bits of the account address. This is how a truly working dynamic sharding is implemented.

We recommend that you familiarize yourself with the network architecture in more detail in the corresponding section \[5] of the [White Paper](https://everscale.network/docs/everscale-whitepaper.pdf).

### Account

In the context of the Everscale blockchain, a smart contract and an account are one and the same, so these terms can be used interchangeably, at least if we work with small (simple) smart contracts. An account is identified by its full address and is fully described by its state. In other words, the account contains nothing but its address and status.

In accordance with the infinite sharding (ISP) paradigm, each account is considered to be in a separate "accountchain", and the (virtual) blocks of these accountchains will be grouped into shardchain blocks to improve efficiency. In particular, the state of a shardchain is, roughly speaking, the state of all its accountchains. Similarly, a shardchain block essentially consists of a collection of virtual "blocks" of some accounts assigned to a given shardchain. Thus, we get a large number of "account-chains", each of which describes a change in the state of only one account. Also, account-chains send messages to each other to transfer data.

As mentioned earlier, in TVM, almost all data is a cell or a collection of cells, and accounts are no exception. The account state includes some data: balance, data and code of a smart contract, permanent data of a smart contract in the form of a tree.

P.S In the zero status (block), there are system accounts and special addresses set manually. They do not pay commissions and use network features that are not used anywhere else, such as Tick and Tock transactions (read more about the latter in the Transactions section).

### Messages

An important part of the Everscale blockchain is the inter-blockchain messaging system.

Each transaction in the network consists of an account that receives one message, changes its state according to certain rules, and can generate 1 more message for other accounts. Each message is generated and delivered once.

In the paradigm of infinite sharding, each account is on its own separate account chain, and the only way to influence the state of any account is to send a message. This means that messages play a fundamental role in the system, comparable to the role of accounts (smart contracts).

External inbound messages help to deploy and invoke the contract from the outside. Internal messages allow contracts to communicate with each other. External outbound messages are used for events that can be found and processed externally.

For example, a simple value transfer can be triggered by an external incoming message (from a person or some service), or an internal message from another contract. This message will create a transaction and an additional internal message with a value passing.

For more information on all information about messages within the network, you can in the [Whitepaper](https://ton.org/tblkch.pdf), in section 4.2.

### Transactions

Each transaction in a block is described by a specific Transaction Type containing a link to exactly one incoming message and a link to one (possibly zero) outgoing message.

The transaction consists of calling TVM with the smart contract code of the corresponding account loaded into the virtual machine from the root cell loaded into one of the registers. The message itself is pushed onto the stack as an argument along with some other important data: the number of tokens attached to the message, the sender's account address, the current balance of the smart contract, etc.

Also, the transaction contains the initial and final state of the account / smart contract, as well as some TVM statistics: gas consumption, transaction phases, etc. It is important to note that unlike Ethereum, interactions between smart contracts in Everscale are asynchronous, which is important for performance.

There are differences between the types of transactions allowed on the master chain and shard chain.

The most common type of transaction is Ordinary transactions, which are the delivery of one incoming message to an account and processing it with the code of that account.

Besides them, there are several types of exotic transactions. There are 6 of them in total.

1. **Ordinary** transactions are account-specific, they process exactly one incoming message, calculate the new account state, and generate multiple outgoing messages.
2. **Storage** transactions can be used by validators at their discretion. They do not process incoming messages and do not call any code. Their only task is to collect payments for keeping the account. This type of transaction is supported, but almost never used.
3. **Tick** ​​transactions do not have an incoming message, but can generate outgoing messages and change account states. For example, the choice of a validator is carried out through a tick transaction of special smart contracts in the master chain.
4.  **Tock** transactions are automatically called as the most recent transaction in each block of the master chain for certain special accounts.

    **Tick ​​and Tock** transactions exist only in the master chain and are used exclusively for the special account.
5. **Split transactions** are called as the last transactions of the block shardchain, before the shardchain split event.
6. **Merge transactions** - similarly called as the first transactions of shardchain blocks after a shardchain merge event.

Please note that out of 6 types of transactions, only 4 can take place in the maxchain and 4 more can occur only in the main chain.

An Ordinary transaction is executed in several phases, which can be thought of as several “partial transactions” tightly linked into one:

1. **Storage phase** - collects payments for storing the state of the account (including the smart contract code and data, if any) until now. As a result of this phase, the smart contract can be frozen.
2. **Credit phase** - the amount of the received incoming message is credited to the account.
3. **Computing phase** - the smart contract code is called inside TVM with certain parameters, including a copy of the incoming message and constant data, and ends with the output of the code, new constant data and a list of actions (for example, an outgoing message to send or activation of a previously uninitialized or frozen account). Gas charges are charged from the account balance.
4. **Action phase** - if the smart contract was successfully completed (with output code 0 or 1), actions from the list obtained at the end of the Computing phase are performed. If it is impossible to complete all of them, then the transaction is aborted and the account status is rolled back. The transaction is also aborted if the smart contract did not complete successfully, or if it cannot be called at all, due to the fact that it was not initialized or was frozen.
5. **Bounce phase** - if the transaction was aborted and the incoming message was marked with the bounce flag, it is automatically returned with an automatically generated outgoing message (with an empty bounce flag) to the original sender. Almost all of the values ​​of the original inbound message (minus gas charges and shipping fees) are passed to the generated message, which would otherwise have an empty body.

In more detail, we recommend that you familiarize yourself with this material in the [Whitepaper ](https://ton.org/tblkch.pdf)in sections (4.2.5, 4.2.4)

### Writing smart contracts

Smart contracts on the Everscale network are written primarily in Solidity and C ++. We will not dwell on this aspect in detail. Instead, we suggest that you go to the appropriate section of the documentation to familiarize yourself in detail with all the nuances of developing smart contracts for the Everscale blockchain.

{% content-ref url="smart-contracts-1/" %}
[smart-contracts-1](smart-contracts-1/)
{% endcontent-ref %}
