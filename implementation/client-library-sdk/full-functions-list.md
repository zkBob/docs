---
description: All available functions of ZkBobClient object
---

# Full Functions List

{% hint style="info" %}
Functions available in the account-less mode are marked with `[*]`
{% endhint %}

## Initializing and Сonfiguring

* [create](configuration/initializing-the-client/)
* [login](configuration/attaching-a-user-account/#login)
* [logout](configuration/attaching-a-user-account/#logout)
* \[\*] [currentPool](configuration/switching-between-pools.md#getting-the-current-pool)
* \[\*] [availabePools](configuration/switching-between-pools.md#getting-available-pools)
* [switchToPool](configuration/switching-between-pools.md#switching-to-another-pool)
* [hasAccount](configuration/attaching-a-user-account/#is-account-attached)
* \[\*] [getProverMode](account-less-mode-operations/using-the-delegated-prover.md#getting-current-prover-mode)
* \[\*] [setProverMode](account-less-mode-operations/using-the-delegated-prover.md#setting-prover-mode)

## Balances and History

* [getTotalBalance](full-mode-operations/balances-and-history.md#getting-the-account-balance)
* [getBalances](full-mode-operations/balances-and-history.md#getting-the-balance-components)
* [getOptimisticTotalBalance](full-mode-operations/balances-and-history.md#getting-the-balance-considering-pending-transactions)
* [giftCardBalance](full-mode-operations/gift-cards-maintenance.md#getting-gift-card-actual-balance)
* [getAllHistory](full-mode-operations/balances-and-history.md#getting-the-transaction-history)
* [getPendingDDs](full-mode-operations/direct-deposits.md#getting-pending-direct-deposits)
* [getComplianceReport](full-mode-operations/balances-and-history.md#getting-the-compliance-report)

## Addresses

* [generateAddress](full-mode-operations/shielded-addresses.md#generating-shielded-address)
* [generateUniversalAddress](full-mode-operations/shielded-addresses.md#generating-universal-shielded-address)
* [generateAddressForSeed](full-mode-operations/shielded-addresses.md#generating-shielded-address-for-another-account)
* [verifyShieldedAddress](full-mode-operations/shielded-addresses.md#shielded-address-verification)
* [isMyAddress](full-mode-operations/shielded-addresses.md#checking-if-a-shielded-address-belongs-to-the-account)
* [addressInfo](full-mode-operations/shielded-addresses.md#decomposing-shielded-address-into-components)

## Transactions

* [deposit](full-mode-operations/sending-transactions.md#depositing-funds)
* [depositEphemeral](full-mode-operations/ephemeral-deposits.md#sending-ephemeral-deposits)
* [directDeposit](full-mode-operations/direct-deposits.md#sending-direct-deposit)
* [transferMulti](full-mode-operations/sending-transactions.md#transfer-funds-inside-a-pool)
* [withdrawMulti](full-mode-operations/sending-transactions.md#withdraw-funds-from-the-pool)
* [redeemGiftCard](full-mode-operations/gift-cards-maintenance.md#gift-card-redemption)
* [waitJobsTxHashes](full-mode-operations/transaction-maintenance.md#waiting-transactions-send-to-the-pool)
* [waitJobTxHash](full-mode-operations/transaction-maintenance.md#waiting-transactions-send-to-the-pool)
* [isReadyToTransact](full-mode-operations/account-state.md#checking-sending-transaction-ability)
* [waitReadyToTransact](full-mode-operations/account-state.md#waiting-for-sending-transaction-ability)

## Preparing Transactions

* \[\*] [getRelayerFee](account-less-mode-operations/transaction-fees.md#getting-relayer-raw-fee)
* \[\*] [atomicTxFee](account-less-mode-operations/transaction-fees.md#estimating-transaction-typical-fee)
* [feeEstimate](full-mode-operations/fee-estimations.md#estimating-transaction-fee)
* [directDepositFee](full-mode-operations/direct-deposits.md#getting-direct-deposit-fee)
* \[\*] [maxSupportedTokenSwap](account-less-mode-operations/transaction-constraints.md#maximum-supported-token-swap-during-withdraw)
* \[\*] [minTxAmount](account-less-mode-operations/transaction-constraints.md#minimum-transaction-amount)
* [calcMaxAvailableTransfer](full-mode-operations/transaction-configuration.md#getting-maximum-available-outgoing-transaction)
* [getTransactionParts](full-mode-operations/transaction-configuration.md#getting-transaction-parts)
* \[\*] [getLimits](account-less-mode-operations/transaction-constraints.md#getting-pool-limits)

## Ephemeral Addresses

* [getEphemeralAddress](full-mode-operations/ephemeral-deposits.md#getting-ephemeral-address-at-index)
* [getNonusedEphemeralIndex](full-mode-operations/ephemeral-deposits.md#getting-the-first-non-used-ephemeral-address-index)
* [getUsedEphemeralAddresses](full-mode-operations/ephemeral-deposits.md#getting-all-used-ephemeral-addresses)
* [getEphemeralAddressInTxCount](full-mode-operations/ephemeral-deposits.md#retrieving-number-of-token-transfers-to-the-address)
* [getEphemeralAddressOutTxCount](full-mode-operations/ephemeral-deposits.md#retrieving-number-of-token-transfers-from-the-address)
* [getEphemeralAddressPrivateKey](full-mode-operations/ephemeral-deposits.md#getting-the-ephemeral-address-private-key)

## Forced Exit

* [isAccountDead](full-mode-operations/forced-exit.md#checking-if-account-destroyed)
* [isForcedExitSupported](full-mode-operations/forced-exit.md#checking-if-emergency-exit-is-supported-by-current-pool)
* [forcedExitState](full-mode-operations/forced-exit.md#getting-forced-exit-state-for-account)
* [activeForcedExit](full-mode-operations/forced-exit.md#getting-committed-forced-exit-details)
* [executedForcedExit](full-mode-operations/forced-exit.md#getting-completed-forced-exit-details)
* [availableFundsToForcedExit](full-mode-operations/forced-exit.md#checking-funds-available-for-forced-exit)
* [requestForcedExit](full-mode-operations/forced-exit.md#making-commit-forced-exit)
* [executeForcedExit](full-mode-operations/forced-exit.md#executing-forced-exit)
* [cancelForcedExit](full-mode-operations/forced-exit.md#cancelling-forced-exit)

## Misc

* \[\*] [shieldedAmountToWei](account-less-mode-operations/converting-token-amounts.md#shielded-to-native)
* \[\*] [weiToShieldedAmount](account-less-mode-operations/converting-token-amounts.md#native-to-shielded)
* \[\*] [networkName](account-less-mode-operations/helpers.md#getting-the-network-chain-name)
* \[\*] [poolId](account-less-mode-operations/helpers.md#getting-the-pool-identifier)
* \[\*] [getRelayerState](account-less-mode-operations/getting-the-state.md#getting-relayer-state)
* \[\*] [getRelayerOptimisticState](account-less-mode-operations/getting-the-state.md#getting-relayer-optimistic-state)
* \[\*] [getPoolState](account-less-mode-operations/getting-the-state.md#getting-pool-contract-state)
* [getLocalState](full-mode-operations/account-state.md#getting-the-local-state)
* [rollbackState](full-mode-operations/account-state.md#rollbacking-the-local-state)
* [cleanState](full-mode-operations/account-state.md#cleaning-the-local-state)
* [updateState](full-mode-operations/account-state.md#syncing-the-local-state)
* \[\*] [getLibraryVersion](account-less-mode-operations/versioning.md#getting-library-version)
* \[\*] [getRelayerVersion](account-less-mode-operations/versioning.md#getting-relayer-version)
* \[\*] [getProverVersion](account-less-mode-operations/versioning.md#getting-delegated-prover-version)
* \[\*] [codeForGiftCard](account-less-mode-operations/gift-cards.md#encoding-gift-card-parameters)
* \[\*] [giftCardFromCode](account-less-mode-operations/gift-cards.md#decoding-gift-card-code)
* [getStatFullSync](full-mode-operations/other-routines.md#getting-the-full-state-sync-statistic)
* [getAverageTimePerTx](full-mode-operations/other-routines.md#getting-average-sync-time)
* [directDepositContract](full-mode-operations/direct-deposits.md#getting-direct-deposit-contract)
* \[\*] [tokenSellerContract](account-less-mode-operations/helpers.md#getting-token-seller-contract)
* \[\*] [getState](account-less-mode-operations/client-library-status.md#getting-the-client-state)
* \[\*] [getProgress](account-less-mode-operations/client-library-status.md#getting-the-client-continuous-state-progress)
