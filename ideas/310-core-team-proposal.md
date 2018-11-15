---
title: Status Core swarm proposal

---
###### tags: `proposal` `core` `SNIP` `SNIP-core`

**NOTE: This doc is a WIP, if you want to change something, just edit straight away. Please don't ask for permission.**

# Next Actions

- [ ] Potentially we can split this team in two
    - (a) "blockchain/cryptoeconomy" team
        - LES, ULC, geth, vipnode, incentivization
    - (b) "everything else"

- [ ] The proposal is reviewed/commented by the team members: "what's missing?" "what should be changed?" (by 10:00 CET Nov, 15)
    - **Reviewed/gave feedback**
    - [x] Igor
    - [ ] Roman
    - [x] Pedro
    - [ ] Adam
    - [x] Andrea MP
    - [ ] Chad
    - [ ] Maciej
    - [ ] Oskar (optionally)
    - [ ] DmitryS

- [ ] Assign outscoped projects

- [ ] Vote for the focus area we want to start with (by Friday, Nov 16, 23:00 CET)
    - [ ] Setup the voting process (igorm, by Nov, 14)

- [ ] Do the first meeting discussing the voting/the first focus area
    - (Probably) Monday, Nov 19 10:00 CET

# Status Core proposal

## Summary

Status Core is responsible for implementing a decentralized, reliable Ethereum reference client for Mobile on Android and iOS. This client should provide a reliable communication medium and ability to access the open decentralized web.

Desktop is out of scope, as is protocol research. Whitepaper use case implementation is partly in scope, partly not, depending on specifics and other teams.

Core needs an accountable, passionate get-shit-done mentality and drive, in contrast to the meandering blame-shifting.


## Budget

Headcount-based. 7 people.

The swarm also has a discretionary budget for bounty based development using Gitcoin, in order to parallelize development.

Assuming average organizational compensation, this would be roughly 60k/m. Possibly more based on performance, etc. A self-imposed ceiling of 100k is proposed for budget bucketing (~10%) for the team as a whole.

Related adjacent activities such as security, devops, marketing, QA, etc will be assumed to be provided and funded by the Gmbh until further notice.

## Core participants

- Adam
- Andrea MP
- Chad (PM)
- DmitryS
- Igor (tech lead)
- Maciej (Design)
- Pedro
- Roman

## Scope

See also: [team and responsibilities](https://notes.status.im/k0xVSu6nRvS5p0UAWV__BA?view)

Core should focus on problems/features that require multidisciplinary understanding and influence the application architecture. With the highest priority of making Status a usable application for consumption.

For simplicity, the responsibilities are split into 2 categories:
* **maintenance** - that means this effort is continuous and doesn't have any end date or exit criteria (publishing a mobile release is a good example, we don't stop)
* **project** - something that has a clear exit criteria, with a few iterations, after which the task is considered completed (for instance, when LES option is there and works)

### Core: Maintenance

#### 1. Battery usage

#### 2. Application performance profiling

#### 3. Mobile Releases

> [pedro] Shouldn't all releases be considered here? Why only mobile? Feels like we'd losing a holistic view.
> [igorm] not sure, the initial idea was to outscope desktop. Isn't it too much for one team?
> [pedro] I'd defer to your opinion since you have the experience of handling the releases, but maybe not too much if we end up splitting in two teams. I was hoping that it would be a small increment to the workload to also handle the desktop release part.

### Core: Projects

> [dmitry] there is nothing about decentralization and discovery.
> [igorm] can you suggest projects related to that?
> [dmitry] establishing a network using desktop clients. we need atleast to reuse libp2p tools descibed here https://github.com/libp2p/go-libp2p/issues/375 . and another thing is discovery, geth plans to refactor discovery v5 and add discovery based on dns. we should integrate atleast this two things.
> another point is censorship resitance. we need to ensure that we can update bootnodes if they get blocked in russia/china/other place.
> [igorm] I will add those as 3 projects then
> [igorm] done

#### 1. Message reliability improvements

The goal of this project is:
* to make messaging extremely reliable;
* to be able to prove that;
* to be able to show that information to a user.

