---
id: 172-topic-democracy
title: Subjective Delegation Liquid Democracy
status: Draft
created: 2018-04-15
category: core
lead-contributor: Ricardo Guilherme Schmidt
contributors:
    - 3esmit
exit-criteria: yes
success-metrics: yes
clear-roles: no
future-iterations: no
roles-needed:
    - UX
    - PM
    - Clojure dev
okrs:
   - "[P2]: SNT is a powerful utility in Status"
---

## Preamble

    Idea: 172-topic-democracy
    Title: Subjective Delegation Liquid Democracy
    Status: Draft
    Created: 2018-04-15

## Summary
A democracy where you can specify delegate for carbon-voting proposals with specific multilevel governance delegation topics, or fallback to a predefined defaults if none set.

## Swarm Participants
- Lead Contributor: Ricardo Guilherme Schmidt
- Testing & Evaluation: <!-- @username -->
- Contributor: <!-- @username -->
- Contributor: <!-- @username -->
- PM: <!--- @username -->
- UX (if relevant): <!-- @username -->

## Product Overview

This product intend replace authority centralized control for networks with  tokenized participation, such as Status Network currently owned by MultiSig contract 0xBBF0cC1C63F509d48a4674e270D26d80cCAF6022.
The product would enhance security of network as an attack would require control of more addresses. 

For a democracy where every member understands basic about every subject required for senstive actions inside the network is utopic. 
As Status Network decisions would be democratic for the users of the platform, a optional voting capability would be given to SNT owners, where they could set their delegate, or vote by themselfs.

When users don't vote and don't delegate, their influence would be delegated to SGT (Status Genesis Tokens) owners consensus.


### Product Description

- Users should be able to participate on decisions or delegate their influence. _Important to democracy._
- Votes are counted as MiniMeToken balance of user at block voting end. _Important to not double tabulating without locking token transfers_ 
- Voting or delegating must not cause direct risks to users balances. _Important to don't cause barriers into democracy process_
- Users that delegates must be able to vote differently then his delegate. _Important to don't cause barriers into setting a delegate._
- Delegates should be able to delegate influence delegated to them, as a delegation chain. _Important to inflience get into experts._
- The voting process of proposals should be divided in two polls, first asking for approval votes, and second asking for reject votes.  _Important to prevent a big delegate changing decision at last moment._
- Approval pool uses a "Executive Delegation" and rejection pool uses a "Veto Delegation". _Important to prevent bribe of delegates._
- Specifics topics should have their own parent topic and specific delegation chain, which if unset by user should fallback to parent topic definition. _Important to influence get into specialists of the topic._
- Users that didnt defined any delegate would by default delegate to SGT Topic Democracy. _Important to don't cause slowness into Status Network development._
- SNT must be owned by SNT Topic Democracy. _Important to democracy._

### Requirements & Dependencies

- MiniMeToken: Important because it allows lookup of snapshot balances in a certain block. This make possible safe tabulation without locking user balances.

### Minimum Viable Product
<!-- Mandatory, completes the Idea in the fastest route possible, can be hacky, needed to feel progress. See https://imgur.com/a/HVlw3 -->
Goal Date: <!-- Date for evaluation in ISO 8601 (yyyy-mm-dd) format --> 

Description: Topic Democracy as DAO Governance
- Users can execution of proposals.
- SNT is owned by topic democracy. 

## Dates
Goal Date: <!-- Date for evaluation in ISO 8601 (yyyy-mm-dd) format --> 

Description: Topic Democracy as "opinion" pool as experimental.
- System is deployed in mainnet.
- Users can cast opinion as vote using SNT for Status proposals throug Topic Democracy..
- Users can delegate opinion for Status proposals using SNT through Topic Democracy.
- Inchain tabulation is not required, because results can be calculated offchain and as no action would be taken by the result, inchain tabulation would be waste of gas.
- Topic Democracy don't owns SNT.
- Users are asked to approve proposal to upgrade into DAO Governance. When community decides this system is ready to take control of Status authority, a pool can be done and tabulated inchain to transfer control to Topic Democracy over a Topic Democracy proposal.
- First DAO Governance can control network/assets by a multisig between current authority.

## Success Metrics

It's difficult to assume a success metric from the voting, as users that just didn't "touched" the product probably are delegating their trust to Status Genesis Token holders.

However if we able to see if users look into the proposals and discuss about them in forums, would be a success signal.

## Exit criteria

Status Network controlled by Topic Democracy.

## Supporting Role Communication
<!-- Once Requirements and Goals are fleshed out, then it should be communicated to supporting organelles if required -->

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
