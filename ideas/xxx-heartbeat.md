---
id: 000-heartbeat
title: Heartbeat
status: draft
created: 2018-05-09
category: chat
lead-contributor: yenda
contributors:
    -
    -
    -
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
    - Contracts dev
    - Designer
    - Community
okrs:
    -
    -
---

## Preamble

    Idea: <to be assigned>
    Title: Hearbeart
    Status: Draft
    Created: 2018-05-09
    Requires (*optional): <Idea number(s)>
    Replaces (*optional): <Idea number(s)>

## Summary

Whisper being a decentralized end to end communication protocol, we don't have any server to acknowledge delivery of messages to the network. Delivery can only be confirmed by the recipient of a message, and he needs to be online to receive messages. Since 1 to 1 chats are using a secured channel negociated during contact request, we need a mechanism to detect lost messages as well as a mean to re-establish communications between peers when one recovers an account and loses access to the secured channel.

The goal of this swarm is to implement a hearbeat mechanism that will fulfill this purpose, in order to improve reliability, recovery, and be independent from the mailservers for message re-delivery.

## Swarm Participants

- Lead Contributor: yenda
- Evaluator (defaults to lead contributor):
- Contributor:
- Contributor:
- QA:
- PM (required for user-facing):
- UX(R) (required for user-facing swarms):

## Product Overview

The swarm will work on extending the current communication protocol by introducing a heartbeat message, a negative-acknowledgement message and a redelivery message.

The heartbeat message will be sent by A over the secured channel when a timeout since last communication with a peer is reached. The recipient of the heartbeat (B) will then be aware that the secured channel is still in use, and that the last messages he has sent since then have been received by A. 
If B hasn't received any communication from A after a timeout, he will retry channel negociation in case A has done a recovery.

When receiving messages from A, if B notices that messages were missing, he will send a negative-acknolwedgement to A. A will resend the messages encapsulated in a redelivery message.

### User Stories

As a user, I still want to be able to receive messages from my contacts after recovery

As a user, I want to make sure lost messages are redelivered

### Security and Privacy Implications

Heartbeats give an indication of users presence online. The timeout shouldn't be too small in order to reduce the leakage of information. As an ehancement, we could develop a ludicrous mode in advanced settings that uses the current protocol for absolute secrecy with reduced reliability.

## Dates

### Minimum Viable Product

Goal Date: 2018-05-18

Description: Nack, redelivery and heartbeat messages are implemented and their usage can be enabled via a flag

### Iteration 1

Goal Date: 2018-05-25

Description: Bugs in MVP are fixed and work is merged into develop. Timeout can be configured to make testing easier

## Success Metrics

Enventually means received within a period of 5 minutes of both users being online, messages being sent before that period and regardless of the connection status of the recipient at the time of sending. Mailserver can be disabled.

- 100% of messages in 1-1 chat are eventually received 
- recovered accounts still receive 99% messages eventually (after 5 minutes)

## Exit criteria

- Nack, redelivery and heartbeat are working in nightlies
- Success metrics are achieved

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
