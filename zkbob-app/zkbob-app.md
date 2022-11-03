---
description: An application for zk-based transactions
---

# UI Overview

Users can perform the following operations when interacting with the zkBob application UI. The app UI is available at [https://app.zkbob.com/](https://app.zkbob.com/).

[BOB tokens](../bob-stablecoin/bob-details.md) are needed to use the application for deposits, transfers or withdrawals.

{% hint style="warning" %}
zkBob is currently optimized for the desktop/laptop environment. It does not work on iPhones and is limited on Android devices.
{% endhint %}

## Steps to Get Started

* [Acknowledge terms](acknowledge-terms.md) to get started.
* [Setup](account-creation/) a zkAccount using a seed phrase or existing web3 wallet.
* [Deposit ](deposits.md)arbitrary token amounts of a stablecoin into the application.
* [Transfer](transfers.md) deposits to other participants using zkSnarks technology (proof of transaction without disclosing details of the sender, recipient, and value).
* [Withdraw](withdrawals.md) arbitrary token amounts securely and privately.
* [Generate secure addresses](generate-a-secure-address.md) for funds transfer within the application.

The zkBob application uses the [Zero Pool](https://zeropool.network/) library to prepare zkproof transactions and interact with the relayer. The application is responsible for:

* Processing transactions
* Restoring local state
* Building zkproofs from user input (ie amount, address)
* Interacting with the relayer



