---
description: >-
  Bitica native bridge is used to relay the Bitica native token between Bitica and
  Ethereum networks
---

# Bitica: Ethereum ↔ Bitica

Bitica native bridge between Ethereum and Bitica is used to relay the Bitica native token from Bitica to Ethereum network

## Architecture Overview

The Bitica bridged is based on POA's bridge implementation, it is used to transfer Bitica tokens between the Bitica chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Bitica or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Bitica tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Bitica chain on Ethereum**

Each cycle the total block reward distributed on Bitica chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Bitica chain, waiting for all bridge validators on Bitica chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the Bitica network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://biticablockchain.com/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0xDF35349c9208eC877C4DD098C8127123a6A81A0E](https://biticablockchain.com/address/0xDF35349c9208eC877C4DD098C8127123a6A81A0E/transactions)

Bitica token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Bitica you send native Bitica token to the home bridge contract. Then you receive an equal amount of the Bitica token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Bitica token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Bitica native token, sent from the home bridge contract.

#### 

