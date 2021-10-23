---
description: Used to encrypt accounts, notes and shared keys
---

# Memo Block Encryption

The main purpose of the memo block is to publish transaction details. Due to transactions secure nature, the list of admitted users to access that data is strictly restricted. There are two critical data encrypted in the memo block: an output account and output notes.

The transaction sender should be admitted to the output account and notes. Output account is used by the sender to keep the wallet state. Notes are used to retrieve outgoing transactions history. Output account should be unavailable to the transaction receiver. Shared secrets are used to implement this feature.

So there are three encrypted entities in the memo block.

### Account Encryption

An output account in the memo block is encrypted with the random key $$key_a$$ by the symmetric algorithm [ChaCha20Poly1305](https://tools.ietf.org/html/rfc8439):

* Generate a random symmetric 256-bit key: $$key_a = random()$$
* Encrypt output account: $$acc^{enc} = ChaCha20Poly1305_{key_a}^{nonce}(acc)$$

{% hint style="info" %}
Nonce for $$ChaCha20Poly1305$$ is a fixed value. It's the first 12 bytes of the $$keccak256("ZeroPool")$$: `0x5bbdffc6fe73c460f1b2b85d`
{% endhint %}

To decrypt output account user should obtain $$key_a$$ from the memo block. The transaction sender only could access this key.

### Notes Encryption

Output notes are encrypted with the ephemeral keys. Steps to encrypt a $$Note_i$$:

* Generate a random 256-bit ephemeral secret key: $$a_i = random()$$
* Calculate an ephemeral public key for the $$Note_i$$: $$A_i = a_i \text{ToSubGroupHash}_{E(F_r)}(Note_i.d)$$
* Derive a symmetric encryption key for the note: $$key_i = keccak256(a_i Note_i.P_d)$$
* Encrypt note: $$Note_i^{enc} = ChaCha20Poly1305_{key_i}^{nonce}(Note_i)$$
* There are two public values for the each note in the memo block: $$A_i$$ and $$Note_i^{enc}$$

To decrypt a note the user should obtain the corresponding $$key_i$$. There are two ways to get it:

* to obtain $$key_i$$ from the shared secrets (a sender case)
* to derive $$key_i$$ from the $$A_i$$ and account's key $$\eta$$ (a receiver case): $$key_i = keccak256(A_i \eta)$$

### Shared secrets encryption

Shared secrets block contains symmetric keys for account and notes encryption: $$keys = (key_a, key_1, key_2, ...)$$. The following actions are used to encrypt these keys:

* Generate a random 256-bit key: $$a_p = random()$$
* Calculate an ephemeral public key for the shared secrets: $$A_p = a_p G$$
* Derive a symmetric encryption key for the shared secrets: $$key_p = keccak256(A_p acc.\eta)$$
* Encrypt $$keys$$: $$keys^{enc} = ChaCha20Poly1305_{key_p}^{nonce}(keys)$$
* Put $$(A_p, keys^{enc})$$ in the shared secrets block

{% hint style="info" %}
$$keys^{enc}$$ could be decrypted with the $$\eta$$ key only
{% endhint %}



