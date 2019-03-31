---
id: #304-core-chat
title: Core Chat
status: research
lead-contributor: Eric
contributors:
    - Eric
    - Vitaliy
    - Tetiana
    - Hester
    - Rachel
    - Maciej
budget:
- actual: xxx
- estimate: yyy
- currency: ETH
---

Chat Swarm Proposal
=

## Summary and Goals

The Core Chat team is going to be primarily responsible in Q12019 for building the P0 SNT Utility feature Tribute to Talk.

This swarm is also responsbile for maintaining and improving the overall chat experience. 

Any capacity leftover from TtT tasks will be dedicated to essential chat features or fixes.

## Contributors

- Eric
- Vitaliy
- Tetiana
- Maciej

(+ Janitor swarm)

## Communication

`Status channel`: #status-core-chat

`Sync schedule`: currently twice weekly

`Meeting notes`: https://notes.status.im/weekly-chat-sync-agenda

`Epic issues board`: https://github.com/orgs/status-im/projects/49

`Small issues board`: https://github.com/orgs/status-im/projects/21

`Pivotal board`: https://www.pivotaltracker.com/n/projects/2231830

## Research

### Phase 1

`Timebox`: Complete by 19/12/18

`Objective`: Define high priority items for chat, outside of Tribute to Talk and independent of current board. 

`Issues`:

#### Hot Potato

- Tribute To Talk

#### P0

- Use of ENS names in chat/for contact resolution* (stateofus.eth only) - [GH issue](https://github.com/status-im/status-react/issues/7114)
- Improve/reduce "fetching messages" appearance* - [GH issue](https://github.com/status-im/status-react/issues/5371)
- Send SNT for a message (Reddit gold) / emoji reactions - [GH issue](https://github.com/status-im/status-react/issues/7118#event-2030637569)
- Mute and/or block users* -- [Rachel: I think this is P0][Hester: Agreed]
- Send images/files*—discuss with browser team, no file browsing yet - [GH issue](https://github.com/status-im/status-react/issues/7120#event-2030639061) 
- Clear/fix 9+ notifications badge*—_already fixed?_ [Rachel: I noticed that 9+ badge is still not clearing from public chats on last nightly—I open, scroll, navigate away, repeat, and still see 9+ new messages]



#### P1

- Public chat preview and/or redesign of join public chat screen to look less like search bar and results. [Hester - from September testing in Berlin]
- Message drafts* (unclear about this) [Hester: yes please! This impacts perception of reliability IMO. If I leave the app while typing a message (e.g. to copy a link), I want to come back to the same message. This issue relates to logout and password saving, but should be P0 IMO]
- @ mentions and notifications* - [GH issue](https://github.com/status-im/status-react/issues/7117#event-2030636257) [Rachel: I'm not sure this is so important with less focus on desktop][Hester: Agreed]
- Mark all as read - [GH issue](https://github.com/status-im/status-react/issues/7119#event-2030637871) [Rachel: I think this is p1 or p2] [Hester: Agreed; would swap with Clear/fix 9+ notifications badge. Seems the root of this requirement]
- Group chat push notifications

#### Unprioritised

- Omnibar to...* [Hester: not sure what is meant with Omnibar, therefore can't judge if it's the right approach to offer search chat and add user.]
    - Search chats
    - Add user
- Rethink "seen"* [Hester: investigate how 'received' translates; more accurate]
- Star, snooze, mark as unread, etc.
- Notification settings
- Bring back contact list?*
- Allow messaging to self* (research required)
- In-app notifications (e.g. receive message notification while in wallet view)?
- Improve delivery failure messages*
- Link previews*
- Refresh chat*
- Translate message button*
- Architecture documentation*
- Better markdown support*
- Threads*?
- Deeplinking to messages*
- Windows platform compatibility
- Priority inbox / messenger browser
- [Hester: 'Notification bundle' seems worthwhile adding, if not captured yet. i.e. it's impossible to see whether the 4 Status notifications are from the same conversation or not]

`Outcome`: TTT and 7 other epic issues have been picked from the list
- MVP1 TTT https://github.com/orgs/status-im/projects/49#card-15834094
- MVP2 ens username in chat https://github.com/orgs/status-im/projects/49#card-15833208
- MVP3 Fetching messages progress bar (DONE) https://github.com/orgs/status-im/projects/49#card-15833629
- MVP4 Block user https://github.com/orgs/status-im/projects/49#card-15962930
- MVP5 SNT and emojis reactions https://github.com/orgs/status-im/projects/49#card-15833648
- MVP6 Mark all as read https://github.com/orgs/status-im/projects/49#card-15833681
- MVP7 Mentions https://github.com/orgs/status-im/projects/49#card-15833631
- MVP8 Send images (as extension) https://github.com/orgs/status-im/projects/49#card-15833961


### Phase 2

`Timebox`: Complete by 10/01/19

`Objective`: Timebox high priority issues. During that phase developpers will experiment with each high priority issue and estimate the time required for each.

## Specification

## Implementation 

## Maintenance

## Copyright

Copyright and related rights waived via CC0.

