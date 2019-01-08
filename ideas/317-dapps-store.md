---
id: #317-dapps-store
title: DApps Store
status: research
lead-contributor: Andy
contributors:
    - Andy
    - Julien
    - Andrei
budget:
- actual: xxx
- estimate: yyy
- currency: ETH
---


DApps Store Swarm Proposal
=

## Summary and Goals

The DApps Store swarm will deliver SNT based curation mechanisms in accordance with the white paper.

It allows individuals to curate DApps by staking SNT and have access to this list within Status.

## Contributors

- Andy
- Julien
- Andrei

(+ Janitor swarm)

## Communication

`status channel`: #317-dapps-store
`sync schedule`: weekly

`Meeting notes`: 

## Research

`Timebox`: wrap by 31/01

Potentially, by the end of Jan, the work can be split into parallel streams where redesign of the current browsing experience on the UI side moves to specification, while topics that require more research (curation mechanism) remain in the research phase.

`Previous work`: 

DApps are currently exposed as a static catalog hardcoded in Status client.
Previous versions of Status relied on a basic discovery protocol to discover new DApps.
[State of the DApps](https://www.stateofthedapps.com/) is an existing curated list of DApps.

Andy [proposed](https://discuss.status.im/t/how-to-curate-dapps-simply/759) a bonded curve based curation mechanism.

`Research questions`:

Below are topics to be addressed in the research phase.
1. What are appropriate incentivization mechanisms? (e.g. Game theory exploration)
2. What is the best way to implement a DApp store given user and business requirements (w.r.t. liability and upgradability)? 
3. What is the most efficient and effective development strategy given the outcome of 2? (bounty to attract team, required level of support by core contributors)
4. What are appropriate ranking mechanisms?
5. What are appropriate mechanisms for user involvement in this ranking (4)?
6. How can new DApps be included in the browse and search experience? (e.g. submission, registration, adding, curation by committee)
7. What are different visual interfaces that can support a browse and search experience? (design exploration)
8. What position/'status' should Status DApps have in it's own store?

`Potential user stories`:
The user stories below need to be detailed and prioritized following the research phase. 

- As a Status user:
- I want to easily browse interesting DApps
- I want to see new DApps frequently.
- I want to see old unusable DApps removed. 
- I want to be confident a DApp is usable / not a scam.
- I want to be able to propose a DApp for inclusion.
- I want to vote for a DApp inclusion.
--
- As a DApp developer:
- I want to be able to propose my DApp for inclusion.
- I want to vote for my DApp inclusion.

## Specification

## Implementation

## Maintenance

## Copyright

Copyright and related rights waived via CC0.
