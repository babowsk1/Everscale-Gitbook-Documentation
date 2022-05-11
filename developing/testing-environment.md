# Testing environment

In order to conveniently test your smart contracts in the Everscale blockchain, you will need the Evernode tool.

### What is Evernode DS?

Evernode is a suite of software developed by a member company of the community network, EverX, that provides interoperability with the Everscale blockchain.

Everscale provides itself with the blockchain as a special distributed computer that receives, provides and stores information, a set of programs that manage computer resources and provide a user and program interface can be called an operating system.

It should be noted that Evernode is not an operating system in the classical sense, but it performs all the functions of an abstract model of a distributed "computer" Everscale.

### What is Evernode SE?

Evernode Startup Edition is a preconfigured Docker image with a simplified standalone node server instance designed only for debugging and testing.

Evernode SE consists of:

* EverX implementation of TON VM written in Rust
* ArangoDB database
* GraphQL endpoint with web playground
* Pre-deployed Giver (smart contract responsible for the distribution of tokens)

### Evernode SE use cases

* Test your applications locally
* Test your contracts
* Run Evernode SE remotely on a server and test your application from different devices

### Difference between local and real blockchain

There are a number of significant differences between local and real blockchain:

* The local blockchain does not create empty blocks like a real blockchain, it only creates blocks if it processes messages
* Absence of sharding and master chain - there is only one shard
* The test blockchain writes interrupted incoming messages to the database. This means that if your contract fails to complete the external incoming message, it will immediately throw an error and you can see the transaction in Graphql
* There is no elections and no elector contract deployed

## Installation

### Before installation

To use the product, you need a machine that supports [Docker](https://www.docker.com/get-started). All the necessary docker images are available at [docker hub](https://hub.docker.com/r/tonlabs/local-node).

### Installing Evernode SE <a href="#241b7b" id="241b7b"></a>

[Evernode SE is a pre-configured Docker image](https://hub.docker.com/r/tonlabs/local-node) with a local blockchain that provides Evernode API.

There are several ways to install Evernode SE:

1. Using the TONDEV CLI (you can learn more about this tool on the corresponding [page on the Github site](https://github.com/tonlabs/tondev/))
2. Using the Docker

You can find detailed installation instructions on the corresponding page on the official TONDEV website.

## Deploying contracts

If you are using Evernode SE for your projects, use its pre-deployed Giver to sponsor your contracts. On the start Evernode SE giver has 5 billion test tokens when you first create the Node container.

You can find more detailed information about this stage on the [corresponding page on the official TONDEV website.](https://docs.ton.dev/86757ecb2/p/00f9a3-ton-os-se-giver)

## Sources

You can find all the necessary sources of the installation files here:

* [**Github**](https://github.com/tonlabs/tonos-se)
* [**Dockerhub**](https://hub.docker.com/r/tonlabs/local-node)
