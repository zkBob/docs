# On the Roadmap

zkBob is a beta application with many developments in process. There are planned improvements as well as exploratory features based on how projects are using zkBob.

To submit a feature request: zkbob@proton.me

## Upcoming Items

These items are ongoing or planned for near-term execution.

* ✅ **Multi-chain expansion**: BOB stablecoin will be minted on additional chains. This has already occurred with Polygon, Optimism, BNB Chain, and Ethereum. The latest deployment was recently on Arbitrum.
* **Salary use case development**: zkBob is already in use by projects looking to pay employees and contractors privately with a stablecoin while taking advantage of inherited KYC (employees and employers already know each other). Additional projects will be onboarded to the platform to expand and promote this use case.
* **DeFi use case development**. [BOB](../bob-stablecoin/bob-details.md) is a novel stablecoin and new use cases such as lending, an expanded collateralization model, compounded interest distributions, and other ideas will be explored within a multi-chain context.
* **CDP platform for the BOB stablecoin**. This platform will allow Uniswap V3 LPs to use their positions to mint and borrow BOB.
* **Governance and decentralization**: BOB protocol is an open-source platform still in beta. Additional measures will be taken to decentralize the workflow and engage the community in making future decisions about platform directions. This is also true for the BOB stablecoin where community members will ultimately make decisions about usage, supply etc. though a tbd governance process. &#x20;
* **✅ Hackathon and conference participation**: The community should be engaged with BOB and zkBob to explore and develop new use cases where privacy and stability are preferred. Recent conferences include
  * [EthDenver](https://mirror.xyz/0x6132eB883e88CD4E007552b871A6444Bfc34E837/-9Lm-1FxedYajuvSS4NUZmudksrC3bOzS8JKEK8J1tc)
  * [EthDubai](https://mirror.xyz/0x6132eB883e88CD4E007552b871A6444Bfc34E837/s5hOPQs-n3Q-Tb4brkhoWRNhy3uo4ufwjC-5k1CwTLs)
* **AML improvements**: Account verification and tiered limits will be refined to keep the protocol secure and policy compliant.
  * Restructure max transaction and monthly limits for basic tier accounts.
  * ✅ Verified accounts with KYC-based NFTs and higher deposit limits. [Optional KYC is now implemented](../zkbob-app/optional-kyc.md) with the Opium Know your Cat protocol.
  * Verify corporate accounts on a case-by-case basis.
* **Wallet screening**: VAF Compliance and PureFI integrations will bolster TRM integration to provide additional protections by screening deposit/withdrawal addresses for AML and sanctions compliance.&#x20;

## Application Improvements

We will continue improving the speed, usability, and efficiency of the application. Items on the roadmap include:

* Mnemonic account import/export. This will increase usability and transportability of accounts.
* UTXO withdrawal details. Multiple UTXOs may need to be processed during a withdrawal. Updates will provide users with more details about withdrawals which can incur higher fees (ie a multi-UTXO withdrawal with 5 individual txs will include a fee of $0.50 rather than $0.10).
* ✅  Multi-sender functionality. Ability to add multiple transfer addresses (input or from a csv file) and send in batches.
* Error reporting enhancements. When a transaction reverts there is currently not enough information for the user. Errors should be clearly displayed for debugging purposes.&#x20;
* Research a PLONK implementation to replace the current Groth'16 zkSNARK. PLONK can reduce proof computation size and creation/execution time. [More on PLONK](https://vitalik.ca/general/2019/09/22/plonk.html).
* Post-beta. Following beta protocol updates will include:
  * Open-source UI
  * Decentralized relayer infrastructure
  * Community ceremony

## Exploratory Features

See [this page for additional items](exploratory-features/) in research and development.

To submit a feature request: zkbob@proton.me
