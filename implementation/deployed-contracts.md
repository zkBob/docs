---
description: zkBob deployed contracts
---

# Deployed Contracts

{% hint style="info" %}
Contract deployments in this section cover all aspects of the zkBob application deployed on several networks.\
\
For BOB specific contract info on other networks ( Ethereum Mainnet, Arbitrum etc) see the [BOB FAQs](broken-reference). \
\
Note the BOB stablecoin is deployed with the same address on all networks: `0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`\

{% endhint %}

## Polygon (BOB->USDC)

RPC: [https://rpc.ankr.com/polygon](https://rpc.ankr.com/polygon)\
Chain ID: 137\
zkBob Pool ID: 0

<table><thead><tr><th width="289">Contract name</th><th>Address</th></tr></thead><tbody><tr><td>BOB Token (pre-migration)</td><td><a href="https://polygonscan.com/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B">0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B</a></td></tr><tr><td>USDC Token</td><td><a href="https://polygonscan.com/address/0x2791bca1f2de4661ed88a30c99a7a9449aa84174">0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174</a></td></tr><tr><td>zkBob Pool</td><td><a href="https://polygonscan.com/address/0x72e6b59d4a90ab232e55d4bb7ed2dd17494d62fb">0x72e6b59d4a90ab232e55d4bb7ed2dd17494d62fb</a></td></tr><tr><td>zkBob Direct Deposits Queue</td><td><a href="https://polygonscan.com/address/0x668c5286ead26fac5fa944887f9d2f20f7ddf289">0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289</a></td></tr><tr><td>Operator Manager</td><td><a href="https://polygonscan.com/address/0x8aEb89D5C689C2cf373Fe8b56c7A0cD5BDc74CE6">0x8aEb89D5C689C2cf373Fe8b56c7A0cD5BDc74CE6</a></td></tr><tr><td>KYC Manager</td><td><a href="https://polygonscan.com/address/0xb8580ea6312dd2311d72bc932b0354a07d974138">0xb8580Ea6312DD2311d72bC932b0354A07d974138</a></td></tr><tr><td>Transfer Verifier</td><td><a href="https://polygonscan.com/address/0xa86c511832ead78d30ad49711874a9f3a1dfb840">0xA86C511832eAd78d30ad49711874a9F3a1dfb840</a></td></tr><tr><td>Tree Update Verifier</td><td><a href="https://polygonscan.com/address/0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D">0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D</a></td></tr><tr><td>Batch Direct Deposit Verifier</td><td><a href="https://polygonscan.com/address/0x9a7b4198065efe631a962e737bdfe1f44f2cb3ee">0x9a7B4198065efE631a962e737bDfE1f44f2CB3EE</a></td></tr><tr><td>Relayer (Operator) Address</td><td><a href="https://polygonscan.com/address/0xc2c4AD59B78F4A0aFD0CDB8133E640Db08Fa5b90">0xc2c4AD59B78F4A0aFD0CDB8133E640Db08Fa5b90</a></td></tr><tr><td>MATIC Faucet (sends 0.1 MATIC to addresses with 0 balance on withdrawal >= 10 BOB)</td><td><a href="https://polygonscan.com/address/0xdf59ba2cf116397de71cf18d85eaa286ce6759ba">0xdf59ba2cf116397de71cf18d85eaa286ce6759ba</a></td></tr></tbody></table>

## Optimism (BOB)

RPC: [https://rpc.ankr.com/optimism](https://rpc.ankr.com/optimism)\
Chain ID: 10\
zkBob Pool ID: 1

<table><thead><tr><th width="294">Contract name</th><th>Address</th></tr></thead><tbody><tr><td>BOB Token</td><td><a href="https://optimism.blockscout.com/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B?tab=contract">0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B</a></td></tr><tr><td>zkBob Pool</td><td><a href="https://optimism.blockscout.com/address/0x1CA8C2B9B20E18e86d5b9a72370fC6c91814c97C">0x1CA8C2B9B20E18e86d5b9a72370fC6c91814c97C</a></td></tr><tr><td>zkBob Direct Deposits Queue</td><td><a href="https://optimism.blockscout.com/address/0x15B8C75c024acba8c114C21F42eb515A762c0014">0x15B8C75c024acba8c114C21F42eb515A762c0014</a></td></tr><tr><td>Operator Manager</td><td><a href="https://optimism.blockscout.com/address/0xF853E272893035a8C6A82616B7b442aB329D92D9">0xF853E272893035a8C6A82616B7b442aB329D92D9</a></td></tr><tr><td>Transfer Verifier</td><td><a href="https://optimism.blockscout.com/address/0x7aD8d97c60BFb59e501e3b6C1d8E564b0bB8195d">0x7aD8d97c60BFb59e501e3b6C1d8E564b0bB8195d</a></td></tr><tr><td>Tree Update Verifier</td><td><a href="https://optimism.blockscout.com/address/0x2C34aFcB1c51796c3c0C7710c72a56Eb72E1E81D">0x2C34aFcB1c51796c3c0C7710c72a56Eb72E1E81D</a></td></tr><tr><td>Batch Direct Deposit Verifier</td><td><a href="https://optimism.blockscout.com/address/0x85afa00f38aD5F353C2B80985407b8E8A27eA38f">0x85afa00f38aD5F353C2B80985407b8E8A27eA38f</a></td></tr><tr><td>Relayer (Operator) Address</td><td><a href="https://optimism.blockscout.com/address/0xb9CD01c0b417b4e9095f620aE2f849A84a9B1690">0xb9CD01c0b417b4e9095f620aE2f849A84a9B1690</a></td></tr></tbody></table>

## Optimism (ETH)

RPC: [https://rpc.ankr.com/optimism](https://rpc.ankr.com/optimism)\
Chain ID: 10\
zkBob Pool ID: 2

<table><thead><tr><th width="294">Contract name</th><th>Address</th></tr></thead><tbody><tr><td>WETH Token</td><td><a href="https://optimism.blockscout.com/address/0x4200000000000000000000000000000000000006">0x4200000000000000000000000000000000000006</a></td></tr><tr><td>zkBob Pool</td><td><a href="https://optimism.blockscout.com/address/0x58320A55bbc5F89E5D0c92108F762Ac0172C5992">0x58320A55bbc5F89E5D0c92108F762Ac0172C5992</a></td></tr><tr><td>zkBob Direct Deposits Queue</td><td><a href="https://optimism.blockscout.com/address/0x318e2C1f5f6Ac4fDD5979E73D498342B255fC869">0x318e2C1f5f6Ac4fDD5979E73D498342B255fC869</a></td></tr><tr><td>Operator Manager</td><td><a href="https://optimism.blockscout.com/address/0xEe174e75c206498649d04050528008020FCEb88A">0xEe174e75c206498649d04050528008020FCEb88A</a></td></tr><tr><td>Transfer Verifier</td><td><a href="https://optimism.blockscout.com/address/0xFc84D2963a1711c98EA7592C91bb207d75Ed1040">0xFc84D2963a1711c98EA7592C91bb207d75Ed1040</a></td></tr><tr><td>Tree Update Verifier</td><td><a href="https://optimism.blockscout.com/address/0xe4F2Ab4eC79A0D23Fb96489b57d558b637C68303">0xe4F2Ab4eC79A0D23Fb96489b57d558b637C68303</a></td></tr><tr><td>Batch Direct Deposit Verifier</td><td><a href="https://optimism.blockscout.com/address/0xf52e8c8eBde32495A9a79B61E0b91f65A71F343A">0xf52e8c8eBde32495A9a79B61E0b91f65A71F343A</a></td></tr><tr><td>Relayer (Operator) Address</td><td><a href="https://optimism.blockscout.com/address/0x65Eb51b16678d57Bb0bB8d160D1b9D0a57880512">0x65Eb51b16678d57Bb0bB8d160D1b9D0a57880512</a></td></tr></tbody></table>

## Sepolia Testnet (BOB)

RPC: [https://rpc.sepolia.org](https://rpc.sepolia.org/)\
Chain ID: 11155111\
Faucet: [https://sepolia-faucet.pk910.de](https://sepolia-faucet.pk910.de) , [https://grabteeth.xyz/](https://grabteeth.xyz/)\
zkBob Pool ID: 0

<table><thead><tr><th width="300">Contract name</th><th>Address</th></tr></thead><tbody><tr><td>BOB Token</td><td><a href="https://sepolia.etherscan.io/token/0x2c74b18e2f84b78ac67428d0c7a9898515f0c46f">0x2C74B18e2f84B78ac67428d0c7a9898515f0c46f</a></td></tr><tr><td>zkBob Pool</td><td><a href="https://sepolia.etherscan.io/address/0x3bd088c19960a8b5d72e4e01847791bd0dd1c9e6">0x3bd088C19960A8B5d72E4e01847791BD0DD1C9E6</a> </td></tr><tr><td>zkBob Direct Deposits Queue</td><td><a href="https://sepolia.etherscan.io/address/0xE3Dd183ffa70BcFC442A0B9991E682cA8A442Ade">0xE3Dd183ffa70BcFC442A0B9991E682cA8A442Ade</a></td></tr><tr><td>Operator Manager</td><td><a href="https://sepolia.etherscan.io/address/0xe342ca03a553383c1983b892c24290c1ce1b614f">0xe342ca03a553383c1983b892c24290c1ce1b614f</a> </td></tr><tr><td>KYC Manager</td><td><a href="https://sepolia.etherscan.io/address/0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C">0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C</a></td></tr><tr><td>Transfer Verifier</td><td><a href="https://sepolia.etherscan.io/address/0x5573D865cF113d44d219FaF1b26F5785Cb2eA3EE">0x5573D865cF113d44d219FaF1b26F5785Cb2eA3EE</a></td></tr><tr><td>Tree Update Verifier</td><td><a href="https://sepolia.etherscan.io/address/0x4b6f007a91c5733cd4f8bbec5ba5951f8303cdab">0x4b6f007a91c5733cd4f8bbec5ba5951f8303cdab</a> </td></tr><tr><td>Batch Direct Deposit Verifier</td><td><a href="https://sepolia.etherscan.io/address/0xB5Fe2F991db54B6c9362FE2ace8f78C9Dd05277e">0xB5Fe2F991db54B6c9362FE2ace8f78C9Dd05277e</a></td></tr><tr><td>Relayer (Operator) Address</td><td><a href="https://sepolia.etherscan.io/address/0xba6f711e1d4db0cbfbc09d1d11c5fb7445160673">0xBA6f711e1D4dB0CBfbC09D1d11C5Fb7445160673</a></td></tr><tr><td>BOB Faucet</td><td><a href="https://sepolia.etherscan.io/address/0xb9988D599A64723462955BfC8441F1Af90335796#writeContract#F1">0xb9988D599A64723462955BfC8441F1Af90335796</a></td></tr></tbody></table>

## Goerli Testnet (BOB->USDC)

RPC: [https://rpc.ankr.com/eth\_goerli](https://rpc.ankr.com/eth\_goerli)\
Chain ID: 5\
Faucet: [https://grabteeth.xyz/](https://grabteeth.xyz/)\
zkBob Pool ID: 16776962 (`0xffff02`)

<table><thead><tr><th width="301">Contract name</th><th>Address</th></tr></thead><tbody><tr><td>BOB Token (pre-migration)</td><td><a href="https://eth-goerli.blockscout.com/address/0x97a4ab97028466FE67F18A6cd67559BAABE391b8">0x97a4ab97028466FE67F18A6cd67559BAABE391b8</a></td></tr><tr><td>USDC Token</td><td><a href="https://eth-goerli.blockscout.com/address/0x28B531401Ee3f17521B3772c13EAF3f86C2Fe780">0x28B531401Ee3f17521B3772c13EAF3f86C2Fe780</a></td></tr><tr><td>zkBob Pool</td><td><a href="https://eth-goerli.blockscout.com/address/0x49661694a71B3Dab9F25E86D5df2809B170c56E6">0x49661694a71B3Dab9F25E86D5df2809B170c56E6</a></td></tr><tr><td>zkBob Direct Deposits Queue</td><td><a href="https://eth-goerli.blockscout.com/address/0xE4C77B7787cC116A5E1549c5BB36DE07732100Bb">0xE4C77B7787cC116A5E1549c5BB36DE07732100Bb</a></td></tr><tr><td>Operator Manager</td><td><a href="https://eth-goerli.blockscout.com/address/0x3f6c6Aaa1674e7178dbD521b1b65DBf61580F00d">0x3f6c6Aaa1674e7178dbD521b1b65DBf61580F00d</a></td></tr><tr><td>Transfer Verifier</td><td><a href="https://eth-goerli.blockscout.com/address/0xAb76044aA1Bd8E55461263BA7d25d122638DAD6d">0xAb76044aA1Bd8E55461263BA7d25d122638DAD6d</a></td></tr><tr><td>Tree Update Verifier</td><td><a href="https://eth-goerli.blockscout.com/address/0x0043e6fF8032299616C770a264a9c6FD1157EF48">0x0043e6fF8032299616C770a264a9c6FD1157EF48</a></td></tr><tr><td>Batch Direct Deposit Verifier</td><td><a href="https://eth-goerli.blockscout.com/address/0x7a5f24D03Aa69F3aB02968CdCA796a8B11E2527d">0x7a5f24D03Aa69F3aB02968CdCA796a8B11E2527d</a></td></tr><tr><td>Relayer (Operator) Address</td><td><a href="https://eth-goerli.blockscout.com/address/0xc45da11d73e6BA6c6b866b26feaae106406D95b5">0xc45da11d73e6BA6c6b866b26feaae106406D95b5</a></td></tr><tr><td>USDC Faucet</td><td><a href="https://eth-goerli.blockscout.com/address/0x56c105D40f637eF3ac04905682b3DAEfF3F13D24?tab=write_contract">0x56c105D40f637eF3ac04905682b3DAEfF3F13D24</a></td></tr></tbody></table>

## Goerli Testnet (ETH)

RPC: [https://rpc.ankr.com/eth\_goerli](https://rpc.ankr.com/eth\_goerli)\
Chain ID: 5\
Faucet: [https://grabteeth.xyz/](https://grabteeth.xyz/)\
zkBob Pool ID: 16776964 (`0xffff04`)

<table><thead><tr><th width="294">Contract name</th><th>Address</th></tr></thead><tbody><tr><td>WETH Token</td><td><a href="https://goerli.etherscan.io/token/0xB4FBF271143F4FBf7B91A5ded31805e42b2208d6">0xB4FBF271143F4FBf7B91A5ded31805e42b2208d6</a></td></tr><tr><td>zkBob Pool</td><td><a href="https://goerli.etherscan.io/address/0xf9dbCF4005497e042838dE9082C817fCa790e945">0xf9dbCF4005497e042838dE9082C817fCa790e945</a></td></tr><tr><td>zkBob Direct Deposits Queue</td><td><a href="https://goerli.etherscan.io/address/0x8F7020DD968B7F8510d889CcDAda4b041C4f3B0b">0x8F7020DD968B7F8510d889CcDAda4b041C4f3B0b</a></td></tr><tr><td>Operator Manager</td><td><a href="https://goerli.etherscan.io/address/0xcb84E60Cf7dAB1dF405bf07113737C2B39d14799">0xcb84E60Cf7dAB1dF405bf07113737C2B39d14799</a></td></tr><tr><td>Transfer Verifier</td><td><a href="https://goerli.etherscan.io/address/0x9C76fA2E25BdD7F4a2827434297538dfF39d05D7">0x9C76fA2E25BdD7F4a2827434297538dfF39d05D7</a></td></tr><tr><td>Tree Update Verifier</td><td><a href="https://goerli.etherscan.io/address/0x351Af131B080F9C458fA0f58b55Ef32143D64492">0x351Af131B080F9C458fA0f58b55Ef32143D64492</a></td></tr><tr><td>Batch Direct Deposit Verifier</td><td><a href="https://goerli.etherscan.io/address/0x49cD0a25a0c453B70cf3EE71018875fC9Fa39260">0x49cD0a25a0c453B70cf3EE71018875fC9Fa39260</a></td></tr><tr><td>Relayer (Operator) Address</td><td><a href="https://goerli.etherscan.io/address/0xb72e1e3ec1fbad9b2b5e35597e698027bd8f06e0">0xb72E1E3Ec1fBaD9B2b5E35597e698027Bd8F06E0</a></td></tr></tbody></table>

## Goerli Optimism Testnet (BOB)

RPC: [https://goerli.optimism.io](https://goerli.optimism.io)\
Chain ID: 420\
zkBob Pool ID: 16776963 (`0xffff03`)

<table><thead><tr><th width="284">Contract name</th><th>Address</th></tr></thead><tbody><tr><td>BOB Token</td><td><a href="https://optimism-goerli.blockscout.com/address/0x0fA7E69b9344D6434Bd6b79c5950bb5234245a5F">0x0fA7E69b9344D6434Bd6b79c5950bb5234245a5F</a></td></tr><tr><td>zkBob Pool</td><td><a href="https://optimism-goerli.blockscout.com/address/0x55B81b0730399974Ccad8AC858e766Cf54126596">0x55B81b0730399974Ccad8AC858e766Cf54126596</a></td></tr><tr><td>zkBob Direct Deposits Queue</td><td><a href="https://optimism-goerli.blockscout.com/address/0x598223503E5A6d8d5b6a6cD5266Bc803169C9633">0x598223503E5A6d8d5b6a6cD5266Bc803169C9633</a></td></tr><tr><td>Operator Manager</td><td><a href="https://optimism-goerli.blockscout.com/address/0x2e7c89E5b5FA64982d2Aff65d52b9cBCdBF20D7A">0x2e7c89E5b5FA64982d2Aff65d52b9cBCdBF20D7A</a></td></tr><tr><td>Transfer Verifier</td><td><a href="https://optimism-goerli.blockscout.com/address/0x9B5F6C35bfE688C61A71164d5d9B37bF340d206C">0x9B5F6C35bfE688C61A71164d5d9B37bF340d206C</a></td></tr><tr><td>Tree Update Verifier</td><td><a href="https://optimism-goerli.blockscout.com/address/0x4f6Cd600d614b54ef2de2E1c8b9146D3e875b09A">0x4f6Cd600d614b54ef2de2E1c8b9146D3e875b09A</a></td></tr><tr><td>Batch Direct Deposit Verifier</td><td><a href="https://optimism-goerli.blockscout.com/address/0xf256149df8e258B4E7Adc55CE28123734A07f91f">0xf256149df8e258B4E7Adc55CE28123734A07f91f</a></td></tr><tr><td>Relayer (Operator) Address</td><td><a href="https://optimism-goerli.blockscout.com/address/0xC325D80FF4A883E0E6bCfaF239B7d9405D6830fb">0xC325D80FF4A883E0E6bCfaF239B7d9405D6830fb</a></td></tr><tr><td>BOB Faucet</td><td><a href="https://optimism-goerli.blockscout.com/address/0x357cA353dbCad28418d5F3110727B2af62803F20?tab=write_contract">0x357cA353dbCad28418d5F3110727B2af62803F20</a></td></tr></tbody></table>

## Governance

All zkBob pool deployments on public networks are controlled by an established governance process. Read more about the current governance setup - [#governance](deployed-contracts.md#governance "mention")
