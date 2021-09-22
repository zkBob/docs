---
description: Define a customer wallet state
---

# Accounts

The account contains complete information about user's private wallet. It definitely linked with a customer by intermediate key $$\eta$$derived from the spending key $$\sigma$$owned by him. The holder of the spending key is called an account owner.

The account holds current balance value and `spent offset` which split all notes in spent and unspent. It's a sufficient data to retrieve a wallet state.

An account is a tuple $$(\eta, i, b, e, t)$$ where

* $$\eta$$ \(32 bytes\) is an intermediate key, derived from the spending key: $$\eta = Hash((\sigma*G).x)$$
* $$i$$\(6 bytes\) is a spent offset. It split used \(spent\) and unused notes. Notes with indexes below $$i$$are considered to be spent
* $$b$$\(8 bytes\) is current account balance
* $$e$$\(8 bytes\) is an "integral" account balance
* $$t$$\(10 bytes\) is a salt. Since transaction contains account hash we must use a random salt to hide possible lack of account changes

Accounts are residing in the transactions data but it never appears unencrypted in public field. Only an account owner can decrypt it. 

