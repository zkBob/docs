---
description: Define a customer wallet state
---

# Accounts

The account contains complete information about user's private wallet. It is linked by the intermediate key $$\eta$$ derived from the spending key $$\sigma$$owned by the user. The holder of the spending key is called an account owner.

The account holds the current balance value and `spent offset` which separates all notes into spent and unspent. It is sufficient data to retrieve a wallet state.

An account is a tuple $$(\eta, i, b, e, t)$$ where

* $$\eta$$ (32 bytes) is an [intermediate key](../zkbob-keys/) derived from the spending key: $$\eta = Hash((\sigma*G).x)$$
* $$i$$(6 bytes) is a spent offset. It separates used (spent) and unused notes in the [Merkle tree](../untitled/) . Notes that indexes below $$i$$ are considered to be spent
* $$b$$(8 bytes) is the current account balance
* $$e$$(8 bytes) is an [energy](../energy-token.md) unit ("integral" account balance)
* $$t$$(10 bytes) is a salt. Since transaction contains account hash we must use a random salt to hide possible lack of account changes.

Accounts take part into the transactions data never appear unencrypted in a public field. Only the account owner can decrypt it.

{% hint style="info" %}
#### Zero account

If user creates the first transaction he still doesn't have an existing account in the Merkle tree. In this case he should use a zero account. In such account all the fields are zero except $$\eta$$​
{% endhint %}
