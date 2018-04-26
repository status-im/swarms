---
id: 095-les-improvement
title: Improvement of LES
status: in-progress
created: 2018-03-20
contributors:
    - themue
    - jeka
    - b00ris
    - zsfelfoldi (external)
---

## Preamble

    Idea: #095-les-improvement
    Title: Improvement of LES
    Status: In progress
    Created: 2018-03-20

## Summary

Current LES is not yet optimized for ultra-light devices like mobile phones. So in the first step introduce
the ULC addressing this kind of clients.

Later add the LES Service Model where clients can subscribe to higher quality services. Different payment
models will be available, negotiation between client and full node is done via auctions based on demands and
capacity. This way full node service provide are able to monetize the services they provide. LES will make the
beginning, Whisper and Swarm may follow.

## Swarm Participants

- Lead Contributor: @themue
- Testing & Evaluation: TBD
- Contributor: @jeka
- Contributor: @b00ris
- PM: @zsfelfoldi (external)
- UX (if relevant):

## Product Overview

Current LES is not optimized for usage on mobile phones. So Status is using Infura with all its assets and
drawbacks. ULC is addressing ultra-light clients and distribution without dependency to central providers.
Instead a network of trusted LES nodes acts as counterpart for the protocol.

So Status is supporting the development and testing of ULC to accelerate integration into *geth*.

Als right now all light clients are treated equal by the full nodes they connect. A future service model will
introduce the separation between free and payed services. As outlined by Felföldi Zsolt:

- LES will be available either as free or paid service,
- paid service can guarantee availability and short response times,
- client bandwidth demand fluctuates with time, good service quality requires reserve capacity,
- for-profit LES servers can still give away their extra capacity for free (with lower priority than paid service),
- free service is a good indicator of high bandwidth capacity and therefore the capability to provide good service, and
- paying clients will prefer servers which already gave them free service so free service can act as an advertisement.

Here Status also supports the development and testing to make the service model become a part of *geth* and be
integrated into Status.

### Remark

For Status it also could become interesting to become a service provider offering payed full node services not only
for own clients. This business case should be evaluated in an own swarm.

### Product Description

Parts of ULC and the LES Service Model introduction are:

- research, definition, and implementation of ULC,
- research, definition, and implementation of connection management system of paying clients for full nodes,
- research, definition, and implementation of auctioning,
- research, definition, and implementation of payment methods and models,
- documentation.

### Minimum Viable Product

Goal Date: TBD (before end of Q2/2018)

Description:

- [ ] New Ultra Light Client mode is added to LES
- [ ] Integrate ULC with `status-go`
- [ ] Collect metrics (CPU, mem, disk, network I/O) when starting with a branch new install and after 1h of inactivity

### Iteration 1

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

LES of `go-ethereum` is extended to use ULC and provide micropayed services with a higher quality
level as well as free services depending on capacity and configuration.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

