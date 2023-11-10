---
description: Emergency funds withdrawal in case the relayer is unavailable
---

# Forced Exit

The zkBob solution involves interacting with the pool through a relayer. You cannot send deposit, transfer, or withdrawal transactions directly to the contract. This is done to facilitate interaction with the pool without the need to pay fees in the native coin. If the relayer subsystem is unavailable for the any reason, there is an option for emergency withdrawal from the pool. In this case, you must interact directly with the pool contract.

In the event of an emergency exit, all available funds will be withdrawn to the specified address, but the zk-account will be destroyed, and you will no longer be able to use it for transactions.

An emergency exit is performed in two stages. In the first stage, you request an exit window from the pool contract, specifying all the necessary parameters in advance, such as the withdrawal address, the amount of funds, and the computed proof for the withdrawal transaction. This operation is known as commit. The exit window opens 1 hour after the commitment and is available for 24 hours after the commit.

The second stage can be completed only during the window's validity period. To perform it you must send an emergency exit execution transaction.

If you miss the exit window, you will need to cancel the previously committed emergency exit in order to request a new exit window.

If the relayer's functionality is restored before executing an emergency exit, and you send any regular transaction to the pool, the existing emergency exit will be invalidated.

{% hint style="danger" %}
If the relayer is in the operational state it will block your transactions from your account during the active exit window.
{% endhint %}

After a successful emergency exit, your account is marked as destroyed on the pool contract and all incoming transfers to that account will burned.

{% hint style="warning" %}
It's important to note that in the case of an emergency exit execution, only the exact amount specified in the commit transaction will be withdrawn. If you receive an incoming transfer after the commit but before the withdrawal is executed, it will not be withdrawn. In this case, you must wait until the exit window expires, cancel the exit, and then create a new one (which takes into account the received funds).
{% endhint %}

The following routines guide you through the emergency exit procedure and help to retrieve related info.

## <mark style="background-color:green;">Checking If Account Destroyed</mark>

The account can be destroyed only during execution of the forced exit.

```typescript
async isAccountDead(): Promise<boolean>
```

