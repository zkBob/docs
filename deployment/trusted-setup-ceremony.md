---
description: Initial mandatory procedure to bootstrap the application
---

# Trusted Setup Ceremony

zkBob uses zkSNARKs to provide transaction correctness proofs for participants. No one can ascertain transaction details but anyone can verify proof that a transaction occurred.&#x20;

To start, the zkSNARK scheme requires parameter and verification scheme generation for each circuit. However, this process produces "toxic waste" which should not be disclosed to anyone.

The most popular approach to get the public parameters and verification keys for the circuit is to involve a group of people in the Multi-Party Computation (MPC) process. At least a single participant in this scheme should be honest to ensure the safety of the entire process. This process is known as a Trusted Setup Ceremony and it was formalized in the following paper: [Scalable Multi-party Computation for zk-SNARK Parameters in the Random Beacon Model](https://eprint.iacr.org/2017/1050).

The aforementioned keys are in fact a collection of encrypted parameters such as secret coefficients and a point in which the polynomials are evaluated and checked during proof generation and verification. Some of those parameters (so called powers of tau) do not actually depend on the circuit itself and could be reused between different circuits or even completely different projects. Furthermore since this scheme has a "one of many" security threshold, and using an external input already tested in different protocols is a good idea.

The [Perpetual Powers of Tau Community Process](https://github.com/weijiekoh/perpetualpowersoftau) can be used as a starting point. However, to provide increased security we provide a way for anyone with an internet connection to participate in the second phase of the ceremony, during which some more circuit specific parameters are created and mingled together amongst different parties.

The final parameters are then hardcoded into the verifying smart contracts and deployed to all chains. The corresponding proving keys are stored inside the web application and relayer and we're ready to go!

## Contribution guide and implementation details

There is a dedicated web application to coordinate trusted setup. Steps to produce final parameters:

1. Initial parameters (Powers of tau) are uploaded to the application and the first contribution for a circuit of interest is made by the core team (not quite safe so far!).
2. A community member accesses the web application dedicated to the ceremony. The web application consists of:
   1. Single Page Application (SPA) with embedded wasm code for contribution.
   2. A database to store contribution history.
   3. An external storage for contributions.
3. The user may choose to authenticate using different credentials such as twitter, github, metamask etc or stay anonymous.
4. When the user chooses to contribute they perform the following:
   1. Download latest parameters from storage.&#x20;
   2. Provide entropy as a random string.
5. The SPA calls the wasm code ( phase2/ contribute ) to apply provided entropy to the parameters.
6. The result is verified and saved in case of successful verification
7. The user is provided with a hash of contribution which can be used to verify against the final result, proving that a particular contribution was indeed included in the final result.

**The Ceremony input:**

* Transfer and tree circuit written with the bellman library
* Powers of tau files
* Random contributions from community members

**The Ceremony output:**

* MPC results (contribution hashes, contributions, collection of intermediate results)
* Transfer verifier circuit parameters (tx\_params.bin)
* Transfer verifier circuit verification key (tx\_vk.json)
* Tree verifier circuit parameters (tree\_params.bin)
* Tree verifier circuit verification key (tree\_vk.json)
