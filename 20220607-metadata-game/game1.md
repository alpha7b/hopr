# Question
The Metadata Games have begun! Gather your community and work on Game 1 -- Transaction Data 👀🟡

One of the most important HOPR use cases for crypto is helping in the ongoing battle with MEV. 🛡

Find an example of an MEV exploit involving $HOPR and explain what happened. The most interesting example with the best explanation will win. 👀

Each team must provide one entry by 2pm CEST on Wednesday June 8th

More details you will find here: https://medium.com/hoprnet/metadata-games-ab2b02946e2b

# My answer

This address (https://sandwiched.wtf/0xaf42db46abbc4b2d7b2a4f783c07b26d38f851ae) is a victim during a sandwich attack in block 
12442637(https://etherscan.io/txs?block=12442637&p=2). 

Here is the overall process:
Step 1: MEV bot detected a large amount of HOPR will be sold in uniswapv2 HOPR/DAI pair, so MEV bot sold some HOPR to lower the HOPR price first.
Step 2: User sold a large amount of HOPR, and made the price even lower.
Step 3: MEV bot bought back the same amount of HOPR that it sold in Step 1, by using less amount of DAI that it received from Step 1.

Here are the transactions of each step.
1. Sandwich open: Swap 74,383HOPR For 38,753DAI. GAS fee: $21.9
https://etherscan.io/tx/0x847112cca21c5f858d80792f52767472a4b1cd85bdd2c850396ee98b40c705c1

2. User transaction: Swap 157,106HOPR For 81,289DAI
https://etherscan.io/tx/0x3afd6434700e6815f6043f3401fb4b32a3676c60657bb8e06a7ef610539cb8a7

3. Sandwich close: Swap 38,623DAI For 74,383HOPR. GAS fee: $14.59
https://etherscan.io/tx/0x19bd85a4352d0fa3a48a062bb2b1bbe2aae62249cfd85d91f810312275db14b5

In this attack, MEV bot earned 38,753 - 38,623 - 21.9 - 14.59 = $93.5

Learn more: What is MEV and how it works
https://ethereum.org/en/developers/docs/mev/
