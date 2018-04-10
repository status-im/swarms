## Preamble

    Idea: 163
    Title: Support ERC721 tokens
    Status: Draft
    Created: 2018-04-10
    
## Summary
Add ERC721 support to Status wallet so that users can see their CryptoKitties, Punks, Celebrities, etc. alongside their other assets.

## Swarm Participants
- Lead/PM: [@rachelhamlin](https://github.com/rachelhamlin)
- Testing & Evaluation: 
- Contributor: [@jeluard](https://github.com/jeluard)
- Contributor: [@goranjovic](https://github.com/goranjovic)
- UX: [@denis-sharypin](https://github.com/denis-sharypin)

## Product Overview

With 100+ digital collectibles on the market and a combined sales volume greater than $50MM, it's important that we allow users to access their NFT collections inside Status right alongside their ETH and ERC20 tokens.

The two primary cases we need to support are:
1. Having my existing collectibles in my Status wallet
2. Buying or receiving new collectibles and seeing them in my Status wallet

Additional use cases may focus on gifting collectibles from one user to another, as well as sending collectibles in a chat.

### Product Description

##### For already owned crypto assets

Users should be able to view their collection of NFTs in a dedicated section of their Status wallet. 
Tokens associated with a user's Mainnet address should appear there automatically. 

Any ERC721 should be supported, and individual assets within a collection should display available metadata such as name or number, properties, creation date, etc. To whatever extent possible, we can standardize the metadata displayed for each type of collectible and provide a link to the DApp for more.

##### For newly purchased crypto assets

When a user buys a new collectible through some other browser, it should automatically appear in their Status wallet. Same goes for collectibles that can be gifted, as is the case with Cryptokitties; Status should recognize when a user receives a new collectible as a gift.

A user should also be able to purchase collectibles from the Status browser, and the collectible should appear in their wallet.

Initially we can use marketplaces to support this by consuming metadata from [Opensea.io](https://opensea.io/) or [Rarebits.io](https://rarebits.io/), but users should also be able to purchase new collectibles inside each DApp. 

### Requirements & Dependencies


### Minimum Viable Product
Goal Date: 

Description:

As there is no way to automatically browse all the existing collectible types, we'll focus on individual support for any collectible DApps that Status currently features.

- UX/UI for collectibles in wallet:
  - Browse collections
  - Browse collectibles
  - View individual collectible
- Add wallet support for any ERC721 featured in Status Selected DApps:
  - CryptoFighters
  - CryptoKitties
  - CryptoPunks
  - etc.
  
### Iteration 1
- Expand collectible support
- Purchase new collectibles via a marketplace

### Exit Criteria
TK

### Success Metrics
TK

## Supporting Role Communication

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
