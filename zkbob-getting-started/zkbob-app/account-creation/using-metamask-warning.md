---
description: When deriving account through Metamask wallet
---

# Using Metamask Warning

zkBob application provide you a convenient account creation way through the Metamask extension. You shouldn't writeup or remember a new seed phrase for your shielded account because zkBob private key can be derived from the Metamask private key by message signing.

When you select using this way the Metamask will ask you to sign a fixed text message. You doesn't pay any fee for signing: it's performed on your local machine and nothing send on blockchain. zkBob application gets your signature and derive private key for the shielded account.

Nobody can reproduce the signature without your Metamask private key. If you change your browser or device - you should simply authorize in your Metamask and resign the same message in zkBob application to get access to your shielded funds. Please be calm: there are no any theoretical possibility to reveal your Metamask private key by signature analyzing.

{% hint style="danger" %}
**Security Warning**

There is a significant threat warning you must to understand before using Metamask for key deriving. An adversary can ask you to sign the _same message_. If you provide a signature to the attacker your zkBob private key becomes leaked. Anybody who know it can steal all your money from the zkBob account. To protect against that threat you always **have to check the source URL** which are send signing request. The genuine application has hosted on [<mark style="color:blue;">**`https://zkbob-ui.herokuapp.com`**</mark>](https://zkbob-ui.herokuapp.com)\[<mark style="color:red;">**TODO**</mark><mark style="color:red;">: change to production URL</mark>] only.

<mark style="color:red;">**TODO**</mark>: <mark style="color:red;">add a Metamask screenshot with</mark> <mark style="color:red;"></mark><mark style="color:red;">`source`</mark> <mark style="color:red;"></mark><mark style="color:red;">field highlighted (when UI moves to the production URL and signing message becomes actual)</mark>
{% endhint %}
