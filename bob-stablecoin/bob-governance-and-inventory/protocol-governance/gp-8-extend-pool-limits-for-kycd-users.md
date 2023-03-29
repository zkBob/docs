# GP 8: Extend pool limits for KYC'd users

{% hint style="success" %}
Proposal was confirmed and executed: \
[https://polygonscan.com/tx/0xd1f394e880ac56f1929f93d49b98b7b318b80544040ffe3009191f46ce438fb3](https://polygonscan.com/tx/0xd1f394e880ac56f1929f93d49b98b7b318b80544040ffe3009191f46ce438fb3)
{% endhint %}

## Objective

Allow KYC'd users to deposit additional funds into zkBOB. An additional tier is added to increase limits to 20,000 BOB per day for users who hold a BAB NFT on Binance Chain.

### BAB NFTs

In 2022, Binance introduced soulbound tokens known as [Binance Account Bound (BAB) tokens](https://www.binance.com/en/support/faq/frequently-asked-questions-on-binance-account-bound-bab-token-adbd05fe149344d59a348f82d5bf359d). These tokens serve as identity credentials for Binance users who have completed KYC verification. These credentials can be extended to other chains using the [KnowYourCat](https://docs.knowyourcat.id/) protocol.

### KnowYourCat Protocol

Information about BAB token ownership can be transferred from BNB Smart Chain to additional chains using the [KnowYourCat](https://docs.knowyourcat.id/) protocol. This protocol creates a cryptographic proof that a user possesses the token on BSC and lets users provide this proof to other supported chains. A user's BAB token status can be obtained from an NFT-compatible contract. The official KnowYourCat contract on Polygon is at [0xE3c6Fd631043A0a1927c4681C736b778aA8F8feF](https://polygonscan.com/address/0xE3c6Fd631043A0a1927c4681C736b778aA8F8feF), as referenced in the [KnowYourCat documentation](https://docs.knowyourcat.id/for-developers/knowyourcat-protocol/contract-addresses).

## Mechanism

To extend limits for BAB token holders, this proposal creates a new tier limit in the zkBob pool and configures a KYC Provider Manager which checks the status of BAB token ownership on the KnowYourCat NFT contract.

The KYC Provider Manager manager is deployed at [0xb8580ea6312dd2311d72bc932b0354a07d974138](https://polygonscan.com/address/0xb8580ea6312dd2311d72bc932b0354a07d974138).&#x20;

This manager contract introduces the method `getIfKYCpassedAndTier` to access the limit tier for a user owning a BAB token. The manager provides `254` as the tier id for users who hold a BAB NFT.

The manager is configured so that each time a user requests a deposit, the account is checked to see if it has its own tier limit. If it does not, the manager is asked to return the tier and default limits apply.

## Proposal breakdown

The corresponding transaction in the governance safe is[ transaction #28](https://app.safe.global/matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x313f81393765ffe7f9353306248891380ad4c14f95a270ef05dbbe520c48acab).

The transaction contains 2 actions:

### Action 1

`setLimits` (the selector is `0xe8fd02e4`) is called from the zkBobPool contract ([0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB)). The method is called to configure limits for tier `254` which is associated with BAB token owners. The limits for this tier differ from tier `0` where `dailyUserDepositCap` and `depositCap` are both 10,000 BOB.

```
tvlCap: 1'000'000 BOB
dailyDepositCap: 300'000 BOB
dailyWithdrawalCap: 100'000 BOB
dailyUserDepositCap: 20'000 BOB
depositCap: 20'000 BOB
dailyUserDirectDepositCap: 10'000 BOB
directDepositCap: 1'000 BOB
```

The `zkBobPool` contract is upgraded to reflect these changes. ([0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB)).&#x20;

The new implementation [0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB](https://polygonscan.com/address/0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB) is applied through the `upgradeTo` call (the selector is `0x3659cfe6`).

### Action 2

`setKycProvidersManager` (the selector 790c3a33) is called from the zkBobPool contract ([0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB)).&#x20;

This method configures the contract [0xb8580ea6312dd2311d72bc932b0354a07d974138](https://polygonscan.com/address/0xb8580ea6312dd2311d72bc932b0354a07d974138) as the KYC Provider Manager.

## Verification

Proposal execution can be verified in the [zkBobPool contract](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB#readProxyContract):

1. The method `kycProvidersManager` must return `0xb8580ea6312dd2311d72bc932b0354a07d974138`
2. The method `getLimitsFor` for an account synchronised with BAB token ownership information through [the KnowYourCat protocol](https://knowyourcat.id/) should display new limits. For example, one could use the account `0x813399e5b08Bb50b038AA7dF6347b6AF2D161828`.





