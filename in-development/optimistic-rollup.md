# Multi-chain Custom Rollup Deployment

zkBob v2 will support a multi-chain deposit/withdrawal environment. Users will be able to initiate a private deposit and receive a withdrawal from their choice of supported chains.&#x20;

Once initiated, shielded transactions will be relayed and deposited into a single consolidated zkpool deployment on an EVM chain of record. Rather than small pools with small anonymity sets deployed to each chain, a single pool fed by multiple cross-chain deposits will vastly increase anonymity for all users and provide the opportunity for faster anonymous withdrawals.

v2 will be deployed within a custom optimistic rollup-based framework. Rollups will be based on Optimism with customizations to support multi-chain assets and hybrid-chain deployment.

### Features

* Deposit contracts deployed to custom rollups on multiple EVM networks.&#x20;
* Pool & Verifier contracts deployed on a single chain to optimize gas usage and consolidate resources into a single zkpool.
  * Gnosis Chain is an ideal candidate as fees are paid with a stable token and the gas market is regulated via EIP-1559.
* zkBob contracts will be deployed on rollups as precompiles to increase tx/sec.
* Fast exits enabled via state-channel bridges.
  * Bridged stable assets can also be leveraged in compounding protocols to earn additional yield.
* Potential whitelisting capabilities.
