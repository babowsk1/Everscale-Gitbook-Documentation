# Staking & Depools

## What is DePool

To achieve high network performance, you need reliable servers with fast connections. At the same time, in order to achieve sufficient decentralization, these servers should be owned by as many owners as possible.

Enabling small token holders to participate in the governance of the network is a very important property of decentralization.

For correct operation, the Everscale blockchain checks all created blocks. To do this, he uses special nodes called "validators" and offers substantial rewards for their work.

However, in order to become a validator, a significant cryptocurrency deposit is required. The amount required may well exceed the budget of an individual validator. On the other hand, blockchain users who do not have a verification system are interested in its implementation.

This is where the decentralized pool smart contract (DePool) comes to the rescue.

DePool is a smart contract that allows other smart contracts to invest stakes in a common pool of funds and, after a certain period of time, receive them back with interest.&#x20;

There are two main use cases for DePool:

* The user has no validator capabilities, but some free funds. The User can be supported by a third-party Validator and receive rewards.
* The user has the capabilities of a validator, but does not have the required amount of funds to participate in the election of a validator and subsequent rewards.

**The DePool Association** is an association of validators to promote the values ​​of decentralization, increase user engagement, and maintain the pool's reputation.

Members of the DePool association receive a reward for supporting the validator node and development resources for DePools, as well as the general privileges of token holders. By nature, DePools are more decentralized than any Staking Pool operator alone.

As members of the DePool Association support the software of the nodes, their ability to support the development of the network is further enhanced by the collection of common DePool stakes, which leads to an even greater decentralization of blockchain governance.

## How DePool works

DePool is designed to receive investment stakes from the Participants, distribute the pool funds to the validator to participate in the GVS elections and, after the end of the validation cycle, distribute the stakes with certain rewards back to the participants.

1. DePool is deployed on basechain. But it cannot directly interact with Elector, because Elector rejects messages from non-masterchain contracts. Thus, there are DePool proxies that deploy to the master chain and deliver messages from DePool to Elector and back. It is also important that the fee for gas and storage in the basechain is 10 times less than in the masterchain.
2. DePool is open to Members stakes at any time, however there is a deadline for participation in the upcoming elections. The term depends on the Elector timer. After the specified period, the incoming stakes will be accumulated for participation in the next elections.
3. DePool distinguishes between stakes received before the deadline and after the deadline, therefore it stores information about the Participants' stakes in separate investment rounds, one for each election, to facilitate subsequent distribution of stakes and rewards. To distribute data exchange with Elector, DePool uses two proxies: one for even rounds and one for odd rounds.
4. The Timer contract is used to call DePool. DePool Helper asks Timer to call it periodically and passes each call from Timer to DePool. The interval between calls is selected according to the selection interval.
5. DePool must be linked to the validator's wallet in order to participate in elections on behalf of the latter. This wallet address of the validator is specified during DePool deployment and cannot be changed later. When the election starts, DePool waits for signed election requests from the linked wallet, then attaches the round's stake to the request and passes it to Elector\`y.
6. A validator can validate multiple DePools using 1 validator wallet. The reputation of the Validator's wallet is available and, over time, can be analyzed.
7. In order for the validator to perform its functions correctly (it was always online and did not "lie" to other validators), the validator's wallet must become a Participant itself and invest in each round of investments at least 20% of the minimum total round stack (minRoundStake), which is initialized in the DePool constructor
8. When Elector unfreezes validator stakes, DePool returns its stake with round rewards. Some of these rewards (25%) go to the balance of the Validator's wallet, which can be withdrawn from the wallet at any time. The other part (5%) goes to DePool itself to cover gas and storage fees. And the last part (70%) is distributed among all Participants of the investment round. All these parts are initialized when DePool is deployed.
9. DePool keeps the balance of each Participant and can automatically reinvest the Participant's stake in the last investment round if the corresponding flag is set.
10. A Participant can transfer part of his common stake to another Participant's stake in the DePool storage. This feature allows you to ensure the liquidity of the stakes.

## Types of stakes

Along with the basic regular stake, which functions according to the rules described above, there are two types of specialty stake: Vesting and Lock.

#### Vesting stake

The stake is cut into pieces. Each subsequent part of the stake becomes available to the validator only at the end of the next transition period. At the end of each round, DePool decides how many pieces of the stake should be unlocked and subtracted from the stake and made available to the validator.

Example: address A makes a 120 EVER stake for 1 year with a period of 1 month and designates address B as the recipient of the stake. This means that after 1 month, 10 EVERs become available for address B, and 110 EVERs are still blocked in the round. After 1 year, the vesting stake will be 0, and the last 10 EVERs will become available to the validator.

#### Lock stake

Funds (whole stake) are blocked in DePool for a certain period. At the end of the period, the blocked stake is returned. Lock stake cannot be divided, moved, or voted on.

One participant can only own one Vesting stake and one Lock stake. When a stake of any of these types is created, it is divided equally into the last two rounds, which means that the minimum value for such a stake is 2 \* minStake + commission.

## How to become a stakeholder?

In order to become a stakeholder and invest your EVERs in Depool, you can follow the instructions on the TON DEV website in the corresponding section.

{% embed url="https://docs.ton.dev/86757ecb2/p/45fa44-depool-faq" %}

{% content-ref url="validating/" %}
[validating](validating/)
{% endcontent-ref %}
