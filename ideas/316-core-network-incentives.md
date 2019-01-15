---
id: #316-core-network-incentives
title: Core Network Incentives
status: research
contributors:
    - igor
    - andrea mp
budget:
- actual: xxx
- estimate: yyy
- currency: ETH/USD/SNT
---

# Core Networking Swarm proposal

## Summary and Goal(s)

Research and develop framework and incentivization structure for people
deploying and using Status nodes according to [the whitepaper](https://status.im/whitepaper.pdf).

One important vision aspect is that the app continues to work if all nodes in Status-hosted cluster is down.

### 1. Offline messaging

This one is the primary topic of research.

The goal is:
* to give the ability for the people ("providers") to run and provide offline messaging to users of the Status app.
    - cryptoeconomic incentives (SNT use-case);
    - lowering the boundaries to install status node (docs, install scripts, etc);

* to users of the Status app to discover and use offline messaging nodes from providers.
    - receiving messages reliabily;
    - being able to choose the best mailservers and knowing the compromises.

* preserve security and privacy;


### 2. Push Notifications [stretch goal]

Distributed push-notification market. Researching ways on how can users pick PN providers.



### Additional contributors
- oskarth
- dmitrys
- andrei m (design)
- a smart contract dev

## Communication
(required)
`status channel (same as swarm id)`: [#316-core-network-incentives](https://get.status.im/chat/public/316-core-network-incentives)
`sync frequency`: Weekly Sync Mondays, 11:00 CET
`document`: https://notes.status.im/2ogTGMkqRwC7VMcGh9mBdA

## Research
(required) 
`timebox research (approx)` 
Research deadline: January 31th

(optional)
`eips`, `competitors`, `existing research`, `wireframes`, `spike (PoC)`
https://1337alliance.com/
https://github.com/status-im/swarms/tree/master/ideas/168-paid-master-nodes
https://status.im/whitepaper.pdf
protocol work and leveraging data sync data, eg

### Weekly Goals
#### W03-19
timebox: Jan 21

widen research to include protocols different than Whisper and our current infra

outcomes:

#### W02-19
timebox: Jan 14

initial research phase

outcomes:
https://hackmd.io/WwDneHimRj2Oqwnjb9uG6A
https://hackmd.io/s/r1ZawmIf4


#### W51-18 Problems/Ideation
timebox: Dec, 21

- trying to figure out which users and Status problems we can solve by users running Status nodes

participants: 
- igorm
- andrea mp
- andrei m

outcome:
- ideas written in https://notes.status.im/2ogTGMkqRwC7VMcGh9mBdA
- discussion on Dec, 21


### 1. Offline Messaging

The goal of this research is to research the ways on how people can run Status
nodes and how we can guarantee good behaviour in the network.

Areas of research:
- viability of ideas;
- cryptoeconomics and incentivization for good behaviour;
- security and privacy aspects;
- UX research for both discovering nodes providing archives and running them;
- MVP and transition using the current protocol;
- risks assesments (what are known risks and unknown risks in implementing this
    idea).

Outcomes:
- a document with the full research;
- a document with MVP proposal;
- list of risks for implementation;
- (optional) a few PoCs;

### 2. Push notifications

Areas of research:
- viability of ideas and their techincal implementation;
- cryptoeconomics and incentivization for good behaviour;
- security and privacy aspects;
- UX research for both discovering PN providers and hosting them;
- MVP and transition using the current protocol;
- risks assesments (what are known risks and unknown risks in implementing this
    idea).

Outcomes:
- a document with the full research;
- a document with MVP proposal;
- list of risks for implementation;
- (optional) a few PoCs;

## Specification

> do after `Research`

(required)
`timebox specification (approx)`

(optional)
`user stories`, `architecture`, `designs`, `PoC`

## Implementation

(required)
`timebox implementation (approx)`

> do after `Specification`

> All swarm contributors should test and break the implementation, especially developers

(required)
`document progress`

(optional)
`townhall demo`

## Maintenance

`lead-contributor`,`post-mortems`

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

