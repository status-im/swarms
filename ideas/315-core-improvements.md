---
id: #313-core-improvements
title: Core Improvements Swarm
status: research
lead contributor: igor
contributors:
    - adam
    - dmitry s
    - roman
    - pedro
budget:
- actual: xxx
- estimate: yyy
- currency: ETH/USD/SNT
---

# Core Improvements Swarm

## Summary and Goal(s)

Status Core Improvements swarm's goal is the preparation of Status Mobile Client to be released publicly (AppStore/GP release tracks).

A few key areas that we need to focus on:

* all the critical security and privacy issues are resolved (including audit);
    - a security and privacy document is delivered (it lists guarantees we make around security and privacy; as well as ways we are falling short)

* all the critical tech debt issues are resolved;
* key UX problems are solved in two areas:
    - adoption issues;
    - retention issues.

The work includes releasing internal "dogfood" builds as well as betas in preparation to the public release.

### Additional contributors
- Andrea MP
- Andrei M (Design)
- Serhy/Anna/Nastya(QA)
- Rachel/Hester (PO)

## Communication
(required)
`status channel (same as Core Team)`: [`#status-core`](https://get.status.im/chat/public/status-core)
`sync frequency`: Weekly Sync Mondays, 10:00 CET (the regular "Core Team" standup)
`meeting notes`: [this running doc on notes.status.im](https://notes.status.im/sm7x7tPpQESkRwu7YNFzSQ)

# Research

### 0. Meta (what this team will be doing?)

Completion by December, 19th (1 week)

Goals:
- Figure out the list of tasks and top UX issues that needs to be fixed
- Rank them by priority (what should we do first)

### 3. Improve Security using native views

Completion by 21/12/2018

Goals:
- Figure out how we can use native code (Java/ObjC) to short-circuit sensitive text views
    to Status-Go, so attacks like [event-stream incident](https://blog.npmjs.org/post/180565383195/details-about-the-event-stream-incident) are impossible.

## Specification

### 2. "Save Password" on Android

* Timeline - January, 14th

The goal is to achieve feature-parity between iOS and Android in terms of
storing the password.

Epic: https://github.com/status-im/status-react/issues/5793

- [ ] Threat modelling (STRIDE) + document about that.

## Implementation

### 0. Meta
* Timeline - EOQ2 2019, continuous process. Each backlog item discovered by
    research will have it's own deadline.

Setup a regular meetings with the stakeholders to adjust the backlog.

`document progress` - keep the backlog and the state up to date with this
document.

Projects from should be put in the correct state to see the progress, etc.

### 1. Message Reliability Improvements

* Timeline - January, 11

The goal of this project is:

* to make messaging extremely reliable;
* to be able to prove that;
* to be able to show that information to a user (especially it is important to
    communicate if the message isn't delivered).

`document progress`: see the epic https://github.com/status-im/status-react/issues/6757

### 2. "Save Password" on Android

* Timeline - January, 21th

Epic: https://github.com/status-im/status-react/issues/5793

- [ ] Implement according to the spec
- [ ] Audit the implementation

## Maintenance

### 1. Battery usage

### 2. Application performance profiling

### 3. Mobile Releases

- [Mobile release guide](https://notes.status.im/mobile-release-guide)
- [Mobile release notes](https://notes.status.im/mobile-release-notes)
- Upgrade policy
    * *User’s data.* User should be able to successfully upgrade preserving all his/her data from 0.9.19 to any beta release.
    * *Messaging/Transactions.* User should be able to successfully interact (make transactions, chat, etc) with users that have 0.9.20 or later release.

## Backlog

This backlog is organized in a prioritized way. The higher the project the more important it is.
When promoting the project, it is also important to make it more detailed.

### Improve secure storage of geth private keys

1. Get rid of `react-native-keychain` and it's dependencies.
2. Patch `go-ethereum`, so AndroidKeyStore and iOS KeyChain (+optional Secure Enclave encryption) are used to store private keys.

### Split Whisper and Ethereum keys



### Improved message compatibility with other versions and other clients (using the *current* version of the protocol)

**Problems**
1. It is too easy to change protocol (message format, etc) in a PR w/o necessary oversight.
2. There are no tests to detect that message format or semantics didn't change after PR is merged.
3. We don't have any procedures and best practices on how to introduce changes to the current protocol.
4. We don't have any procedures and best practices on how to handle breaking changes gracefully and coordinate them between the clients.
5. We don't have any procedures, tools and best practices to handle breaking changes in mailservers.

### Spam filtering & DDoS Protection

We lack the way of protecting our network from spam, especially on the network
layer where a bot can relatively easily spam channels or at least waste users'
traffic.

### Reproducible builds

**Problems**
1. Right now it's hard to tell exactly which commit of any dependency was used to build a particular release
2. Users don't have guarantees that the release they downloaded matches the official release (i.e. hasn't been tampered with).
3. A user should be able to build the sources on his own machine and obtain exactly the same binaries. 


### Reduce unnecessary bandwidth usage

https://github.com/status-im/status-go/issues/1266

Make sure that we identify and fix all the unnecessary bandwidth usage cases. We need to be able to test the usage regressions in the future, so these issues don't happen anymore.

Currently, it looks like our application uses too much bandwidth.

**Why?**

1. We don't have bandwidth tests in place.
2. Mailserver requests seems to be very expensive in bandwidth and we probably receive a lot of duplicate messages.
3. We don't know all the places where networking is used, so we can't measure bandwidth client-side (we have to only rely on iOS/Android settings to check that).

### Improve mechanisms of storing/using sensitive information on mobile

**Problems in this area**

1. It is possible (and it happened before) to leak sensitive data through logs and debugging information.
2. Unsafe defaults in some publicly available builds in the application.
3. Sensitive information is used directly (accessible to most of the app components), whereas the best practices is to provide minimal APIs to do whatever needs to be done w/o exposing data (see Secure Enclave data signing)
4. (potentially) Storing sensitive information which we don't have to store.


### Support LES and ULC

Add an option to use LES and ULC in our application. It should work on Ropsten and Mainnet with working discovery.

Status can host clusters for LES and ULC, for both testing and reliability purposes, but the usage of LES/ULC shouldn't be limited to that.

See more and up-to-date info in the Epic: https://github.com/status-im/status-react/issues/6905

### Reduce metadata leakage

### Audited private group chat and PFS

### Integrate with `libp2p`

### Better discovery

1. Support/integrate geth initiatives

### Be able to update bootnodes list if they are blocked

1. Being able to update bootnodes list if they are blocked

### Push Notifications v2

https://ideas.status.im/ideas/086-push-notif-v2/README

### LES/ULC: Economic incentives

> [dmitry] is it about proposal from Jacek?
> [igorm] probably, I'm not sure. it isn't the priority unless LES/ULC is just functional.

### VipNode support


### Implement EIP-681
https://eips.ethereum.org/EIPS/eip-681

> A standard way of representing various transactions, especially payment requests in Ethers and ERC #20 tokens as URLs.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).


