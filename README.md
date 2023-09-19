# xNFT Grant Delivery

This is repo contains the deliverables for [xNFT](https://github.com/w3f/Grants-Program/blob/master/applications/xNFT.md) grant.

## Contents
1. [NFT pallet](https://github.com/antiers-solutions/xNFT/tree/master/nfts) 
2. [xNFT Pallet](https://github.com/antiers-solutions/xNFT/tree/master/pallet-xnft)

## Overview
#### NFT Pallet
- We have used the official [NFT Pallet](https://github.com/paritytech/substrate/tree/polkadot-v0.9.43/frame/nfts) in Substrate, but with some modifications to enable the functionality of the xNFT pallet.
- Following are the changes made in NFT pallet: 
- Create_delete_collection.rs: [line 18](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/features/create_delete_collection.rs#L18); added public access specifier
- Lib.rs: [line 65](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/lib.rs#L65); changed the type to public
- Removed super from all these structs; pub struct [CollectionDetails](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/types.rs#L85), pub struct [ItemDetails](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/types.rs#L134) and pub struct [CollectionMetadata](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/types.rs#L157).

#### xNFT Pallet
Purpose of the pallet is to :-
1. Transfer collection from parachain to parachian 
2. Transfer NFTs from parachain to parachain 
##### **NOTE:-**
- For multi NFT transfer, there is a limitation of maximum 3 transaction in XCM queue while using transact function. Due to this the maximum number of nft that can be transferred at one time is 3.
- The sibling account must have enough funds to perform the transactions.