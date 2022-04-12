---
description: Dive into Everscale here!
cover: ../.gitbook/assets/everscale-overview.png
coverY: 0
---

# Everscale Overview

Everscale is a fast, secure and scalable blockchain capable of handling millions of transactions per second on demand, user and service provider friendly. You can think of Everscale as a huge distributed supercomputer, or rather, as a huge "super server" designed to host and provide various services.

The history of Everscale begins with the creation of another project - Telegram Open Network (TON), developed by the best specialists of Pavel Durov's Telegram team. TON was designed as a decentralized ecosystem based on the principles of P2P networks that implement messaging, value, data storage, and an entire operating system to run decentralized applications. The transaction speed in TON is so high and stable (1 million transactions per second) that the project was ready to compete with MasterCard and Visa.

After attracting more than $ 1 billion in funds for the development of the network, the SEC became interested in the project, deciding to close it due to a number of regulatory violations.

After the official closure of the project, the TON source code was made publicly available, attracting the interest of professional validators and developers, and thereby laying the foundation for the Everscale network. \
\
You can learn more about the history of the project and its roadmap in the corresponding section:

{% content-ref url="history.md" %}
[history.md](history.md)
{% endcontent-ref %}

#### **Everscale as a governance**

The Everscale community began to grow rapidly immediately after the launch of the network, attracting like-minded people around the world.

The key principle of the network is complete decentralization, including at the level of project management, therefore all Everscale development takes place thanks to Sub-goverances. Sub-governances are a range of community groups with significant expertise in a variety of industries. These groups make proposals for the development of the network in various directions (DeFI, e-sports, NFt and etc), receiving rewards in EVER in case of successful implementation of the initiative.

In addition to the efforts of the community to develop the network, a number of large projects are partnering with Everscale, going through the approval procedure for the “partner statement” in a decentralized format.

You can learn more about the network management device, community and rewards for network development initiatives in the corresponding section:

{% content-ref url="../dao-management/contributors-guide.md" %}
[contributors-guide.md](../dao-management/contributors-guide.md)
{% endcontent-ref %}

**Everscale as a technical solution**&#x20;

The Everscale blockchain is actually a collection of blockchains (even a collection of blockchains of blockchains, or 2-blockchains), because no single blockchain project is capable of achieving the goal of processing millions of transactions per second, as opposed to the now-standard dozens of transactions per second. The blockchains in this collection are: The unique master blockchain, or masterchain for short, contains general information about the protocol and the current values of its parameters.

Several (up to 232) working blockchains, or workchains for short, which are actually the main workers of the network containing the value-transfer and smart-contract transactions. Different workchains may have different "rules", meaning different formats of account addresses, different formats of transactions, different virtual machines (VMs) for smart contracts, different basic cryptocurrencies and so on.

Each workchain is in turn subdivided into up to 260 shard blockchains, or shardchains for short, having the same rules and block format as the workchain itself, but responsible only for a subset of accounts, depending on several first (most significant) bits of the account address.

Each block in a shardchain (and in the masterchain) is actually not just a block, but a small blockchain. Normally, this block “blockchain" or "vertical blockchain" consists of exactly one block, and then we might think this is just the corresponding block of the shardchain (also called "horizontal blockchain" in this situation). However, if it becomes necessary to fix incorrect shardchain blocks, a new block is committed into the "vertical blockchain", containing either the replacement for the invalid "horizontal blockchain" block, or a "block difference", containing only a description of those parts of the previous version of this block that need to be changed. This is a Ever-specific mechanism to replace detected invalid blocks without making a fork of all shardchains involved. Each shardchain (and the masterchain) is not a conventional blockchain, but a blockchain of blockchains.

Also, Everscale has the following features and advantages that are important for understanding over other blockchains: Infinite Sharding Paradigm - the network automatically increases the number of shards when the load increases and decreases when it decreases. Instant Hypercube Routing - in Everscale, you can directly access your account from any shard, without having to go through the entire chain of other shards. Everscale Virtual Machine (improved analogue of EVM), which supports Turing complete smart contracts and allows writing in Solidity and C ++. Token Formats - The network supports the ability to create up to 232 different tokens. The Everscale architecture is a truly new, better approach to blockchain technology implementation. Get to know her better and contribute to the development of the network and the crypto industry as a whole by developing a Dapp on the fastest blockchain:

{% content-ref url="../developing/developer-guide.md" %}
[developer-guide.md](../developing/developer-guide.md)
{% endcontent-ref %}

_<mark style="color:purple;">P.S. Tens of thousands of Everscale community users are waiting for your product!</mark>_

**Everscale as a profitable place for validators**

The Proof-of-Stake (POS) algorithm is used to ensure network consensus. The maximum number of validators is 1000. For each workchain, several validators are periodically elected to ensure the creation of blocks. In order to become a validator, you need to deploy a node, generate ADNL keys, start participating in elections by providing a certain amount of coins (stake) to a certain address. In case you do not have enough funds to run a validator node, you can turn to the help of DePool, which is an add-on over a node that allows you to collect funding from third-party network participants, rewarding them with a part of the profit from block validation. Among them you can find well-known Everscale validators: Certus, Minergate, Chorus. For a more detailed study of the direction of validation and to view the step-by-step instructions “how to become a validator”, we recommend that you visit the corresponding section:

{% content-ref url="../validating/validator-guide.md" %}
[validator-guide.md](../validating/validator-guide.md)
{% endcontent-ref %}

**Everscale features**&#x20;

The main features of Everscale are the speed and low cost of commissions and real decentralization in every sense, not just in terms of technology.&#x20;

The network is rapidly developing, attracting specialists and crypto enthusiasts from all over the world with its ideology and technical superiority. The Everscale community has created many resources where you can study all aspects of the network in more detail and get imbued with its ideology. We also recommend that you familiarize yourself with our guides for individual and institutional users in order to personally get acquainted with the network in 10 minutes and find interesting projects for yourself in the Everscale ecosystem:

{% content-ref url="../individuals-and-institutionals/" %}
[individuals-and-institutionals](../individuals-and-institutionals/)
{% endcontent-ref %}

More community resources with information about Everscale:

{% embed url="https://en.freeton.wiki/Free_TON_Wiki" %}

