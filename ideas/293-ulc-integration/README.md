---
id: 293-ulc-integration
title: ULC integration
status: draft
created: 2018-08-06
category: core
lead-contributor: b00ris
contributors:
    - b00ris Go dev
    - jeka Go dev
exit-criteria: no
success-metrics: no
clear-roles: no
future-iteration: no
roles-needed:
    - Go dev
    - Go dev
    - Clojure dev
    - QA
okrs:
    - Core. [P0] LES and/or ULC are operational and used by at least 10% of all users.
    - Research. Integrate and test ULC in a manner “graceful downgrade”: use infura by default and if it fails, start ULC node.
---

## Preamble

    Idea: 293-ulc-integration
    Title: ULC integration
    Status: Draft
    Created: 2018-08-06
    Requires (*optional): #254

## Summary
Status app can use LES and ULC as Ethereum providers instead of Infura.

## Swarm Participants
- Lead Contributor: @b00ris
- Contributor: @jeka
- Contributor: @mandrigin
- Contributor: TBD
- QA: TBD

## Product Overview
We need LES client enabled on mobile device to be really decentralized and to enable all web3 features for dApps.

### Requirements & Dependencies
Depends on research swarm #254

### Security and Privacy Implications
* Free slots for LES servers
* Trusted nodes selection

### Minimum Viable Product
* LES can work as the second Ethereum provider in status app.
* ULC can work as the third Ethereum provider in status app with static trusted nodes.

Goal Date: 2018-10-08

Description:

### Iteration 2018-08-13 - 2018-08-27

Goal Date: 2018-08-27

Description:
* investigate les integration problems and fix them
* ULC in go-ethereum master(#254)

### Iteration 2018-08-27 - 2018-09-10

Goal Date: 2018-09-10

Description:
* run ULC compatible nodes in staus cluser
* integrate ULC to status-go as a patch

### Iteration 2018-09-10 - 2018-09-24

Goal Date: 2018-09-24

Description:
* debug and run status app with ULC and status cluster
* graceful downgrade(use infura by default and if it fails, start ULC node)

### Iteration 2018-09-24 - 2018-10-08

Goal Date: 2018-10-08

Description:
* reserved for shifting

## Success Metrics
* Status app can use LES and ULC provider instead of Infura.

## Exit criteria
* Running on Mainnet

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
