---
cover: ../.gitbook/assets/Validator Guide (2).png
coverY: 0
---

# 👉 Validator Guide

### Let's start!&#x20;

To raise a validator node in the Everscale network, you will need to purchase a EVER to provide a stake, as well as acquire a server that will withstand the projected loads due to block validation.

### Administrative part of validating

As stated above, in order to become a validator, you need to have EVER to provide a steak. There are several ways to buy EVER, you can familiarize yourself with all of them in the “Buy / Sell” section of the documentation.

{% content-ref url="../individuals-and-institutionals/buy-sell-trade.md" %}
[buy-sell-trade.md](../individuals-and-institutionals/buy-sell-trade.md)
{% endcontent-ref %}

It should also be understood that being a validator means being responsible. If a validator signs an invalid block, it can be punished by losing part or all of its stake, and being temporarily or permanently excluded from the set of validators. If a validator refrains from creating new blocks for a long time, it may lose part of the stake and be temporarily or permanently excluded from the set of validators.

Everscale also has decentralized pools. First of all, Depools were created to solve the following possible problems:&#x20;

1. The user lacks the capabilities of a validator, but at the same time he has some free funds. In this case, the user can be supported by a third-party Validator and receive rewards.&#x20;
2. The user has the capabilities of the validator, but at the same time the lack of the required amount of funds to participate in the election of the validator and subsequent rewards.

In the Everscale network, the number of validators can reach 1000, up to 100 validators of which can perform block validation in the masterchain (the main chain of blocks), and the rest validate blocks in shardchains (secondary chains of blocks).

### Preparing to set up the Validator node

&#x20;Before installing a validator node, you need to make sure that all the requirements are met for this. Deployer and custodian actions may be performed on Linux, Mac OS or Windows systems. Note: Node is included in the DApp Server, and doesn't have to be installed separately.

| Configuration | CPU (cores) | RAM (GiBs) | Storage | Network |
| ------------- | ----------- | ---------- | ------- | ------- |
| Minimal       | 8           | 16         | 1000    | 1       |
| Recomended    | 16          | 32         | 1000    | 1       |

You can find detailed requirements in the instructions provided by [TON Lab](https://docs.ton.dev/86757ecb2/p/708260-run-validator).

### Set up the Node and start to validate&#x20;

An article with step-by-step information and code examples on how to start your own node is in the documentation of one of the key community members, EverX, who are involved in both validation and network development:&#x20;

{% embed url="https://docs.ton.dev/86757ecb2/p/708260-run-validator" %}
