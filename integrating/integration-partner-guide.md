---
cover: ../.gitbook/assets/Integration Partner Guide Guide (1).png
coverY: 0
---

# 👉 Integration Partner Guide

## Let's start!

If you are not yet familiar with the Everscale network, we recommend that you read the Overview section of the documentation, where you can learn about the main features and benefits of the network.

Before starting to study this guide, I would like to note that there are two concepts of integration with the network:

1. Technical integration of the network, listing of coins.
2. Mutually beneficial partnership.

Regarding the first point in the article below, you will find all the necessary information.&#x20;

If you want to become an official partner of the network and start working together on mutually beneficial terms, you can use one of the following integration opportunities:

1. Submit your application to the [Free TON DeFi Alliance](https://tonaliance.org) if your offer is related to the listing or the DeFi industry.
2. Prepare and publish a partnership proposal on the forum for its further evaluation and adoption.

{% content-ref url="../dao-management/partners-application.md" %}
[partners-application.md](../dao-management/partners-application.md)
{% endcontent-ref %}

## Add EVER to your exchange

In order to connect to the Everscale blockchain and use EVER, you will need to access the blockchain and add the ability to manage your deposit account.

**Connection to blockchain options:**

1. Configure Access Using TON OS Cloud
2. Set up your own node

**Deposit account management options:**

1. With TON Wallet Api
2. Using the TON OS-CLI tool
3. With TON SDK

Below you can find a brief description of all the above tools and capabilities.

### Setting up access to the blockchain

There are two ways to set up Everscale blockchain access: you can use TON OS Cloud or set up your own DApp server.

#### Using TON OS Cloud

TON OS Cloud allows you to work with the Everscale blockchain and development network without having to launch your own node. TONOS-CLI and SDK can connect to it like a normal node. It has the same API as the node and provides all the capabilities needed to run the exchange capability.

#### Using DApp Server

If you prefer to run your own node, you can set up your own TON OS DApp server. This is a complete node that can be configured on your own servers and provide full access to either Everscale or the development network.

You can find instructions on setting up a DApp Server on the TON.Dev website ([by this link](https://docs.ton.dev/86757ecb2/p/10aec9-add-ton-crystal-to-your-exchange)) in the Using Dapp Server section.

### Setting up a deposit account

#### Ton Wallet Api&#x20;

Ton Wallet Api is a turnkey HTTP Api solution for a wallet running on the Everscale network developed by Broxus, one of the leading development teams. You can find detailed information on using this solution on the official [Github Broxus page.](https://github.com/broxus/ton-wallet-api)

#### Using TONOS-CLI

TONOS-CLI is a command line tool for the TON blockchain that allows you to deploy any smart contracts on the blockchain, call all contract methods, sign transactions, and generally manage your account. TONOS-CLI has versions for Linux, Windows and Mac. It supports both TON OS Cloud and DApp Server based integrations. Also, this tool can be used to withdraw funds from a deposit account. You can find instructions on using TONOS-CLI on the TON.Dev website ([by this link](https://docs.ton.dev/86757ecb2/p/10aec9-add-ton-crystal-to-your-exchange)) in the Using command line tool section.

#### Using the SDK

You can integrate the above escrow account deployment process into your exchange backend. This functionality is supported in the TON SDK. TON OS SDK is supported in 14 programming languages ​​for all popular platforms. Also, the SDK has built-in the ability to monitor the account deposit, which allows you to reliably know about all inputs to customer accounts. With the help of the SDK, you can also integrate the ability to withdraw funds from a deposit account into your backend. You can find instructions on using the SDK on the TON.Dev website ([by this link](https://docs.ton.dev/86757ecb2/p/10aec9-add-ton-crystal-to-your-exchange)) in the Using SDK section.&#x20;

<mark style="color:purple;">P.S. The TON.Dev team currently recommends the officially confirmed SafeMultisig contract for use on escrow accounts. It is well tested and secure, supports multiple custodians, and can be configured to require multiple independent signatures for any translations.</mark>

