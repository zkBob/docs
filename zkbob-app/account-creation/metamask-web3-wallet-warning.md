---
description: When deriving a zkBob account using MetaMask
---

# Metamask / Web3 Wallet Warning

zkBob provides a convenient method to create an account using Metamask (MM) or another web3 wallet using Wallet Connect. When deriving an account with a web3 wallet there is no need to write down or remember a new seed phrase for your shielded account.&#x20;

![](../../../.gitbook/assets/create1.png)

With this method, a zkBob private key is derived using your Metamask private key. You sign a message to enable this derivation. There is no fee, the operation is performed on your local machine and nothing is sent to the blockchain. The zkBob application collects your signature and creates a private key for the shielded account.&#x20;

No one can reproduce the signature without access to your Metamask private key. If you change your browser or device, simply authorize Metamask and resign the same message in the zkBob application to get access to your shielded funds.&#x20;

This method is secure and anonymous, it is not possible to reveal your private key through signature analysis.

{% hint style="danger" %}
**Security Warning**

Be vigilant when using Metamask or another web3 wallet, as an adversary can ask you to sign the _same message_ on a spoofed site.

If you provide a signature to the attacker your zkBob private key is leaked and the attacker can steal all funds from the zkBob account. To protect against this threat you must always **check the source URL** sending the  signing request.&#x20;

The genuine application has hosted on [<mark style="color:blue;">**`https://zkbob-ui.herokuapp.com`**</mark>](https://zkbob-ui.herokuapp.com)\[<mark style="color:red;">**TODO**</mark><mark style="color:red;">: change to production URL</mark>] only.

<mark style="color:red;">**TODO**</mark>: <mark style="color:red;">add a Metamask screenshot with</mark> <mark style="color:red;"></mark><mark style="color:red;">`source`</mark> <mark style="color:red;"></mark><mark style="color:red;">field highlighted (when UI moves to the production URL and signing message becomes actual)</mark>
{% endhint %}
