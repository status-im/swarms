---
id: ???-ultra-light-client
title: Integration of ULC in Status
status: Draft
created: 2018-05-02
category: research
contributors:
    - themue
    - jeka
    - b00ris
    - zsfelfoldi (external)
exit-criteria: no
success-metrics: no
clear-roles: no
future-iterations: no
---

## Preamble

    Idea: #???-ultra-light-client
    Title: Integration of ULC in Status
    Status: Draft
    Created: 2018-05-02

## Summary

Current LES is not yet optimized for ultra-light devices like mobile phones. So in the first step introduce
the ULC addressing this kind of clients.

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

So Status is supporting the development and testing of ULC to accelerate integration into `go-ethereum` as
well as into Status itself.

### Product Description

- Research of ULC design
- Definition and implementation of ULC
- Integrate ULC in `statusd` and the `lib`
- Documentation

### Minimum Viable Product

Goal Date: 2018-06-30

Description:

- [ ] New Ultra Light Client mode is added to patched LES
- [ ] Integrate ULC with `status-go`
- [ ] Collect metrics (CPU, mem, disk, network I/O) when starting with a branch new install and after 1h of inactivity
- [ ] Keep battery and network consumption at least as low as today with Infura

### Iteration 1

Goal Date: TBD

Description:

- [ ] Support integration of ULC into `go-ethereum`
- [ ] Documentation

## Artifacts

- None

## Success Metrics

LES of `go-ethereum` is extended to use ULC.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

