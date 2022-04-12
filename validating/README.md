# Validate

## Who is a validator

A Everscale validator is a network node (server) that participates in the validation of generated new blocks of the blockchain.

Validators are a group of network nodes that have been selected as validators for a certain period (validation cycle), during which they participate in validation together.

Validation is the signing of blocks by several nodes in order to reach a consensus (general agreement) on the correctness of the block. The very procedure of reaching consensus is necessary for the network to ensure the reliability of its functioning, that is, resistance to failures of individual nodes or deliberate attacks.

In fact, validators provide the basis for the functioning of a decentralized network. For their work, they receive remuneration consisting of a processing fee (1,7 EVER for a new block in the masterchain, 1 EVER for a new block in the shardchain), as well as from the emission of new tokens distributed to validators. In the current network parameters, the emission is fixed at the level of \~0.5% per year. It is distributed each validation cycle to all validators in proportion to their stakes.

The list of validators can be seen in the blockchain Explorer on [https://ever.live/validators?section=all](https://ever.live/validators?section=all)

In the Everscale network, the number of validators can reach 1000, up to 100 validators of which can perform block validation in the masterchain (the main chain of blocks), and the rest validate blocks in shardchains (secondary chains of blocks).

### Validator staking

Stake - deposit of the validator required for participation in the election of validators and subsequent validation in the Proof-of-Stake blockchain.

Validator income - the validator is rewarded at the end of each validation cycle. Income consists of 2 parts:

* emission of new tokens (fixed in the network at the level of \~0.5% per year);
* fee for signed blocks (1,7 EVER for each block in the masterchain and 1 EVER for each block in the shardchain).

At the moment, all validators are rewarded in proportion to their stake. In other words, if the validator placed a stake in the amount of 1% of the total amount of stakes, then his remuneration will be 1% of the total remuneration.

As the size of the stake is too large for a common participant, and the number of validators is limited, the DePool smart contract was developed that allows any participant with a small amount to participate in the staking and receive their part of the reward. The smart contract guarantees that the validator cannot use the participants' funds in any other way, thereby guaranteeing the security of their funds from the validator's dishonesty.

Validator elections occur (based on the current network configuration) every 18 hours. Each period consists of 3 phases:

* the election is open, the elector's smart contract accepts new stakes, and previous validators can return their stakes from the elector's smart contract;
* the election is over and the smart contract determines the group of validators for the next phase;
* a new group of validators starts working. The stakes of the former group of validators are temporarily frozen.

It looks like this:

[![Validation cycle.jpg](https://en.freeton.wiki/w/images/8/82/Validation\_cycle.jpg)](https://en.freeton.wiki/File:Validation\_cycle.jpg)

Defining a group of validators - the smart contract of the elector operates according to the following rules:

* The following parameters are read from the network configuration:
  * min and max number of validators;
  * min and max size of the stake;
  * max\_factor the maximum difference between the first (maximum) and last (minimum) validator stakes.
* The maximum/wrap group of validators is recruited, starting from the first and then in order (the order corresponds to a decrease in the size of the stake, and if the stakes match, then by increasing the time it is served), which has a difference between the largest and smallest walls no more than max\_factor.
* For the next stake (it can be from one or several validators), the sum of all the stakes is calculated in such a way as to comply with the max\_factor rule. To do this, the maximum stake (or stakes) is cut to meet the max\_factor rule. If the resulting sum of all the stakes has become larger, the smart contract of the elector tries to get the next stakes, following the same procedure of cutting stakes according to the max\_factor rule.
* As soon as the total stake calculated using this procedure stops growing, i.e. the maximum amount of stakes is found, this state is considered to have passed the election. Then all the past elections will be validated by the validators for the next election period, and the cut parts of the stakes (if any) are immediately returned to the wallets from which they were sent.

Source:[ Everscale wiki](https://en.freeton.wiki/Validator)
