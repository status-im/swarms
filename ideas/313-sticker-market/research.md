Sticker Market Research
===

This document captures thoughts on the technical implementation for the [sticker market](https://github.com/status-im/swarms/blob/master/ideas/313-sticker-market.md) (section I), based on a set of potential user stories (section II).


### Selected use cases for MVP

+ As a user, I want to view and select stickers from my stickers within a chat.
+ I want to send and receive stickers in chat.
    + I can only send one sticker at a time.
+ I want to install new stickers pack via a marketplace accessible from chat (both free or paid).

### To define in spec 
*Thoughts on these items are below, but will be formatted into an easy-to-read product spec with visuals and diagrams where necessary.*

- Which elements are native UI vs. extension
- Stickers as ERC721 tokens vs. regular images
- Standard metadata for a sticker pack
- Sticker image format
- Storage of sticker images
    - Methods for preventing stolen images
- Requirements for pack registry
    - Sticker pricing methods
- MVP user flow & UI


# I. Technical considerations

## Implementation

Will be implemented in native ClojureScript (i.e. not as an extension)

## I.I Packs

A pack is just a vehicle to transfer a set of stickers.
Those stickers are logically grouped as packs via some MetaData.

Packs must be installed before stickers can be used in status.

2 families of packs: free and paid

* free packs must not require any transaction
* paid packs trigger transactions

### Packs as extension

Extensions provide the necessary lifecycle and runtime features needed for packs support.
They also provide the necessary extensibility for features that might be considered in a second phase.

At first a pack would be an extension listing associated NFT stickers.

```edn
{meta
 {}
 
 hooks/chat.sticker.pack
 {:stickers [{:id 4}]}}
```

Pack installation will be done transparently in the stickers UI. The usual extension installation screens won't be displayed.
Trying to install a pack a user doesn't own will be rejected.

### Registry

A contract keeps tracks of all existing packs, and who owns each packs. Free packs must be accessible at no cost (including gas).

An artist can register a new pack and eventually define a price. This is permissionless and has no cost (besides gas).

A user can aquire a paid pack. SNT amount is sent back to the artist.
Buying a pack doesn't require ETH for gas? (https://medium.com/gitcoin/native-meta-transactions-e509d91a8482)

_Open question (Rachel)_ Status fees?

This registry works first registered, first served.

Specifically the contract must allow to:

* list all available packs (paid and free)
* know which paid packs are owned by a user
* register a new pack
* unregister an existing pack (only owner, eventually Status)
* aquire a paid pack
* access pack details (paid packs are only accessible to owners)

```solidity
contract Pack {
  packs() {
    // ids? enumeration?
  }

  pack(uint256) {
    // details required to show off in marketplace: name, author, price,  overview image
  }

  packDetails(uint256) {
    // Link to file containing details about images
    // If free, anyone. If paid, only owner
  }

  registerPack(...) {}

  registerPack(..., uint price, uint256 numberOfPacks) {}
  // price sent back to registering address. Status takes a cut?

  unregisterPack(uint id) {
    // only owner
  }

  aquirePack(uint256) {
    // pay for the pack, transfer ownership of all associated stickers
  }
}
```

As a second step, we can add some arbitrary filters. Packs that we pre-populate and which artists submit should both contain consistent metadata.

_Open question (Rachel)_ Does Status needs special access to update the registry? (blacklist)
_Open question (Ricardo)_ Need a clear path to move to a curated regitry.
_Open question (Ricardo)_ Could [ERC998](https://eips.ethereum.org/EIPS/eip-998) be useful here?
_Open question (Ricardo)_ If packs are always priced in SNT, should we attempt to 'peg' the price to a certain amount in USD or DAI to prevent variations?_

_Note_ As installing a free pack doesn't mutate the blockchain (no transaction) it will be necessary to track their installation Status side. This implies that those won't be available on others devices and won't survive account restoration.

### Add arbitrary metadata to packs

### Curation (2nd phase)

Packs are curated by a 3rd party contract. This registry contract will be used by Status to discover packs.

Work on DApps store will be leverage.

## I.II Stickers

Implemented as ERC721.

[ERC721x](https://erc721x.org/) extends ERC721 by allowing batch transfers (lower gas cost) and class support (tokens can have an associated quantity).

```solidity
contract Sticker is ERC721x {
   function pack external view returns (uint256 _pack);
}
```

Leveraging ERC721 allows to benefit from the whole NFT ecosystem and associated standards e.g. accessories via [ERC998](https://eips.ethereum.org/EIPS/eip-998)

This also allows stickers to be compatible with existing NFTs trading platforms ([OpenSea](https://opensea.io/), [RareBits](https://rarebits.io/), [0x Instant](https://0x.org/instant), [EMoon](https://www.emoon.io/), [loom](https://loom.games/trading/), ...)

[Ethmoji](https://ethmoji.io/) is related experiment implementing emojis as NFT.

### Add arbitrary metadata to stickers

A set of key/value pair is associated to stickers.
Those metadata are stored using ERC721 default metadata mechanism and OpenSea [standard](https://docs.opensea.io/docs/2-adding-metadata) augmented by sticker specific features.

MetaData files are accessed via [ERC721Metadata#tokenUri](https://eips.ethereum.org/EIPS/eip-721) (encoded as a [URL](https://github.com/ipfs/in-web-browsers/blob/master/ADDRESSING.md#addressing-with-native-url)) and stored on a distributed storage (links is encoded using method described in [EIP 1577](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-1577.md)).

### Common metadata available

A set of metadata is predefined and will be reused by Status to provide extra features.

* link a sticker to an existing emoji. Allows to suggest a sticker when using an emoji (as in telegram)
* filter stickers by emotion (e.g. happy, sad, ..)

_TODO define this set_ e.g. author, emoticon, emotion, ... Specify optional/mandatory aspect.

It might be worth noting than MetaData could be used to link to per sticker `extension`. This would allow to plug custom arbitrary sticker behavior.

## Stickers image format

### Telegram

The image file should be in PNG format with a transparent layer and must fit into a 512x512 square (one of the sides must be 512px and the other 512px or less).

### WeChat

GIF? The official maximum size is for a WeChat Sticker is 300KB

### WhatsApp

512x512 square image, with a transparent background, max 100KB , images packaged as mobile application :)

## Sending stickers

Stickers owned by a user must then be made accessible to message recipient.
There are different ways to achieve this.

Sending a sticker does not imply sending a token. NFT ownership is preserved.

### As a message payload

Status chat protocol doesn't allow sending messages with big payload.

There are no short term plans to mitigate this.

### As a hyperlink / hash

Messages can embed a link to stickers stored on distributed storages layers.

_Note_ Current IPFS support relies on HTTP gateways (e.g. infura). This is a potential privacy issue as metadata will be leaked to those external providers.

## Stickers cache (optional)

Implement a local cache to improve bandwidth consumption. Fixed cache size, remove automatically older stickers.

ReactNative has partial images support. OOB, only remote images and local images known at compile time can be displayed.

Status uses `react-native-fs` for reading files from filesystem. We can use it to write files (sticker's images). `DocumentDirectoryPath` exists on both platforms and is writable.

## Stickers assets storage

Stickers assets are stored as is in a distributed storage. Copyright infringement will be solved using the curated registry.
Stickers assets of paid pack should only be accessible to pack owners.

## Storage layer performance

Status currently has no native IPFS nor SWARM clients. For IPFS access it relies on INFURA gateway. Cloudflare also provides an [IPFS gateway](https://www.cloudflare.com/distributed-web-gateway/).

It's been validated that the performance is sufficient.

## I.III UI

What do people love about stickers? 
How do they use them?
[Survey by Jinho of 63 community members & friends in S Korea](https://docs.google.com/presentation/d/1ksXL3aFFWZicXRvjE530qiMZDLQJgubG3E-UwVQsHDs/edit#slide=id.g4a1fef5fbe_0_128)
[Observational research of 5 users in S Korea by Philip](https://docs.google.com/presentation/d/1ulDaM5XYffT6E9DNArv5Ds8sQU7xSQrfsZMSLPm254M/edit#slide=id.p)

Stickers UI is created from scratch. There is no plan to update chat command UI to match sticker one.

Stickers are displayed in such a way that it is easy to distinguish them from regular images.

As a sticker recipient it is very easy to install the associated pack (e.g. long press triggers a contextual menu with relevant action)

Tentative mockups:

* https://www.figma.com/file/aS1ct66VQ6V0cio7vSqS8UoG/Chat?node-id=1506%3A0
* https://framer.cloud/yShsJ

### Notes from call with Ricardo 20/12

+ Packs are a bunch of static stickers
+ Some paid, some free
+ Stickers will be ERC721 so we can leverage this standard in the future
+ LOOM team 721X 
+ ERC721 offers metadata and also the ability to gift/transfer 
+ We could rely on that metadata for building added features
+ Ricardo to work on registry contract


### Notes from 9/1/19 call (Julien, Ricardo, Rachel)


**For MVP**

- Both free & paid packs? Packs listed (free for now) in status are registered in the registry contact. 
Not necessary to have any cost, to include on registry only. No transaction to buy because the client can have a hardcarded rule to display a sticker from the free packs available. It will not check ownership of that sticker pack. 

*Requirement:* Client needs to see which are paid and which are free, and which pack a user already owns (paid). 

*  Do we open registration to anyone? If yes status must be able to deactivate / remove some.
Could handle this in the contract with carbon voting.
Curation market will dovetail with DApp store work.

*MVP requirement:* Only Status can register packs. Closed to outside parties. 

*Open question:* Fee to submit to marketplace. Goes directly to Status and can be used to slash packs from the marketplace if they are violating copyright or similar. 

* Can we have a pack with a fixed price in DAI, but have users pay in SNT only?

*Research*: MakerDAO contract - can we get this rate? Probably queryable via ABI.

* Status takes a configurable cut per sale (non status packs)

*Requirement*: Need option to configure this in contract globally. Percentage of price? Percentage fixed at time of registration. 1% stays at 1% even if Status changes cut to 5%. 

* Users can only send stickers they own (from paid packs or not).
  What if some of those are NFTs transfered to a 3rd party?
  Can we efficiently list stickers owned by an address?
  
*Notes*: Should be easy to query when the node is synced. 

* Sticker metadata scheme; How the pack strickers data is stored in the smartcontract and how it identifies individual stickers?

*Notes*: ERC721 (StickerPack) and StickerMarket is not holding an individual sticker data. When you buy a sticker, you mint a sticker pack token. The whole pack is the token. Ricardo is working on a way to split this pack. It's fairly complicated to create an interface in the sticker contract registry. Too much information to store in the smart contract at once. Hash of all the packs, each sticker is a merkle leaf that points to JSON in decentralised storage. When you create a pack, you create merkle tree and register pack to the root. When you want to send a message, the client will check if you own the sticker you are sending because the sticker is an IPFS link. You are sending along the merkle proof certifying that you own the pack it contains as in ERC721 (StickerPack)



**Not for MVP but probably needs to be considered now**

* Is ERC721x interesting to reduce gas costs?


* Combining NFTs to have custom tokens is a great plus. What is needed to make sure we can leverage ERC998 later on?


* What is needed to be prepared to potential registry spamming? Assuming all packs will be browsable from within status.


* Can we prepare the stickers contract so that it could be paid in SNT only (via relayer)?


* How do we prepare for transitions to next phases registry? (open to paid packs, curation based, ..) Via a proxy?


# II. Guiding use cases

## End users

### Anyone can see sent stickers

No need to have the associated pack installed.

### I have access to default sticker packs

A set of free packs might be made available by default.

### I can aquire a new sticker pack

Once aquired, I can send messages containing stickers to someone (1-1, private/public group chat). One sticker at a time.

### I can discover new sticker packs via a curated marketplace

### I can easicily be redirected from the marketplace 

e.g. by clicking on a sticker I just received.

### I own a pack aquired

My sticker pack is associated to my wallet address.
A sticker pack might have limited availability (i.e. only X packs can be minted - thus bought -)

### I can send stickers to any chat

Anyone is able to see those stickers.

### I can send a pack as a gift (optional)

I buy a pack which is then associated to the receiver address

Note: 53% of respondents to [Jinho's survey](https://docs.google.com/presentation/d/1ksXL3aFFWZicXRvjE530qiMZDLQJgubG3E-UwVQsHDs/edit#slide=id.g4a1fef5fbe_0_281) of 60+ friends and community members in Korea have gifted stickers

### I can see animated stickers (optional)

Android might have limited support or animated files.
File types might be limited (e.g. GIFs)

We have to limit file types

### I can send any regular NFT as sticker (optional)

## Creators

_Those stories are part of a second iteration_

List of artists we could reach out to -> [Sticker artists](https://notes.status.im/s/Sy4R8uLlE) 

### I can submit a new pack

No validation step, no censorship. There are transaction cost (gas) associated to publishing a pack.

Evenually curated by SNT holders.
If the curation registry is not ready a simple registry (controlled by Status) will be used.

Copyright and othe legal concerns are delegated to the curation mechanism.

### I can easily create a pack (optional)

Creation of a pack from a set of images should be straightforward.

What the competition offers:

* https://creator.line.me/en/studio/
* https://faq.whatsapp.com/general/26000226

Potentially could be achieved via an extension to simplify pack creation from local images.

* https://blog.wechat.com/2018/11/23/whats-new-in-wechat-6-7-4-for-ios-selfie-stickers/

### I can specify the price of a pack

Price can be updated manually by contracts owners.

See https://medium.com/protea/exploring-bonding-curve-collateral-c37d4f922bbd

### I can remove one of my pack from the registry

### I cannot upgrade a pack

A pack is immutable. To update a pack, remove and create a new pack.


# III. Links, etc.

Extra semantic can be associated to NFTs. e.g.

* [ENS domains](https://ensnifty.com/)
* [Charity donation](https://radi.cards/)
* [Conference tickets](https://forum.aragon.org/t/limited-edition-happy-holidays-aragon-nft-now-available/421)

### Red envelope

* https://qz.com/872560/alibaba-baba-and-tencent-hkg-0700-are-borrowing-from-pokemon-go-to-upgrade-red-envelope-cash-giving/
* https://github.com/weijiekoh/caishen
* https://messengernews.fb.com/2018/12/17/messengers-new-camera-updates-can-help-spread-holiday-cheer/ (AR stickers)
* https://app.cryptoxmas.xyz/#/send/0x7957f8e67cd4d9634888bacbd216527e1e80b6fe934e9710364fe61036ebe53d (NFT christmas card, here also providing access to DAppCon)

### References

* https://github.com/gitcoinco/Kudos721Contract/blob/master/contracts/Kudos.sol
* https://medium.com/@theofreybote/stifties-turn-any-cryptocollectible-into-a-chat-app-sticker-d9c194809eb9
* https://github.com/mralbertchen/stifties
* https://wax.io/blog/wax-stickers-new-blockchain-based-product-coming-soon
* https://www.kickstarter.com/projects/328862817/zombie-battleground-the-new-generation-of-ccg-tcg
* https://medium.com/loom-network/erc721x-a-smarter-token-for-the-future-of-crypto-collectibles-335ba5f706d1
* https://hackernoon.com/uncovering-information-hidden-in-the-smart-contracts-of-gods-unchained-755cc057974a
* https://github.com/OpenZeppelin/openzeppelin-solidity/tree/master/contracts/token/ERC721
* https://github.com/dharmaprotocol/charta/blob/master/contracts/ERC721TokenRegistry.sol
* https://devpost.com/software/pully
