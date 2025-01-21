---
description: >-
  Yota native bridge is used to relay the Yota native token between Yota and
  Ethereum networks
---

# Yota: Ethereum ↔ Yota

Yota native bridge between Ethereum and Yota is used to relay the Yota native token from Yota to Ethereum network

## Architecture Overview

The Yota bridged is based on POA's bridge implementation, it is used to transfer Yota tokens between the Yota chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Yota or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Yota tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Yota chain on Ethereum**

Each cycle the total block reward distributed on Yota chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Yota chain, waiting for all bridge validators on Yota chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the CYBYOTA network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://cybyotascan.com/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0xf39f8f3223aDB78F87836eeD365ca858D876873a](https://cybyotascan.com/address/0xf39f8f3223aDB78F87836eeD365ca858D876873a/transactions)

Yota token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Yota you send native Yota token to the home bridge contract. Then you receive an equal amount of the Yota token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Yota token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Yota native token, sent from the home bridge contract.

#### 

