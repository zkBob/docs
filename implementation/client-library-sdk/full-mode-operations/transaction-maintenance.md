---
description: Monitoring transactions after sending
---

# Transaction Maintenance

The relayer queues, verifies and sends your transaction upon receipt. It can take up to several minutes. To be able to track the transaction statuses the relayer provides you a job ID for each received transaction. You can use it in the following methods

## <mark style="background-color:green;">Waiting Transactions Send to the Pool</mark>

Waiting all provided jobs to be sent to the pool contract

```typescript
async waitJobsTxHashes(jobIds: string[]): Promise<{jobId: string, txHash: string}[]>
```

The corresponding version for single job ID is also available:

```typescript
async waitJobTxHash(jobId: string): Promise<string>
```

### Parameters

`jobIds` - array of job identifiers or

`jobId` - job identifiers

### Returns

`Promise` returns the array of objects where jobId is one of requested jobs and txHash - transaction hash associated with that job (or just a txHash for `waitJobTxHash`)

### Example

```typescript
const res = await zkAccount.waitJobsTxHashes(['123', '124']);
console.log(`Done ${res.map((j) => `job #${j.jobId}: ${j.txHash}`).join(`\n`)}`);
// output:
// job #123: 0xf1fcf095b4cfd9bda5b18024acf6a1fdf6d9e040a1ec4abed140088b802f73df
// job #124: 0xd5e8960bad7f5964dd3cf3c8853b33e4368c3ec4f3626ef1ea546b5405deeb58
```
