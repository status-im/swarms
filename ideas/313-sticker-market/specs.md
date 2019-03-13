# Sticker Market Specifications

## MVP

### Goal
Ship the bare minimum sticker market to drive SNT transactions and boost engagement in chat. The sticker market MVP will cater *only to end users* (not sticker creators), and will have no curation mechanism and a limited set of sticker packs commissioned by Status. 

Two primary user stories: **(1) use a sticker**; **(2) buy a sticker pack**.

### User Stories 
**Using stickers**
- As a user, I want to send stickers to my friends so that I can be more expressive and liven up my chats.
- I want to first choose from the packs I own. 
- I want to to select a specific sticker from within a given pack.
- When I send a sticker, I want everyone to be able to see it, regardless of whether they have the same pack installed. 
- If I have no stickers downloaded, I want to buy some directly from chat.
- When I receive a sticker in chat, I want to click on it to open it in the store and purchase the same pack for myself. 

**Buying stickers**
- I want to buy stickers in the context of use, from chat.
- I want to browse all sticker packs available.
- I want to use basic filters to find what I want, e.g. free/paid, search by emotion, etc. (dependent on metadata attached to each pack)
- When I find a pack I like, I want to know the price in SNT and fiat. 
- If I purchase a pack, I want to use it from my sticker drawer right away.

