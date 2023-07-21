# Configuration

There are two configuration points: [client](initializing-the-client/client-configuration.md) and [account](attaching-a-user-account/account-configuration.md)

The **client** configuration is applied during library initialization (`ZkBobClient` instantiation). It's a base level config. The client interacts with concrete private pools, designated relayers and RPCs, and other common properties.

The **account** configuration is applied to the `ZkBobClient` when we want to interact with customer's funds. Account configuration defines a customer wallet inside a privacy pool.
