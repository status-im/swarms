---
id: #311-wallet
title: Wallet Swarm
status: implementation
lead-contributor: Goran - Clojure
contributors:
- Nastya - QA
- Tanya - QA 
- Patrick - UXR
- Denis - UX
- Rachel - PM
budget:
- actual: xxx
- estimate: yyy
- currency: ETH/USD/SNT
---

# Wallet Swarm

## Summary and Goal(s)

The Wallet swarm focuses on the Wallet tab within Status, and related transaction actions throughout the app, such as in Chat with `/send ETH 0.5`.

### Problem

> What problem are you solving? Who are you solving this for?

Status Wallet facilitates ethereum usage and transactions, but does not offer a compelling reason for users to download and open the app.  Our research ([July ‘18](https://docs.google.com/presentation/d/1eJP-Hh4tN6XZREIy73GNuJP1LqGg41EvP5QpVlFZQ78/edit#slide=id.g3e1b33ca7e_2_36), [June '14](https://docs.google.com/presentation/d/11vEgAbZgXvCwiS2QdMmW3vjOBApx5y8ARXNbFLyJBuk/edit#slide=id.g3beee3ddf4_0_0)) has shown there are two main problems that prevent wallet usage:

- Usability issues that prevent simple transaction and erode trust
  - Usability issues of our wallet specifically (e.g. how much am I sending, what is the value in fiat when sending via wallet and via chat)
  - Usability issues of Ethereum itself (e.g. what does it mean 5 confirmations, was it sent or now? what is gas?)
 
- Lack of killer features that drive adoption
  - Lack of a goal-driven interaction flow. E.g. buy SNT/Cryptokitty
  - For non crypto users; a lack of introduction or guidance. “I'll look into that later because I don't know what I'm doing.” E.g. what would a gentle transition from a DApp to wallet look like.

### Why

> Will solving this problem advance the goals of Status and adhere to its principles?

Status aims to be a gateway to ethereum, and wallet and transactions are at the core of this ambition. Many aspects of the Status vision including the whitepaper depend on a functioning wallet that is secure, private, and easy to use, therefore it is important that Wallet creates a core foundation of usability and delight through best-in-class UI and compelling features.

Furthermore, the central Wallet feature - transaction signing - is essential for dapp usage within Status , and vice versa.

Solving usability bottlenecks and introducing killer features that give users a reason to open Status will ensure that Status drives adoption and will unblock more advanced use cases outlined in the whitepaper and beyond.

### Success Criteria

> How will we know when this problem has been addressed? What are qual and quant metrics that will help evaluate?

Success for wallet is having the best mobile user experience for transactions, is super easy to use, offers compelling features, and is the best way to easily get tokens.  A fun onboarding experience is essential to give new users something to do and people to connect with.

- 80%+ of UXR subjects report a positive experience when transacting
- 5+ organic reports of users using Status for transactions (eg tweets, sightings, etc)
- 3+ way for users to acquire tokens


## Communication

- `status channel`: [#status-core-wallet](https://get.status.im/chat/public/status-core-wallet)
- `sync frequency`: Weekly Sync
- Github:
  - Project boards
    - [Wallet epic project board](https://github.com/orgs/status-im/projects/48)
    - [Maintenance project board](https://github.com/orgs/status-im/projects/24)
  - Label: [wallet](https://github.com/status-im/status-react/labels/wallet)
  
## Projects 

### Wallet redesign

Fix usability issues and create meaningful improvements with regard to interaction patterns, feedback, labeling and copy of the current flows.
Epic: [#6921](https://github.com/status-im/status-react/issues/6921)

Status: Implementation

#### Research & Specification

UXR already done.
Designs based on research already done - https://www.figma.com/file/SIeZPHvrX7KUwEBW8VQct8C5/WIP_New-send-transaction?node-id=0%3A1

#### Implementation

`(timebox 2 weeks)`


### Custom ERC20 Tokens

Let users control their own wallet and add any erc20 token they possess. Currently Status only supports a limited fixed list which is manually maintained by core contributors.
Epic: [#6939](https://github.com/status-im/status-react/issues/6939)

Status: Specification

#### Research & Specification

UXR already done.
Designs based on research already done - https://www.figma.com/file/XUehMnhyD1FGcWzvGz6SXqvh/Mobile-wallet?node-id=160%3A3954

#### Implementation



### Functional Transaction/Transfer History


Status depends on Etherscan API to display ethereum transactions and it depends on Infura to display ERC-20 token transfers.
Epic: [#6940](https://github.com/status-im/status-react/issues/6940)

Status: Research

#### Research 

`(timebox 5 days)`

#### Specification

`(timebox 1 day)`

#### Implementation

`?`

### Address Validity

Implement EIP-55
Epic: [#6941](https://github.com/status-im/status-react/issues/6941)

Status: Research

#### Research

`(timebox 1 day)`

Research [EIP-55](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-55.md)

#### Specification

`(timebox 1 day)`

#### Implementation 

`(timebox 1 day)`

### Ethereum Links and QRs

Implement EIP-681 and EIP-831 to facilitate easy and standards-compliant transfers
Status: Research

#### Research

`(timebox 1 day)`

Research [EIP-681](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-681.md) and [EIP-831](https://github.com/ethereum/EIPs/blob/master/EIPS/eip-831.md)

#### Specification

`(timebox 1 day)`

#### Implementation 

`(timebox 1 day)`


## Maintenance

This effort is continuous and doesn't have any end date or exit criteria (internal security reviews, bugfixing, refactoring, bounties, community engagement).

### Security

Security champions, reviews.

### Bugfixing and refactoring

Standing rule to prioritize critical bugs above any other work until resolved. After the critical fix, there should be a follow up to determine how can the same type of bug be prevented from reoccurring in the future. The action taken could be a refactor, a new kind of automated/manual test case or both.

### Community engagement

Communication activities in primarily in relation to implementation of relevant standard proposals and to community involvement in general.

### Outscoped/Postponed

#### Desktop

Bring wallet to more platforms which can lead to more adoption. Wallet will have feature parity on mobile and desktop.

Epic: [#6297](https://github.com/status-im/status-react/issues/6297)

Status: Design

#### Get Tokens

Help users get tokens by means of credit, teller network, and exchange.

Status: Research

#### Point of Sale

Create a proof of concept that would help merchants use Status to transact.

Status: Research

#### Native Token Swaps
Make it easy for users to swap tokens natively in chat

Status: Research


## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
