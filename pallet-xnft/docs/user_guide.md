# USER GUIDE
This guide includes steps for a user to leverage the xNFT pallet to transfer NFT cross-chains

## Prerequisites
1. Establish bidirectional HRMP channel between parchains through relay chain. For help, use [this](https://docs.substrate.io/reference/how-to-guides/parachains/add-hrmp-channels/) guide.
2. Create a collection, and mint some NFTs using the [NFT Pallet](https://github.com/antiers-solutions/xNFT/tree/master/nfts).

## Following are the steps that you will need to follow in order to use the xNFT functionality:-
#### **COLLECTION TRANSFER**
Here we are transferring the collection with collection ID = 0 along with its associated metadata. 

1. Transfer the collection to destination chain through xNFT pallet. 
- Go to developers tab then go to extrinsics.
- Select **xNFT** pallet inside this select **collectionTransfer** function. Set the parameters as per your requirement.
![ss8](https://github.com/w3f/Grant-Milestone-Delivery/assets/60818312/ad5aca5c-ca9a-4b25-8dd7-b2c861433460)

**Events popped at source chain will be as follows:-**
- collectionSent
- collectionMetadataTransfer
- collectionTransferedSuccessfully
![ss9](https://github.com/antiers-solutions/xNFT/assets/100279864/3d7d8ddb-557e-40c4-8f67-92af75f58a5b)

**Events popped at destination chain will be as follows:-**
- created
- success 
- collectionMetadataSet
![ss10](https://github.com/antiers-solutions/xNFT/assets/100279864/538fb8a8-187a-4081-b3d5-db0299f8b440)

#### **NFT Transfer**
Here we are transferring NFT with NFT ID = 0 present at collection with collection_id = 0. It transfers NFT along with its associated metadata and assign a new owner to the NFT. 
2. Transfer the NFT.
- Go to developers tab then go to extrinsics.
- Select **xNFT** pallet inside this select **nftTransfer** function. Set the parameters as per your requirement.
![ss11](https://github.com/antiers-solutions/xNFT/assets/100279864/6c958858-5cf2-4ea0-a11f-3f76352110e4)

**Events popped at source chain will be as follows:-**
- NftSent
- itemMetadataTransfered
- nftOwnershipTransfered
- Burned

![ss12](https://github.com/antiers-solutions/xNFT/assets/100279864/70116563-3637-46c8-a45b-b86901db7465)
**Events popped at destination chain will be as follows:-**
- issued 
- success 
- itemMetadataSet
- transfered
![ss13](https://github.com/antiers-solutions/xNFT/assets/100279864/227b7e58-9bbd-4df4-89ba-13b4f8e47f0b)

#### **TRANSFER MULTIPLE NFTs**
Here we are transferring NFTs with NFT ID = 1,2,3 present in collection with collection ID = 0. It transfers just the NFTs at the destination chain.
3. Transfer the multi NFT. 
- Go to developers tab then go to extrinsics.
- Select **xNFT** pallet inside this select **transferMultiNfts** function. Set the parameters as per your requirement.
![ss14](https://github.com/antiers-solutions/xNFT/assets/100279864/c8fb480d-02da-422f-9965-884e857d3e9a)


**Events popped at source chain will be as follows:-**
- NftSent
- Burned
![ss15](https://github.com/antiers-solutions/xNFT/assets/100279864/480d2d8e-ee5b-447b-85ad-ed5ecef458ab)
**Events popped at source chain will be as follows:-**
- issued 
- success
![ss16](https://github.com/antiers-solutions/xNFT/assets/100279864/259fa068-b999-4fec-847c-28313382637c)

#### **TRANSFER NFT METADATA**
Here we are transferring above sent NFTs metadatas. 
4. Transfer metadata of NFTs. 
- Go to developers tab then go to extrinsics.
- Select **xNFT** pallet inside this select **transferNftMetadata** function. Set the parameters as per your requirement.
![ss17](https://github.com/antiers-solutions/xNFT/assets/100279864/64e80c5e-6171-494f-b0e8-182f0247d809)

**Events popped at source chain are as follows:-**
- itemMetadataTransfered
![ss18](https://github.com/antiers-solutions/xNFT/assets/100279864/c2a517f8-59ef-4cb6-a0c3-c307544d450d)

**Events triggered at destination chain are as follows:-** 
- itemMetadataSet
- Success
![ss19](https://github.com/antiers-solutions/xNFT/assets/100279864/b2ecc925-1dfa-4ea6-9622-22608077a0c5)


#### **TRANSFER NFT OWNERSHIP**
Here we're assigning the ownership of NFTs sent in step 10. 
5. Change the owner of the NFTs.
- Go to developers tab then go to extrinsics.
- Select **xNFT** pallet inside this select **tansferNftsOwnership** function. Set the parameters as per your requirement.
![ss20](https://github.com/antiers-solutions/xNFT/assets/100279864/2bfb0b5f-3d5f-4737-9dfb-aa4d7932834c)

**Events popped at source chain are as follows:-**
- NftOwnershipTransfered
      
![ss21](https://github.com/antiers-solutions/xNFT/assets/100279864/76872a5a-799b-4e6b-a89c-47aa895108a9)

**Events triggered at destination chain are as follows:-** 
- transfered
- Success
![ss22](https://github.com/antiers-solutions/xNFT/assets/100279864/e1be92bd-1b95-479a-9af7-ab1f75a9bb4b)


#### **COLLECTION OWNER TRANSFER**
Here we change the owner of collection that is being sent from source chain to destination chain.For this we need to accept the ownership at destination chain for the collection of which we are changing the ownership.
6. Change the owner of the collection.
- Go to destination chain.
- Go to developers tab then go to extrinsics.
- Select **NFT** pallet inside this select **setAcceptOwnership** function. Set the parameters as per your requirement.
![ss23](https://github.com/antiers-solutions/xNFT/assets/100279864/0507ac05-f847-4129-926b-e58fc26ca239)

- Then go back to the source chain select developer tab.Next, select extrinsics. 
- Select **xNFT** pallet inside this select **transferCollectionOwnership** function. Set the parameters as per your requirement.
![ss24](https://github.com/antiers-solutions/xNFT/assets/100279864/d7bbee9a-cf3e-4e85-9f62-9ff434a11150)

**Events popped at source chain are as follows:-**
- collectionOwnershipTransfer
      
![ss25](https://github.com/antiers-solutions/xNFT/assets/100279864/9d7ec17c-865c-4f2a-a47f-372662adc7d5)

**Events triggered at destination chain are as follows:-** 
- ownerChanged
- Success
![ss26](https://github.com/antiers-solutions/xNFT/assets/100279864/39d325eb-2f99-4562-a709-8a260b09fc45)