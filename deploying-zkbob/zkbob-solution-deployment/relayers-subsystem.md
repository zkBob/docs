---
description: Deployment scheme
---

# Relayers Subsystem

{% hint style="info" %}
zkBob solution currently supports single relayer configuration only. If you deploy your own relayer it won't be able to interact with the pool contract due to operator manager contract's restriction. We are work hard on the relayers subsystem scalability. So this page is just a development notes at this moment
{% endhint %}

Deploy at least one relayer to finalize the deployment process. This requires a full-time available server with a fast connection.

1\) First prepare the relayer environment. Use any linux-based operating system with Node.js and Rust implementation installed. Get the [latest codebase from our repository ](https://github.com/zkBob/zeropool-relayer)and download all dependencies.

```
git clone https://github.com/zkBob/zeropool-relayer
cd zeropool-relayer
git submodule update --init
git submodule update --recursive --remote
yarn install --frozen-lockfile
```

2\) Build the main library.

```
cd libzeropool-rs/libzeropool-rs-node
npm install
cd ../../
```

3\) Copy the circuit parameters and transfer the verification key.

```
cp <path_to_tree_params.bin> ./zp-relayer/params/tree_params.bin
cp <path_to_tx_params.bin> ./zp-relayer/params/transfer_params.bin
cp <path_to_tx_vk.json> ./transfer_verification_key.json
```

4\) Build the relayer.

```
yarn build:memo
yarn build:relayer
```

5\) Create `.env` file and populate it with the actual parameters.

```
cd zp-relayer
cp .env.example .env
nano .env
```

6\) Run the relayer.

```
yarn workspace zp-relayer run start:prod
```
