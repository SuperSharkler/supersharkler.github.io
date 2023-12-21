---
layout: single
title:  Build an NFT project from scratch
date:   2023-12-20 23:00:00 -0700
categories: Software
---

## Project
[Link - Sharkler NFT](https://robosharkler.github.io/sharkler-nft-frontend-react/)

![demo](/assets/images/sharkler-nft-demo.gif "Demo")

Dependencies:
* PC or Mac web browsers (Chrome recommended)
* Meta mask browser extension
* A wallet for Seoplia ETH test net
* Some fake ETH in the wallet


## How I built it
NFT went super viral in 2022, with famous stories of selling a JPEG for millions of dollars. And even though it has been a bit too late to call it a trend, I still want to figure out what is NFT - kinda like cyber archeology. Therefore, this blog documents how I built it from scratch. The tutorial I followed was [fireship.io](https://fireship.io/lessons/web3-solidity-hardhat-react-tutorial/). 

First of all, for any NFT project, there would be four major components - digital arts, ETH wallets, a smart contract, and a frontend.

#### Digital arts
The digital arts are usually stored in IPFS, a decentralized file system. If the art is stored on the ETH chain directly, I guess the gas fee would be extremely high. 

#### Smart contract
The smart contract is the core. It is a piece of code that is deployed to the ETH blockchain net. Each smart contract will be one block on the chain, thus each smart contract will have a unique contract address, very similar to the concept that a website has a unique URL. With the contract address, people can interact with the contract through their wallets.

In our NFT project, the smart contract will be responsible for receiving money (ETH) from the user wallet, generating the NFT - essentially an association between an integer token ID and a string, and transferring the ownership of that token ID from the contract address to the user wallet address. In most NFT cases, the string will be an IPFS link pointing to a JSON file, in which there is another IPFS link pointing to the digital art, e.g. [ipfs.io](https://ipfs.io/ipfs/QmR9nXy6XHmJcGLXHDjWN79BhaQEN21LU4kU4V2QvkdbDN/1.json). The JSON format needs to follow a certain standard so that the NFT can be scanned and loaded properly by most NFT marketplaces like OpenSea.

Therefore, an NFT project is essentially selling the ownership of the association between the token ID and a string. 

After knowing what we want to achieve with the smart contract, we can start coding. The implementation is quite straightforward - 
* Go to [openzeppelin](https://docs.openzeppelin.com/contracts/5.x/wizard) to generate the ERC721 standard contract template
* Implement a new method that takes ETH payment and transfers the token ownership in return
* Implement a new method that can withdraw the cumulated ETH from your contract address to yourself (contract owner)
* Deploy it with hardhat

My smart contract reference - [here](https://github.com/robosharkler/sharkler-nft-contract)

#### Wallet
We can have a better understanding of this topic by comparing a web2.0 user account and a web3.0 wallet.

For most modern sites, to interact with them through the internet, you need to have an account with them; For smart contracts, you will need a wallet to interact with them through the blockchain net.

The interaction between the user and a website will require a small amount of computation, which is usually covered by website servers. The interaction between the user and a smart contract will require a HUGE amount of computation, which is usually covered by the user (known as the gas fee). I guess that this is one reason why a user account in the blockchain world is called a "wallet" as most actions in this world would cost something from the user account.  

In terms of implementation, no code is required for this, we just need to download a wallet from app stores and fund it with some ETH. If you are using a test net, there should be a fountain where you can get fake ETH to your test wallet. 

#### Frontend
If without a frontend, users would need to talk to your smart contract through something like [etherscan](https://sepolia.etherscan.io/address/0x80156eb2148a43d3036bd94b837a11978a00b55b#writeContract), which is not very intuitive. 

The frontend is responsible for making it easy and appealing for users willing to pay their ETH to your smart contract, therefore, we need to implement the below features - 
* Connect to the user's wallet
* Show minted (purchased) NFTs by displaying the digital arts linked to them
* Show a loot box representing the next unminted NFT, and a button for the user to mint it

My react frontend reference - [here](https://github.com/robosharkler/sharkler-nft-frontend-react)