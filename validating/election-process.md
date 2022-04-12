# Election process

This article briefly describes the process of selecting a validator using an electoral contract. You can find a detailed technical description of how the selection of validators works in the documentation on the TON Dev website.

{% embed url="https://docs.ton.dev/86757ecb2/p/456977-validator-elections" %}

The elector contract functions according to certain configuration parameters with the global blockchain. Elections of validators take place (according to the current network configuration) every 18 hours. Each period consists of 3 phases:

1. The election is open, the elector's smart contract accepts new stakes, and the previous validators can return their stakes from the elector's smart contract.
2. The elections are over and the smart contact determines the group of validators for the next phase.
3. A new group of validators starts working. For the previous group of validators, the stakes are temporarily in the "freeze" phase.

![](https://lh3.googleusercontent.com/Si0XTzuN56lIHJtSofuC16nfOBlMSBymeCJ1fNzMPxVYRJYGkZpI1ts8OH08Q--VFAAhCNFIMyzkKhmD7zYmXlJPYV3Ig4hChvPgTc5FcxSykXIGBgAqoomz6mxXXxt\_4XMqj-9B)

### Defining a group of validators

The electoral smart contract operates according to the following rules:

1\) The following parameters are read from the network configuration:

1. Min and Max number of validators
2. Min and Max stake size
3. Maximum difference between the first (maximum) and last (minimum) validator stakes

2\) The maximum group of validators is recruited, starting from the first and further in order (the order corresponds to a decrease in the size of a stake, and if the stakes coincide, then an increase in the time of its serving), which has a difference between the largest and smallest stakes no more than max\_factor.

3\) For the next stake, the sum of all the stakes is calculated in such a way as to comply with the max\_factor rule. For this maximum stake (or stakes) are trimmed to meet the max\_factor rules. If the resulting sum of all the stakes has become larger, then the elector's smart contract tries to select the next stakes, following the procedure for cutting stakes according to the max\_factor rule.

4\) As soon as the total stake calculated according to such a procedure stops growing, that is, the maximum amount of stakes is found, then this state is considered to have passed the elections - then, all past elections, validators will begin to validate for the next election period, and the trimmed parts of the stakes (if any) are immediately returned to wallets from which they were sent.

You can learn more about the technical process of choosing a validator on the TON.Dev website and on the corresponding page of the Free TON Wiki.

{% embed url="https://docs.ton.dev/86757ecb2/p/456977-validator-elections" %}

{% embed url="https://en.freeton.wiki/Validator" %}

