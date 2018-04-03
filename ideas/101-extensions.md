## Preamble

    Idea: 101
    Title: Status extensions
    Status: Draft
    Created: 2018-03-26

## Summary

A set of extension points so that external developers can enhance status

## Swarm Participants

- Lead Contributor: @jeluard
- Testing & Evaluation: ??
- Contributor: ??
- PM: @andytudhope
- UX: @denis-sharypin

## Product overview

As an ecosystem status needs to offer extension capacities so that external developers can develop on top of it.
This swarm will review the current state of our extensions, specify a updated mechanism based on our current knowledge and eventually implement it.

### Product Description

3rd party developers will have access to API and documentation allowing them to extend status via various hooks using a simple API.
There won't be any distinction between those extensions and status itself (it will feel native).

### Requirements & Dependencies

None

### Minimum Viable Product

* document existing working features offered by status [API](https://docs.status.im/)
* list (potential) new types of extensions
* prepare new workflow / mockups (special care for chat extensions)
* prepare draft specifications detailing technical solution to be discussed with team (development, distribution, incentivization)
* detail how to integrate with status API / screens

During definitions of specifications a number of potential use cases must be considered, namely:

* retrofit existing chat commands
* ethereum standards (721, ..)
* video sharing technologies ([livepeer](https://livepeer.org/))
* token transfers (https://raiden.network/)
* https://ethlend.io/en/, https://trustlines.network/, ...
* extensions mechanisms provided by other chat applications

First status hackathon is also a good starting point. [Feedback](https://github.com/status-im/status-react/wiki/Hackathon-Feedback) has been shared and [winners](https://blog.status.im/announcing-winners-of-the-status-global-hackathon-a44fb54e98f7) give us a good hint on extensions potential.

Note that idea #96 might be the first guinea pig of extensions.

Goal Date: 3 weeks after beginning

## Dates

Iterations will be defined based on specification and team feedback.

## Exit criteria

* current API state is documented
* mockups and documentation of proposed changes of extensions are available and have been discused by team
* extensions API is implemented and documented
* an extensive example is available

## Success Metrics

- 2 internal extensions shipped 
- 3 external extensions shipped
- quality of documentation recognized: few support request related to extensions

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).