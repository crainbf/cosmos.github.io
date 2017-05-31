~~~
title: "Fundraiser Refunds"
slug: fundraiser-refunds
date: 2017-05-30
author: The Cosmonauts
excerpt: An update on fundraiser refunds
~~~

Dearest Cosmonauts,

This a quick overdue update on some loose ends from the fundraiser, 
namely what to do about the Cosmic Whale that contributed 40k ether, 
what to do about late Bitcoin transactions,
and what we're doing about hedging our position.

We'll also remind you that you can check your suggested Atom allocation at https://fundraiser.cosmos.network/.
To get your Cosmos Address, download the command line tool from: https://github.com/cosmos/fundraiser-cli/releases/tag/2.11.3.
On an offline computer, enter your twelve word mnemonic.

# The Whale

The fundraiser terms stated a limit of 1M USD per contributor.
For the purpose of the fundraiser, the price of ether was $45.23 USD.
Thus, the maximum acceptable contribution was 22109.21954455008 ETH.
An excited member of the community disregarded this limit and contributed 40k ETH.
So 17890 ETH were returned, and the difference (0.78045544992 ETH) was kept as an administration fee.

Rest assured, a signed statement was secured from the Cosmic Whale 
requesting the funds be sent back to the sending address.
The text of that statement is as follows:

```
I am a single individual that donated more than the limit in the Cosmos fundraiser and would like the excess funds sent back to my address 0x1926851A0457Dd9046f26c0cedDCbED749e6A55b . 47faddc1ae97514dc30c6f9a3e9f9bec6a7aaf661195e2ea956fc339c0dc4a62
```

and the signature:

```
0x2e6bd79cae4e9b9ac7f6ded70d4a3b33a7cd7158d0f3f9a5607e2dd1dd66d54953eb9765531458c9a070322e217a63d3aa463f96c1e78e520e1eda013ad21a9800
```

which can be confirmed to have come from address 0x1926851A0457Dd9046f26c0cedDCbED749e6A55b.

The refund consisted of the following transactions:

https://etherscan.io/tx/0xcdb9f8213a11800f582b2b96354763cbc2c2ed5dca2c22b6be36d3537c1dc142
https://etherscan.io/tx/0x317280bfcfab32f85c68244d82256108c13bd8867b055867256920b7b531de18
https://etherscan.io/tx/0x03d30c121c47e3ed744f62d597b47fd09814d4af9c5702ae15bfe6dadcc9eb36

Note that the last two are the final transactions in a 2-of-3 multisig sequence. 
Since these were the first transactions out of the treasury, they were executed extra-carefully and initiated with small amounts
before sending the larger sum.
Feel free to investigate further on the blockchain.

# Late Bitcoin Transactions

The fundraiser hit its hidden cap limit of 17M USD rather quickly.
Due to the expressiveness of Ethereum smart contracts, further Ether contributions were prevented from this point.
Regarding Bitcoin, it was announced that transactions would only be accepted for three more blocks.
The final block in which donations were accepted was block number 460660.
That said, due to issues with delayed transactions and ambiguity, donations with an intermediate transaction in block 460660 and a final transaction in block 460661 were accepted as well.
All funds received after block 460661 have been refunded to their respective intermediate address.

If your donation transaction was committed in a block after 460661, you should reclaim the bitcoins 
sent back to your intermediate address. To do so, download the command line tool from: https://github.com/cosmos/fundraiser-cli/releases/tag/2.11.3

On an offline machine, run the program and enter your twelve word mnemonic. It will output your Cosmos Address,
as well as your intermediate Bitcoin address and private key. Import the private key into a Bitcoin wallet
of your choice and send the Bitcoin to wherever you like.

The refunds occured over two transactions:
https://blockchain.info/tx/395bfd3c076ccc96796c951442c0c9fb4bc8c213c4afff5342629b3486a5dc37
https://blockchain.info/tx/0bff17da7d317bd4c5d1a528bd13a17b23f2136d0ff808f495608c6b81a9d78b

# Hedging Strategy

We have committed to a conservative hedging strategy of 50% USD, 25% Bitcoin, 25% Ether, denominated in USD.
In an effort to work towards this, we have been steadily liquidating ether.
So far we have liquidated more than half of it.

You can monitor our progress here: https://etherscan.io/address/0xe825363f3bedabc95b2a9d42dbc73ec7b82b57d3#internaltx

# Up Next

We have lots of exciting things in the pipeline, including new Tendermint releases, 
testnets supporting Interblockchain Communication, UIs, and more, that we will be rolling out imminently. Stay tuned!

