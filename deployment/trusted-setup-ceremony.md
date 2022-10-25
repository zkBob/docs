---
description: Initial mandatory procedure to bootstrap the application
---

# Trusted Setup Ceremony

<figure><img src="../.gitbook/assets/2_Deployment Overview.jpg" alt=""><figcaption></figcaption></figure>

zkBob uses zkSNARKs to provide transaction correctness proofs for participants. No one can ascertain transaction details but anyone can verify proof that a transaction occurred.&#x20;

To start, the zkSNARK scheme requires parameter and verification scheme generation for each circuit. However, this process produces "toxic waste" which should not be disclosed to anyone.

A proven approach to get the public parameters and verification keys for circuits is to involve a group of people in the Multi-Party Computation (MPC) process. As long as a single participant in this scheme is honest, the process is considered secure.&#x20;

The verification keys are in fact a collection of encrypted parameters such as secret coefficients and a point where the polynomials are evaluated and checked during proof generation and verification.&#x20;

Some of these parameters (so called powers of tau) do not actually depend on the circuit itself and can be reused between different circuits or even completely different projects. Since this scheme has a "one of many" security threshold, using an external input already tested in different protocols is a good idea.

This process is known as a Trusted Setup Ceremony and it was formalized in the following paper: [Scalable Multi-party Computation for zk-SNARK Parameters in the Random Beacon Model](https://eprint.iacr.org/2017/1050).

The [Perpetual Powers of Tau Community Process](https://github.com/weijiekoh/perpetualpowersoftau) can be used as a starting point. However, to provide increased security, anyone with an internet connection can also participate in the community phase of the ceremony, during which additional circuit specific parameters are created and mingled together amongst different parties.

The final parameters are then hardcoded into the verifying smart contracts and deployed to all chains. The corresponding proving keys are stored inside the web application and relayer and the application is ready to go!

## zkBob Trusted Ceremony Process

zkBob launch is a multi-phase process initiated by the team and completed by the community. Phases 1 & 2 have already been accomplished to launch the MVP product.&#x20;

Phase 3 will involved the greater community to provide additional entropy, decentralization, and safety as only a single participant must be honest to ensure a secure application.

### :white\_check\_mark: Phase 1:  Generate Proving and Verification Keys

An existing pre-generated set of parameters [https://github.com/weijiekoh/perpetualpowersoftau/](https://github.com/weijiekoh/perpetualpowersoftau/) along with an additional secret input is used to generate proving and verification keys. To produce this, the contributing group:

1. Downloads latest phase 1 contribution from Perpetual powers of tau: [https://ppot.blob.core.windows.net/public/response\_0071\_edward](https://ppot.blob.core.windows.net/public/response\_0071\_edward)
2. Adds additional entropy in the form of a future block hash
3. Runs compute constrained with entropy.

### :white\_check\_mark: Phase 2:  Create Circuit Parameters and MVP Launch

Processes use a dedicated [circuit library](https://docs.rs/phase2/latest/phase2/) to create the transfer verifier and tree update verifier circuits. High-level steps below describe the processes completed by the coordinator. Step 3 involves an independent & distributed group of contributors to create additional entropy.

1. Generate radix files by providing the last response from phase 1 to the circuit library. This process can take several hours and requires RAM 2x the size of the response file.
2. Multi-Party Computation (MPC) parameter generation:  Generate circuit parameters and additional metadata required for ceremony coordination.
3. MPC contributions to add additional forms of entropy. Each contributor shares the output of this step with the coordinator.
4. Export fawkes-compatible parameters.
5. Test in the [libzeropool](https://github.com/zkBob/libzeropool) repo.
6. Get verification key for each circuit (transfer and tree).
7. Generate verification contracts (`transfer_verifier.sol` and `tree_update_verifier.sol`) using the [libzeropool ](https://github.com/zkBob/libzeropool)repo.
8. Launch application.
   1. Deploy verification contracts and zkBOB contract.
   2. Copy params files (\*.bin and JSONs) to the relayer’s system.
   3. Deploy UI.

### Phase 3: Community Participation

To facilitate wide community participation, a dedicated web application will coordinate the trusted setup. Steps to produce final parameters:.

1. Community members access the web application dedicated to the ceremony. The web application consists of:
   1. Single Page Application (SPA) with embedded wasm code for contribution.
   2. A database to store contribution history.
   3. An external storage for contributions.
2. A user may choose to authenticate using different credentials such as twitter, github, metamask etc or stay anonymous.
3. Contributors:
   1. Download latest parameters from storage.&#x20;
   2. Provide entropy as a random string.
4. The SPA calls the wasm code ( phase2/ contribute ) to apply provided entropy to the parameters.
5. The result is verified and saved when successful.
6. The user is provided with a hash of the contribution which can be used to verify against the intermediate contributions and the final result, proving that any particular contribution was indeed included in the final result.
7. A new verifier contract is generated using the final result.

## Ceremony Inputs and Outputs

**The Ceremony input:**

* Powers of tau files
* Transfer and tree circuit written with the bellman library
* Random contributions from community members

**The Ceremony output:**

* MPC results (contribution hashes, contributions, collection of intermediate results)
* Transfer verifier circuit parameters (tx\_params.bin)
* Transfer verifier circuit verification key (tx\_vk.json)
* Transfer verification contract (transfer\_verifier.sol)
* Tree verifier circuit parameters (tree\_params.bin)
* Tree verifier circuit verification key (tree\_vk.json)
* Tree verifier contract (tree\_update\_verifier.sol)
