---
description: Round-robin relayer selection
---

# Operator Manager Contract

{% hint style="info" %}
An operator and relayer are equivalent entities in the contacts layer
{% endhint %}

The current zkBob implementation supposes that just a single relayer can interact with the pool contract at the same time. So we should define an approach to select a single relayer for the every time interval within a multiple-relayers configuration.

The simplest way to do that is to select a relayer from the list via round-robin manner. We implement this method in the RoundRobin contract.

The relayer list is managed by the contract owner which can add or remove relayer anytime. The contract owner should transfer operator manager contract to the maintenance state to change the list of approved relayers. In that state the main functionality is disabled and all regular methods will be reverted.

{% hint style="info" %}
#### Relayer list management

We accept strictly approved relayers to avoid malfunction operations. The relayer should be stable available through the public networks and it should have quality communication link. The relayer should have a maintainer which available to fix operating issues.

<mark style="color:red;">**TODO:**</mark> <mark style="color:red;"></mark><mark style="color:red;">need to develop and describe the relayer approval procedure</mark>
{% endhint %}

### The operator manager life-cycle

The operator manager contract lifetime is divided by the time slots. Each slot contains a fixed amount of underlying blockchain's blocks. It is started with the Genesis slot (the first 1000 blocks after contract deployment). The Genesis slot's purpose is to configure contract by the owner and prepare relayers to operating state. In that block the owner should create an operator list with at least one entry.

Each relayer should periodically inform the operator manager contract that it's ready to operate with the Pool. To do that a relayer should invoke `claim()`contract method. The claim received in the current slot is intended for the next one. If relayer does not provide a claim for the specified block it will be ignored in the round-robin selection and the next available one will be used. This approach is intended for decrease unavailable relayers selection probability.

If there are no claims for the current slot, the last operator sent a claim will be selected. So it's not necessary for operator to send claims for the each slot in the single relayer configuration.

{% hint style="info" %}
#### The regular slot

The default slot size is 120 blocks which is approximately equals to 10 minutes on the xDai chain. It can be changed by the contract owner with the `setSlotSize()` method in the maintenance state.

Please keep in mind that selection sequence will be changed after the slot size modification
{% endhint %}

The current operator index $$i$$ (within an operator list with the length $$N$$) for the each slot with index $$S_i$$ is calculated with the round-robin manner as following:

$$
i = (S_i - 1) \text{mod} N
$$

The Genesis slot has the index 0 so the operator selection during that slot is unavailable. The resulting index $$i$$can be changed in the interval $$[0, N-1]$$ inclusively.



![Relayer selection scheme](../../.gitbook/assets/auction\_240ppi.png)

In the picture above you can explore selection mechanism. After the contract deployment the owner adds three approved relayers (named RL-1, RL-2 and RL-3). The first and the second relayer claimed for the slot 1 during Genesis slot, so the first one will be selected as an active operator.

The third relayer has become available only in slot 2, so his first claim is intended for the slot 3. Fortunately the third operator should be selected in the slot 3 exactly (according to the round-robin scheme). So it's become an active relayer in the slot 3.

During the slot 3 the first relayer (RL-1) has been failed, and operator manager contract didn't receive a claim from it. That's why in the slot 4 the RL-1 has been ignored and the next claimed operator (RL-2) has been selected.

In the slot 4 the third relayer (RL-3) has been failed too, so only the single claim has been received from RL-2. In the slot 5 RL-2 should be selected according to the round-robin scheme.

Let's imagine that RL-2 has decided to stop claim sending after the slot 4. This led to absence any claims for the slot 6. In that case the last claimed operator (RL-2) will be selected for the each next slot.

### Getting the current relayer

Anyone can invoke the following contract methods to retrieve the current relayer properties in the normal state:

* <mark style="color:blue;">`operator`</mark>`()` will return the current operator blockchain address. In the maintenance state  method call will be reverted. If there are no selected relayers for the current slot, this method returns <mark style="color:purple;">`address`</mark>`(0)` \[<mark style="color:red;">**To be discussed: return 0 or revert?**</mark>]
* <mark style="color:blue;">`operatorURI`</mark>`()` will return the current operator's endpoint URL (string)
* <mark style="color:blue;">`operatorName`</mark>`()` will return the current operator name (string)
* <mark style="color:blue;">`amIOperator`</mark>`()` will return a boolean value indicating that a message sender is an active operator at that time

### The contract maintenance state

If the contract owner intends to make some changes it should move the contract in the maintenance state. In that state all regular method calls are reverted and operator manager accepts the service calls only. After maintenance has finished, the contract should be returned in the regular state to proceed a normal flow. Changing contract's state is performed by the method `setMaintenance(bool)`

In the maintenance state the following service methods are available:

* <mark style="color:blue;">`addOperator`</mark>`(`<mark style="color:purple;">`string`</mark><mark style="color:red;">`name`</mark>`,`` `<mark style="color:purple;">`address`</mark><mark style="color:red;">`addr`</mark>`,`` `<mark style="color:purple;">`string`</mark><mark style="color:red;">`endpoint`</mark>`)` will add a new operator with the specified name, blockchain address and URL endpoint
* <mark style="color:blue;">`removeOperator`</mark>`(`<mark style="color:purple;">`address`</mark><mark style="color:red;">`addr`</mark>`)` will remove the operator with the specified address. Please note that the last operator in the list will be relocated to the vacant place
* <mark style="color:blue;">`setSlotSize`</mark>`(`<mark style="color:purple;">`uint32`</mark>` ```` `<mark style="color:red;">`blocks`</mark>`)` will change slot size (specified in blocks). The number of blocks should be greater than 0

