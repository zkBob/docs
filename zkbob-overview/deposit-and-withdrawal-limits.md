# Deposit & Withdrawal Limits

Limits are imposed to protect against large deposits which may result from illegal activity (for example a hack where attackers need to quickly move a large amount of funds). By default, new users are limited in the amount they can deposit and withdraw. Established users or businesses with inherent KYC can access higher limits through [tiered limits](deposit-and-withdrawal-limits.md#undefined).

### Default Limits

**Deposits**

1. A single deposit cannot exceed 10,000 BOB.
2. A single address cannot deposit more than 10,000 BOB during a single 24 hour period.
3. All deposits from all addresses (see tiers below for more info) cannot exceed 300,000 BOB during a single 24 hour period.
4. The overall size of a pool cannot exceed 1,000,000 BOB.

**Withdrawals**

1. All withdrawals from all addresses cannot exceed 100,000 BOB during a single 24 hour period.

**Transfers**

1. Transfers amongst users in the pool are unlimited. The minimum transfer amount is $0.05 BOB. All transfers incur a $0.10 BOB fee.

{% hint style="info" %}
The $10,000 default deposit limit is an established reporting standard relevant to travel, banking, and other industries.
{% endhint %}

### Tiered Limits

Up to 255 limits can be set for established users and users meeting sufficient off-chain KYC requirements. These limits are configurable based on user and project needs (for projects with high payrolls for example).&#x20;

Tiers increase deposit limits for individual accounts, but do not impact the overall pool size.

### Tier example

\-> **Tier 0** (default tier) allows the following:

* A single deposit cannot exceed 10,000 BOB.
* A single address cannot deposit more than 10,000 BOB during a single 24 hour period.

\-> **Tier 1** increases the deposit limits for an individual account:

1. A single deposit cannot exceed 100,000 BOB.
2. A single address cannot deposit more than 100,000 BOB during a single 24 hour period.

\-> **Both tiers** adhere to the following limits:

* **All deposits from all addresses** cannot exceed **300,000 BOB** during a single 24 hour period.
* The overall size of a pool cannot exceed 1,000,000 BOB.

This means that if someone in Tier 1 deposits 300,000 BOB, no additional deposits can be made (Tier 0 or Tier 1 participants) during that same 24 hour period. This is because the **all deposits from all addresses** **criteria of 300,000 BOB** has been met.

Deposits can resume the following day.&#x20;



