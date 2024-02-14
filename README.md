# Trappist

[![Check Set-Up & Build](https://github.com/paritytech/trappist/actions/workflows/check.yml/badge.svg)](https://github.com/paritytech/trappist/actions/workflows/check.yml)
[![XCM Simulator](https://github.com/paritytech/trappist/actions/workflows/simulate.yml/badge.svg)](https://github.com/paritytech/trappist/actions/workflows/simulate.yml)

**Trappist** is a web3 developer playground for experimenting with [cross-chain applications and services](https://polkadot.network/cross-chain-communication/) built on the technologies spearheaded by the [Polkadot Network](https://polkadot.network/), namely:
* [Substrate](https://substrate.io/), a Blockchain framework that enables developers to quickly and easily build future proof blockchains optimized for any use case.
* [Cumulus](https://github.com/paritytech/cumulus), a set of tools for writing Substrate-based Polkadot parachains.
* [XCM](https://polkadot.network/cross-chain-communication/), a common language for secure messaging across Polkadot  parachains, and with external networks via bridges.
* [Rococo](https://polkadot.network/blog/statemint-becomes-first-common-good-parachain-on-polkadot/), Polkadot’s Parachain Testnet.
* [Statemint](https://polkadot.network/blog/statemint-becomes-first-common-good-parachain-on-polkadot/), Polkadot's common good parachain which provides functionality for deploying and transferring assets — both Fungible and Non-Fungible Tokens (NFTs).
* [Contracts Pallet](https://github.com/paritytech/substrate/tree/master/frame/contracts), enable WebAssembly smart-contracts executions.
* [ink!](https://paritytech.github.io/ink/), an eDSL to write smart contracts in Rust for blockchains built on the Substrate framework.

Altogether those technologies enable an array of exciting cross-chain applications & services:

![XCM use cases](/docs/media/xcm-use-cases.png)


This repository contains the source code of **Trappist**, a feature-rich parachain for exploring and learning about cross-chain applications and services, along with a script to run a complete local multi-chain environment that includes:
* Rococo relay-chain
* Statemine common good asset parachain
* Trappist feature-rich parachain
* An additional parachain capable to execute ink! smart contracts.

All these pre-configured to allow cross-chain communication via XCM messages on HRMP channels.

## Getting Started

Follow the steps below to get started.


#### Rust Setup

First, complete the [basic Rust setup instructions](./docs/rust-setup.md).


#### Build

Use the following command to build the Trappist collator binary:

```bash 
cargo build --release
```

### XCM Playground via Zombienet

Create a `Binaries` folder into the root of this repository and place the following binaries inside of it:
For mac users
- `polkadot` (which you can download from [the drive](https://drive.google.com/file/d/1nu02QoODHpLLMAAVL24uhW5tqBR_kBId/view?usp=sharing))
- `parachain-template-node` (which you can download from [the drive](https://drive.google.com/file/d/1nu02QoODHpLLMAAVL24uhW5tqBR_kBId/view?usp=sharing))
- `zombienet-macos` (which you can download from [the drive](https://drive.google.com/file/d/1nu02QoODHpLLMAAVL24uhW5tqBR_kBId/view?usp=sharing))

For Linux users(Ubuntu 22.04)
- `polkadot` (which you can download from [the drive](https://drive.google.com/drive/folders/1Y5tuClPb4bMreeKY_y7UED4ucaFnfZ8Y?usp=sharing))
- `parachain-template-node` (which you can download from [the drive](https://drive.google.com/drive/folders/1Y5tuClPb4bMreeKY_y7UED4ucaFnfZ8Y?usp=sharing))
- `zombienet-linux` (which you can download from [the drive](https://drive.google.com/drive/folders/1Y5tuClPb4bMreeKY_y7UED4ucaFnfZ8Y?usp=sharing))


make all the binaries executable:
```bash
$ chmod +x zombienet-macos or chmod +x zombienet-linux
$ chmod +x polkadot
$ chmod +x parachain-template-node
```

Then, start the **Trappist** playground with:
```bash
cd Binaries
./zombienet-macos -p native spawn .././zombienet/trappist_rococo.toml
 or
./zombienet-linux -p native spawn .././zombienet/trappist_rococo.toml
```

- Before testing transfer funds to the Sibling accounts of Parachains:
1. ParaID 1000: 5Eg2fntNprdN3FgH4sfEaaZhYtddZQSQUqvYJ1f2mLtinVhV
2. ParaID 1836: 5Eg2fnsjAAr8RGZfa8Sy5mYFPabA9ZLNGYECCKXPD6xnK6D2


## License
Trappist is licensed under [Apache 2](LICENSE).
