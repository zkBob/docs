# BOB Inventory

BOB inventory is handled via a [multi-sig Safe](https://gnosis-safe.io/app/matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/home) by a distributed reserve board. To facilitate inventory, BOB liquidity is deployed on DEXs including Uniswap v3 & Kyberswap, and paired with a stable asset such as USDC or BUSD.  Inventory positions are tuned to a very narrow range and maintained through the [AMM concentrated liquidity algorithm](https://docs.uniswap.org/protocol/concepts/V3-overview/concentrated-liquidity). This keeps BOB stable, and is known as an **inventory LP position**.

Any circulating supply of BOB available for users is purchased from this inventory (at \~1:1 for USD stable assets). Users can then choose to create their own **non-inventory LP positions** using purchased BOB + another tokens of their choice (for example BOB/WETH, BOB/WMATIC, BOB/GNO etc).&#x20;

The inventory safe does not have any administrative rights in regards to zkBOB; the only function for the safe is to oversee the inventory process. Additional decentralization measures are in development to maintain and balance optimal BOB inventory based on usage and demand.

Below are inventory position increases that have occurred to date.

### Polygon

1. 100 BOB for zkBOB testing purposes.\
   &#x20;Sep-09-2022 09:00:11 AM +UTC\
   [0x363eabc1c221a6a85cbb77c1b6e556f7db853ddb439774a6089871da1bd37e10](https://polygonscan.com/tx/0x363eabc1c221a6a85cbb77c1b6e556f7db853ddb439774a6089871da1bd37e10)
2. 1,000,000 BOB for [Uniswap pool inventory LP](https://zkbob.page.link/getBOB).\
   Sep-12-2022 07:51:16 PM +UTC\
   [0xb0574223b2c7be69999a4204e1e414179fa7f88f48df3a37ba55725706567f03](https://polygonscan.com/tx/0xb0574223b2c7be69999a4204e1e414179fa7f88f48df3a37ba55725706567f03)
3. 1,000,000 BOB to support[ ](https://info.uniswap.org/#/polygon/pools/0xe65a85bf544b4e4017cdb12387844683a9c86641)additional inventory pool.\
   Oct-13-2022 12:48:03 PM +UTC\
   [0x563b56bf3a1c9dd6f2e5f6bc12feae5df7f80801ee9b276efcfd83871c3bd922](https://polygonscan.com/tx/0x563b56bf3a1c9dd6f2e5f6bc12feae5df7f80801ee9b276efcfd83871c3bd922)
4. 5,000,000 BOB to increase inventory for the USDC/BOB pool.\
   Nov-03-2022 02:39:26 PM +UTC\
   [0x3e168dc82de33894c85f5f1f4e68afb0e25f43cc6685d8f9307fd4c9a12787de](https://polygonscan.com/tx/0x3e168dc82de33894c85f5f1f4e68afb0e25f43cc6685d8f9307fd4c9a12787de)

### Ethereum&#x20;

1. 100 BOB to substantiate BOB contract on Ethereum and facilitate token list inclusion.\
   Sep-27-2022 07:47:59 PM +UTC\
   [0x40dd99372285c6c2447718d12f4090daf257c076e5f65a4fba08e43b7f52cc10](https://etherscan.io/tx/0x40dd99372285c6c2447718d12f4090daf257c076e5f65a4fba08e43b7f52cc10)
2. 1,000,000 BOB for [Uniswap pool inventory](https://app.uniswap.org/#/swap/?chain=ethereum\&inputCurrency=0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48\&outputCurrency=0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).\
   Sep-30-2022 05:48:23 PM +UTC\
   [0x1c63241d212dc7f5f64d7e684d256582172022872e08a8685cb3dc353668c622](https://etherscan.io/tx/0x1c63241d212dc7f5f64d7e684d256582172022872e08a8685cb3dc353668c622)
3. 5,999,950.94 BOB to bolster inventory in Uniswap pool.\
   Oct-26-2022 01:50:35 PM +UTC\
   [0x3f1e4fafd917ec97540a047f5b042ccdb14b6d2971552bc98e450d6812623182](https://etherscan.io/tx/0x3f1e4fafd917ec97540a047f5b042ccdb14b6d2971552bc98e450d6812623182)

### Optimism

1. 1,000,000 BOB for [Uniswap inventory LP](https://app.uniswap.org/#/swap/?chain=optimism\&inputCurrency=0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48\&outputCurrency=0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).\
   Oct-06-2022 07:59:04 PM +UTC\
   [0x57039c5a011c6a41f5e89e8928adafe2e964d20c005b2114eb73687a0cff09af](https://optimistic.etherscan.io/tx/0x57039c5a011c6a41f5e89e8928adafe2e964d20c005b2114eb73687a0cff09af)

### Binance BNB Chain

1. 100 BOB to substantiate BOB contract on BSC and facilitate token list inclusion.\
   Nov-02-2022 01:48:41 PM +UTC\
   [0x8f6e4a59cdeffbb2a13cbc5d59b40aeb441c63906bd544fa986438cef2fe207b](https://bscscan.com/tx/0x8f6e4a59cdeffbb2a13cbc5d59b40aeb441c63906bd544fa986438cef2fe207b)
2. 1,000,000 BOB for [Kyberswap inventory LP](https://kyberswap.com/swap/bnb/bob-to-usdc).\
   Nov-07-2022 02:32:10 PM +UTC\
   [0x27f833734e9b3f018ff6b903fe856bf2bbc3a853aa585b5836c6e22308975aa9](https://bscscan.com/tx/0x27f833734e9b3f018ff6b903fe856bf2bbc3a853aa585b5836c6e22308975aa9)
