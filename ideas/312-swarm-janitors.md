---
id: #312-janitors
title: Swarm Janitors
status: research
lead-contributor: jarrad 
contributors:
    - nabil
    - oskar
    - hester
    - rachel
budget:
- actual: xxx
- estimate: yyy
- currency: ETH
---

# Swarm proposal

## Summary and Goal(s)
The Status Janitors oversee the delivery and completion of the [Status white paper](https://status.im/whitepaper.pdf) by the end of Q1, with a hard deadline of the end of Q2 2019.

## Communication
(required)
`status channel (same as swarm id)`: [#312-janitors](https://get.status.im/chat/public/312-janitors)
`sync frequency`: Weekly Sync, Monday 10am UTC

Meeting notes: https://notes.status.im/384OqZPUR1-viP7l2Fxeew?edit

## Research
Completion by the 17th December (one week)

Goals of Specifications:
- Swarm Framework
- Define critical path for completing the swarm goal
    - SNT utility swarms
    - Identify essential non-SNT swarms (e.g. onboarding, product teams)
    - https://notes.status.im/critical-path - started here / Oskar
- Report organisational progress regularly during Town Hall
- Regular check-ins with swarms

_Unknowns_
* Security audit timing
    * [NN] What do we want to audit? Our entire codebase? status-go and our smart contracts only? status-react? DApps should probably have their own securit audit (TN and DAO)
* Launch (i.e. public app store) release scope
    * [NN] Can be determined once we see the critical path
    * [OT] Checking with Corey as well
* Software for process management
    * Resource allocation to get swarm cost
    * Global view of state
    * Critical path
    * Monte Carlo simulations

## Specification

**Timeline** 15th Jan to complete specifications of all > P2 features below.
**Swarm Framework**: https://github.com/status-im/swarms
**SNT Utility Swarms**:
* Teller Network [P0] (Iuri and co + Wallet for hooks)
* Tribute to Talk [P0] (Chat swarm)
    * Anti-spam [P2]
* Sticker Market [P0] (Extensions)
* Network Incentivisation [P1] (Core)
-- [OT] With this, do we mean a possibly half-baked solution assuming the existing protocol? One concern would be if we change things around later on, but we can also provide this and clarify it isn't great and will likely be replaced. It depends on how much weight we put on ticking off boxes in whitepaper.
* DApp store / Discover [P1] (Andy/DevRel)
* User acquisition engine [P2]
* Web of Trust / Trustlines [P3]

-- Get legal guidance on what is acceptable for completion of the White Paper --

**Essential Swarms**:
1. DAO (Iuri and co)
2. Onboarding/Patient Zero/Polish (Core/Relevant teams)
3. Status Protocol (Oskar and co)

**Team Structures**
- Core (Igor)
- Chat (Eric)
- Wallet (Goran)
- DApp browser (Julien)
- Desktop (?)
- Keycard (Guy-Louis)

## Implementation
**Timeline**: 
* Soft deadline - EOQ1 2019
* Hard deadline - EOQ2 2019

> All swarm contributors should test and break the implementation, especially developers

For above swarms to be in research phase: https://github.com/status-im/swarms/issues/338

(required)
`document progress`

(optional)
`townhall demo`

## Maintenance

`lead-contributor`,`post-mortems`

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
