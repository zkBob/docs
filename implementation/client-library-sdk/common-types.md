---
description: The types used within the different library methods
---

# Common Types

## <mark style="background-color:green;">Transaction Type</mark>

```typescript
enum TxType {
  Deposit,
  Transfer,
  Withdraw,
  BridgeDeposit,
}
```

* `TxType.Deposit`: the deposit via token approval

{% hint style="warning" %}
The type `TxType.Deposit` is supported but isn't in active use because it requires an extra approve transaction from the user. Use `TxType.BridgeDeposit` instead.
{% endhint %}

* `TxType.Transfer`: move tokens inside a pool to the destination zk-addresses
* `TxType.Withdraw`: withdrawal tokens from the pool to the destination 0x-address
* `TxType.BridgeDeposit`: deposit tokens to the privacy pool via permit scheme (the primary type for deposit tx)

## <mark style="background-color:green;">Relayer Raw Fee</mark>

```typescript
interface RelayerFee {
    fee: {
        permittableDeposit: bigint;
        transfer: bigint;
        withdrawal: bigint;
        deposit: bigint;
    };
    oneByteFee: bigint;
    nativeConvertFee: bigint;
}
```

where

* `fee` - base cost of the transaction execution depending on the transaction type.

{% hint style="info" %}
In most cases of deposit `fee.permittableDeposit` is used instead of `fee.deposit` (because the 2nd one belongs to the deposits via approve which is not currently used on the deployed pools)
{% endhint %}

* `oneByteFee` - calldata byte cost (may be zero depended on relayer configuration).
* `nativeConvertFee` - additional cost needed to swap withdrawn tokens to native coins (only for the withdrawal transactions).

## <mark style="background-color:green;">Fee Amount Required for Request</mark>

```typescript
interface FeeAmount {
  total: bigint;
  txCnt: number;
  calldataTotalLength: number;
  relayerFee: RelayerFee;
  insufficientFunds: boolean;
}
```

where

