---
description: Retrieve user's shielded funds and activity
---

# Balances and History

## <mark style="background-color:green;">Get the Account Balance</mark>

```typescript
async getTotalBalance(updateState: boolean = true): Promise<bigint>
```

{% hint style="info" %}
Only completed (mined on the pool smart contract) transactions are used to calculate the balance. To include pending txs use the[`getOptimisticTotalBalance`](balances-and-history.md#getting-the-balance-considering-pending-transactions) method instead.
{% endhint %}

### Parameters

`updateState` - update the state before calculating the balance if `true`

{% hint style="info" %}
It's recommended to set `updateState` to `false` in case of sequential operations where we recently updated the state. So you can reduce the sync tyme and the relayer requests count
{% endhint %}

### Returns

`Promise` returns the shielded token's balance in the pool dimension (account + all unspent notes)

### Example

```typescript
const balance = await zkClient.getTotalBalance();
console.log(`Your balance in the private pool is: ${balance}`);
// output: Your balance in the private pool is: 150000000000
```

## <mark style="background-color:green;">Get the Balance Including Pending Transactions</mark>

Get the balance including transactions owned by the account that have been submitted to the pool contract but not yet mined.

```typescript
async getOptimisticTotalBalance(updateState: boolean = true): Promise<bigint>
```

### Parameters

`updateState` - update the state before calculating the balance if `true`&#x20;

### Returns

`Promise` returns the shielded token's balance (including pending transactions) in the pool dimension (account + all unspent notes).

### Example

```typescript
const confirmedBalance = await zkClient.getTotalBalance();
const optimisticBalance = await zkClient.getOptimisticTotalBalance(false);
console.log(`Your confirmed balance:  ${confirmedBalance}`);
console.log(`Your optimistic balance: ${optimisticBalance}`);
// output: Your confirmed balance:  150000000000
//         Your optimistic balance: 170000000000
```

## <mark style="background-color:green;">Get the Balance Components</mark>

The customer's balance consists of the account balance and the unspent notes. The notes are produced by incoming transfers. Each user-originated transaction collects the 3 oldest notes to the account and marks them as spent ones. The balance configuration (funds distribution between account and notes) may affect the outgoing transfers and withdrawals. The following method retrieves the total balance as well as the account and notes components.

```typescript
async getBalances(updateState: boolean = true): Promise<[bigint, bigint, bigint]>
```

### Parameters

`updateState` - update the state before calculating the balance if `true`&#x20;

### Returns

`Promise` returns the tuple `[total, account, notes]` where `total = account + notes`  without pending transactions (all balances are in the pool token dimension).

### Example

```typescript
const [total, acc, note] = await zkAccount.getBalances();
console.log(`Balance:  ${total} (${acc} on the account and ${notes} in notes)`);
// output: Balance:  170000000000 (150000000000 on the account and 20000000000 in notes)
```

## <mark style="background-color:green;">Get the Transaction History</mark>

```typescript
async getAllHistory(updateState: boolean = true): Promise<HistoryRecord[]>
```

### Parameters

`updateState` - update the state before calculating the balance if `true`&#x20;

### Returns

`Promise` returns an array of [`HistoryRecord`](../common-types.md#history-record) objects

### Example

```typescript
const records = await zkAccount.getAllHistory();
console.log(`The account contains ${records.count} history records`);
// output: The account contains 42 history records
```

## <mark style="background-color:green;">Get the Compliance Report</mark>

The compliance report is an extended version of the regular history. It contains transaction details including input notes, decryption keys and other fields needed to show historical integrity.

```typescript
async getComplianceReport(
    fromTimestamp: number | null,
    toTimestamp: number | null,
    updateState: boolean = true,
  ): Promise<ComplianceHistoryRecord[]>
```

### Parameters

* `fromTimestamp` - the start time for the compliance report request (seconds since Jan 01 1970)
* `fromTimestamp` - the final time for the compliance report request (seconds since Jan 01 1970)
* `updateState` - update the state before calculating the balance if `true`&#x20;

### Returns

`Promise` returns the array of [`ComplianceHistoryRecord`](../common-types.md#compliance-history-record) objects

### Example

```typescript
const records = await zkAccount.getComplianceReport();
console.log(`Generated ${records.count} compliance history records`);
// output: Generated 42 compliance history records
```

