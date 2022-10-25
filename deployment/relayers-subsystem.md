---
description: Deployment scheme
---

# Relayer Subsystem

A zkBob solution currently supports a single relayer. The relayers subsystem will be scaled in the future to support multiple relayers.

{% hint style="success" %}
Relayer setup and configuration details are available here: [https://github.com/zkBob/relayer-launch#readme](https://github.com/zkBob/relayer-launch#readme)
{% endhint %}

A relayer requires the following specs:

* Persistent Linux machine with docker installed
* Accessible from the public internet via a fixed IP address.&#x20;
* Hardware minimum requirements:  4 CPU, 8 GB RAM, 100 GB SSD.

{% hint style="info" %}
We will update details when multiple relayers are introduced. For now, if you deploy your own relayer it will not be able to interact with the pool contract due to restrictions with the operator manager contract.&#x20;
{% endhint %}