* `total` - absolute fee value needed to process request (in pool dimension)
* `txCnt` - number of transactions needed to process request
* `calldataTotalLength` - number of calldata bytes occupied by all transactions
* `relayerFee` - [RelayerFee](common-types.md#relayer-raw-fee) which was used for fee estimation
* `insufficientFunds` - true when the local balance is insufficient for requested tx amount

## <mark style="background-color:green;">Pool Limits</mark>

```typescript
interface Limit {
    total: bigint;
    available: bigint;
}

interface PoolLimits {
    deposit: {
        total: bigint;
        components: {
            singleOperation: bigint;
            dailyForAddress: Limit;
            dailyForAll: Limit;
            poolLimit: Limit;
        };
    }
    withdraw: {
        total: bigint;
        components: {
            dailyForAll: Limit;
        };
    }
    dd: {
        total: bigint;
        components: {
            singleOperation: bigint;
            dailyForAddress: Limit;
        };
    }
    tier: number;
}
```

where

* `Limit` - is an abstract limit with `total` and `available` tokens in the pool dimension
* `PoolLimits.deposit` - limits for deposit from the specified address
  * `total` - total available to deposit from specified address right now
  * `components.singleOperation` - maximum deposit amount in the single tx
  * `components.dailyForAddress` - deposit limit for the specified address during that day
  * `components.dailyForAll` - deposit limit for any address during that day
  * `components.poolLimit` - TVL limit
* `PoolLimits.withdraw` - limits for withdrawal transaction
  * `total` - total available to withdraw right now
  * `components.dailyForAll` - withdraw limit for any address during that day
* `PoolLimits.dd` - limits for direct deposit transaction
  * `total` - total available to direct deposit right now
  * `components.singleOperation` - maximum direct deposit amount in the single tx
  * `components.dailyForAddress` - direct deposit limit for the specified address during that day
* `tier` - provided address tier (the higher tier - the higher limits), default 0

## <mark style="background-color:green;">Prover Mode</mark>

```typescript
enum ProverMode {
  Local,
  Delegated,
  DelegatedWithFallback
}
```

* `Local` - use local prover (most secure)
* `Delegated` - use external proving machine (aka Delegated Prover)
* `DelegatedWithFallback` - work primarily in Delegated mode; switch to Local is Delegated is unavailable

## <mark style="background-color:green;">Tree State</mark>

```typescript
interface TreeState {
    root: bigint;
    index: bigint;
}
```

where

* `root` - Merkle root value (assuming all leaves placed at indices greater than or equal to `index` should be zeroed)
* `index` - the index in Merkle tree where the next transaction will be placed

#### Example

```typescript
const exampleState: TreeState = {
    root: 20259123668790783065614334268308370728058669663334716067122266810210516357394n,
    index: 533760n
}
```

## <mark style="background-color:green;">Gift-Card Properties</mark>

```typescript
class GiftCardProperties {
    sk: Uint8Array;
    birthIndex: number;
    balance: bigint;
    poolAlias: string;
}
```

where

* `sk` - spending key (keep it in secret: everybody who know the key is able to use the gift-card's funds)
* `birthIndex` - index in Merkle tree where gift-card was created. It's needed to speed-up card redeeming process
* `balance` - preassigned card balance in pool dimension (it's not an actual balance, just a label for smooth UI)
* `poolAlias` - the card destination privacy pool name (it should be defined in [client configuration](configuration/initializing-the-client/client-configuration.md))

## <mark style="background-color:green;">Service Version</mark>

It's a common interface to keep external service version information. Currently external service include relayer and delegated prover

```typescript
interface ServiceVersion {
  ref: string;
  commitHash: string;
}
```

where

* ref - short version string (e.g. `3.1.0`)
* commitHash - corresponded commit hash in version control system (e.g. `4535bc9592057706614d62889713be2ba9555838`)

## <mark style="background-color:green;">History Record</mark>

A single history record always describes a single transaction to the pool.

```typescript
enum HistoryTransactionType {
  Deposit = 1,
  TransferIn,
  TransferOut,
  Withdrawal,
  AggregateNotes,
  DirectDeposit,
}

enum HistoryRecordState {
  Pending = 1,
  Mined,
  RejectedByRelayer,
  RejectedByPool,
}

interface TokensMoving {
  from: string,
  to: string,
  amount: bigint,
  isLoopback: boolean,
  ddFee?: bigint,
}

class HistoryRecord {
    type: HistoryTransactionType,
    timestamp: number,
    actions: TokensMoving[],
    fee: bigint,
    txHash: string,
    state: HistoryRecordState,
    failureReason?: string,
    extraInfo?: any,
}
```

where

* `HistoryTransactionType` describes all possible transaction types
* `HistoryRecordState` describes the transaction state. `Pending` state means tx was sent to the relayer but not mined on the pool contract yet. The transaction in `HistoryRecordState.Mined` state is a finalized one. `HistoryRecordState.RejectedByRelayer` and `HistoryRecordState.RejectedByPool` reflect transactions which wasn't completed
* `TokensMoving` is an universal interface describing tokens amount and direction. A single history record may contain a few `TokensMoving` objects
  * `TokensMoving.from` and `TokensMoving.to` contain origin and destination addresses of the funds transferring. There are no strict restrictions for these fields. E.g. `TokensMoving.to` field may contain `0x` address for the withdrawal transaction as well as shielded address for the outgoing transfers inside a privacy pool. Due to privacy transactions nature one of these fields are always void string
  * `TokensMoving.amount` is a token transferring value in the pool dimension
  * `TokensMoving.isLoopback` is applicable for the outgoing transfers only. This field contain true in case of transferring funds to the own account
  * `TokensMoving.ddFee` is an optional field which exists only for direct-deposit associated transactions and contains a direct deposit fee amount
* `HistoryRecord.type` is one of the `HistoryTransactionType` enum members
* `HistoryRecord.timestamp` is an associated transaction time (in seconds since Jan 01 1970)
* `HistoryRecord.actions` is a set of token moves (e.g. a multitransfer transaction may contain several destination addresses)
* `HistoryRecord.fee` is a transaction cost (relayer's reward) in pool token dimension. The incoming transfers always have zero in this field
* `HistoryRecord.txHash` is an associated transaction hash (to the pool smart contract)
* `HistoryRecord.state` is a transaction state (an `HistoryRecordState` member)
* `HistoryRecord.failureReason` is an optional `string` field which contain a problem description in case the history record is in a rejected state
* `HistoryRecord.extraInfo` is an optional field of any type which may contain transaction related info. For example, direct deposits made with the payment link may contain the following object in that field:

```
interface DDPaymentInfo {
  note: string | null;
  sender: string;
  token: string;
}
```

## <mark style="background-color:green;">Compliance History Record</mark>

The compliance history record provides additional details than the regular history record. It contains fields needed to provide evidence of historical ownership. Anyone can provide a regular history to the 3rd parties. But only the compliance-based history proves the records are unmodified and that all of them belong to the concrete account.

```typescript
class ComplianceHistoryRecord extends HistoryRecord {
  public index: number;
  public nullifier?: Uint8Array;
  public nextNullifier?: Uint8Array;
  public encChunks: { data: Uint8Array, index: number }[];
  public ecdhKeys:  { key: Uint8Array, index: number }[];
  public acc?: Account;
  public notes:  { note: Note, index: number }[];
  public inputs?: {
    account: {index: number, account: Account},
    intermediateNullifier: string,
    notes: {index: number, note: Note}[],
  };
}
```

where

* `index` - the transaction index in the Merkle tree (the first leaf index)
* `nullifier` - transaction [nullifier](../transaction-overview/the-nullifiers.md) needed to chain the transaction sequence (`undefined` for incoming transfers)
* `nextNullifier` - the nullifier based on the transaction output account (will be used in the next transaction)
* `encChunks` - encrypted elements (a chunk corresponds to encrypted account or note)
* `ecdhKeys` - keys to decrypting chunks at the corresponding indexes
* `acc` - decrypted output [account](../account-and-notes/accounts.md) (`undefined` for incoming transfers)
* `notes` - a set of decrypted [notes](../account-and-notes/notes.md)
* `inputs` - transaction inputs (undefined for incoming txs)
  * `account` - decrypted input account (the first transaction has always zero account in that field)
  * `intermediateNullifier` - a nullifier pre-image, may be safely disclosed to 3rd parties without sharing intermediate key $$\eta$$. Used to calculate nullifier in conjunction with input account.
  * `notes` - set of decrypted input notes which were aggregated to the account balance

## <mark style="background-color:green;">Shielded Address Components</mark>

The shielded address decomposition on the low-level components (see [shielded address structure](../zkbob-keys/address-derivation.md) for details)

```typescript
interface IAddressComponents {
    format: string;
    d: string;
    p_d: string;
    checksum: Uint8Array;
    pool_id: string;
    derived_from_our_sk: boolean;
    is_pool_valid: boolean;
}
```

where

* `format` is one of the following values:&#x20;
  * `'old'` - prefix-less address format, deprecated
  * `'pool'` - pool-specific address which should be used on the concrete privacy pool
  * `'generic'` - universal address which may be used on any pool
* `d` - address diversifier (a random number, decimal string)
* `p_d` - diversifier public part (derived from the diversifier and account intermediate key $$\eta$$, decimal string)
* `checksum` - 4 bytes to verify address correctness
* `pool_id` - the pool ID in string representation which the address belongs to (`'any'`  for generic addresses)
* `derived_from_our_sk` - indicating is it own address
* `is_pool_valid` - indicating is the address can be used on the current pool

## <mark style="background-color:green;">Signature Request</mark>

The signature can be requested from the user during depositing funds into the shielded pool. The following interface describes request details. There are two signature types which can be requested depends on the deposit scheme (deposit scheme defined in the pool configuration)

```typescript
enum SignatureType {
    PersonalSign, // signature for deposit-via approve
    TypedDataV4,  // permit deposit scheme
}

interface SignatureRequest {
    type: SignatureType,
    data: any,  // an string for personal sign, object for typed signatures
}
```

where

* `format` is one of the following values:&#x20;
  * `'old'` - prefix-less address format, deprecated
  * `'pool'` - pool-specific address which should be used on the concrete privacy pool
  * `'generic'` - universal address which may be used on any pool
* `d` - address diversifier (a random number, decimal string)
* `p_d` - diversifier public part (derived from the diversifier and account intermediate key $$\eta$$, decimal string)
* `checksum` - 4 bytes to verify address correctness

## <mark style="background-color:green;">Transfer Request</mark>

The following object is used to describe transfers inside a privacy pool or withdrawal directional in some cases

```typescript
interface TransferRequest {
  destination: string;
  amountGwei: bigint;
}
```

where

* `destination` is an address of funds receiver (shielded or `0x`)
* `amountGwei` - token amount in pool dimension

## <mark style="background-color:green;">Transfer Config</mark>

The following object describes configuration of the _**single**_ transfer/withdrawal transaction to the privacy pool

```typescript
interface TransferConfig {
  inNotesBalance: bigint;
  outNotes: TransferRequest[];
  calldataLength: number;
  fee: bigint;
  accountLimit: bigint;
}
```

where

* `inNotesBalance` is a sum of input note values which will be aggregated on the account when transaction processed&#x20;
* `outNotes` - set of [transfer requests](common-types.md#transfer-request) processed with the transaction
* `calldataLength` - transaction's calldata bytes count
* `fee` - absolute transaction fee (in pool dimension)&#x20;
* `accountLimit` - minimum account remainder after transaction (not in use currently, always `0n`)&#x20;

## <mark style="background-color:green;">Direct Deposit Type</mark>

```typescript
enum DirectDepositType {
    Token,
    Native
}
```

* `Token` - sending token to the pool
* `Native` - sending native coins to the pool (available only for pools which are serve the native wrapped token like WETH)

{% hint style="info" %}
`DirectDepositType.Native` is only available for pools which are serve the native wrapped token like WETH. Such pools must have `isNative = true` in the the[client-configuration.md](configuration/initializing-the-client/client-configuration.md "mention")
{% endhint %}

## <mark style="background-color:green;">Direct Deposit</mark>

The following object describes direct deposit transaction in the different states

```typescript
enum DirectDepositState {
    Queued,    // was sent to the DD queue contract
    Deposited, // was included in the privacy pool's state
    Refunded,  // was returned to the fallback address
}

interface DirectDeposit {
    id: bigint;
    state: DirectDepositState;
    amount: bigint;
    destination: string;
    fallback: string;
    timestamp: number;
    queueTxHash: string;
}
```

where

* `id` unique DD identifier
* `state` - Queued/Deposited/Refuded
* `amount` - DD value (in pool dimension, without fee)
* `destination` - zk-address in the privacy pool to be deposited
* `fallback` - `0x` address to refund DD in case of it wasn't processed in time
* `timestamp` - when it got into the current state
* `queueTxHash` - initial transaction hash

## <mark style="background-color:green;">Ephemeral Address</mark>

Ephemeral addresses are used in the external deposit scheme. This is an EOA with the key management inside the library&#x20;

```typescript
interface EphemeralAddress {
    index: number;
    address: string;
    tokenBalance: bigint;
    nativeBalance: bigint;
    permitNonce: number;
    nativeNonce: number;
}
```

where

* `index` - index of address inside a pool (last HD path component)
* `address` - 0x native address
* `tokenBalance` - token balance in pool dimension (meaning the token on which the pool operates)
* `nativeBalance` - native address balance in wei
* `permitNonce` - number of executed permit allowances (token transfers)
* `nativeNonce` - number of outgoing native transactions

## <mark style="background-color:green;">Synchronization Statistic</mark>

```typescript
interface SyncStat {
  txCount: number;
  cdnTxCnt: number;
  decryptedLeafs: number;
  fullSync: boolean;
  totalTime: number;
  timePerTx: number;
}
```

where

* `txCount` - total transactions fetched (relayer + CDN)
* `cdnTxCnt` - number of transactions fetched in binary format from CDN (cold storage)
* `decryptedLeafs` - number of loaded leafs in the Merkle tree (deposit/withdrawal = 1 leaf, transfer = 1 + notes\_cnt leafs)
* `fullSync` - `true` in case of bulding full Merkle tree on the client
* `totalTime` - syncing time in milliseconds
* `timePerTx` - average time per transaction in milliseconds

## <mark style="background-color:green;">Client Library State Callback</mark>

The callback is used to notify the application that the internal state has been updated. There are regular and continuous states. The second one has a `progress` property (a number from 0 to 1).

```typescript
type ClientStateCallback = (state: ClientState, progress?: number) => void;

enum ClientState {
  Initializing,
  AccountlessMode,
  SwitchingPool,
  AttachingAccount,
  // the following routines belongs to the full mode only
  FullMode,
  StateUpdating,           // fast sync
  StateUpdatingContinuous, // sync which takes longer than threshold
  HistoryUpdating,
}
```

The following client library states distinguished:

* `Initializing` - the state during the client instantiation. This state is short-term. After client initialization the state sets to `AccountlessMode`
* `AccountlessMode` - the client library is ready to operate but no account was attached. Limited functionality is available in that state (see [account-less-mode-operations](account-less-mode-operations/ "mention"))
* `SwitchingPool` - the client switches current privacy pool. Most routines are unavailable during this state
* `AttachingAccount` - the user account is initializing. This state also appears on pool switching when the client operates in full mode (if account was already attached to another pool it should be reattached to the new one)
* `FullMode` - Regular state: client and account are ready to operate. All routines are available
* `StateUpdating` \ `StateUpdatingContinuous`- the client is syncing the user account state with the pool. The continuous state using in case of state sync take over threshold (1 sec currently)
* `HistoryUpdating` - the history synchronization. Additional activities are needed to produce history records from the local state so it may take some time.

## <mark style="background-color:green;">Forced Exit State</mark>

Forced exit is an optional pool contract feature for emergency withdraw of user funds if the relayer is unavailable.

```typescript
enum ForcedExitState {
  NotStarted,
  CommittedWaitingSlot,
  CommittedReady,
  Completed,
  Outdated,
}
```

where:

* `NotStarted` - the regular account state: forced exit was not initiated
* `CommittedWaitingSlot` - forced exit was committed (the first stage) but the exit window isn't opened yet (and you cannot send the execute transaction)
* `CommittedReady` - the first stage (commit) was performed and exit window is available, so you are able to execute your committed forced exit now
* `Completed` - the forced exit was executed and the account was destroyed
* `Outdated` - forced exit was committed but the exit window has passed. You cannot execute a forced exit but you can cancel it and create a new one.

## <mark style="background-color:green;">Committed Forced Exit</mark>

The committed forced exit retrieved from the pool contract

```typescript
interface CommittedForcedExit {
  nullifier: bigint;
  to: string;
  operator: string;
  amount: bigint;
  exitStart: number;
  exitEnd: number;
  txHash: string;
}
```

where:

* `nullifier` - the last account nullifier which was marked for forced exit
* `to` - an address to withdraw funds
* `operator` - address who allowed to execute forced exit (no execution limitations in case of operator equals zero address)
* `amount` - value to withdraw (in pool dimension)
* `exitStart` - timestamp when exit window opened (in seconds)
* `exitEnd` - timestamp when exit window closed (in seconds)
* `txHash` - commit transaction hash

## <mark style="background-color:green;">Finalized Forced Exit</mark>

The executed or cancelled forced exit retrieved from the pool contract

```typescript
interface FinalizedForcedExit {
  nullifier: bigint;
  to: string;
  amount: bigint;
  cancelled: boolean;
  txHash: string;
}
```

where:

* `nullifier` - the last account nullifier associated with the forced exit
* `to` - an address to withdraw funds
* `amount` - value to withdraw (in pool dimension)
* `cancelled` - false for successful forced exit, true for canceled one
* `txHash` - execute transaction hash

## <mark style="background-color:green;">Transaction to be Send</mark>

The following interface describes the transaction request which should be sent by the superior user or application. It can be approve or direct deposit transaction. For example:

```typescript
interface PreparedTransaction {
    to: string;
    amount: bigint;
    data: string;
    selector?: string;
}
```

where:

* `to` - transaction destination address
* `amount` - amount of native coins to be sent with transaction
* `data` - prepared raw transaction data (depends on underlying blockchain)
* `selector` - an optional field which can be used on some chains (e.g. Tron) where selector is separated from transaction data (for EVM networks selector is included in `data` field so that field remains `undefined`)
