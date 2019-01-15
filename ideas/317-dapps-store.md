---
id: #317-dapps-store
title: DApps Store
status: research
lead-contributor: Andy
contributors:
    - Andy
    - Ricardo (smart contracts)
    - Andrei (design)
    - Julien (Clojure help, mostly to remove current code)
budget:
- actual: xxx
- estimate: yyy
- currency: ETH
---


DApps Store Swarm Proposal
=

## Summary and Goals

The DApp Store swarm will deliver SNT based curation mechanisms in accordance with the white paper. Our first goal is to build the store as a web DApp and design it in such a way that it solves our first few user stories about being able to navigate the store easily, discover new DApps, and have an up-to-date list of DApps that are currently popular/being used.

The aim is to write the smart contracts that will control the economic mechanism in as general a way as possible so that they can be used for the curation of any arbitray data type, whether that represents a DApp, a sticker pack or anything else which we might want to open up to community curation, rather than Status centralization.

## Contributors

- Andy
- Ricardo
- Andrei
- Julien

(+ Janitor swarm)

## Communication

`status channel`: #317-dapps-store
`sync schedule`: weekly

`Meeting notes`: 

## Research

`Timebox`: wrap by 31/01

By the end of Jan, the work can be split into parallel streams where redesign of the current browsing experience on the UI side moves to specification, while topics that require more research (curation mechanism) remain in the research phase.

`Previous work`: 

DApps are currently exposed as a static catalog hardcoded in Status client.
Previous versions of Status relied on a basic discovery protocol to discover new DApps.