{% hint style="info" %}
This is a single function related to the emergency exit flow which works even if the forced exit feature is unsupported by the privacy pool. For other routines you should [check forced exit support](forced-exit.md#checking-if-emergency-exit-supported-by-current-pool) first.
{% endhint %}

### Returns

`Promise` returns `boolean` indicating if the forced exit procedure was performed for the account.

### Example

```typescript
if (await zkClient.isAccountDead()) {
    console.log('Sorry, you cannot transact anymore: your account was destroyed');
} else {
    console.log('Forced exit was not performed yet');
}
// output: Forced exit was not performed yet
```

## <mark style="background-color:green;">Checking If Emergency Exit is Supported by Current Pool</mark>

The forced exit functionality can be unsupported in the certain pools. Use the following routine to check if this feature is supported.

```typescript
async isForcedExitSupported(): Promise<boolean>
```

### Returns

`Promise` returns `boolean` indicating if the forced exit is supported by the current pool contract.

### Example

```typescript
if (await zkClient.isForcedExitSupported()) {
    console.log('Okay, let\'s try to withdraw your funds emergency');
    // ...forced-exit related flow...
} else {
    console.log('Sorry, emergency exit is unsupported by the pool');
}
// output: Okay, let's try to withdraw your funds emergency
```

## <mark style="background-color:green;">Getting Forced Exit State for Account</mark>

To check forced exit state for your current account you can use the following routine:

```typescript
async forcedExitState(): Promise<ForcedExitState>
```

### Returns

`Promise` returns [`ForcedExitState`](../common-types.md#forced-exit-state) enum member.

### Example

```typescript
switch (await zkClient.forcedExitState()) {
    case ForcedExitState.NotStarted:
        console.log('Forced exit was not started');
        break;
    case ForcedExitState.CommittedWaitingSlot:
        console.log('Forced exit commited but not available yet');
        break;
    case ForcedExitState.CommittedReady:
        console.log('Forced exit commited and ready to execute');
        break;
    case ForcedExitState.Completed:
        console.log('Forced exit completed');
        break;
    case ForcedExitState.Outdated:
        console.log('Forced exit outdated');
        break;
    default:
        console.error('Unknown forced exit state');
        break;
}
// output: Forced exit was not started
```

## <mark style="background-color:green;">Getting Committed Forced Exit Details</mark>

When you commit a forced exit the set of parameters should be specified. The following method retrieves the committed forced exit parameters (if the exist).

```typescript
async activeForcedExit(): Promise<CommittedForcedExit | undefined>
```

{% hint style="info" %}
This method returns a forced exit object only in the following states: `CommittedWaitingSlot`, `CommittedReady`, `Outdated`

The result is `undefined` in case the forced exit was executed, cancelled, or not started
{% endhint %}

### Returns

`Promise` returns [`CommittedForcedExit`](../common-types.md#committed-forced-exit) object or `undefined` if unavailable.

### Example

<pre class="language-typescript"><code class="lang-typescript">const committed = await zkClient.activeForcedExit()
if (committed) {
    console.log('Found committed forced exit');
<strong>    console.log(`Nullifier:  ${committed.nullifier}`);
</strong><strong>    console.log(`Operator:   ${committed.operator}`);
</strong><strong>    console.log(`Receiver:   ${committed.to}`);
</strong><strong>    console.log(`Amount:     ${committed.amount}`);
</strong><strong>    console.log(`Start time: ${new Date(committed.exitStart * 1000).toLocaleString()}`);
</strong><strong>    console.log(`End time:   ${new Date(committed.exitEnd * 1000).toLocaleString()}`);
</strong><strong>    console.log(`Tx hash:    ${committed.txHash`);
</strong><strong>}
</strong>// Found committed forced exit
// Nullifier:  7151204415055949250553114361348271896976012357469097285489034137873972583466
// Operator:   0x6D16337B9a1651556749230eeAA4Dc602A22DcAf
// Receiver:   0x6D16337B9a1651556749230eeAA4Dc602A22DcAf
// Amount:     677000000000
// Start time: 24.10.2023, 21:49:12
// End time:   25.10.2023, 20:49:12
// Tx hash:    0x2cb5eb49f7b89810675fce988f259b7f47a63710029a303ab0906b59a5bba7b2
</code></pre>

## <mark style="background-color:green;">Getting Completed Forced Exit Details</mark>

The following structure describes the second stage result. It's available only in the `ForcedExitState.Completed` state.

```typescript
async executedForcedExit(): Promise<FinalizedForcedExit | undefined>
```

{% hint style="info" %}
Although [FinalizedForcedExit](../common-types.md#finalized-forced-exit) object contains the cancelled property which can indicate the forced exit was cancelled, the current method doesn't return an object for the cancelled forced exit (because it's difficult to locate it due to nullifier updates).
{% endhint %}

### Returns

`Promise` returns [`FinalizedForcedExit`](../common-types.md#finalized-forced-exit) object or `undefined` if unavailable.

### Example

<pre class="language-typescript"><code class="lang-typescript">const executed = await zkClient.executedForcedExit()
if (executed) {
    console.log('Found completed forced exit');
<strong>    console.log(`Nullifier:  ${executed.nullifier}`);
</strong><strong>    console.log(`Receiver:   ${executed.to}`);
</strong><strong>    console.log(`Amount:     ${executed.amount}`);
</strong><strong>    console.log(`Tx hash:    ${executed.txHash`);
</strong><strong>}
</strong>// Found completed forced exit
// Nullifier:  13575656066236883124312534101991453259859429227583973074085956794292119880492
// Receiver:   0x6e9aE59020788AfCaAb243FCD0e9317189a81435
// Amount:     7000000000
// Tx hash:    0x6df714f0e6100f1755611e0f3e58e23111b4642a3f437fca0062b685ab84db9e
</code></pre>

## <mark style="background-color:green;">Checking Funds Available for Forced Exit</mark>

You should always check available funds and compare with the account balance before committing to the forced exit.

{% hint style="danger" %}
Keep in mind your account configuration may consist of a lot of incoming transfers (notes) which cannot be withdrawn within a single transaction. For the forced exit flow you can use just an account balance with three notes. You cannot initiate an aggregation transaction to collect unspent notes by direct pool contract interaction. Additional details about notes handling can be found [here](../../../zkbob-overview/fees/unspent-note-handling.md)
{% endhint %}

{% hint style="info" %}
The forced exit flow doesn't require the relayer so you shouldn't pay the relayer fee. But you should have a few native coins to pay the pool contract transaction fee.
{% endhint %}

```typescript
async availableFundsToForcedExit(): Promise<bigint>
```

### Returns

`Promise` returns amount of tokens in pool dimension which can be withdrawn during the forced exit.

### Example

```typescript
const feFunds = await zkClient.availableFundsToForcedExit();
const balance = await zkClient.getTotalBalance();
if (feFunds < balance) {
    console.log(`You can withdraw just ${feFunds} of ${balance}`);
} else {
    console.log(`You can withdraw all of your balance (${feFunds})`);
}
// output: You can withdraw all of your balance (677000000000)
```

## <mark style="background-color:green;">Making Commit Forced Exit</mark>

This is the first stage of the emergency exit flow. The following method will prepare all values needed to send the commit transaction and invoke a callback to send it.

```typescript
async requestForcedExit(
    executerAddress: string,
    toAddress: string,
    sendTxCallback: (tx: PreparedTransaction) => Promise<string>
  ): Promise<CommittedForcedExit>
```

### Parameters

`executerAddress` - who will be able to send execute transaction (set to zero address to disable constraints).

`toAddress` - who will receive funds during forced exit execution.

`sendTxCallback` - callback will be invoked by this method when commit transaction should be sent. You should sign and send the requested transaction (described by [PreparedTransaction](../common-types.md#transaction-to-be-send)) in your callback and return a transaction hash.

### Returns

`Promise` returns [`CommittedForcedExit`](../common-types.md#committed-forced-exit) object or `undefined` if unavailable

### Example

<pre class="language-typescript"><code class="lang-typescript">const committed = await zkClient.requestForcedExit(
    '0x6D16337B9a1651556749230eeAA4Dc602A22DcAf',
    '0x6D16337B9a1651556749230eeAA4Dc602A22DcAf',
    async (tx: PreparedTransaction) => 
        this.sendAndSendTx(tx.to, tx.amount, tx.data);
);
    
if (committed) {
    console.log(`Forced exit has been committed ${committed.txHash}`);
<strong>    console.log(`Wait until ${new Date(committed.exitStart * 1000).toLocaleString()}`);
</strong><strong>}
</strong>// Forced exit has been committed 0x2cb5eb49f7b89810675fce988f259b7f47a63710029a303ab0906b59a5bba7b2
// Wait until 24.10.2023, 21:49:12

</code></pre>

## <mark style="background-color:green;">Executing Forced Exit</mark>

Use the following routine to complete the committed forced exit. It will automatically collect all needed data and invoke the callback to send a transaction.

{% hint style="info" %}
This routine should be invoked only in `ForcedExitState.CommittedReady` [state](forced-exit.md#getting-forced-exit-state-for-account) otherwise an `InternalError` will thrown
{% endhint %}

```typescript
async executeForcedExit(
    sendTxCallback: (tx: PreparedTransaction) => Promise<string>
): Promise<FinalizedForcedExit>
```

### Parameters

`sendTxCallback` - callback will be invoked by this method when execute transaction should be sent. You should sign and send requested transaction (described by [PreparedTransaction](../common-types.md#transaction-to-be-send)) in your callback and return a transaction hash

### Returns

`Promise` returns [`FinalizedForcedExit`](../common-types.md#finalized-forced-exit) object or `undefined` if unavailable

### Example

<pre class="language-typescript"><code class="lang-typescript">const completed = await zkClient.executeForcedExit(
<strong>    async (tx: PreparedTransaction) => 
</strong>        this.sendAndSendTx(tx.to, tx.amount, tx.data);
);
    
if (completed) {
    console.log(`Forced exit has been completed: ${completed.txHash}`);
<strong>    console.log(`Check address ${completed.to} for withdrawn funds`);
</strong><strong>}
</strong>// Forced exit has been completed: 0x6df714f0e6100f1755611e0f3e58e23111b4642a3f437fca0062b685ab84db9e
// Check address 0x6e9aE59020788AfCaAb243FCD0e9317189a81435 for withdrawn funds
</code></pre>

## <mark style="background-color:green;">Cancelling Forced Exit</mark>

If you miss the exit window, you need to first cancel the exit (with the current nullifier) before creating a new one. Use the following method:

{% hint style="info" %}
This routine should be invoked only in `ForcedExitState.Outdated` [state](forced-exit.md#getting-forced-exit-state-for-account) otherwise an `InternalError` will thrown
{% endhint %}

```typescript
async cancelForcedExit(
    sendTxCallback: (tx: PreparedTransaction) => Promise<string>
): Promise<FinalizedForcedExit>
```

### Parameters

`sendTxCallback` - callback will be invoked by this method when cancel transaction should be sent. You should sign and send requested transaction (described by [PreparedTransaction](../common-types.md#transaction-to-be-send)) in your callback and return a transaction hash.

### Returns

`Promise` returns [`FinalizedForcedExit`](../common-types.md#finalized-forced-exit) object or `undefined` if unavailable.

### Example

<pre class="language-typescript"><code class="lang-typescript">const cancelled = await zkClient.cancelForcedExit(
<strong>    async (tx: PreparedTransaction) => this.sendAndSendTx(tx.to, tx.amount, tx.data);
</strong>);
    
if (cancelled) {
    console.log(`Forced exit has been cancelled: ${cancelled.txHash}`);
<strong>}
</strong>// Forced exit has been cancelled: 0x81039f753be2078a467370947807fdbdca571630f21920b6d6337b305fb488d4
</code></pre>
