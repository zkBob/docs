# Transfers

{% hint style="warning" %}
All actions are performed on a test application running on Kovan testnet. Instructions will be updated when app is live in production.
{% endhint %}

Transfers are made within the zkpool between zkAccounts. You do not transfer to an 0x account, but rather to another zkAccount holder's one-time address. Typically you receive a sending address from a friend via a private channel.&#x20;

zkAccount addresses are not fixed. You can (and are encouraged to) generate a new address for each incoming transaction. It is not possible to link different private addresses to one another or to the primary account. Only the account owner can confirm ownership of a private address.

Each created address is encoded in base58 format. For example `5fkW3dXTvA8Kizt1EbuRyjWofuqR4Ud1YTjGgY1r8nGosDeSaUreq6bwfF61jWL`

Any previously generated address can be used indefinitely, so if you send an address to one party and then generate a new address to send to another party, both can be used to receive transferred tokens.&#x20;

1\) Check your zkAccount is connected. Since you will not be depositing funds, your web3 wallet does not need to be connected, but it can be as well.



