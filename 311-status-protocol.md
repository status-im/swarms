---
id: 311-status-protocol
title: Protocol Engineering Swarm
---

# Protocol Engineering Swarm

Draft, 2018-12-01.

## Summary
This swarm will research and develop a set of open protocols that is a
reflection of our [our principles](https://our.status.im/our-principles/).

This set of protocols will as a whole enable the implementation of the Status
whitepaper, and similar use cases, through various clients. Part of the effort
will be about selecting existing protocols and standards, when appropriate, and
part of it will be about developing new protocols to meet our needs.

Initial focus is on providing an anonymous communication protocol, which is
developed in conjunction with other teams in the Web3 / secure communication space.

## Goals

1. Create a set of open protocol(s) for secure communication that reflects our
   principles.

2. Produce an open, independent protocol specification can be audited, tested
   independently and implemented in many languages.

3. Work with other teams in the Ethereum, Web3, decentralized web and secure
   communication space to ensure maximum interoperability and a high quality
   specification that other actors take seriously.

4. Use a layered protocol approach that is mindful and explicit about what it
   requires, what it provides, under what threat models, and with what
   trade-offs.
   
5. Enable implementation of clients to participate in the Status Network, and
   work with teams such as Status Core, to find a graceful path to implement and
   integrate the new set of protocols.

## Requirements

### Weekly progress reports and accessible updates
The swarm will provide weekly updates on research progress, either through this
document, Discuss posts, Town Hall, or similar medium.

The swarm will also periodically post more accessible material to explain the
effort, challenges and trade-offs faced.

### Using a layered and modular approach
This swarm will ensure the the protocols are designed in a layered and modular
fashion. This allows subproblems to be studied and progressing in isolation, as
well giving the ability to swap out components per layer based on needs.

Very rough thinking right now:
- Initial trust establishment (e.g. something like BQP)

- P2P Overlay layer (e.g. something like libp2p)
- Transport privacy layer (e.g. something like Loopix)
- Conversational security layer (e.g. something like BTP)
- Syncing layer (e.g. something like BSP)

- Chat clients (public/private/group chat)

### Team growth and collaboration with other teams
This effort is about creating open specifications, so we need access to a wide
range of specialized skill sets, as well as general consensus among community.
Creating a protocol in isolation would likely lead to a lackluster result.

This swarm will collaborate with Ethereum / Web3 / decentralized web / secure
messaging teams in an attempt to re-use existing work and create protocols
together.

Additionally, this team will involve individuals with relevant expertise.
Ideally individuals who have designed 1-2 open, battle-tested p2p protocols.

### Reflection of our principles

The protocol should be a [reflection](https://our.status.im/tag/our-principles/)
of [our principles](https://our.status.im/our-principles/).

- I. Liberty - enable sovereignty of individuals with things like key
  management, as well as economic freedom, etc, by enabling transaction of funds
  and socio-economic coordination between small groups of people.

- II. Censorship resistance - enable censorship resistance through things like
  pluggable transports, as well as being agnostic to the information being
  transported.

- III. Security - use state-of-the-art technologies, and research new security
  methods and technologies to make strong security guarantees.

- IV. Privacy - protect privacy in communication and transactions, and strive to
  provide right to total anonymity.

- V. Transparency - be open about what we are doing, allow community
  contributions and be clear about trade-offs.

- VI. Openness - specification is open and under a permissive license.

- VII. Decentralization - p2p network, maximizing number of computers/humans who
  can control and use the protocol we are building.

- VIII. Inclusivity - easy to use our protocols, as well as working towards
  interopability with other protocols, and educating users.

- IX. Continuance - network should be incentivized to continue on its own.

- X. Resourcefulness - work with other teams to avoid duplication of effort,
  study prior work deeply to minimize wasted and duplicate effort.

### Anonymous Communication Protocol requirements

The purpose of an anonymous communication (AC) protocol is to ensure metadata
isn’t leaked when messages are communicated between peers. It deals with how
messages are transported, and not what is in them.

This is the inital focus and work has begun together with Web3 Foundation and
Validity Labs. Note that this list of requirements is tentative.

1. Sender Anonymity
2. Receiver Anonymity
3. Sender-Receiver Unlinkability
4. Reasonable Latency
5. Reasonable Bandwidth
6. Adaptable Anonymity
7. Scalable
8. No specialized Services

Up for debate: incentives, network spam, asynchronous messaging.

Additionally, it should be resigned with mobile in mind (internet connection is
unstable and mostly missing, CPU resources are limited, we can't stay in
background for a long time and we are behind very strict firewalls that makes
it hard for NAT to pass through.)

For more details and the latest updates,
see [w3f/messaging](https://github.com/w3f/messaging).

## Budget

Headcount based. Small group.

## Team / contributors

### Status

- Oskar
- <1-2 protocol engineerings>

Review/part-time, pending other commitments:
- Jacek
- Andrea MP
- Corey
- Jarrad

### Anonymous Communication Protocol

- Web3 Foundation
- Status
- Validity Labs
- who else?

## Scope
The above plan is ambitious and the team size is currently limited. It is thus
likely the scope will be limited, at least initially, to ensure solid progress
in the most fruitful direction and avoid scope creep.

Expect the precise scope and requirements to change somewhat as we get more
familiar with the problem domain, and depending on how research and
collaborations with other teams go.

## Milestones

Hard to provide with research, but rough timeline to indicate effort.

### Team formation, initial research, and rough project timeline

#### November 2018 - December 2018

#### Goals:
1. Study state of the art deeply
– includes p2p and networking basic literature
– as well as anonymity/secure p2p specific (Tor, Briar, etc)
2. Sketch out rough layers of concerns
3. Team formation and collaboration with others in the space
4. Do write-up of lessons learned so far
- Consider presentation at TH re landscape and lessons learned

### Data replication/sync layer

#### December 2018 - January 2018

#### Goals
Provide 'in-between layer' that synchronizes data over delay-tolerant p2p
networks.

Core abstraction that we are currently missing in the app and will give us more
freedom going forward, as we implement more chat-like coordination mechanisms,
and make progress on alternative transports like PSS and AC protocol below.

Requires secure transport layer, and provides a way for clients to sync data on
a peer to peer basis. Thinking very much in line with what BSP provides.

Research and specification (protobuf) thereof. Sketch for how to provide with
existing app, and work with Core team to make it into a reality.

### Anonymous Communication Protoocol

More details after conversations with Web3 Foundation etc.

#### December 2018 - March 2018

#### Goals
- Requirements and goals in more details
- Workshop with relevant teams
- Specification that enables theoretical analysis of properties

(- Later: theoretical analysis of properties)
(- Later: viable implementation)

### TBD.

Other pieces here. Underspecified at the moment, but see general goals for
direction. As research effort continues and above milestones are being achieved,
this will be updated.

## Research log

### December 3 - December 9
<CURRENT>

WIP:
- Looking into distributed/replicated state (BSP, protobuf)
- Swarm proposal with rough milestones, clear separation and problem statements, 1 milestone

### November 26 - December 2
- Started awesome secure messaging GH repo: https://github.com/status-im/awesome-secure-messaging
- Looking into distributed state / async messaging, some mixnetwork basics to understand how differ design-wise
- Working with W3F, trying to setup time for workshop
- Also separate Whisper spec effort ongoing

### November 19 - November 25
1. Sketch out requirements doc for anonymous communication protocol
2. Talk with Web3 Foundation and Validity Labs
3. Joint initiative started [here](https://github.com/w3f/messaging)

See here for more details:
https://discuss.status.im/t/protocol-anonymous-communication-requirements-and-brief-update/792

### November 5 - November 18
1. Initial rough proposal based on discussion at Devcon
2. Initial early research orientiation
3. Initial team scoping 

See here for more details: https://discuss.status.im/t/hello-protocol-progress-since-prague/736

## Resources

- [Awesome Secure Messaging](https://github.com/status-im/awesome-secure-messaging)
- [Status Protocol / Swarm Chat](https://get.status.im/chat/public/status-protocol)
- [Riot / Web3 Messaging Chat](https://riot.im/app/#/room/#web3-messaging:matrix.org)
- [Anonymous Communication Protocol](https://github.com/w3f/messaging)

## Copyright

Waived, CC0.
