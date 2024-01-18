# xNFT pallet
Pallet for cross chain NFT transfer.
version = release-polkadot-v1.1.0
## Overview
The pallet contains the following features:-
1. Transfers collection from parachain to parachian 
2. Transfers NFTs from parachain to parachain 
#### **Please note:** In the latest version of the XCM protocol (v3), there's a limitation to the number of NFTs that can be transferred in a single transaction. Users are currently restricted to transferring a maximum of three NFTs at a time.
## Installation
#### Prerequisites:
- Rust. [Installation Guide](https://docs.substrate.io/install/). (Recommended version: rustc 1.68.0-nightly (574b64a97 2022-12-31))
- Substrate version polkadot-v0.43 [Installation Guide](https://github.com/paritytech/substrate/tree/polkadot-v0.9.43). 
- pallet_nft and pallet_xnft
- Relay-para environment
- Channel between the para chains
#### Steps:-
1. Add the pallets to your chain. Refer this [guide](https://docs.substrate.io/tutorials/build-application-logic/add-a-pallet/) for help with the integration. 
2. Add the following snippet to your runtime:
```rust
impl pallet_xnft::Config for Runtime{
	type RuntimeEvent = RuntimeEvent;
	type XcmExecutor = XcmExecutor<XcmConfig>;
	type ExecuteXcmOrigin = xcm_builder::EnsureXcmOrigin<RuntimeOrigin, LocalOriginToLocation>;
	type XcmSender = XcmRouter;
	type RuntimeOrigin = RuntimeOrigin;
	type RuntimeCall = RuntimeCall;
	#[cfg(feature = "runtime-benchmarks")]
	type Helper = ();
}
```
3. Build the repo using the following command:
```
cargo build --release
```
4. Set your relay-para connection. For help refer to the following links:-
- [Connect to a Relay Chain](https://docs.substrate.io/reference/how-to-guides/parachains/connect-to-a-relay-chain/)
- [Connect to a Local Parachain](https://docs.substrate.io/tutorials/build-a-parachain/connect-a-local-parachain/)
## Testing Guide
- Run the following command to execute the test cases:
```
cargo test --package pallet-xnft --lib -- test --nocapture 
```
- For ecosystem testing using trappist:
1. checkout to the [trappist](https://github.com/antiers-solutions/xNFT/tree/trappistPara) branch.
2. follow the readme in that branch for help with the setup.
#### Licence: Apache-2.0
## Notes
- We have used [trappist](https://github.com/paritytech/trappist) for help with ecosystem testing. A few changes have been made to the readme and the repo for integrating our pallet effectively.
- For multi NFT transfer, there is a limitation of maximum 3 transaction in XCM queue while using transact function. Due to this the maximum number of nft that can be transferred at one time is 3.
- The sibling account must have enough funds to perform the transactions 
- Following are the changes made in NFT pallet: 
- Create_delete_collection.rs: [line 18](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/features/create_delete_collection.rs#L18); added public access specifier
- Lib.rs: [line 65](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/lib.rs#L65); changed the type to public
- Removed super from all these structs; pub struct [CollectionDetails](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/types.rs#L85), pub struct [ItemDetails](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/types.rs#L134) and pub struct [CollectionMetadata](https://github.com/antiers-solutions/xNFT/blob/f4b5a9387a24bfc4be0fd4dc79872a07902a22bb/nfts/src/types.rs#L157).