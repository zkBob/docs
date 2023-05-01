# GP 12: Raise Polygon limits

{% hint style="success" %}
The proposal was confirmed and executed.&#x20;

* Polygon Safe [Transaction 29](https://app.safe.global/transactions/tx?safe=matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x741bc135755be4a08ae7a2081e6444c419066da63630ee2a7d2825372dbd3596)
* Polygon tx:\
  [https://polygonscan.com/tx/0x22fe28fab4ed42e17f3d4d5c2ae5e48a854b58a81e24d01e7f219f03b4524e19](https://polygonscan.com/tx/0x22fe28fab4ed42e17f3d4d5c2ae5e48a854b58a81e24d01e7f219f03b4524e19)
{% endhint %}

## Proposal objective

zkBob pool usage on Polygon has increased and daily limits have been reached several times. To support growth, this proposal raises the overall pool size and the daily withdrawal limits on Polygon.&#x20;

## Proposal details

Limits should be raised for the 3 current usage tiers on zkBob. See [Deposit & Withdrawal limits](../../../zkbob-overview/deposit-and-withdrawal-limits.md) for more info on usage tiers.

* **Daily withdrawal limit**: Raised from 100,000 BOB per day to 300,000 BOB per day.
* **Overall pool size**: Raised from 1,000,000 BOB to 2,000,000 BOB.

## Proposal breakdown

Transaction [#29](https://app.safe.global/transactions/tx?safe=matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x741bc135755be4a08ae7a2081e6444c419066da63630ee2a7d2825372dbd3596) in the Polygon Safe contains 3 actions:

**Action 1: Tier 1**

Set limits for tier id `0`

**Action 2: Tier 2**

Set limits for tier id `254`

**Action 3: Tier 3**

Set limits for tier id `1`

### Additional verification

Check transaction logs using Tenderly.





