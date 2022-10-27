# On the Roadmap

zkBob is a beta application with many developments in process. There are planned improvements as well as exploratory features based on how projects are using zkBob.

To submit a feature request: zkbob@proton.me

## Upcoming Items

These items are ongoing or planned for near-term execution.

* Multi-chain expansion: BOB stablecoin will be minted on additional chains. This has already occurred with Polygon, Optimism and Ethereum. The next likely candidates are additional L2s on Ethereum.
* Salary use case development: zkBob is already in use by projects looking to pay employees and contractors privately with a stablecoin while taking advantage of inherited KYC (employees and employers already know each other). Additional projects will be onboarded to the platform to expand and promote this use case.
* DeFi use case development. [BOB](../bob-stablecoin/bob-details.md) is a novel stablecoin and new use cases such as lending, an expanded collateralization model, compounded interest distributions, and other ideas will be explored within a multi-chain context.
* Governance and decentralization: zkBob is an open-source platform still in beta. Additional measures will be taken to decentralize the workflow and engage the community in making future decisions about platform directions. This is also true for the BOB stablecoin where community members will ultimately make decisions about usage, supply etc. though a tbd governance process. &#x20;
* Hackathon participation: The community should be engaged with BOB and zkBob to explore and develop new use cases where privacy and stability are preferred.

## Application Improvements

We will continue improving the speed, usability, and efficiency of the application. Items on the roadmap include:

* Research a PLONK implementation to replace the current Groth'16 zkSNARK. PLONK can reduce proof computation size and creation/execution time. [More on PLONK](https://vitalik.ca/general/2019/09/22/plonk.html).
* Mnemonic account import/export. This will increase usability and transportability of accounts.
* UTXO withdrawal details. Multiple UTXOs may need to be processed during a withdrawal. Updates will provide users with more details about withdrawals which can incur higher fees (ie a multi-UTXO withdrawal with 5 individual txs will include a fee of $0.50 rather than $0.10).
* Multi-sender functionality. Ability to add multiple transfer addresses (input or from a csv file) and send in batches.&#x20;
* Error reporting enhancements: When a transaction reverts there is currently not enough information for the user. Errors should be clearly displayed for debugging purposes.

## Compliance Improvements

We will continue to implement best practices in regards to regulation and compliance. This ensures regular users can maintain privacy for ordinary transactions while bad actors are discouraged from using zkBob. Areas of work and research include:

* Large transaction transparency: Future versions may increase overall deposit, withdrawal, and pool limits, however deposits and withdrawals that exceed the 10K soft limit may be subject to "on-demand" reveals. This means 3rd parties (regulators, paid service) can request access to specific transactions and those details will be provided if the criteria are met. _Note this will not be possible for transactions under the soft limit._
* KYC for large-tx/power users:  We are researching ways to combine on-chain reputation and off-chain KYC to assign non-transferable NFTs to users who pass checks. These users can then access additional features in the application such as increased limits and incentives.
* TRM integration: Screen deposit/withdrawal addresses for AML and sanctions compliance.&#x20;

## Exploratory Features

See [this page for additional items](exploratory-features/) in research and development.

To submit a feature request: zkbob@proton.me
