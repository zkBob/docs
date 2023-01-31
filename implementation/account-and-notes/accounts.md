---
description: Define a customer wallet state
---

# Accounts

The account contains complete information about a user's private wallet. It is linked by the intermediate key $$\eta$$ derived from the spending key $$\sigma$$owned by the user. The holder of the spending key is called an account owner.

The account holds the current balance value and `spent offset` which separates all notes into spent and unspent. This is sufficient data to retrieve a wallet state.

An account is a tuple $$(d, P_d, i, b, e)$$ where:

* $$d$$ (10 bytes) is a random diversifier which is updated every time an account is updated. It acts like a salt.
* $$P_d$$ (32 bytes) is diversified public key (a value derived from the $$d$$ and intermediate key $$\eta$$): $$P_d = \eta * \text{ToSubGroupHash}_{E(F_r)}(d)$$
* $$i$$(6 bytes) is the spent offset. It separates used (spent) and unused notes in the [Merkle tree](../untitled/) . Note that indexes below $$i$$ are considered to be spent.
* $$b$$(8 bytes) is the current account balance
* $$e$$(8 bytes) is an [energy](../../roadmap/exploratory-features/xp/)(XP) unit ("integral" account balance)

The raw account size is 64 bytes.

Account transaction data never appears unencrypted in a public field. Only the account owner can decrypt it.

{% hint style="info" %}
#### Zero account

When a user creates their first transaction there will not be an existing account in the Merkle tree. In this case a zero account should be used where all fields are zero except $$\eta$$.​
{% endhint %}
