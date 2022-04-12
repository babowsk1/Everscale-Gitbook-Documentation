# TON Virtual Machine

TON Virtual Machine (TON VM or TVM) is a virtual machine designed to execute smart contracts in the master chain and base work chain. Other workchains can use other virtual machines together or instead of TVM.

Thanks to TVM, the Everscale functionality allows not only making payments, but also implementing any contractual logic in the form of smart contracts.

TVM supports all operations necessary for parsing incoming messages and permanent data, as well as for creating new messages and changing permanent data.

Among other things, TVM meets the following requirements:

* TVM provides for possible extensions and improvements in the future, while maintaining full compatibility with previous versions and interoperability due to the fact that after being implemented in the blockchain, the smart contract code should execute predictably, regardless of future modifications of the Virtual Machine.
* TVM strives to provide a high density of “(virtual) machine code” so that typical smart contract code takes up as little permanent storage as possible on the blockchain.
* TVM is fully deterministic. In other words, each run of the same code with the same input data leads to the same result, regardless of the features of the software and hardware.

TVM does not provide for a hardware implementation (for example, in a special microprocessor die), as it implies a software implementation on standard hardware.

As a result, TVM was able to implement some high-level concepts and operations that would require complex code in hardware, but the software implementation of these concepts and operations is not a problem.

Such operations are effective for ensuring high code density and minimizing the byte parameter occupied by the smart contract code of space in the data store in the TON blockchain.

You can learn more about the principles of TVM operation on the TON.DEV website in the section below.

{% embed url="https://docs.ton.dev/86757ecb2/p/822e19-2-ton-blockchain" %}

