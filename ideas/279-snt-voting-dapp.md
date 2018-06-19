---
id: 279-snt-voting-dapp
title: SNT Voting Dapp
status: draft
created: 2018-06-05
category: dapp
contributors:
    - Barry 
    - 3esmit
    - rramos
    - rachelhamlin
exit-criteria: yes
success-metrics: yes
clear-roles: yes
future-iteration: yes
roles-needed:
    - QA
    - UXR
    - Designer
okrs:
    -
    -
---

## Preamble

    Idea: 279
    Title: SNT Voting Dapp
    Status: Draft
    Created: 2018-05-21
    Requires (*optional): 172-topic-democracy

## Summary

Provide Status users with a dApp to vote on ideas using their SNT thru carbon voting, without affecting their token balance.

## Swarm Participants

- Lead Contributor: @3esmit
- Contributor: @Barry
- Contributor: @rramos
- QA:
- PM (required for user-facing): @rachelhamlin
- UX(R) (required for user-facing swarms):

## Product Overview

We want to provide a mechanism for SNT Holders to be able to vote on proposals and features using their token balance. 

Each token represents 1 vote, and the balance can be allocated proportionally between the different options a proposal may have, in order to determine the interest level and priorize features.


### Requirements & Dependencies

The final goal for this DApp is to be managed via Liquid Democracy. Idea #172 needs to be implemented before the final iteration of this swarm is completed


### Minimum Viable Product

Goal Date: 2018-07-29

Description:
For the initial delivery, these are the minimum features proposed:
- UI to list all items subject to votation
- UI to allow SNT holders to vote / cancel vote 
- UI to view details about an item
- UI to create voting items by the contract owner
- Use contracts from Idea #172 for creation of proposals and to handle voting.
- After N blocks a votation is closed and results tabulated

### Iteration 1

Goal Date: TBD

Description: 
- Design / Prototypes are created
- Design and layout of dApp is updated
- SNT holders may create items to vote
- Proposals may contain different options, and SNT can be allocated among them.

### Iteration 2

Goal Date: TBD

Description: 
- UI for vote delegation is created
- Vote tabulation based on Liquid Democracy
- Multiple choice polls can be created


## Success Metrics

Initial emphasis is on deliver a working product with no bugs at contract level and no critical bugs for the UI

- Items to vote on can be created
- Users can browse on the different proposals
- Users can vote with their SNT tokens
- Users can cancel their vote
- After a votation period ends, votes are tabulated correctly.

## Exit criteria

- Launch voting DApp in the mainnet
- Users are able to vote on ideas

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
