---
description: >-
  The main transaction part containing the encrypted data to restore balances
  and history
---

# Memo Block

### Fields overview

The memo block contains detailed transaction data such as output notes, accounts, transaction fee and other specific fields.

The memo block consists of the following fields. There are two optional fields in the memo block, dependent on transaction type: `native amount` and `receiver`. These values included in the withdrawal transaction's memo block only.

![The memo block structure](../../../.gitbook/assets/memo\_new\_eng.png)

| Field name            | Size (bytes)            | Description                                                                                                                                                      |
| --------------------- | ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| fee                   | 8                       | Assets amount transferred to the relayer                                                                                                                         |
| native amount         | 8                       | Assets amount for withdrawal. This field is optional for withdrawal transactions only                                                                            |
| receiver              | 20                      | A destination address for withdrawal transaction (chain-specific)                                                                                                |
| $$ItemsNum$$          | 4                       | Number of encrypted elements in the memo block. An element is an account or a note. Note has a fixed number of items currently: one output account and 127 notes |
| $$Hash(acc)$$         | 32                      | Output account hash (with updated balance)                                                                                                                       |
| $$Hash(Note_i)$$      | 32                      | Output note hash                                                                                                                                                 |
| $$A_p$$               | 32                      | Ephemeral public key. It's using to decrypt $$Keys^\text{enc}$$by transaction sender                                                                             |
| $$Keys^\text{enc}$$   | 32 \* $$ItemsNum$$ + 16 | Encrypted keys to decrypt output account and notes. Only the transaction sender can decrypt these keys                                                           |
| $$acc^\text{enc}$$    | 86                      | Encrypted output account with an updated balance                                                                                                                 |
| $$A_i$$               | 32                      | Ephemeral public key for notes. It's using to decrypt $$Note_i^\text{enc}$$ by note owner (receiver)                                                             |
| $$Note_i^\text{enc}$$ | 76                      | An encrypted note. It can be decrypted with $$A_i$$ by owner or by transaction sender through a $$Keys^\text{enc}$$ disclosure                                   |

### **Memo block encryption**



