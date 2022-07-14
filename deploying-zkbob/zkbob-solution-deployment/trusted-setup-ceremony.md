---
description: Initial mandatory procedure
---

# Trusted Setup Ceremony

zkBob uses zkSNARKs to provide transaction correctness proofs for participants. No one can ascertain transaction details but anyone can verify proof that a transaction occurred. To start, the zkSNARK scheme requires parameter and verification scheme generation for each circuit. However, this process produces "toxic waste" which should not be disclosed to anyone.

The most popular approach to get the public parameters and verification keys for the circuit is to involve a group of people in the Multi-Party Computation (MPC) process. At least a single participant in this scheme should be honest to ensure the safety of the entire process. This process is known as a Trusted Setup Ceremony and it was formalized in the following paper: [Scalable Multi-party Computation for zk-SNARK Parameters in the Random Beacon Model](https://eprint.iacr.org/2017/1050)

The aforementioned keys are in fact a collection of encrypted parameters such as secret coefficients and a point in which the polynoms are evaluated and checked during proof generation and verification correspondingly. Some of those parameters (so called powers of tau ) do not actually depend on the circuit itself and could be reused between diferent circuits or even completely different projects. Furthermore since the this scheme has a "one of many" security threshold, using an external input that was already tested in diffrerent protocols seems like a good idea. 

Fortunately for us there is a [Perpetual Powers of Tau Community Process](https://github.com/weijiekoh/perpetualpowersoftau) which can be used as a starting point. However for the sake of event better security we're providing a way for literally anyone to participate in the second phase of the ceremony, during which some more circuit specific parameters are created and mingled together between different parties 

After all of the hassle above the final parameters are hardcoded into the verifying smart contracts and deployed to all the chains. The corresponding proving keys are stored inside the web application and the relayer and we're ready to go! 

**The Ceremony input:**&#x20;

* Transfer and tree circuit written with the bellman library.

**The Ceremony output:**

* Transfer verifier circuit parameters (tx\_params.bin)
* Transfer verifier circuit verification key (tx\_vk.json)
* Tree verifier circuit parameters (tree\_params.bin)
* Tree verifier circuit verification key (tree\_vk.json)



