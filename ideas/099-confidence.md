---
id: 099-confidence
title: Confidence in Messaging
status: Aborted
created: 2018-03-22
category: core
lead-contributor: PombeirP
contributors:
    - lukaszfryc
    - dmitryn
    - chadyj
    - nikitalukianov
    - jpbowen
    - hesterbruikman
exit-criteria: yes
success-metrics: yes
clear-roles: yes
future-iterations: yes
---

# Preamble

    Idea: 99
    Title: Confidence in Messaging
    Status: Aborted
    Created: 2018-03-22

## Summary

As end users we currently don't have confidence that messages are being sent, delivered and read. This swarm aims to address this.

## Swarm Participants

- Lead Contributor: @PombeirP
- Testing & Evaluation: @lukaszfryc
- Contributor (Clojure): @cammellos
- Contributor (Clojure): @dmitryn
- PM: @chadyj
- UX: @nikitalukianov @jpbowen @hesterbruikman

## Product Overview

We currently don't have confidence in the reliability of messaging in Status. The reasons for this lack of confidence ranges all the way from how 'read' status is displayed in the app, to trivial - and non-trivial - bugs, to bad uptime of critical infrastructure, to how push notifications are decoupled from Whisper messaging, to a fundamental lack of (understanding of) reliability guarantees Whisper protocol provides.

What all these issues have in common is that they cause the end user to not have confidence in their messages being delivered and read. This swarm aims to attack this from a user point of view. It is expected additional swarms might be spawned for more core technical areas as these are identified (e.g. network visibility or push notifications v2).

### Product Description

This section is based on user feedback spawned as part of 75-status-everyday (https://docs.google.com/document/d/1pkfZWxr9I0AqidEuOfogzxEXrcg6ofs2bUkh-HSKD6o/edit)

1. Messages should always be sent.

    - Generally: lack of trust in messages being sent
    - Provide better feedback of when messages are or aren’t sent
    - Allow re-send of individual messages a la Whatsapp

1. Messages are in wrong order.

    - Confirm fixed in 1on1
    - Make decision re migrations for old messages
    - Understand and clarify work needed for private group / public (placeholders)
    - Design: Deal with right order but “message arriving too late” (see sidebar)

1. Messages lack timestamps.

    - This appears to contribute to a lack of confidence in messaging
    - Design (then dev): Add this to UI

1. Messages don’t arrive despite being sent, or they arrive late.
    - Disambiguate offline from mail server node copy
    - Understand what is needed to make mail server HA
    - Give user feedback while it is fetching messages (non-instant)
    - Understand if there are more reasons messages would arrive late

1. Messages should always be delivered, 100% of the time.

    - Similar to 1 but stronger
    - What happens if mail server goes down?
    - Can we implement read/re-send semantics at Whisper level (mailserver)?
    - Look into how read receipts can be improved
    - Clarify UI a la Whatsapp double-tick
    - Consider tracking send/delivered ratio as a metric

1. Offline inboxing not working in public chat.

    - Clarify perf dependency on smooth-ui swarm
    - While perf is being worked on, educate user about offline only being 1-1

1. Perception of lack of notifications.

    - UXR: understand expectation -  for non-contacts? Public chats? in-app?
    - Separate PN swarm, clarify dependency with this swarm

1. Get notification but nothing visible in app.

    - PN delivery being decoupled from Whisper delivery, see point 7 above
    - Clarify dependency on PN v2 swarm and where work done

1. Perception of never received messages from other people.

    - Investigate if same as filter while offline bug and current limitations
    - More 7: Investigate non-contact PN possibility
    - More 7: Public chat PN?
    - UXR: Understand this problem and perception better

1. Sometimes need to change mail server manually to get messages working.

    - Make failure of individual mail server apparent and prompt switching
    - Automated switching?
    - How ensure no switching is necessary? (HA, see 4)

### Requirements & Dependencies

- ~~[Request messages history after background](https://github.com/status-im/status-react/pull/3493)~~
- ~~[New protocol](https://github.com/status-im/status-react/pull/3273)~~
- [New Status App communication protocol idea](https://github.com/status-im/ideas/blob/master/ideas/087-new-protocol.md)

### Security and Privacy Implications

None currently known.

### Iteration 1

Complete several reliability improvements that have been identified so far:

- ~~[#3827 Message reliability survey](https://github.com/status-im/status-react/issues/3827)~~
- ~~[#3793 Improve timestamps in chat messages](https://github.com/status-im/status-react/issues/3793)~~
- ~~[#3787 Improve network offline and mail server error messaging](https://github.com/status-im/status-react/issues/3787)~~
- ~~[#3784 Provide users with delivery status feedback when sending messages](https://github.com/status-im/status-react/issues/3784)~~
- ~~[#3792 Measure message send/receive ratio on internal builds](https://github.com/status-im/status-react/issues/3792)~~
- ~~[#828 Send an expiration signal when envelope wasn't delivered to any peer](https://github.com/status-im/status-go/pull/828)~~
- ~~[#810 Notify clj side when the message actually "left" local node.](https://github.com/status-im/status-go/issues/810)~~
- ~~[#3785 Remove "seen by everyone" from public chat](https://github.com/status-im/status-react/issues/3785)~~

### Iteration 2

After iteration 1 is complete the swarm will meet and discuss the results of the UXR survey, send/receive ratio results, review current UX and discuss future iterations. Work will then be planned for a future iteration, or the swarm will be closed.

## Exit Criteria

- 95% of a group of 100 users surveyed - who don't have additional context beyond Status providing a p2p IM capability - using the app for an extended period of time, should answer 'yes' to the question: "Do you trust Status to deliver messages for you?" (and possibly variants of this).

  This is fundamentally a soft or qualitative goal. It is thus necessary but not necessarily sufficient, and additional harder numbers might be used as we develop the capability to measure this.

## Success Metrics

- >99% message deliverability from [#3792](https://github.com/status-im/status-react/issues/3792)

- Zero instabug reports within 30 days of alpha release

## Retrospective

- What went well?

  - Andrea: Effort was well focused, results were good (although hard to measure)
  - Chad:
    - Shipped beta on time
    - Chat Team worked much better together than previous swarm(s)
    - Dramatically increased chat reliability!
    - Coordinated from multiple angles, eg UXR surveys, mixpanel stats, automated testing
    - Chat board was like night and day compared to previous way
  - Lukasz:
    - Switching to teams helped focus a lot
    - Almost no Instabug reports regarding reliability recently
  - Dmitry: switch to teams, focus on Beta release, reliability and performance increase
  - Pedro: having a Chat team was helpful any time a high-priority bug or a question appeared. People know where to go to discuss that without cluttering #core.

- What could we do better?

  - Andrea: The measuring part could have been more fleshed out, we focused more on fixing the current issues rather than fixing and preventing new ones from happening, but overall minor points compared to the benefits of the initiative.
  - Chad:
    - Find a better way to measure
    - Still had a handful of users complaining
    - Have a proactive way to spot regressions
  - Lukasz:
    - Maybe try to monitor on cluster side in the future?
    - Some issues with Jenkins, seems to be solved now
  - Pedro:
    - Better tooling, eg reliable surveys + instabug
  - Eric: maybe the team effort can work just as well as a swarm, we just need better control of when a swarm is ready to start
  - Dmitry: reliability metrics (in-app and cluster monitoring)

- What do we want to implement/improve?

  - Better monitoring and better communication between infra and chat teams
  - Continue with Chat team for Q3

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
