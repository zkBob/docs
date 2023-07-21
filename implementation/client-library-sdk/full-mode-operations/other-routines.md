---
description: Statistic routines etc
---

# Other Routines

## <mark style="background-color:green;">Getting the Full State Sync Statistic</mark>

The following function is used to evaluate syncing performance during the full state synchronizing

```typescript
getStatFullSync(): SyncStat | undefined
```

{% hint style="info" %}
The statistic within that function build during the full state sync only
{% endhint %}

### Returns

[SyncStat](../common-types.md#synchronization-statistic) object containing different performance indicators

### Example

<pre class="language-typescript"><code class="lang-typescript"><strong>const stat = zkClient.getStatFullSync();
</strong><strong>if (stat) {
</strong>   console.log(`Full state sync: ${stat.totalTime / 1000} sec`);
   console.log(`  avg speed:    ${stat.timePerTx.toFixed(1)} ms/tx`);
   console.log(`  total tx:     ${stat.txCount}`);
   console.log(`  cold-storage: ${stat.cdnTxCnt} txs`);
   console.log(`  memo items:   ${stat.decryptedLeafs}`);
}
</code></pre>

## <mark style="background-color:green;">Getting Average Sync Time</mark>

To retrieve average time spent on processing one transaction in the local state you can use the following method

```typescript
getAverageTimePerTx(): number | undefined
```

{% hint style="info" %}
The estimate can be inaccurate because the regular sync (opposite with the full one) fetches just few latest transactions so overhead can affect the average time
{% endhint %}

### Returns

average time per transaction in milliseconds or `undefined` if there is no statistic collected

### Example

<pre class="language-typescript"><code class="lang-typescript"><strong>const avg = zkClient.getAverageTimePerTx();
</strong>console.log(`Average sync time: ${avg ?? -1} ms/tx`)
<strong>// output: Average sync time: 0.8 ms/tx
</strong></code></pre>
