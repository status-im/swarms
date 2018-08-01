---
id: 292-decouple-whisper-wallet-keys
title: Decouple whisper key from wallet key
status: draft
created: 2018-08-01
category: core
lead-contributor: pilu (Andrea Franz)
contributors:
    - cammellos
exit-criteria: no
success-metrics: no
clear-roles: no
future-iteration: no
roles-needed:
    - QA
    - PM
    - UXR
    - Clojure dev
    - Go dev
    - Designer
    - Community
okrs:
    -
    -
---

## Preamble

Idea: 292
Title: Decouple whisper key from wallet key
Status: Draft
Created: 2018-08-01

## Summary

For security and privacy reasons, we want to decouple the whisper key from the wallet key,  so that users don't expose their Ethereum address while chatting in one-to-one and public chats.

## Swarm Participants

> Here all roles in swarm are defined and filled, one of the contributors should
> responsibility of the Idea as Lead.
>
> Lead Contributor is the Owner of the Idea. If required, they can get support
> from a PM, but should be responsible for end to end execution of the Idea.
> This includes ensuring appropriate resources are allocated, setting realistic
> timelines and milestones, and any post-launch metrics or bug fixes that are
> attributed to the Idea
>
> A swarm requires at minimum 3 contributors. For user-facing swarms
> PM/UX(R)/Eng functions have to be present.
>
> For swarms lead by core contributors, swarm lead is evaluator by default.
>
> 'Contributor' should be replaced with a descriptive role type.

- Lead Contributor: [@pilu](https://github.com/pilu)
- Contributor: [@cammellos](https://github.com/cammellos)
- Evaluator (defaults to lead contributor):
- Contributor:
- Contributor:
- QA:
- PM (required for user-facing):
- UX(R) (required for user-facing swarms):

## Product Overview

In the current implementation, the same key pair is used for the whisper identity and the wallet.
The Status contact code is an uncompressed public key, and users share it with other people to be contacted.
In public chats, anyone can see the public key of a user by clicking on  the avatar near the message.

### Problem

Since the whisper key pair is the same that we use for the wallet, it means that from the Status contact code, anyone can derive the wallet address and easily check a user's balance and transaction history.
Any user with a fair amount of value in their wallet can be target of phishing attacks, especially in public chats where any malicious user can track the wallets of all the active users.

### Technical solution

Status already implements a Hierarchical Deterministic wallet (HD Wallet) that allows us to derive multiple determinist keys from the same 12 mnemonic words.
For the wallet keys, we can continue to use the current derivation path, which is the one described by BIP44: `m/44'/60'/0'/0/0`.
We can then extend the key store structure to have an additional key used for the whisper identity and derived with a different derivation path that needs to be decided.

### Changes in the chat/wallet flow

In the current implementation, users can send ETH/SNT via the chat without asking the wallet address of the recipient, since it can be easily derived from the chat contact code, which is the public key.
If we add a different key for the chat/whisper identity, we need to implement a protocol such that user A need to request the address of user B before being able to start a transaction. User B can decide to approve the request and reveal or not the wallet address.

### Compatibility

The key pair used for the wallet will remain the same, so the wallet address won't change.

The chat contact will change so after the upgrade, users will need to exchange their contact again to be able to chat.

### Problems to solve for old clients

1 -  user A is using an old client
2 -  user B is using a new client
3 -  user A is chatting with user B and sends a transaction from the chat
4 -  the transaction from the old client will be sent to the address derived from the chat contact code of user B
5 - user B won't see the transaction in the wallet because the wallet address is derived from a different key.

(funds are not really lost since the chat key is still a valid ethereum key)

### User Stories

TODO

> What user stories are you solving?

### Requirements & Dependencies

TODO

> Are there bugs or feature requests in other repositories that are part of this
> Idea?

### Security and Privacy Implications

TODO

> If the security and privacy implications of the idea are non-trivial,
> elaborate on the problem space and a plan for resolving it here.

## Dates

> Description of deliverables at a given date, for example each Town Hall (default).
> Add more iterations as required.
>
> Evaluator accepts responsbility to checkin at Goal dates, forces discussion to
> continue implementation or recommend disband and post-mortem.
>
> Upcoming Town Halls this quarter:
> 2018-04-23, 2018-05-07, 2018-05-21, 2018-06-04, 2018-06-18

### Minimum Viable Product

TODO

> Mandatory, completes the Idea in the fastest route possible, can be hacky,
> needed to feel progress. See https://imgur.com/a/HVlw3

Goal Date:

Description:

### Iteration 1

Goal Date:

Description:

## Success Metrics

TODO

> Assuming the idea ships, what would success look like? What are the most
> important metrics that you would move?
>
> Example: Onboarding conversion rate. Target >30% full funnel

## Exit criteria

TODO

> Example: Launch new onboarding UI flow

## Supporting Role Communication

TODO

> Once Requirements and Goals are fleshed out, then it should be communicated to
> supporting organelles if required

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

