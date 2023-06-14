---
description: An application for zk-based transactions
---

# UI Overview

## UI actions

* [Setup](account-creation/) a zkAccount using an existing web3 wallet or a secret phrase.&#x20;
* [Deposit ](deposits.md)arbitrary token amounts of teh BOB stablecoin into the application.
* [Transfer](transfers/) deposits to other participants using zkSnarks technology (proof of transaction without disclosing details of the sender, recipient, and value).
* [Withdraw](withdrawals/) arbitrary token amounts securely and privately.
* [Generate secure addresses](generate-a-secure-address.md) for funds transfer within the application.

## ZeroPool Library

The zkBob application uses the [Zero Pool](https://zeropool.network/) library to prepare zkproof transactions and interact with the relayer. The application is responsible for:

* Processing transactions
* Restoring local state
* Building zkproofs from user input (ie amount, address)
* Interacting with the relayer