That includes research & investigation, creating toolkit to monitor and test reliability.

Currently, it doesn't look like messaging is reliable enough.

**Why?**
1) Message history differs between desktop and mobile for the same user being online at the same time.
2) Mailserver requests looks like take long.
3) Push notifications being received way before messages are downloaded, leading to "phantom" push notifications.
4) We don't have any way to check if the message history is consistent on the server side.
5) We don't have any way to check if mailservers are in sync with each other.
6) We don't have any way to check if there are network partitionings.
7) If a mailserver is down, it takes a long time to figure this out and switch to another one.
> [andrea] Not sure I understand point 8 100%, maybe worth rewording? Are we saying that it takes a long time for messages to be received and there's no feedback (i.e a spinning wheel)?
> [igorm] there is a feedback, but the time span between sending a request and a user seeing messages looks unreasonably long, even if we have a spinner (taking into account that the mailserver response time seems fairly quick)
> [andrea] cool, thanks for updating the description, clearer
> 
8) Receiving messages from a mailserver (from a user perspective, the time between requesting messages from mailserver and actually rendering new messages) looks suspiciously long. And we have no way of measuring it and splitting into components.
9) If there are no new messages received, user doesn't know that he is up to date. There is no way to figure out if the request failed vs. user is up-to-date.
10) If a topic is crowded (like we witnessed in Prague) the response from the mailserver can quickly consume the data plan from the user. We need to think about ways to mitigate this (maybe request a preview from the mailserver so we can inform the user that messages won't be downloaded automatically for the selected chat if he's on 4G?)

See also: https://discuss.status.im/t/diagnosing-chat-reliability-issues/729

#### 2. Support LES and ULC

Add an option to use LES and ULC in our application. It should work on Ropsten and Mainnet with working discovery.

Status can host clusters for LES and ULC, for both testing and reliability purposes, but the usage of LES/ULC shouldn't be limited to that.

User should be able to create custom networks based on LES and ULC.

User should be able to manage trusted peers in ULC and static peers in LES.

User should be able to disable discovery if needed.

We should add some basic optimizations for LES, especially for the initial sync.

We should probably have some background sync enabled too, on both iOS and Android if static peers are available.

Disable sync on mobile network or low battery charge.

#### 3. LES/ULC: Economic incentives

> [dmitry] is it about proposal from Jacek?
> [igorm] probably, I'm not sure. it isn't the priority unless LES/ULC is just functional.

#### 4. VipNode support


#### 5. Implement EIP-681

https://eips.ethereum.org/EIPS/eip-681

> A standard way of representing various transactions, especially payment requests in Ethers and ERC #20 tokens as URLs.

#### 6. Reduce unnecessary bandwidth usage

https://github.com/status-im/status-go/issues/1266

Make sure that we identify and fix all the unnecessary bandwidth usage cases. We need to be able to test the usage regressions in the future, so these issues don't happen anymore.

Currently, it looks like our application uses too much bandwidth.

**Why?**

1. We don't have bandwidth tests in place.
2. Mailserver requests seems to be very expensive in bandwidth and we probably receive a lot of duplicate messages.
3. We don't know all the places where networking is used, so we can't measure bandwidth client-side (we have to only rely on iOS/Android settings to check that).

#### 7. Support multi-device experience

We need to be able to see the same message history on multiple devices (desktop + mobile is the common scenario).

#### 8. Improve mechanisms of storing/using sensitive information on mobile

**Problems in this area**

1. Whisper uses the same keypairs as the blockchain, exposing one of them leads to losing funds.
2. It is possible (and it happened before) to leak sensitive data through logs and debugging information.
3. Unsafe defaults in some publicly available builds in the application.
4. Sensitive information is used directly (accessible to most of the app components), whereas the best practices is to provide minimal APIs to do whatever needs to be done w/o exposing data (see Secure Enclave data signing)
5. Only a single protection mechanism for sensitive data (should be at least two).
6. (potentially) Storing sensitive information which we don't have to store.

#### 9. Improved message compatibility with other versions and other clients (using the *current* version of the protocol)

