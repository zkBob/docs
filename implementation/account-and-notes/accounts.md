---
description: Define a customer wallet state
---

# Accounts

The account contains complete information about user's private wallet. It is linked by the intermediate key $$\eta$$ derived from the spending key $$\sigma$$owned by the user. The holder of the spending key is called an account owner.

The account holds the current balance value and `spent offset` which separates all notes into spent and unspent. This is sufficient data to retrieve a wallet state.

An account is a tuple $$(\eta, i, b, e, t)$$ where:

* $$\eta$$ (32 bytes) is an [intermediate key](../zkbob-keys/) derived from the spending key: $$\eta = Hash((\sigma*G).x)$$
* $$i$$(6 bytes) is a spent offset. It separates used (spent) and unused notes in the [Merkle tree](../untitled/) . Notes that indexes below $$i$$ are considered to be spent
* $$b$$(8 bytes) is the current account balance
* $$e$$(8 bytes) is an [energy](../../in-development/xp/) unit ("integral" account balance)
* $$t$$(10 bytes) is a salt. Since transaction contains the account hash we must use a random salt to hide the possible lack of account changes.

Accounts take part into the transactions data never appear unencrypted in a public field. Only the account owner can decrypt it.

{% hint style="info" %}
#### Zero account

If a user creates the first transaction there is not an existing account in the Merkle tree. In this case a zero account should be use where all fields are zero except $$\eta$$.​
{% endhint %}
