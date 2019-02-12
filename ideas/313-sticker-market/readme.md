---
id: #312-janitors
title: Swarm Janitors
status: research
lead-contributor: Julien/Rachel
contributors:
    - Andrey
    - Julien
    - Nastya
    - Rachel
    - Hester
budget:
- actual: $21k
- estimate: yyy
- currency: USD
---

Sticker Market Swarm Proposal
===

## Summary and Goals

Stickers are a must-have for any messenger, particularly with Asian markets in mind.

The goal of the Status sticker market is two-fold:

1) Allow users to buy and use stickers in chat using SNT.
2) Allow creators to sell stickers permissionlessly through a curated marketplace, for SNT.

For the initial scope, the focus is on use case #1.

We can commission a set of stickers to populate the marketplace starting out.

## Contributors

- Julien
- Andrey
- Nastya
- Ricardo
- Maciej

(+ Janitor swarm) 

## Communication

`status channel`: [#313-sticker-market](https://get.status.im/chat/public/313-sticker-market)

`sync schedule`: biweekly sprint planning, ad hoc meetings as needed

`Pivotal project:` https://www.pivotaltracker.com/projects/2231918

`Meeting notes:` https://notes.status.im/wyjNCxeURu6lYSwWGh3biw

`Research notes:` https://notes.status.im/stickers-market-research

## Latest

Monday, 11/2
- Sticker UI is complete
- Andrey working on contract/UI interface
- Illustrator hired
- [Community contest planning](https://docs.google.com/document/d/1LxVHnWzdS9D1xO5b6lcferKX8xeIySzQ95u5eLZh8Q0/edit?ts=5c61c866) underway

Friday, 1/2
- First iteration of UI complete
- Design issues identified by Maciej
- Rachel talking with sticker illustrators
- Ricardo making final changes to contract to:
- Allow multiple categories per pack
- Include a function to globally set a burn percentage. One more option: global fee to all packs, only controller can set it.
- Add new contract state restricting all market functions to controller but “buyToken”

## Research 

`Timing`: wrap on 28/12

`References`: LINE & Kakao are two of the best sticker markets. Looking at these two alone can give ample guidance on great sticker market UX. Telegram another worthy reference.

`Initial stories to inform technical research`:
- As a user, I want to view and select stickers from my stickers within a chat.
- I want to send and receive stickers in chat.
- I want to buy new stickers via a marketplace accessible from chat.<br>
--<br>
- As a creator, I want to push my stickers to the market without waiting for approval.
- I want my stickers to be hosted in a decentralized way.
- I want my stickers to be protected from free use/stealing.

`Research questions`:
- What are the pros & cons of implementing as an extension vs. native feature?
- Does one smart contract handle...?
    - Price setting
    - Payment from users
    - Payout to creators
- Which audience are we designing these stickers for? How should character design be informed?
- What's the cost to commission 1-3 initial sticker packs?
- Sticker usage:
    - How many sets do people own on average?
    - How many do they use?
    - What makes certain characters popular?
    - etc.

## Specification

## Implementation
### 21st January Update
- Finalizing specs for registry contract
- Basic UI POC 

### 4th February Update
- Finalized specs
- Contract implemented and deployed on Ropsten
- Awaiting audit info
- First stage of MVP UI merged
- In talks with sticker illustrators




## Maintenance

## Copyright
Copyright and related rights waived via CC0.
