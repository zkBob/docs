---
description: An application for zk-based transactions
---

# UI Overview

## UI actions

* [Setup](account-creation/) a zkAccount using an existing web3 wallet or a secret phrase.
* [Deposit ](deposits.md)arbitrary token amounts of a supported token into the application.
* [Transfer](transfers/) deposits to other participants using zkSnarks technology (proof of transaction without disclosing details of the sender, recipient, and value).
* [Withdraw](withdrawals/) arbitrary token amounts securely and privately.
* [Generate secure addresses](generate-a-secure-address.md) for funds transfer within the application.
* [Create and use payment links](payment-links.md) to accept donations or payments from other users who may even know about zkBob. They do not need a zkBob account and can pay with any token.

## ZeroPool Library

The zkBob application uses the [Zero Pool](https://zeropool.network/) library to prepare zkproof transactions and interact with the relayer. The application is responsible for:

* Processing transactions
* Restoring local state
* Building zkproofs from user input (ie amount, address)
* Interacting with the relayer
