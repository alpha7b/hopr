# Question
Welcome to the last of our five Metadata Games: Wallet / IP Addresses. Gather your community and work on the next task. 👀🟡

DERP (derp.hoprnet.org) has been a cornerstone of our outreach to other projects, highlighting just how far web3 and crypto have to go to provide a sufficient level of privacy. 🔐

The DERP site has three examples of how crypto services leak your data – we’d like you to find some more. The most interesting example with the best explanation will win. 👀

🛑 While submitting your entry, which is ideally a video of DERP in action, please don’t doxx yourself. 

Each team should submit one entry by 2pm CEST on Monday June 13th.

Learn more about the games: https://medium.com/hoprnet/metadata-games-ab2b02946e2b

# My answer
TBH I haven't found any examples as meaningful as the three exsiting ones. These dapps are just what I have investigated.

## Crosschain bridges
- https://app.multichain.org/
- https://app.hop.exchange/

Before we bridge asset frome one chain to another, UI can display our asset on both the source chain and destination chain. I want to check what kind of informaiton will be exposed during bridge. However only [DERP ETH RPC](https://derp.hoprnet.org/rpc/eth/mainnet) is working now. [DERP XDAI RPC](https://derp.hoprnet.org/rpc/xdai/mainnet) is not working on my side. I'm wondering whether we can see the exposed informaiton on both RPCs if they are working and setup in one metamask.

Let's see what happens on hop.exchange if we try to send eth from Ethereum chain to Gnosis chain. 

Open app.hop.exchange, adjust source and destination accordingly. Then input 0.01eth and click Send.
![image](https://user-images.githubusercontent.com/55778604/173566197-60715176-75fe-4a58-a231-07e1dcd671f1.png)

In derp.hoprnet.org, we can see the following information.
- eth_getCode: this address is the [HOP token contract](https://etherscan.io/token/0xc5102fe9359fd9a28f877a67e36b0f050d81a3cc)
```[
  "0xc5102fe9359fd9a28f877a67e36b0f050d81a3cc",
  "0xe44b5e"
]
```
- eth_getBalance: get balance of my current address
```
[
  "[myAddress]",
  "0xe44b68"
]
```
- eth_call: get balance of all my addresses in metamask. This is absolutely more than the app needs.
```
[
  {
    "to": "0xb1f8e55c7f64d203c1400b9d8555d050f94adf39",
    "data": "0xf0002ea9000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000000000000000000000000000000000e00000000000000000000000000000000000000000000000000000000000000004000000000000000000000000[addr0]0000000000000000000000000[addr1]000000000000000000000000[addr2]000000000000000000000000[addr3]00000000000000000000000000000000000000000000000000000000000000010000000000000000000000000000000000000000000000000000000000000000"
  },
  "0xe44b6f"
]
```
- eth_call: this is the most important one: [Hop Protocol Ethereum Bridge](https://etherscan.io/address/0xb8901acb165ed027e32754e0ffe830802919727f)
```
	
[
  {
    "to": "0xb8901acb165ed027e32754e0ffe830802919727f",
    "data": "0x01ffc9a7d9b67a2600000000000000000000000000000000000000000000000000000000"
  },
  "0xe44b30"
]
```
- eth_estimateGas: 
```
[
  {
    "value": "0x2386f26fc10000",
    "from": "[myAddress]",
    "to": "0xb8901acb165ed027e32754e0ffe830802919727f",
    "data": "0xdeace8f50000000000000000000000000000000000000000000000000000000000000064000000000000000000000000[myAddress]000000000000000000000000000000000000000000000000002386f26fc1000000000000000000000000000000000000000000000000000000234f2219f7993b0000000000000000000000000000000000000000000000000000000062b1a94c00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
  }
]
```
