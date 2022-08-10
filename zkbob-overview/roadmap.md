# Roadmap

{% hint style="info" %}
In process. Date estimates and additional items will be added as implementation details are clarified.
{% endhint %}

## V1

* :white\_check\_mark: Testing application (CLI and UI) deployed to Kovan
* :white\_check\_mark: Parallel transaction processing through relayers
* :white\_check\_mark: UI improvements (ongoing)
* Automated retry for failed txs.
* Eliminate password requirement for MetaMask zkaccount generation and usage.
* Bob token creation
* Uniswap v3 instance for liquidity
* Stable optimistic rollup deployment
* MVP zkBob production application

## V2

* XP token exploration. The energy token may be leverage in future iterations to reward users or for additional tbd purposes.
* Explore secure multi-chain functionality. A single zkpool will reside on a chain of record with withdrawals/deposits flowing through this pool. Transactions can be initiated from the originating chain, flow to the zkpool on the chain of record, then withdrawn to a destination chain of choice.
* Multi-relayers to improve speed and storage capabilities. Mechanisms are in development for determining relayer order and responsibilities to prevent any possible conflicts.&#x20;
* In-app zkBob private messaging