**Problems**
1. It is too easy to change protocol (message format, etc) in a PR w/o necessary oversight.
2. There are no tests to detect that message format or semantics didn't change after PR is merged.
3. We don't have any procedures and best practices on how to introduce changes to the current protocol.
4. We don't have any procedures and best practices on how to handle breaking changes gracefully and coordinate them between the clients.
5. We don't have any procedures, tools and best practices to handle breaking changes in mailservers.
> [pedro] Same thing for mailservers. Just recently there was a change to status-go that made it incompatible with the deployed eth.beta mailservers. We have no way to deal with backward compatibility, and having mailserver pinned makes it especially problematic.
> [igor] added this part too

#### 10. Reduce metadata leakage

#### 11. Audited private group chat and PFS

#### 12. Reproducible builds

**Problems**
1. Right now it's hard to tell exactly which commit of any dependency was used to build a particular release
2. Users don't have guarantees that the release they downloaded matches the official release (i.e. hasn't been tampered with).
3. A user should be able to build the sources on his own machine and obtain exactly the same binaries. 

#### 13. Integrate with `libp2p`

#### 14. Better discovery

1. Support/integrate geth initiatives

#### 15. Better censorship resistance

1. Being able to update bootnodes list if they are blocked


## Process

Process can be revisited through retrospective. Probably, the process should go to a github repository as a markdown file and using PRs to update it.

Taking as little of the parallel projects as possible. For example, we have to do maintenance anyway, so adding one other project as a focus area should be okay.

Weekly sync-up calls
- goals for the week
- focus area, progress
- post-meeting report in a Discuss thread

Post-project retrospective with post-mortem
- when the project milestone is done/failed
- when we are deciding to switch to another focus area