1. [Discover - What it is and How it Works](https://docs.google.com/document/d/1PC4Qu_5qw0OssDptiDiV3qkxkVfaG1DGVHMY7FAy7EM/edit)
2. [Discover Exchange Protocol](https://docs.google.com/document/d/1MQRcv1BmMSl08by7VLGaQArXV-z467PtkwyRpVs7Ok8/edit)
3. [Discover - Open Questions](https://docs.google.com/document/d/1J-mZewaD_jOs06m0ljIs-wooL-Tux9bjWI8-mcFQp3o/edit)

---

[State of the DApps](https://www.stateofthedapps.com/) is an existing curated list of DApps which we could use as a means of showing off the most popular DApps across the network. It would involve an API call, which we generally try to stay away from, but if it is one of many options, the API becoming inaccessible would not break the application as a whole nor remove entirely the functionality of the DApp Store specifically, so it's probably not a bad option to include froma UX perspective in the first iterations of this. We have also spoken at length to [DAppist](https://discuss.status.im/t/curating-dapps-in-status/435) and there are other good teams such as [OpenSea](https://opensea.io/) and others also working on this problem (in tandem with figuring out how to curate ERC-721s and other such things).

Andy [proposed](https://discuss.status.im/t/how-to-curate-dapps-simply/759) a bonded curve based curation mechanism. You can watch the [video here](https://www.youtube.com/watch?v=82wMcgHSej0).

### Intial Spec

#### Version 1

1. A new option in the global navigation for DApps, rather than mixing them in with chats on the home screen. This is currently one of the item in the #Core backlog and @andytudhope to communicate with @igorm about implementation and dates.
2. DApp Store to be designed & built as a separate web DApp based on feedback from @jarradhope @jeluard @admironov @hesterbruikman and others, as will be the case for the Sticker Market.
2. Parallel to changing the global nav bar, design work to be delivered by 15/02/2019 for intial DApp Store.
    1. This will solve the first 2 User Stories below - being able to browse easily interesting DApps, and being able to see new content regularly.
    2. The basic idea is still to show the current categories we have: `Exchanges`, `Marketplaces`, `Fun and Games`, `Social Networks`, `Media` and `Utilities` (though these are up for discussion with designers), but organise them in a more attractive and easily-browsable fashion.
    3. We also need to begin to train users to use filters to organise what is displayed to them according to their preferences (before we are ready to introduce smart contract based curation and Discovery). So, part of the design spec for v1 is to include two, very simple filters: one reliant only on Status for `Most Recently Used`; and one which calls some API(s) to get a list of the `Most Popular` and `Trending` DApps across Ethereum. Once a filter is selected, we need not show the categories on the "Home" page of the DApp Store (though this is also up for design discussion).
    The thinking here is that relying on an API (could be StateOfTheDapps, OpenSea, Dappist, all of the above, etc.) is not too bad if it is one of multiple options and if it being unavailable doesn't break entirely the functioning of the store.
    4. Note the point in User Story 1 about thinking of ways in the design to make it clearer that there is a chat/community directly behind each DApp, using the global whisper topic made from the DApp's name. I think this is a powerful feature we could really try and emphasise so that more already existant communities begin to use Status rather than Telegram/Rocket Chat etc.

#### Version 2

1. Add an `Editorial` or `User Reviews` section to the DApp store, much like Apple recently added. Here, we can incentivise users to submit good feedback about DApps, or well-known "celebs" to share curated lists of their favourite DApps; most interesting (or worst/most scammy) ICOs; most liquid (or cheapest) exchanges; most fun games etc. Research on this can take place in parallel, but it would likely be the simplest possible incentivization mechanism: user's pay some fee defined by whoever creates the editorial/curated list directly to them (though routed through a simple contract for access-control) in order to access their list. No middlemen, no hidden fees/complexity.
2. Implement smart contract based curation of DApps. Hopefully, all this means from a design perspective is adding a `balance` beneath each DApp and some up/down vote `carrots` to the right of it. Delivery dates depend heavily on research and final smart contracts though.
3. @andytudhope to work with @3esmit on smart contract research and design until at least 15/02/2019, the general aim being to write contracts that can handle _curation in general_. That is, we should try and build our contracts in such a way that they can be used to curate any arbitrary data type, whether it be a DApp or a sticker pack, or whatever else we feel could benefit from community curation.
4. Both to work with @corpetty on making sure that the spec for smart contracts is easily auditable and follows all the best practices being worked on by ethsecurity.
4. Editorials/curated lists likely added as a separte page, but navigated to through filter list, which also has `SNT curation` as an option.

#### Version N

1. Replace the APIs used for `Trending` and `Most Popular` with data from some form of discovery using our as-yet-to-be-defined new protocol/data sync layer so that you can build a social graph out of nodes near/interesting to you and figure out (without compromising anonymity) what they are discussing/using most.

### User stories:
The user stories below need to be detailed and prioritized following the research phase. 

**As a Status user:**
1. I want to easily browse interesting DApps (Design, v1. There is also the chance to make it much clearer that each DApp has a open chat/community behind it. I think this should be considered and surfaced more in the design too).
    - The key question here is what defines `interesting`. The filtering options defined above in the various iterations are meant as the answer to this. That is, we don't answer it, but rather let people decide for themselves what they find interesting/relevant, using as many or as few filters as they like. This means that the emphasis will be on creating as many non-correlated filters as we possibly can, rather than debating what the mythical "average user" will find useful.
2. I want to see new DApps frequently (Design, potential use of an API (gasp)?, v1)
3. I want to see old unusable DApps removed. (This is like proving a negative, I don't think it can be done).
4. I want to be confident a DApp is usable / not a scam (Achieved bestwith economic curation mechanism, requires smart contracts, v2. Having an `Editorial` section will also likely help though.)
5. I want to be able to propose a DApp for inclusion (Requires smart contracts, v2).
6. I want to vote for a DApp inclusion (Requires smart contracts, v2).

--

**As a DApp developer:**
- I want to be able to propose my DApp for inclusion.
- I want to vote for my DApp inclusion.

### Research questions:

Below are topics to be addressed in the research phase.

**1. What are appropriate incentivization mechanisms? (e.g. Game theory exploration)**

This is the first question for a lot of folks thinking about curation, but it is fundamentally flawed, imo. The assumption behind it is: because we can't curate lists ourselves as an organization, let's farm that work out to the community and incentivise them with some kind of token to do it for us. However, there are 2 major issues with this.
    1. The point of mechanism design is to build systems where power does not accumulate in any one place/that have no single point of failure - **including the community**.
    2. It will lead to end users having hundreds of different tokens in their wallets, each of which require unique actions on chain for different projects and will quickly become impossible to track. Users have no incentive to curate the links that appear first in their Google searches (and likely do not want to ever have to think about that). Google wants to ensure those links are relevant, but are also incentivised to place ads above and to the right of them in order to boost their revenue. We want to build a system where the incentives are more closely aligned between platform builders and developers/advertisers, and make sure the users simply benefit as a side-effect of those better-aligned mechanisms.


**2. What is the best way to implement a DApp store given user and business requirements (w.r.t. liability and upgradability)?**

1. User requirements: I do not want to have to track a unique token that requires actions from me on chain in order to curate DApps or stickers or anything else in Status. It is too much mental overhead - I just want to see interesting and new DApps regularly, get a sense of which ones are being used the most, and have easy access to a list of the DApps I use most often myself. That said, if DApps are being curated, I want to be able to see and understand at a glance how that is happening and why different DApps appear where they do (and, if I feel **really strongly** about it, I want to be able to affect those rankings).
2. Business requirements: Need some input here from @jarradhope @hesterbruikman and anyone else willing to pitch in.

**3. What is the most efficient and effective development strategy given the outcome of 2? (bounty to attract team, required level of support by core contributors)**

Given the highly constrained resources available for this swarm, it's fairly clear that most of the work will need to happen through bounties. It may well be worth experimenting with different kinds of bounties, like engaging a separate team to build out some of the simulations for the curation mechanism we settle on, but that's likely to happen in a fairly ad hoc way. It's also clear that CCs are not going to contribute much to this one: Julien is willing to remove the code for the old DApp store, but can't commit much further to anything given his own time constraints. The same concerns apply to Andrei and how much time he will actually have to work on this given everything else he is doing.

**4. What are appropriate ranking mechanisms?**

[Bonded curves](https://blog.relevant.community/bonding-curves-in-depth-intuition-parametrization-d3905a681e0a) seem to be the best mechanism for this kind of work. We do not need a full-blown Token Curated Registry, but bonding votes to SNT certainly seems like the simplest and most effective way of achieving our goal. The exact shape and kind of curve we used is something Ricardo and Andy are still researching (i.e. both parameters and kind of curve: exponential vs. sigmoid vs. ?)

**5. What are appropriate mechanisms for user involvement in this ranking (4)?**

User involvement needs to be minimal! Otherwise we violate user expectations and introduce them to yet something else they have to understand in an already-complicated and quite intimidating application. We want things to be easy for users, while allowing them the kind of access and influence they desire to have if they are willing to go up the learning curve (though going up that curve also needs to be an active choice they make, not a requirement of using the system at all). A bonded curve does give them the opportunity to vote and effect the rankings (either downvoting a DApp they dislike or donating directly to, and protecting the ranking of, their favourite DApp), but they do not need to just to enjoy a well-curated list and discover new and interesting DApps.

**6. How can new DApps be included in the browse and search experience? (e.g. submission, registration, adding, curation by committee).**

With a bonded curve, it is quite simply a case of sending a transaction with the relevant information to a smart contract. If we have other parts of the store which use the StateofTheDapps API (or similar), then getting to the top of those sorts of rankings is also a way to be included. DApps could also be "discovered" on the network by looking at what channels/hashtags are trending and what nodes close to you on the social graph are mentioning most often, but I do not understand this well enough and sense it will be left for a much later iteration.

**7. What are different visual interfaces that can support a browse and search experience? (design exploration)**

This is really for Andrei to answer, and will form the bulk of the work for v1 (which need not even contain any smart contracts). Simply organising the store better and providing a few different ways of browsing through/finding new and different DApps is entirely a Design problem, which we should look to solve first before adding smart contracts (which will need to be tested & audited etc.) to the mix. Obviously, a lot of the work can happen in parallel, but a new design is easier to settle on then new contracts on mainnet, and the auditing and security concerns those raise.

**8. What position/'status' should Status DApps have in it's own store?**

Once we implement an economic curation mechanism, this question should be answered entirely by that mechanism, not by us. We also need to build and market more aggressively some Status Dapps (apart from Quadratic Voting and ENS Usernames).

## Specification

## Implementation

## Maintenance

## Copyright

Copyright and related rights waived via CC0.
