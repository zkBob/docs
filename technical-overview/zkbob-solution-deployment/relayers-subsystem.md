---
description: Deployment scheme
---

# Relayers Subsystem

You should deploy at least one relayer to finalize solution deployment process. It's supposed you has a full-time available server with a fast connection link before you start.

First of all you should prepare the relayer environment. Please use any linux-based operating system with Node.js and Rust implementation installed. Get the latest codebase from our repository and download all dependencies.

```
git clone https://github.com/zkBob/zeropool-relayer
cd zeropool-relayer
git submodule update --init
git submodule update --recursive --remote
yarn install --frozen-lockfile
```

Build the main library

```
cd libzeropool-rs/libzeropool-rs-node
npm install
cd ../../
```

Copy the circuit parameters and transfer verification key

```
cp <path_to_tree_params.bin> ./zp-relayer/params/tree_params.bin
cp <path_to_tx_params.bin> ./zp-relayer/params/transfer_params.bin
cp <path_to_tx_vk.json> ./transfer_verification_key.json
```

Build the relayer

```
yarn build:memo
yarn build:relayer
```

Create `.env` file and populate it with the actual parameters

```
cd zp-relayer
cp .env.example .env
nano .env
```

Run the relayer

```
yarn workspace zp-relayer run start:prod
```
