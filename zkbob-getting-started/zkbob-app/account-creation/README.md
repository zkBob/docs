# Account Creation

There are 2 ways to create a zkBob shielded account.&#x20;

1. ****[**Use a seed phrase**](./#seed-phrase). The application generates a seed phrase for you to store securely. You can use this seed phrase to restore your account as needed from any computer.
2. ****[**Use a web3 wallet**](./#web3-wallet) **(MetMask/WalletConnect)**. The application collects a signature locally on your browser - not on the blockchain. It uses the private key from your web3 wallet to derive a secure zkBob account address.

## Seed Phrase

1\) Press the **zkAccount** button on the home screen.

![](../../../.gitbook/assets/zkbob-acct.png)

2\) Select **Create from seed phrase** in the popup box.

![](../../../.gitbook/assets/seed-phrase-1.png)

3\) View and write down your phrase somewhere safe (offline). It is not recommended to use the copy feature or to keep your seed phrase on the computer.&#x20;

![](../../../.gitbook/assets/seed-2.png)

4\) Re-enter your phrase by clicking on the words in order. Click Verify when you are done.

![](../../../.gitbook/assets/confirm-seed.png)

5\) Create and confirm a password to use for accessing your account. You will enter this password each time the page refreshes and to access your account.

![](../../../.gitbook/assets/zkbob-password.png)

5\) Your zkBob account is created! The name of the account is auto-generated, beginning with zk.

![](../../../.gitbook/assets/zkbob-final.png)

{% hint style="success" %}
Next, connect your 0x wallet on Gnosis Chain to deposit funds to your zkAccount.
{% endhint %}

{% hint style="warning" %}
When using the same computer/browser for future zkBob sessions, you can access your account using only your password (assuming local storage has not been cleared). If you change browsers/computers or clear local storage, you will re-enter your seed phrase and create a new password to restore the account.
{% endhint %}

## Web3 Wallet

1\) Press the **zkAccount** button on the home screen.

![](../../../.gitbook/assets/zkbob-acct.png)

### Web 3 Wallet Not Connected

{% hint style="info" %}
If your MetaMask or other web3 wallet is not yet connected to the application, you will be prompted to connect. If your web3 wallet is already connected, [skip to the next section](./#web-3-wallet-connected).
{% endhint %}

2a) Click **Connect wallet**.

![](../../../.gitbook/assets/connect-wallet.png)

2b) Select Wallet type.

![](../../../.gitbook/assets/wallet-type.png)

2c) Follow prompts to connect and switch to Gnosis Chain network if needed. Once connected you be redirected to the home screen and your 🦊 wallet and balance displayed.  Click the **zkAccount** button to continue.

![](../../../.gitbook/assets/zk1.png)

### Web 3 Wallet Connected

2\) Select Wallet Key in the popup box.

![](../../../.gitbook/assets/zk-walletkey.png)

3\) Generate Key (this is a no-cost message, key is stored locally).&#x20;

![](../../../.gitbook/assets/generate-key.png)

4\) Sign message in MetaMask. __ Make sure to double check that Origin is the correct URL. [More info here](metamask-web3-wallet-warning.md). _(need updated screenshot with correct URL once app is out of testing phase)._

![](../../../.gitbook/assets/connect5.5.png)

5\) Create and Re-enter password.

![](../../../.gitbook/assets/connect-6.png)

6\) You should now have 2 connected accounts, your web 3 wallet account 🦊 and a second zk account, which is auto-named beginning with zk...

![](<../../../.gitbook/assets/connect-7 (1).png>)



