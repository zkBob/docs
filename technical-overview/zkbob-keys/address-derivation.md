---
description: Private payment address
---

# Address derivation

The zkBob's account doesn't contain any fixed address. Instead if you want to receive funds you should generate and provide one of private addresses. In general new private address can be generated for every incoming transaction. Nobody can link different private addresses derived from the single account to each other or to this account. Only the account owner can confirm that a private address belong to him.

In order to generate a new private payment address you should perform the following steps:

* Generate a random 80-bit diversifier $$d$$
* Calculate diversifier subgroup generator point: $$G_d = \text{ToSubGroupHash}_{E(F_r)}(d)$$
* Derive diversifier public part: $$P_d=\eta G_d$$​
* Prepare address data buffer ($$buf$$, 42 bytes): join 10 byte of the diversifier with 32 bytes of the $$P_d.x$$
* Get address checksum: $$checksum = keccak256(buf)$$
* Attach $$checksum$$ first 4 bytes to the $$buf$$
* Encode $$buf$$ with Base58 to the string

Thus the address string contains diversifier public key $$(d, P_d)$$ protected with checksum to avoid typos. Checking any private addresses for ownership is very straightforward . You should decode address string and extract $$d$$ and $$P_d$$ values. Next you derive $$P'_d$$​ with the your $$\eta$$ key. The private address belongs to your account only if $$P'_d = P_d$$.

### Address derivation example

Let's imagine you have an account with the intermediate key:

$$\eta = \mathrm{0x2dedcb9b32000d350bf1055d764302b9d4f4a3820015ea49aaf02438aaa72a85}$$​

{% hint style="info" %}
**The big numbers representation**

All big numbers on this page are presented in the hexadecimal form to reduce lines width. If you want to convert them to the decimal form please use one of third-party tools ([example](https://www.rapidtables.com/convert/number/hex-to-decimal.html))
{% endhint %}

To derive a private address we should generate a random diversifier $$d$$ and calculate the [Poseidon](../the-poseidon-hash.md) hash for it:

$$d = \mathrm{0xc2767ac851b6b1e19eda}$$

$$Hash(d) = \mathrm{0x998ed1a2c59ea1ac23ea4519bd11e88cefe5c888d22bf245b8c22923b4b5488}$$​

Convert scalar $$Hash(d)$$ to the subgroup generator point:

$$G_d = \{\\x = \mathrm{0x2f6f6ef223959602c05afd2b73ea8952fe0a10ad19ed665b3ee5a0b0b9e4e3ef}, \\ y = \mathrm{0x2e23e2751abbb64461e9a852b7b20c8337fc279ed748c77dfa23cf6158f6a6c3}\}$$​

Put $$d$$ and $$G_d.x$$ into the buffer as little-endian numbers (start with the last significant byte):

$$
\mathrm{da\ 9e\ e1\ b1\ b6\ 51\ c8\ 7a\ 76\ c2\ ef\ e3\ e4\ b9\ b0\ a0\ } \\ \mathrm{e5\ 3e\ 5b\ 66\ ed\ 19\ ad\ 10\ 0a\ fe\ 52\ 89\ ea\ 73\ 2b\ fd\ } \\ \mathrm{5a\ c0\ 02\ 96\ 95\ 23\ f2\ 6e\ 6f\ 2f}
$$

Then we should add a checksum. To do it we must compute keccak256 hash from the buffer above:

$$\mathrm{f4\ e1\ d3\ a9\ 45\ a0\ c6\ 4a\ 2c\ 8c\ 60\ a6\ 4b\ ad\ 38\ 04\ 0f\ 3f\ 75\ 24\ 30\ 79\ 7c\ 30\ d1\ 41\ 91\ a8\ 0a\ b5\ 4a\ be\ }$$​

Get the first 4 bytes from the hash above and append them to the end of buffer:

$$
\mathrm{da\ 9e\ e1\ b1\ b6\ 51\ c8\ 7a\ 76\ c2\ ef\ e3\ e4\ b9\ b0\ a0\ } \\ \mathrm{e5\ 3e\ 5b\ 66\ ed\ 19\ ad\ 10\ 0a\ fe\ 52\ 89\ ea\ 73\ 2b\ fd\ } \\ \mathrm{5a\ c0\ 02\ 96\ 95\ 23\ f2\ 6e\ 6f\ 2f\ f4\ e1\ d3\ a9}
$$

Finally encode this buffer with the Base58 to get private address:

_**QsnTijXekjRm9hKcq5kLNPsa6P4HtMRrc3RxVx3jsLHeo2AiysYxVJP86mriHfN**_