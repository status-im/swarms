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

### Meta - Done

### Meta (what this team will be doing?)
Backlog is created

### 3. Improve Security using native views - Done
PoC is created for using native views

## Specification

### 2. "Save Password" on Android - Done

Epic: https://github.com/status-im/status-react/issues/5793

## Implementation

### Done

### 0. Meta

* Timeline - EOQ2 2019, continuous process. Each backlog item discovered by research will have it's own deadline.

Setup a regular meetings with the stakeholders to adjust the backlog.

`document progress` - keep the backlog and the state up to date with this
document.

Projects from should be put in the correct state to see the progress, etc.

### 1. Message Reliability Improvements

* Timeline - January, 31

`document progress`: https://www.pivotaltracker.com/epic/show/4178343

+ improving mailservers handling: https://www.pivotaltracker.com/epic/show/4198376

### 2. "Save Password" on Android

* Timeline - January, 31th

`document progress`: https://www.pivotaltracker.com/epic/show/4179882

leftovers:
- 

### 3. Slow sign-in - DONE

### 4. Dependency audit for reproducible builds

* Timeline - January, 25

`document progress`: https://www.pivotaltracker.com/epic/show/4182830

### 5. Fix critical issues with traffic consumption

* Timeline - January, 31
`document progress`: https://www.pivotaltracker.com/epic/show/4182828

### 6. Message compatibility & upgradeability guarantees

* Timeline - March 1st 
`document progress`: https://www.pivotaltracker.com/epic/show/4179927

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

See Pivotal Tracker: https://www.pivotaltracker.com/n/projects/2232205


## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).