### Designs
[Figma link](https://www.figma.com/file/aS1ct66VQ6V0cio7vSqS8UoG/Chat?node-id=1506%3A0)

[Notes from design review 11/1/19](https://docs.google.com/document/d/1jNDWV2LkLbb7CiSRJyPfDSgDULxzViTJp4317TsdLp8/edit?usp=sharing)

### Price, Purchasing
- All packs will be priced in SNT; SNT is required for purchase.
- Stickers will be sold as packs, not individually.
- Status-commissioned packs will be priced around $2 in SNT, average for most sticker packs. 
- Creators can customize the price for their packs.

### Status Fees
- Propose that Status collects a percentage (50%) of all sales.
- Note: App stores typically require a 30% cut of all in-app purchases; we break this rule with SNT utility features.
- Alternative proposal: Require a fee to enter the marketplace, which can also be slashed to remove bad packs. 

### Measurement & Tracking
**MVP metrics**
- Number of addresses purchasing packs
- Number of packs purchased
- Number of purchases per pack
- Popularity of pack categories
- Avg. # of packs per user

**Future metrics**
- Number of packs registered by creators
- Number of packs removed by creators
- Popularity of categories registered by creators

Note: Free packs will likely not be trackable, only paid.

### Open Questions
- Agreement on Status fees?
- Need to modify or minimize the wallet flow in context of sticker purchase?

## Implementation Details

### Stickers
**Will have optional metadata**

Individual stickers will have optional metadata associated: 
- Emotion
- Emoji—in order to suggest a sticker for users when typing emojis, similar to Telegram feature

The metadata will be stored as key/value pairs in the extension file.

**Image formats**
- Supported file types are PNG, JPG/JPEG and GIF.
- Background should be transparent.
- Size is limited to 300kb (same as WeChat)
- Minimum size is 512x512px

**Storage and Accessibility**
- Stickers will be stored on a distributed system, starting with IPFS.
- Assets from a given sticker packer are accessible for use only by pack owners, but visible to all users in chat.

*Optional:* Use a local cache to reduce bandwidth consumption with a fixed cache size.

**Sending and Delivery**

Stickers are sent to recipients as hyperlinks (pointing to decentralized storages like IPFS) and resolved locally.

Sending a sticker does not mean transferring ownership of sticker or pack. 

*Limitation:* IPFS currently relies on HTTP gateways (Infura), which is a potential privacy issue as metadata will be leaked to external providers.

### Packs 
**Will be installed as extensions**

A pack is just a vehicle to transfer a set of stickers. The stickers are logically grouped as packs using metadata.

Extensions provide the necessary lifecycle and runtime features needed to support packs, and are a great way to allow creators to sell their packs permissionlessly via the Status market in a future phase.

Packs must be installed before stickers can be used in Status.

**Will have common metadata**

- Pack Name
- Creator
- Thumbnail
- Preview
- CreationDate
- Price
- Categories—these should be predefined (reference LINE, Kakao), allow multiple

The metadata will be stored as a set of key/value pairs in the pack extension file.

**Suggested categories**

Anime, TV & Movies, Humor, Animated, Cute, Love & Romance

Trending/Popular category will be possible based on on-chain purchase metrics. 

*Note:* By design of the contract, it will be possible to edit these categories and metadata associated with packs later.

**Free vs. paid**

Free packs will not require any transaction.
Paid packs trigger transactions.

**Pricing**

Should be optional for creator to set and edit the price of a sticker pack after publishing, to allow for adjustments in response to any currency volatility.

### Open Questions
- Use of a local cache for sticker storage?

### Security Concerns
- Using IPFS to host stickers means reliance on Infura

## Registry Contract

Only a simple registry contract is necessary to launch the MVP of the sticker market.

As packs are added to the registry, they will be listed in that order. 

Links to extensions are encoded similarly to what is done with EIP1577, allowing us to abstract away the underlying location.

A Status multisig must have the option to remove packs, for security, until an arbitration mechanism can be used to phase out this control.

Key functions of the contract:
- List all existing packs (returns a unique ID)
- Get details on a specific pack (links to an extension file)
- Buy a pack (identified by unique ID)
- List owned pack (follow [ERC721 pattern](https://eips.ethereum.org/EIPS/eip-721), balanceOf/tokenOfOwnerByIndex)
- Register a pack
- Set price of a pack
- Edit price of a pack
- Edit categories/metadata associated with a pack
- Add new sticker categories
- Gift a pack to another user (from own collection or directly from store)

Free packs, although they can not be bought or owned, should also be listed and offer details.

### Potential Risks
- Registered pack manipulation (3rd party attempting to remove or modify registered pack, including price)
- Pack payment is sent to the wrong address
- Pack fees are sent to the wrong address
- Status multi-sig address modified

### Contract Migration Strategy

**Migratable Data/Funds**

The migration approach to update behavior of smart contract is : “read in old, write in new, erase in old”, and should be done on demand by the users when it violates previous agreement, specially interfering with user funds.  
The contract should be stoppable and accept a migration interface.  

e.g. ens usernames stops accepting registrations after called moveRegistry, and only allows migration path from that on to the new contract. 
[Reference code 1](https://github.com/status-im/ens-usernames/blob/04bd8921516584a25a0bd9af15ddec3c4830265a/contracts/registry/UsernameRegistrar.sol#L382), [Reference Code 2](https://github.com/status-im/ens-usernames/blob/master/contracts/registry/UsernameRegistrar.sol#L311)

*Net* needs to update to new address and this can be limited in some types of smart contracts. User interface can figure out latest address if an ens node points to the latest version. 

It would be possible to encapsulate Data/Funds in a separate contract, which would allow the transfer of ownership from old contract to new contract, making the whole update cheaper as its “one transaction”, however this comes with additional cost of accessing another contract for data R/W, and the net cost of using this would be more expensive then if everyone had to migrate at their own once when the update is needed. It’s like charging a smaller fee forever for a potential future upgrade, over having to pay once to move the data when you want that to happen. 
This approach also makes the agreement vulnerable to controller attack - as the controller can just move everything at once by his will of migrate.

**Upgradable Behavior**

This approach allows changing the behavior and extending the contract storage schema. 
Reshape schema would be as costly as at least the cost of rewriting it twice of all contract data to blockchain state again, but for incremental updates this would not be needed. 
E.g. If new user account data is needed, the upgraded contract can rule to require owners of specific assets inside contract to fulfil new requirements before continue.
It is more net friendly because it keeps the same address and data/assets dont need to be moved for any simple change.
It can behave like Migration, as the controller could update it to a “migrate only code”, so it’s the most flexible. 
However it makes agreement vulnerable to controller attack, as violates the trust of contract behavior to controller, as it would be always possible to run a code to withdraw everything or do whatever controller wants.

The design of the contract MVP must account for potential changes needed by later introduced features, e.g.:
- Scarcity 
- ERC721 support
- Gifting packs

e.g. As a sticker creator, I want to sell a limited number of packs to increase my pack's value.

## Future Iterations

**Using stickers**

- I want to use shortcuts for my favorite or recently used stickers.
- I want to remove a pack I already own. 

**Selling stickers**

MVP
- I want an easy-to-use web interface to publish my stickers in the Status sticker market.
- I want to set the price for each pack I sell.
- I want the size and image requirements to be very clear.
- I want to receive an error if my image is too large or misproportioned.
- I want to upload my images to a decentralized storage solution directly from this interface.
- I want to name my packs. 
- I want to publish as many sticker packs as I would like. 
- I want to add tags/categories from a pre-determined list, so that my packs are more easily found. 
- I want to remove packs I’ve published to the store.

Questions for MVP
- Should artist set address for payment manually or by connecting to wallet?
- Does the artist need an artist name or can/should we pull Status username?
- Do artists upload pack images individually or as a group?

Later
- I want to edit the price of a pack.
- I want my pack to be limited edition (e.g. only a fixed amount of packs can be owned at a time)

**Gifting stickers**
- I want to buy a pack of stickers to give to a friend.
I want to give/trade my limited edition sticker pack to a friend.
