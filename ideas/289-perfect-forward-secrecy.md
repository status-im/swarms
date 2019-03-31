---
id: 289-perfect-forward-secrecy
title: Perfect Forward Secrecy
status: Active
created: 2018-07-23
category: core
lead-contributor: cammellos
contributors:
    - yenda
    - pedro
exit-criteria: yes
success-metrics: no
clear-roles: no
future-iteration: no
roles-needed:
    - QA
    - Clojure dev
    - Go dev
    - UX designer
okrs:
  - "[P0]: Objective: Reduce our wall of shame"
  - "[P0]: KR: Implement perfect forward secrecy for chat, including draft of a formal spec"
---

## Preamble

    Idea: 289
    Title: Perfect Forward Secrecy
    Status: In Progress
    Created: 2018-07-23

## Summary

Perfect Forward Secrecy (PFS) is a must-have for a secure  messaging application. This swarm aims to implement PFS in Status and proceed to some architecture refactoring to make the communication protocol that is usable as a third-party library.

## Swarm Participants

- Lead Contributor: @cammellos
- Contributor: @yenda
- Contributor: @pedro
- QA:
- UX:

## Product Overview

During the Basel Meetup, we defined PFS as one of the key priorities.

> Forward secrecy protects past sessions against future compromises of secret keys or passwords.

There are two main goals to this swarm: to migrate Status to a PFS implementation and to provide a written specification that can be audited independently.

Ideally the message content structure specification is written in a machine-readable format which can be used to generate client code in a chosen language. Protobuf has been suggested as a candidate (Signal also happens to use it).

The implementation of PFS requires some changes and refactoring of the communication protocol. This swarm aims to add PFS to 1:1 chats. Group chats are currently out of the scope of this swarm.

---
Part of this swarm is comprised of research. Here are some of the questions we must provide answers for:

**Q: How should we describe our protocol in a machine-readable format?**

**A:** > Protobuf seems well-suited because it gives us good support on different languages, JSON conversion, decent performance, and is machine-readable. [Multiformats](https://multiformats.io/) was suggested by @arnetheduck and it supports Protobuf, so that will be investigated as a possibility.

**Q: How will we deal with the transition to PFS for existing clients?**

**A:** The same way that we've been doing migrations in chat so far. That is to say:

- Version `x - 1` reads/publishes old message;
- `x` is able to read old and new message format, publishes in the old format (compatible with `x - 1`);
- `x + 1` is able to read old/new messages format, publishes in the new format (compatible with x, incompatible with < `x`);
- `x + 2` reads new messages/publishes new messages (compatible with `x + 1`, incompatible with < `x + 1`).

**Q: What approach should be taken when a user wants to contact someone but doesn't have a bundle?**

**A:** TODO

Options:

1. Allow sending messages, but until a sucessful exchange they won't have PFS.
1. Force the user to send a contact request first.

---

### Details

#### X3DH

X3DH works by having client apps create a bundle of prekeys (the `X3DH bundle`) that can be requested by other interlocutors when they wish to start a conversation with a given user.

In Signal's specification, a server is typically used to store bundles and allow other users to download them upon request. Given our goal of decentralization, Status cannot rely on the same infrastructure and must achieve the same result using other means (e.g., public chats, one to one, QR codes, contact codes, possibly ENS and eventually [Swarm](https://swarm-guide.readthedocs.io/en/latest/introduction.html) storage when ready). A permanent decentralized storage system like Swarm is the ideal solution for this problem. IPFS is an option - however, it has not been explored very much, and we don't know the requirements regarding bandwidth to run on mobile. More investigation is needed.

Given the uncertainty and the unknowns of the two options above, the strategy is to work around those issues, build a system that works well in a P2P setting without decentralized (or centralized) storage and eventually "close the gap" once we find a suitable decentralized solution.

The idea is that as long as the contact has been discovered or shared through the Status app, the user will have a bundle and PFS can be guaranteed.
In case you don't have a bundle (let's say that you copy and paste the address in Slack and the user has pasted their PK instead of contact code), the initial message will not have forward secrecy but will contain a bundle, and any reply will do.

#### SDK

