---
id: 095-les-service-model
title: Adding a service model to LES
status: Draft
created: 2018-03-20
category: research
lead-contributor: b00ris
contributors:
    - themue
    - jeka
    - b00ris
    - zsfelfoldi (external)
exit-criteria: yes
success-metrics: no
clear-roles: yes
future-iterations: yes
---

## Preamble

    Idea: 095-les-service-model
    Title: Adding a service model to LES
    Status: Draft
    Created: 2018-03-20

## Summary

Add the LES Service Model where clients can subscribe to higher quality services. Different payment models will
be available, negotiation between client and full node is done via auctions based on demands and capacity. This
way full node service provide are able to monetize the services they provide. LES will make the beginning, Whisper
and Swarm may follow.

## Swarm Participants

- Lead Contributor: @b00ris
- Testing & Evaluation: TBD
- Contributor: @jeka
- PM: @zsfelfoldi (external)
- UX (if relevant):

## Product Overview

Right now all light clients are treated equal by the full nodes they connect. A future service model will
introduce the separation between free and payed services. As outlined by Felföldi Zsolt:

- LES will be available either as free or paid service,
- paid service can guarantee availability and short response times,
- client bandwidth demand fluctuates with time, good service quality requires reserve capacity,
- for-profit LES servers can still give away their extra capacity for free (with lower priority than paid service),
- free service is a good indicator of high bandwidth capacity and therefore the capability to provide good service, and
- paying clients will prefer servers which already gave them free service so free service can act as an advertisement.

Here Status supports the development and testing to make the service model become a part of *geth* and be
integrated into Status.

### Remark

For Status it also could become interesting to become a service provider offering payed full node services not only
for own clients. This business case should be evaluated in an own swarm.

### Product Description

Parts of the LES Service Model introduction are:

- research, definition, and implementation of connection management system of paying clients for full nodes,
- research, definition, and implementation of auctioning,
- research, definition, and implementation of payment methods and models,
- documentation.

### Minimum Viable Product

Goal Date: TBD

Description:

- [ ] Auctioning protocol between client and full node is defined
- [ ] Payment methods and interfaces are defined
- [ ] Initial implementation validates auctioning and micropayment in automated tests

## Artifacts

- [Information about Micropayment](micropayment.md)
- [Logfile](log.md)
- [Links](links.md)

## Success Metrics

LES of `go-ethereum` is extended to provide micropayed services with a higher quality
level as well as free services depending on capacity and configuration.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

