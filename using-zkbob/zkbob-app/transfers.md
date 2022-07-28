# Transfers

{% hint style="warning" %}
All actions are performed on a test application running on Kovan testnet and using test Dai rather than Bob tokens. Instructions will be updated when app is live in production.
{% endhint %}

Transfers are made within the zkpool between zkAccounts. You do not transfer to an 0x account, but rather to another zkAccount holder's one-time address. Typically you receive a sending address from a friend via a private channel.&#x20;

zkAccount addresses are not fixed. You can (and are encouraged to) generate a new address for each incoming transaction. **It is not possible to link different private addresses to one another or to the primary account.** Only the account owner can confirm ownership of a private address.

Each created address is encoded in base58 format. For example `5fkW3dXTvA8Kizt1EbuRyjWofuqR4Ud1YTjGgY1r8nGosDeSaUreq6bwfF61jWL`

Any previously generated address can be used indefinitely, so if you send an address to one party and then generate a new address to send to another party, both can be used to receive token transfers.

## Sending a Transfer

1\) Check your zkAccount is connected. Since you will not be depositing funds, it is your choice whether or not to connect your web3 wallet (this may also depend on how you set up your zkAccount — using a [seed phrase](account-creation/#seed-phrase) or a [web3 wallet private key](account-creation/#web3-wallet)).

![](../../.gitbook/assets/connected-1.png)

2\) Enter information and initiate transfer.

1. Amount to transfer.
2. Receiver's address.
3. Press **Transfer.**

{% hint style="info" %}
Receiver should send you a generated address from the application _\<see_ [_Receiving a Transfer_](transfers.md#receiving-a-transfer)_>_
{% endhint %}

![](../../.gitbook/assets/image-2.png)

3\) **Confirm** transfer details.

![](../../.gitbook/assets/image-3.png)

4\) Wait for proof generation and transfer completion. Transfer costs are subsidized, you will not need to pay for these costs or use your web3 wallet for the Tx.

![](../../.gitbook/assets/proof.png)

![](../../.gitbook/assets/complete.png)

5\) Check the History tab to see transfer details. Click on the transaction hash to view the private Tx in Etherscan.

![](<../../.gitbook/assets/history tab.png>)

* Tx details in Etherscan: [0x3a510a0b06f6f077283731208da4c53ae0548a91ef6aeed066b78b71965a5466](https://kovan.etherscan.io/tx/0x3a510a0b06f6f077283731208da4c53ae0548a91ef6aeed066b78b71965a5466)

![](../../.gitbook/assets/etherscan.png)

## Receiving a Transfer

Generate and send a zkAddress to the sender to receive a shielded transfer.

1\) Press the zkAddress button.

![](../../.gitbook/assets/receive1.png)

2\) Press **Generate receiving address**.

![](<../../.gitbook/assets/generate (1).png>)

3\) Copy generated address and send to your friend via a private channel of your choice.

![](../../.gitbook/assets/copy-address.png)

4\) Wait for receipt. If your zkBob application remains open, you may need to refresh the page to see the changes. In this case, you will need to re-enter your password to proceed.

Once received, check the history tab to see the transaction, and press the tx hash for more details.

![](../../.gitbook/assets/history-tab.png)

* Tx details in Etherscan: [0x3a510a0b06f6f077283731208da4c53ae0548a91ef6aeed066b78b71965a5466](https://kovan.etherscan.io/tx/0x3a510a0b06f6f077283731208da4c53ae0548a91ef6aeed066b78b71965a5466)

![](../../.gitbook/assets/etherscan.png)