The inner working of the chat protocol will be moved to [status-go](https://github.com/status-im/status-go), with the exception of the persistence layer, since that is not strictly required for this swarm. Moving the persistence layer can be done at a future stage, perhaps on a separate swarm.

### User Stories

As a user, I want Status to employ PFS so that my past communications are protected even if my secret keys are compromised (mitigation of potential information disclosure).

As a third party developer, I want to be able to use the communication protocol with minimal setup and boilerplate, so that I can create bots or Dapps that use the protocol.

### Requirements & Dependencies

> Are there any bugs or feature requests in other repositories that are part of this
> Idea?

### Security and Privacy Implications

PFS is critical functionality for a secure messenger to reduce the risk of information disclosure. Our implementation should be audited and confirmed as a correct implementation of the Signal Double Ratchet Algorithm (https://signal.org/docs/specifications/doubleratchet/) and X3DH Key Agreement Protocol (https://signal.org/docs/specifications/x3dh/).

## Dates

### Minimum Viable Product

Goal Date: 2018-08-13

Description:

- X3DH and double ratchet implemented on status-go side;
- Bundle is exchanged through public / 1-to-1 chats.

### Iteration 1

Goal Date: 2018-08-27

Description:

- A bundle can be exchanged by QR code;
- Investigate storing bundle on ENS;
- Sessions keys and messages are stored encrypted on device;

### Iteration 2

Goal Date: 2018-09-11

Description:

- Chat primitives are provided as a library.
- A preliminary version of the protocol specification is available.

### Iteration 3

Goal Date: 2018-09-25

Description:

- Investigate UX solution for when bundle is not available

## Success Metrics

Does not apply here

## Exit criteria

- PFS is implemented;
- The communication protocol is specified with schemas for the messages and RFC describing it;
- We provide a library to use our chat primitives.

## Q&A

What does the impact of using a server (X3DH) have on reliability? What happens if a user changes mail server, or it is down?

> We are not relying on mailservers to exchange x3dh bundles and we are allowing users to communicate if no bundle is exchanged, so reliability will not be impacted. Mailserver up/down will not have an effect, will make message/bundle propagation more difficult (only online->online messages will be sent/received), but that impacts the whole system.

What happens if a user is changing device? Recovering account?

> The problem we faced before with account/recovery is that if a shared key is established and the message is sent using a symmetric key through whisper, the user that has recovered the account will not be able to decrypt it.
>
> This is not the case anymore as the receiving user is able to decrypt the header.
>
> If a user receives a message that they're not able to decrypt because they are missing that keyId/conversation, we can prompt the user and say: "X wants to contact you but seems like they are using a key from a different device, do you want to add them to your contacts?"( or something on those lines :) ).
>
> The message contains a bundle so x3dh can be performed if the user decides to reply/add them back to their contacts.

What guarantees do we get in terms of forward secrecy? What makes it PFS as opposed to weak FS?

> PFS if a bundle is exchanged, otherwise a successful message exchange needs to happen to have PFS on both sides, at least in the initial implementation. Key re-use can be guarded against. Regarding weak forward secrecy I would need to think about it a bit more, but as per doc only impersonating future sessions is possible if one of the identity keys is compromised.

What guarantees can we make and not make in terms of deniability?

> If a bundle is exchanged, plausible deniability, otherwise none for the initial message at the protocol level.
Currently, we sign all messages at the whisper layer, so there's no PD. We can change that, but that's a separate problem.

Where you see a formal spec coming out of this, i.e. something other people can implement, and at some point also get peer reviewed?

> The protocol messages (communication between two status peers) will be defined using protobuf so that people can re-use the schema if they wish to do so.
>
> The protocol interactions will be described in a document similar to https://tools.ietf.org/html/rfc6101#section-5.6.3.
>
> The public high-level RPC api can be described again using protobuf including the endpoints https://developers.google.com/discovery/v1/reference/apis, so that you can generate clients programmaticaly from the protobuf files.

What's the rationale behind protobuf?

> There's not really a strong push for protobuf, we just had an informal conversation and it's open to discussion, but why is suited is that it gives us is good support on different languages, JSON conversion, decent performance and is machine-readable.

At what point an audit would make sense. I.e. it is something useful in terms of guarantees, and unlikely to change for some time?

> Provided we are happy with the implementation, there are 2 points where we could have an audit:
>
>1. If we can 100% guarantee that a bundle is exchanged (say that we manage to get Swarm working for example), that is a good time.
>1. If we don't, we can still have a security audit, with different guarantees (PFS if you exchanged a bundle, no PFS until successful interaction, PFS after that)
>
> If we audit at 2) and then we move to 1) the only new bit that would need to be audited is the actual fetching of the bundle from Swarm/etc (which is not part of the protocol btw, it's just another way to retrieve a bundle), as we would be completely disable non-PFS first messages, so the protocol would not be changed other than removing stuff.

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
