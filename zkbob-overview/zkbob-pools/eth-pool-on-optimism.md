---
description: The first zkBob ETH pool is deployed on Optimism
---

# ETH Pool on Optimism

To access, select Optimism in the Network dropdown and choose the ETH pool.

<figure><img src="../../.gitbook/assets/network-dropdown-1.png" alt=""><figcaption></figcaption></figure>

You can deposit ETH or WETH into the pool. ETH deposits use the [direct deposit](../../zkbob-app/zkbob-direct-deposits.md) functionality, and can take longer to process. WETH deposits use the standard deposit functionality with proofs constructed locally on your machine.

Note your connected external 0x account will show your total ETH + WETH balance.&#x20;

<figure><img src="../../.gitbook/assets/combined.png" alt=""><figcaption></figcaption></figure>

When depositing, select ETH or WETH from the token dropdown menu. The amount available to deposit will not be combined, you can only deposit your available ETH or WETH with the transaction.

<figure><img src="../../.gitbook/assets/to-eth.png" alt=""><figcaption></figcaption></figure>

Once deposited, WETH and ETH both become ETH in the zkAccount.

On withdrawal, select a wallet to receive the ETH from your zkAccount. All withdrawals are processed as ETH, not WETH.

## FAQ

<details>

<summary>Why can a regular ETH transaction take up to 10 minutes?</summary>

\=ETH deposits use the direct deposit functionality, where proofs are constructed remotely. This decreases the gas costs for the relayer, but can result in additional time for the transaction to process.&#x20;

</details>



\-> What are the deposit and withdrawal limits?

\-> Can I use KYC to increase my limits?

\-> Why are fees different for WETH or ETH deposits?

\->&#x20;





