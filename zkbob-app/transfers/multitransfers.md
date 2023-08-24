---
description: >-
  Now Bob can transfer to the whole crew....Alice, Carlos, Dave, Erin,
  Frank....with a single transaction!
---

# Multitransfers

{% hint style="warning" %}
Examples are performed with BOB on Polygon. However, **the BOB pool is now a USDC pool on Polygon**. You can also follow the instructions to deposit BOB or ETH on Optimism.
{% endhint %}

Multitransfer allows multiple transfers to be processed in a single transaction. There are no limits to the number of transfers, and the entire process can be completed with a single proof and a single 0.10 relayer fee.  Each transfer adds an additional note to the zkproof, which can slightly increase proof generation time. Other than that, multitransfer is as smooth and seamless as an ordinary zkBob transfer!

{% hint style="info" %}
💡 Learn more about how multitransfers sets zkBob apart as a privacy solution i[n this mirror post](https://mirror.xyz/0x6132eB883e88CD4E007552b871A6444Bfc34E837/mjYXeD7a005fdCu6dKdohfrSpcqpsuetW6djT46bDFk).
{% endhint %}

## Get Started

1\) To start a multitransfer, go to the **Transfer tab** and toggle the multitransfer switch.&#x20;

<figure><img src="https://lh5.googleusercontent.com/6kqw8dXidUF5PbSnyA4lG8hcKvUsE14PLyvZ3e0sZLOPpVPmHk30rEMnXWYRu1CZRqMpK420XRTI6jrM76O0lYtmNZvgDALDn6lFjEg1nQcM0lR9iXkAN7mk1J-w3lXmhjLcCn83-JQ9v0BQBCTqGNJoenkAsiqv0kfdGJEJUUv8Uc_yQEvNINgxJNWv3g" alt=""><figcaption></figcaption></figure>

2\) The interface will change to allow entry of multiple zkAddresses and amounts. You can either add manually or by uploading a csv.\
\
**Manually**: Add in the zkAddress along with the amount to transfer, 1 per line. The format should be ZKADDRESS, AMOUNT

Press Proceed to continue.

<figure><img src="https://lh5.googleusercontent.com/PxBlXi8rVqpzwHRqR_A4q6vV27g44mo6CSs7ei01UGTGin5LmFy3hK0yfxY6i0uNuP1B97HKqonRWn4F13FytFUIGogLnkQdXsPBZ3yppdH07zp1Ew46LXvu08tDf5Tkk25pS2frp3Ds8K5WoEILxGFc2ucRBRT5TlV0L7oi8dfMMezc-JHJjUKJ9ND3BA" alt=""><figcaption></figcaption></figure>

**CSV:** If preferred, you can add directly from a CSV. Click Upload CSV and select a completed csv file from your computer (ZKADDRESS, AMOUNT  one  per line). The information will automatically populate into the box on the app.

<figure><img src="../../.gitbook/assets/upload-1.png" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lh5.googleusercontent.com/2XZ2X-urfp79wscz8hwNLTaC-_0Qftk6srWxcjutvgnT8WBHHWhG4H54aCRFuJRF4v5Rmpf6Y4kN8IQdnL4Lt8fXhbEDxbBOW3eHIfxBnfM5wsFX6SC-uqVavwxjru7At6jvV_0Mv-CPBDJnSNPuk-BskE3w1FNIPwCiefjii3l9ysaOHgRTC_k8O8lLGA" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lh5.googleusercontent.com/PxBlXi8rVqpzwHRqR_A4q6vV27g44mo6CSs7ei01UGTGin5LmFy3hK0yfxY6i0uNuP1B97HKqonRWn4F13FytFUIGogLnkQdXsPBZ3yppdH07zp1Ew46LXvu08tDf5Tkk25pS2frp3Ds8K5WoEILxGFc2ucRBRT5TlV0L7oi8dfMMezc-JHJjUKJ9ND3BA" alt=""><figcaption></figcaption></figure>

3\) Next, check the details (Click view all).

<figure><img src="https://lh6.googleusercontent.com/y7EeH0urhAiAO2BBXOz2eIaaHqcHIlOX-QHUTCMCbzUs4kFmSkVr9pKefH-VFFaGUlXtOcSH7hEjV6iB-zlciUKGAsZwpbZGrlQH_bPwWuTE8BLsGkc1zu61FaA5VzkCCb83GRyXjuUV0Jpf7e8ilZJs1d-Q8SwjPUEVGlpMrsd8BpIZ2BsEx5pfDsKWAg" alt=""><figcaption><p><br></p></figcaption></figure>

<figure><img src="https://lh3.googleusercontent.com/QElUsXGgKkj8CP4e7Mi1mVo7aaaStZ6IdJIjfZUtEMOcpF5cUoZhxDpPg3M0MMdk_OdC-LUE4rvXy-a5Ezyu9zXJwMpYy6rT-OEbDUwvGcnbk6YGTriq8rdAbHbGKeXV8S1bdnr-zMvunN42uQAIX9l58qwecmEjIsijUJsh8A4UlmRPNqcPSOQzCvlO0Q" alt=""><figcaption></figcaption></figure>

4\) If all looks good close the modal and click **Confirm multitransfer**.&#x20;

<figure><img src="https://lh5.googleusercontent.com/9a92rjirE0L9tspgeeRZWlK919bkp0415VxOkXewNWVHL0-qA7d0p9UvcVIZvMF0tyVWCt2nqY9RRSX1NiSv-Fs-h2SKv9TC7BjNZjum8QkKbhhiFOJZ_7kmHYRs3WLcyF0ox3CwYN6fKVVDFt6pJ-pZVL6nCV_enDL1v_N1cNDytQnNkvGLMkqOr4tahQ" alt=""><figcaption></figcaption></figure>

5\) The application will generate a proof and your transaction will process. Once completed you can see details about multitransfers in your transaction history.

<figure><img src="https://lh6.googleusercontent.com/pHK-0t-T8G9kL9F5LIdhxdQHHw9STsOXKDyxBfdZALUG7q7NEV68jju2VSkBdn64kSPdczzl8p5X9W-fVdE-YzZ2C4Klxp3KAcmrreJ7squYpGBtyoWilERhkL54y1dHpLEQ3djgTRPsJHfbC-aR1LbDeaLaPq7S_mnYSHu0_NMAGzAfWbijUq8ynZBGOw" alt=""><figcaption></figcaption></figure>

<figure><img src="https://lh4.googleusercontent.com/JMS7bDOkYkvl3vPka2D5Dpl_Z8GtvRUAmrQVhh02JaVf6vv85wblvBAYiFa3fQxnHW7wv_OxBXrlFbsX27NubIHdjIqqehD9S0oOaA27Mo0ypfOs-AkkjEPdwT36PIJW0HKBo_WRVjZJV-SizhlpOdw7ik3HXlMGGOHvekoJ8X9lRSuXMaSrbHHBD0EfJA" alt=""><figcaption></figcaption></figure>
