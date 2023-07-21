---
description: External transactions to the privacy pool
---

# Direct Deposits

Direct deposits allow other dApps and partners to make direct zkBob deposits by knowing receiver zk-address, without dealing with zk-cryptography. This greatly simplifies integration with other dApps and smart contracts

## <mark style="background-color:green;">Sending Direct Deposit</mark>

You can deposit your account via direct deposit scheme

{% hint style="warning" %}
Direct deposit processing can take up to 20 minutes
{% endhint %}

<pre class="language-typescript"><code class="lang-typescript"><strong>async directDeposit(
</strong>    type: DirectDepositType,
    fromAddress: string,
    amount: bigint,
    sendTxCallback: (tx: PreparedTransaction) => Promise&#x3C;string>,
): Promise&#x3C;void>
</code></pre>

### Parameters

`type` - [direct deposit type](../common-types.md#direct-deposit-type) (token or native)

{% hint style="warning" %}
For DD with `DirectDepositType.Token` type you must ensure the [direct deposit contract address](direct-deposits.md#getting-direct-deposit-contract) has allowance to spend your tokens. Before direct deposit sending you must approve needed amount of tokens (do not forget the fee)
{% endhint %}

{% hint style="info" %}
`DirectDepositType.Native` is only available for pools which are serve the native wrapped token like WETH. Such pools must have `isNative = true` in the the[client-configuration.md](../configuration/initializing-the-client/client-configuration.md "mention")
{% endhint %}

`fromAddress` - the `0x`-address which will be used to depositing funds

`amount` - token amount to deposit into an account (in pool dimension)

{% hint style="warning" %}
Direct deposit fee will be fetched and added to the `amount` under the hood. Do not include it yourself
{% endhint %}

`sendTxCallback` - a callback with prepared transaction which should be sent by user. After sending user should return a transaction hash. Transaction to be sent describes as following:

```typescript
interface PreparedTransaction {
    to: string;    // DD queue contract address
    amount: bigint;    // amount in native dimension
    data: string;    // transaction raw data
}
```

### Example

```typescript
const myAddress = '0x49C92c016d2c7A245aAF5351BD932D9D61536eC0';
await zkClient.directDeposit(
    DirectDepositType.Token,
    myAddress,
    50000000000n,  // 50 BOB
    async (tx: PreparedTransaction) => {
      const txObject: TransactionConfig = {
        from: myAddress,
        to: tx.to,
        value: tx.amount.toString(),
        data: tx.data,
      };

      const gas = await this.web3.eth.estimateGas(txObject);
      const gasPrice = Number(await this.web3.eth.getGasPrice());
      txObject.gas = gas;
      txObject.gasPrice = `0x${BigInt(gasPrice).toString(16)}`;
      txObject.nonce = await this.web3.eth.getTransactionCount(address);
  
      const signedTx = await this.web3.eth.signTransaction(txObject);
      const receipt = await this.web3.eth.sendSignedTransaction(signedTx.raw);
  
      return receipt.transactionHash;
    }
);
```

## <mark style="background-color:green;">Getting Pending Direct Deposits</mark>

Until sent direct deposits are processed and included in the privacy pool you can fetch queued DD transactions belonging to your account

{% hint style="warning" %}
Direct deposit processing can take up to 20 minutes
{% endhint %}

```typescript
public async getPendingDDs(): Promise<DirectDeposit[]>
```

### Returns

`Promise` returns array of pending [DirectDeposit](../common-types.md#direct-deposit)s

### Example

```typescript
const pendingDDs = await zkClient.getPendingDDs();
console.log(`You have ${pendingDDs.length} pending direct deposit(s) in queue`);
// output: You have 3 pending direct deposit(s) in queue
```

## <mark style="background-color:green;">Getting Direct Deposit Fee</mark>

Direct deposit transaction should include extra cost for the relayer

```typescript
async directDepositFee(): Promise<bigint>
```

### Returns

`Promise` returns the direct deposit fee in the pool dimension

### Example

```typescript
console.log(`DD fee: ${await zkClient.directDepositFee()}`);
// output: DD fee: 100000000
```

## <mark style="background-color:green;">Getting Direct Deposit Contract</mark>

The DD contract is a part of the privacy pool solution. So each pool has own direct deposit queue contract

```typescript
async directDepositContract(): Promise<string>
```

### Returns

`Promise` returns the direct deposit queue contract address

### Example

```typescript
console.log(`${await zkClient.directDepositContract()}`);
// output: 0xE3Dd183ffa70BcFC442A0B9991E682cA8A442Ade
```