[DRIs](https://www.forbes.com/sites/quora/2012/10/02/how-well-does-apples-directly-responsible-individual-dri-model-work-in-practice/#38840682194c) for focus areas / maintenance tasks:
- single point of contact
- focused on one thing (one can be a DRI only to one focus area/maintenance task)

---

# Outscoped Projects (to other teams)

#### 14. Better CI experience

To DevOps team?

Not sure if the core team responsibility (igorm).
This is one of the problems that everyone depends on. If/when our CI is unstable, essentially, the whole dev team cannot work. 
> [???] Although I agree that this is mission critical, I would like to see this offloaded to a different team, it requires a specific skillset (which we might have in the core-team, but not only) and not many dependencies, also our plate is quite full as it is.
> [igorm] Agree, I just want to make sure it will be prioritized by some team, and asap. 

**Problems**
1. Issues with builds scripts on macOS builders (not isolated)
2. Way too many network requests on each build process (if any of these fails, all the build procedure fails). 
3. No retries of commonly unstable steps (again, when it fails, everything fails).
4. No decent caching/reusing of artifacts (that makes the build process very slow).


#### 6. SNT in transaction history

To the Wallet team.

---

# Raw Data

## (legacy) Scope

This document reads a little unfocused already.


## Notes

Please remove this section once consensus among stakeholders have been reached.

While additional hires/individuals might be wanted, it is desirable to keep the group size to a minimum for several reasons. See "two pizza rule" and Swarmwise for rationale. There are also budget constraints to consider, and bounty-based development allows for parallelization of efforts. E.g. going from 7 to 8 people would increase manpower by 14% but communication/relationship overhead by 33%.

The structure of this document is also subject to change.

Misc bits from Jarrad convo:
- wallet feature as out of scope, but tx signing as in scope 
- -- relates to key handling discussion with Corey as well
- fundamental things in scope
- browser url foo.ens not lol.ipfs.io 
- same dapp and chat features, unless impl requirement for all application
- message reliability is core, keycard is core
- UI features bells and whistles are not, incl self-destruct messages

## Requirements // Responsibilities

TODO: Clean up

1. Messaging EXTREMELY reliable and perceived to be reliable (incl history).
- before we had positive ack + timeout + retransmission ala TCP, not clear on to what extent or why we removed it? not sure how this would play with mailserver (hard part :D), but it seems like semantics for getting "reliability over unreliable transport" would be useful.
- Pedro: I don't remember us having had retransmission, but I do recall a proposal by @yenda to add such a mechanism. Maybe the removal of positive ack was for privacy reasons (we don't want to signal to people if we're online)?
4. Support for LES & ULC with basic optimizations (e.g. CHT, WiFi only sync).
-  OT: this should include economic model so ULC isn't just PoA (but it can be in first iter)
6. SNT first-class citizen (tx history); implement EIP-681.  <- is this core or wallet?
    - Pedro: I'd say wallet, with perhaps support from Core.
    - feature a bit low level, but as a guiding thing
    - on hold a bit
7. Bandwidth, network and battery usage non-issues. <- while this is a core concern, might be unavoidable for core and relies on new protocol design?
- BW: https://github.com/status-im/status-go/issues/1266
- in scope, possibly not possible with current protocol setup
- e.g. android running in bg, metrics on client
- Pedro: would be good to identify current problem areas and determine what consumption is intrinsic to protocol and what, on the other hand, can be optimized without changes to protocol.
8. Multidevice state. (primarily chat but also possibly contacts)
-
10. Ensure data security and privacy on mobile (e.g. seedphrase or private keys).
- phrase positive version
- be two mistakes away from leaking
- Pedro: we could have a component through which we pass data to ensure nothing critical is being passed. This component would:
  - analyze data streams and detect data patterns such as private keys/12 word recovery phrase, etc.
  - be used by e.g. the logging mechanism or any phone-home component that we might use with the users permission so that anything that gets logged has a chance to be vetoed/blacked out.
11. Ensure messaging compatibility with Desktop client.
- coordinate with other clients and ensure non-frivolous upgrades
12. Reduce metadata leakage (Infura, Etherscan, etc).
- provide alternative LES, for some people don't care but is option
- be honest about it
13. Enable a cluster-free Status experience through Status nodes.
- 
15. Weekly progress reports with relevant links to artifacts.
- makes sense
- okrs? concept ok but execution/followup so-so
- don't think team should create okrs in isolation
- objective metrics still useful, make sure some progress, unclear how measure
- requirements as okrs if polished
- problem: quarterly, do and leave for quarter don't change - doesn't jive with responsive to feedback etc, vs static
- if takes little to do then ok, but if overhead then not great
- okrs in past previously useful, but product was more stable, Status not in that phase yet
- weekly goals might be more reasonable
16. Community-involvement, leverage bounties to parallelize development. <- is this core? leave this to DAO
- team skill not just code but also communication and problem identification
- hopefully lower barrier entry
- problem description hasn't been great for bigger ones, research vs execution
- still useful to do problem identification beforehand
- vagrant machines for dev to simplify
17. Deliver in accordance with our principles, and be explicit about trade-offs.
- 
17. Do post-mortems after disruptive incidents to improve collectively.
- 
(18. ?)


### Specific bugs in scope but too low level (possibly generalizable)
2. Takes far too long to 'sign-in' / relogin (20+ seconds) making Status impractical for instant messaging. Signing in isn't even correct terminology.
-- can look at it, more of a bug, not requirement per se, too low level
3. Remember password on Android; fingerprint login/signing on android and iOS.
-- too low level, bug, in scope
5. Audited private group chat and PFS.
-- too low level, but in scope, feature
9. Search and public chat links on mobile. <- is this core or chat?
-- small bug just fix

### Unclear to what extent in scope
14. Ensure we have reproducible and signed builds.
-- stretching a bit far, plate quite full
-- narrow enough, can be factored out
-- possibly cna work with conan etc but expand scope a lot

## Long-term goals

- 80%+ of Devcon5 participants to use Status daily to transact.
- North star: Implement Status whitepaper in line with our principles.

## First task

Self-organize and figure out what is missing / wrong. This could be people, requirements as well as initial plans, goals. Anything necessary to make the plan more legitimate (consensus, anchored in reality) and credible (plan of action) to funders.

## Copyright

Waived, CC0.

## Nov 6th Meeting Notes

- Oskar: Goal is to have a much smaller team that is responsible for core functionality.
- Nabil: This is still very early, so we're trying to figure out how to slice things up. Dapps and devs team will be separate team. Further communication with other teams will be done at next TH.
- Adam: I've a question about current teams. What happens to them?
- Nabil: We'll disband current teams.
- Oskar: the problem of diffusion of responsibility is examplified by e.g. chat and P2P teams.
- Pedro: Seems like with new structure I'll be disincentivized from helping out Desktop team from doing Windows port
- Nabil
- Oskar
- Andrea: ?
- Oskar: If we brought Desktop team into Core, the team size would grow too big and we would lose the benefits of having a small team.
- Andrea: If we enforce strong boundaries across teams, then we need to talk about contracts, etc. Otherwise, we can work across boundaries and make sure that our feature works as expected.
- Oskar: Everyone in this team seems to care above avg about engineering practices. Hopefully that can spread across the org.
- Adam: Do we want to treat this team as a tiger team? Do we want to fix things quickly or think more longer term?
- Oskar: probably case-by-case. We might do a short term fix and also work on improvements longer term.
- Nabil: Ideally we'd leave this meeting with a clear list of priorities. Right now it's a laundry list.
- Maciej: How does design fit into this new team structure?
- Oskar: Not sure yet. Regarding being out-of-scope, this came out of a convo with Jarrad.
- Nabil: If that's the route we're taking, we'll need to change a lot of things.
- Oskar: in the last few months, we probably focused too much on bells and whistles and not so much on things like LES
- Nabil: that's BS, bells and whistles have been implemented by people who're not focused. If this is not going to be a UI-focused team, then we'll be recreating the problem.
- Oskar: I agree that onboarding and others is core
- Nabil: If we punt everything that is UI facing to other teams, then we've gained nothing.
- Oskar: if we look at the problems that the app has, it is mostly fundamentals (non-UI stuff like LES).
- Nabil: If you have a team of 8, you have enough room to hopefully implement functionality and fix bugs or improve existing features.
- Roman: we need to skip Desktop from our scope. We can't perform well if we have too many things on our plate. Also, we discussed with Oskar and Igor that we'll probably have some changes in the technology we're using, not sure if this is in scope.
- Oskar: writing the app on another tech is something that might be sponsored by the DAO, but it is not Core.
- Adam: From my perspective, since we ditched Slack, we need to make sure Desktop is usable
- Nabil: That concern is short term, for the time being we'll still focus on having a stable Desktop
- Adam: I think that the problem with LES was due to the team split. We tested LES to some degree but then it was kind of handed out to other people, but that was a mistake, because those people didn't have the knowledge we had gained while doing the initial PoC. If this split is going to address this kind of issues, then I think it is a good move.
- Oskar: building a mobile P2P app is a fundamentally hard problem, it is not the same thing as a mobile app that just talks to some REST API.
- Adam: I think the stack we currently have is changing too fast. If I try to build status-react after 2 weeks of not doing, it's not working anymore and if it does, it is too slow.
- Nabil: Maciej, when do you think the new system will be available?
- Maciej: looking to early November.
- Nabil: Great
- Adam: The problem with identity is a big pain. I have no idea who I'm talking to. The rest is kinda fine.
- Oskar: That's a problem that probably falls on Core's lap
- Oskar: a year ago Dapps we much more visible with Discover, we intentionally hid that while reworking the app UI. We seem to change things every 3 months. How do we make sure we make something that lasts?
- Nabil: You keep bringing up LES, how much effort will it be to bring it to fruition? Is it 4 people working for 3 months, or 1 person for 6 weeks?
- Oskar: do we want to bring new people to the team?
- Roman: we started a year ago with a small team and then hired a lot, so it seems by doing that, we'd be repeating the same mistake. Having a small team will allow us to have a clear idea of what each person is working on and what the priorities are.
- Pedro: will there be a wallet team?
- Oskar: the way I see it wallet should be a Dapp. We should make it pluggable so that we can swap the implementation.


... edit in doc

- hopefully less bikeshading with smaller team, improve and open-minded

- focus on one thing as a team at once possibly better, generally speaking
