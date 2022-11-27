---
description: Incorporate privacy into everyday applications
---

# Hackathon

{% hint style="info" %}
* [zkBob Intro](hackathon.md#intro)
* [zkBob API & Cloud Wallet](hackathon.md#zkbob-api-and-cloud-wallet)
  * [Use case ideas](hackathon.md#use-case-examples)
  * [API key](hackathon.md#api-key)
  * [Receiving address](hackathon.md#receiving-address)
  * [Notes](hackathon.md#notes)
  * [Payment flow](hackathon.md#payment-flow)
* [Get Started](hackathon.md#get-started)
* [References Table](hackathon.md#references-table)
* [Prizes](hackathon.md#prizes)
{% endhint %}

<figure><img src="../.gitbook/assets/bob-privacy.png" alt=""><figcaption></figcaption></figure>

## Intro

Privacy is normal. We are all entitled to privacy in many aspects of our lives, and this includes our finances. It is normal to keep details such as how much money you have, how much money you make, and how you choose to spend your money private. This can be difficult on-chain.

Enter zkBob. zkBob is a privacy application which anonymizes transfers between users. The BOB stablecoin lets users exchange value in a stable, predictable manner. zkSnarks prove certain actions have occurred without revealing details about who completed the action or the amount transferred. Compliance features deter bad actors and illicit usage. zkBob gives privacy back to the everyday user.&#x20;

zkBob UI is developed as a client side application which generates zkproofs on a user's machine. This is ideal from a security and privacy standpoint, however it can introduce some obstacles for application developers.  To simplify zkBob interactivity and reduce friction for users and application developers, we have released the zkBob API and cloud wallet into beta.&#x20;

## zkBob API and Cloud Wallet

With the API, developers do not need to use a client SDK to manage crytpographic keys, client application state and other complexities. Users do not need to secure keys entirely on their own or wait for cryptographic proof generation.&#x20;

The hosted version of the zkBob REST API and cloud wallet greatly expands the possibilities for interaction. For the hackathon, we want you to explore new use cases for private transactions using the zkBob API and BOB stablecoin.&#x20;

### Use Case Ideas

* Donation platform where donors maintain anonymity
* Fundraising platform with internal KYC while maintaining public privacy
* DAO accounting application
* Private payment-splitting application for friend groups
* Wallet integration for private payments - integrate BOB payments into an open source wallet
* Tip bot/extension (telegram bot, twitter bot, browser extension)
* Food delivery service with private payments
* BOB powered vending machine/POS
* \*Extra credit: Direct library integration, direct deposits
* Your idea here!!!

### API Key

In the ZkBob Cloud Wallet every developer has their own secret api key used to manage funds. The key is usually kept on the server and given individually to each team. [See below](hackathon.md#get-started) for more info on receiving an API key.

### **Receiving address**

Since all payments are settled on a public blockchain privacy can be complicated. To avoid obvious correlations between txs we use special receiving addresses that can’t be linked in any way to the account. Using a new receiving address for every incoming transaction eliminates any possibility of deanonymizing the recipient.

### **Notes**

Balance management may seem complex but it is actually straightforward. There are notes and accounts — the difference is similar to physical paper notes in your wallet and your bank account. Most of the time this doesn’t matter to users or devs, but there is one edge case when it’s important. **Due to technical restrictions the user cannot spend more than 3 notes in one operation.** If the user needs to do this there will be one or more additional technical transactions to accumulate the balance to the account prior to the transfer itself.

### Payment Flow

This is a typical payment process flow. Here you see example relationships between Alice and Charlie, but any transactional relationship can be created here. Charlie can use a self-custodial ZkBob wallet, or they both can share a single ZkBob cloud account.

<figure><img src="https://lh4.googleusercontent.com/Ui2B8RryXkWAd467o90_hq7AgXYKb30yml5KHnQjm2BUmZ8RDGHCDXjp6ddEckiGHyclnD2Tu4gnIoe_5rA7S8d19I1ImQ4hvTyntuVudDy58OX16sC8t0_G5Tb9HUMg2UQbr6BA_9czusxSvrRkDUmmzNRSFAHyJ77ne12ILjTKjUM1CJMS0uI-vC5L" alt=""><figcaption></figcaption></figure>

## Get Started

<figure><img src="../.gitbook/assets/2.png" alt=""><figcaption></figcaption></figure>

* **Get an API Key & BOB:** Join the telegram at [https://t.me/+sMbZvmVzYmQ3ODlk](https://t.me/+sMbZvmVzYmQ3ODlk) to request your API key. The API key is used to generate and interact with the zkBob cloud wallet. You will receive 10 BOB into the account to use for testing, functionality and demonstration purposes.
* **HackMD:** View the HackMD with extended API documentation and usage examples.
* **Explore API Methods:** Use Swagger and Postman links to view available methods for shielded account interaction. Note that the current API does not include deposit and withdrawal functionality, only proving mechanisms related to transfers. Deposits and withdrawals may be performed manually.

## References Table

|                       |   |
| --------------------- | - |
| API structure         |   |
| API description/calls |   |
| Swagger               |   |
| Postman               |   |

## API call sequence diagram / Other additional info

## Prizes

For the EthIndia hackathon, 5 prizes of $2000 BOB ($2000 USD equivalent) will be awarded to the top 5 projects utilizing the zkBob API. Creativity, innovation, and implementation will be considered during judging.

<figure><img src="../.gitbook/assets/zkBob-3.png" alt=""><figcaption></figcaption></figure>
