# xNFT Grant Delivery

This is repo contains the deliverables for [xNFT](https://github.com/w3f/Grants-Program/blob/master/applications/xNFT.md) grant.

## Contents
1. [xNFT Pallet](https://github.com/antiers-solutions/xNFT/tree/master/pallet-xnft)

## Overview
#### NFT Pallet
- We have used the official [NFT Pallet](https://github.com/paritytech/substrate/tree/polkadot-v0.9.43/frame/nfts) in Substrate

#### xNFT Pallet
Purpose of the pallet is to :-
1. Transfer collection from parachain to parachian 
2. Transfer NFTs from parachain to parachain 
##### **NOTE:-**
- For multi NFT transfer, there is a limitation of maximum 3 transaction in XCM queue while using transact function. Due to this the maximum number of nft that can be transferred at one time is 3.
- The sibling account must have enough funds to perform the transactions.