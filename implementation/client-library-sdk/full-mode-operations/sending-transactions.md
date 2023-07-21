---
description: Deposit, transfers and withdrawals
---

# Sending Transactions

## <mark style="background-color:green;">Depositing Funds</mark>

Send tokens to the privacy pool

```typescript
async deposit(
    amountGwei: bigint,
    signatureCallback: (request: SignatureRequest) => Promise<string>,
    fromAddress: string,
    relayerFee?: RelayerFee,
): Promise<string>
```

<details>

<summary>See Also</summary>

* [directDeposit(type, fromAddress, amount, sendTxCallback)](direct-deposits.md#sending-direct-deposit)
* [depositEphemeral(amount, ephemeralIndex, relayerFee)](ephemeral-deposits.md#sending-ephemeral-deposits)
* [getLimits(address, directRequest)](../account-less-mode-operations/transaction-constraints.md#getting-pool-limits)

</details>

### Parameters

`amountGwei` - token amount to deposit into an account (in pool dimension)

`signatureCallback` - a callback with [SignatureRequest](../common-types.md#signature-request) which invoked when needed to ask user to sign data

{% hint style="info" %}
The signature request type depends on deposit scheme which set in the pool configuration during library init. Currently all deployments use `SignatureType.TypedDataV4` signature
{% endhint %}

`fromAddress` - the `0x`-address which will be used to depositing funds

`relayerFee` - a raw [relayer fee object](../common-types.md#relayer-raw-fee) which will be used to estimate total transaction fee (will requested under the hood when undefined)

### Returns

`Promise` returns `jobId` returned by relayer which can be use to monitor transaction

### Example

<pre class="language-typescript"><code class="lang-typescript"><strong>const jobId = await zkClient.depositPermittable(
</strong>      100000000000n, // 100 BOB in pool dimension
      async (signingRequest) => {
          switch (signingRequest.type) {
          case SignatureType.TypedDataV4:
              // signingRequest.data is an object for typed signature
              // which contains domain, types, primaryType and message fields
              return signTypedData(signingRequest.data); // use a 3rd-party lib to sign
          case SignatureType.PersonalSign:
              // signingRequest.data is hex-string representation of signing data
              return sign(signingRequest.data); // use a 3rd-party lib to sign
          default:
              throw new Error(`Signing request with unknown type`);
          }
      },
      '0x49C92c016d2c7A245aAF5351BD932D9D61536eC0',    // depositor address
      undefined    // the actual relayer fee will be requested under the hood
   );
console.log(`Deposit sent to the relayer. A job with ID ${jobId} has been assigned`)
// output: Deposit sent to the relayer. A job with ID 42 has been assigned
</code></pre>

## <mark style="background-color:green;">Transfer Funds Inside a Pool</mark>

Transfer tokens inside a pool to the requested addresses. The function creates a set of transactions (needed to process requests), sends it to the relayer in sequence order and returns a set of job IDs assigned by relayer

```typescript
async transferMulti(
    transfers: TransferRequest[],
    relayerFee?: RelayerFee
): Promise<string[]>
```

{% hint style="info" %}
This routine may produce several transactions in rare cases when you have a lot of unspent notes. It can increase overall fee needed for transferring requested funds amount. Please refer to the examples described [here](../../../zkbob-overview/fees/unspent-note-handling.md) to better understanding notes aggregation flow
{% endhint %}

### Parameters

`transfers` - a set of transfer destinations. A single destination should contain the receiver shielded address and associated funds amount to transfer

{% hint style="info" %}
Please keep in mind the single transaction can include up to 127 output notes, i.e. if your request contains more than 127 destination addresses additional transactions can be created
{% endhint %}

`relayerFee` - a raw [relayer fee object](../common-types.md#relayer-raw-fee) which will be used to estimate total transaction fee (will requested under the hood when undefined)

### Returns

`Promise` returns array of job IDs (each sent transaction associated with the unique job ID assigned by relayer)

### Example

```typescript
transfers = [{
   // Alice will receives 15 BOB
   destination: zkbob_sepolia:CFSGGVWQpmwxmHEiZ123PXKVxbpv3LthegaSiwS1RKW1o5ExL3zRSRTg3TR9sHF,
   amountGwei: 15000000000n
}, {
   // Bob will receive 42 BOB
   destination: zkbob_sepolia:ELg4LcwsynhEaZWh9SNgWBbK7Xg2tjVyTNCgaxvoy4c7jLNudcJqAdL459RHBdg
   amountGwei: 42000000000n
}];
const jobIds = await zkClient.transferMulti(transfers);
console.log(`Accepted by relayer. Job(s) ${jobIds.join(', ')} created`)
// output: Accepted by relayer. Job(s) 43 created
```

## <mark style="background-color:green;">Withdraw Funds From the Pool</mark>

Withdraw tokens to the `0x`-address. The function creates a set of transactions (needed to process withdraw), sends it to the relayer and returns a set of job IDs assigned by relayer

```typescript
async withdrawMulti(
    address: string,
    amountGwei: bigint,
    swapAmount: bigint,
    relayerFee?: RelayerFee
): Promise<string[]>
```

{% hint style="info" %}
This routine may produce several transactions in rare cases when you have a lot of unspent notes. It can increase overall fee needed for the funds withdrawal. Please refer to the examples described [here](../../../zkbob-overview/fees/unspent-note-handling.md) to better understanding notes aggregation flow
{% endhint %}

<details>

<summary>See Also</summary>

* [getLimits(address, directRequest)](../account-less-mode-operations/transaction-constraints.md#getting-pool-limits)
* [maxSupportedTokenSwap()](../account-less-mode-operations/transaction-constraints.md#maximum-supported-token-swap-during-withdraw)

</details>

### Parameters

`address` - a `0x` destination address to the sending withdrawn tokens

`amountGwei` - tokens amount to be withdrawn (in pool dimension)

`swapAmount` - part of `amountGwei` which requested to swap to the native coins on withdrawal (in pool dimension)

{% hint style="info" %}
Swap ability doesn't supported on the each pool. Use method [maxSupportedTokenSwap](../account-less-mode-operations/transaction-constraints.md#maximum-supported-token-swap-during-withdraw) to request how many tokens you can swap on the waithdrawal transaction&#x20;
{% endhint %}

`relayerFee` - a raw [relayer fee object](../common-types.md#relayer-raw-fee) which will be used to estimate total transaction fee (will requested under the hood when undefined)

### Returns

`Promise` returns array of job IDs (each sent transaction associated with the unique job ID assigned by relayer)

### Example

```typescript
const jobIds = await zkClient.withdrawMulti(
    '0x09d967A5268b64E8334f3a65336C33B7538BFe69',
    25000000000n, // withdraw 25 BOB
    5000000000n,  // swap 5 (of 25 BOB) to MATIC
);
console.log(`Accepted by relayer. Job(s) ${jobIds.join(', ')} created`)
// output: Accepted by relayer. Job(s) 44 created
```
