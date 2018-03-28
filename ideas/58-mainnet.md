## Preamble

    Idea: 58-mainnet-default
    Title: Use Mainnet as the default network
    Status: In progress
    Created: 2017-12-08


## Summary
Alpha builds of Status should default to Mainnet. We should be using Status in a real-world environment.

## Swarm Participants

- Lead Contributor: @adambabik
- Testing & Evaluation: <!-- @username -->
- Contributor: @themue
- Contributor: <!-- @username -->
- PM: @chadyj 
- UX (if relevant): <!-- @username -->

## Product Overview

Currently the Status alpha builds use testnet, but using Mainnet is a key milestone for the public launch of Status. There will be potentially be major performance and security implications so these issues should be surfaced as soon as possible so the app can be tested in a real-world environment. 

From a users perspective, Mainnet should be used as it is required by most popular DApps, and is needed for real transactions, so the full potential of Status can't be seen until we switch.

## Product Description

This is a default setting change, so there aren't any user facing options.

Some users, such as DApp creators may want to test their app on testnet (or some other use case), so they will be able to toggle networks as can be done currently.

## Requirements & Dependancies

Security and performance should should be discussed and considered.

Also, several Dapps should be tested. 

## Minimum Viable Product

**This MVP does not mean that after it's finished we deploy the app with Mainnet enabled by default but defines prerequisites that should be done before we consider doing so.**

Goal Date: 2018-04-06

1. [ ] Development of required components is done. The work is tracked here: https://github.com/orgs/status-im/projects/15,
1. [ ] There is a Status App build with mainnet available,
1. [ ] All components have been tested by the Q&A Team.

## Audit iteration

Goal Date: 2018-04-20 (?)

1. [ ] Security audit is finished by an independent company,
1. [ ] The final report is available,
1. [ ] All reported security issues are evaluated and fixed.

## Marketing iteration

Goal Date: 2018-04-??

1. [ ] Status App Bug Bounty program is announced and will last for at least X weeks.

## Success Criteria

1. Mainnet is operational just like testnets. It's possible to select it from the Status App profile.
1. The audit is completed with a final readout.
1. There is a blog post with Status App Bug Bounty.

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

