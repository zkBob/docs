---
description: Receiving key, outgoing viewing key
---

# Ephemeral keys

Ephemeral keys are used to encrypt transactions data (accounts and notes). The symmetric cipher algorithm ([ChaCha20Poly1305](https://datatracker.ietf.org/doc/html/rfc8439)) which applies to the memo block is require to use different keys for security reasons.

There are two cases where ephemeral keys are generated: [notes encryption](../transaction-overview/untitled-1/memo-block-encryption.md#notes-encryption) and [shared secrets encryption](../transaction-overview/untitled-1/memo-block-encryption.md#shared-secrets-encryption). In booth cases ephemeral keys are derived from the random secret keys generated before the each encryption operation. The account's intermediate key is used for derivation process.

The **receiving key** is a set of intermediate key $$\eta$$ and ephemeral public key $$Ai$$ which are used to derive note encryption key. Successfully decrypted notes with the $$\eta$$ key are considered as received ones by a client.

The **outgoing viewing key** is used to decrypt shared secrets in the memo block. Shared secrets contains symmetric keys which are used to decrypt output account and notes for the current transaction.

