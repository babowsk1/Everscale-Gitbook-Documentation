# Getting started with Everscale smart contracts

Smart contracts on the Everscale network are written primarily in Solidity and C ++.

The TON Dev team provides a complete set of compilers and tools to support the full cycle of smart contract development in Everscale, opening the following opportunities:Write source code on [Solidity](https://docs.ton.dev/86757ecb2/v/0/p/950f8a-write-smart-contract-in-solidity), [C++](https://docs.ton.dev/86757ecb2/p/828241-c-tutorial) or [C](https://docs.ton.dev/86757ecb2/p/16892e-giver-in-c)

* Compile source to assembly: invoke optimizing [compilers ](https://docs.ton.dev/86757ecb2/p/552389-general)generating native code for TON VM (TVM)&#x20;
* Translate assembly text to binary: assemble and link contract code with standard or custom libraries&#x20;
* Secure blockchain interaction: generate or use an existing key pair to communicate with the contract in the blockchain
* Define account address: compute a unique address for the contract based on its code, initial data and keys&#x20;
* Create an account: prepare an account for contract deployment by sending a message transferring blockchain currency to the account address
* Secure contract deployment: encode the contract binary and sign it with the key pair
* Initialize the account: send the prepared constructor message to the contract address
* Work with the contract: use the contract as intended by sending messages to the account address in the blockchain

You can get acquainted in detail with writing smart contracts in Everscale on the [TON.Dev documentation page](https://docs.ton.dev/86757ecb2/p/12d2bf-getting-started-with-ton-smart-contracts), where you will find all the necessary instructions and tools.



\


\


{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}
