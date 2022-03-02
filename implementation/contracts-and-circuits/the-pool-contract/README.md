---
description: Main transaction processor
---

# The Pool Contract

The main purpose of the Pool contract is to process user transactions. It receives transactions from the operators (relayers) or users directly, checks the proofs and updates the current contract state.

### The Pool Initialization

Every pool serves a single token. To support multi-pool solutions every pool has own identifier (`pool_id`). Currently pool\_id is an unsigned 24-bit arbitrary integer.

You should provide all of the linked contracts (verifiers, operator manager, token and voucher token) before the Pool deployment. The Pool contract initialized by the following constructor method:

```solidity
constructor(
        uint256 __pool_id,
        IERC20 _token,
        IMintable _voucher_token,
        uint256 _denominator,
        uint256 _energy_denominator,
        uint256 _native_denominator, 
        ITransferVerifier _transfer_verifier,
        ITreeVerifier _tree_verifier,
        IOperatorManager _operatorManager,
        uint256 _first_root);
```

The are three denominators used in the Pool which are applied to the token (`denominator`_), energy (_`_energy_denominator`) and native coin (`_native_demominator`) amount in related actions. E.g. when user wants to withdraw 5 tokens from the pool, he specify in the corresponding transaction field value '5'. The pool will multiply this value by the token denominator and send resulting tokens value to the receiver address (in wei).

You also should to provide initial Merkle tree root value through the `_first_root` parameter. For the Merkle tree with a desired total height 48 without any leaves (all leaves are zero) the root is a fixed value:

```
11469701942666298368112882412133877458305516134926649826543144744382391691533
```

### Making a transaction

The Pool contract process incoming transactions via the `transact()` method. All required data for the transaction passed through the calldata.

```solidity
function transact() external payable onlyOperator;
```

Before the transaction is processed the proofs are checking by the verifier contracts.

Please pay attention to the `onlyOperator` modifier. It will check transaction sender address (`tx.origin` field) via the Operator Manager and revert transaction when the origin sender doesn't allowed to interact with the Pool contract currently.



### Source and Deployment data

The contract source code: [Pool.sol](https://github.com/zkBob/pool-evm-single-l1/blob/main/contracts/Pool.sol)

Mainnet contract address:&#x20;

Mainnet contract proxy:&#x20;

Testnet contract address: [0x78E276E79d026BDE5FD37df1c04554Ca9C993Ab4](https://kovan.etherscan.io/address/0x78E276E79d026BDE5FD37df1c04554Ca9C993Ab4)

Testnet contract proxy: [0x3453A3FB52cE634d994fB498447C92D78AbBE49f](https://kovan.etherscan.io/address/0x3453A3FB52cE634d994fB498447C92D78AbBE49f)



