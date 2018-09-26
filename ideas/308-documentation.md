---
id: 308-documentation
title: Documentation
status: draft
created: 2018-09-26
category: multi-category
lead-contributor: andytudhope (Andy Tudhope)
contributors:
    - easye
    - rachelhamlin
    - jeluard
    - hazel
    - Jakub
exit-criteria: no
success-metrics: 
    - re-styled according to Hazel's designs to match web-refresh
    - global header navigation to move across all Status domains
    - clear documentation that is easy to contribute to and manage
    - kept up-to-date month on month, with at least 5 contributions and 2 tutorials
    - clear user journeys established once content is flowing
clear-roles: no
future-iteration: yes
roles-needed:
    - Go team janitor
    - Clojure team janitor
    - Nimbus janitor
    - Hardwallet janitor
    - Technical tutorial writer (perhaps video too?)
    - Communication janitor
    - UXR janitor
okrs:
    - Developer Relations (get 240 monthly visit to documentation)
---

## Preamble

Idea: 308
Title: Ducmentation
Status: Draft
Created: 2018-09-25

## Summary

We need to manage documentation better, in accordance with the findings in [ethreport.info](https://ethreport.info). Documentation has been a long-running battle at Status because our codebase moves so fast, but with a good team managing it, with clear responsibilities and an easy contribution pipeline for anyone to edit and update our docs, we can become the best-documented project on Ethereum.

## Swarm Participants

I have called everyone I need `janitors` rather than `leaders` or any other term in line with Swarmwise, the summary of which you can find [here](https://docs.google.com/document/d/12Qema_8hPWuzDhqb8Tim66QZleVFcMXkVWICyH4nIT8/edit). We need people to serve their teams, clean up after all the amazing work that is being done and ensure that it is properly documented at all times.

- Lead Contributor: [@andytudhope](https://github.com/andytudhope)
- Contributor: [@easye](https://github.com/easye)
- Contributor: [@rachelhamlin](https://github.com/rachelhamlin)
- Evaluator (defaults to lead contributor):
- Contributor: [@jakubgs](https://github.com/jakubgs)
- QA:
- PM: [@rachelhamlin](https://github.com/rachelhamlin)
- UX(R):

## Product Overview

We have changed our documentation to use the same theme as the [Embark docs](https://embark.status.im): [hexo.io](https://hexo.io). All technical documentation will use this theme going forward, and we will style it according to the designs created by Hazel and Andrei. We will also implement a global header navigation, so that it is easy to move between all the different parts of Status, no matter where you are in our online web of information.

We will also set up [the current repo](https://github.com/status-im/docs.status.im) so that the `master` branch serves to `docs.status.im` and the `develop` branch serves to a staging site. That way, anyone can commit directly to `develop`, see the changes themselves, and submit a link for review so that the process can run as smoothly and quickly as possible.

### Problem

Documenting all the disparate parts of Status has always been a challenge. Rather than coming up with specific user journeys when we still have so few actual users seems to be the wrong way to go about building a great documentation site. I think we should rather make it as easy as possible for people to contribute to a really good-looking documentation site, and then craft user journeys out of the content we see generated across the organisation.

With a good global navigation, the same theme as our other sites, and an easy-to-use and review pipleline, we can make sure that each project can easily maintain their own documentation adn that Status remains - as a whole - the best documented project in addition to the most active developer one. We need to achieve this is in the service of mass adoption of Ethereum because good education precedes mass use and acceptance.

It also contributes greatly to many of our [principles](https://our.status.im/our-principles/), especially `openness`, `inclusivity`,`transparency`, `decentralization` and `continuance`. 

### Technical solution

- Style hexo.io to Hazel and Andrei's new designs. 
- Work with Jakub to set up the pipeline detailed above with `master` and `develop` serving to different places so that we don't end up with the mess of branches currently accumulating there. 
- Set up the `Edit on GitHub` button on each page to edit directly on `develop` and build the changes submitted so that it's automatic to see the effect of your changes as a contributor.
- Think about how we can use Swarm and/or IPFS to serve our docs.
- Think about incorporating user feedback mechanism like the `SNT clap` @exiledsurfer is planning for the blog.

### User Stories

- I want to understand how to build Status easily so I can contribute to the core codebase.
- I want to understand how to build Desktop easily so I can contribute to the core codebase.
- I want to understand how I can use Status to connect to my DApp.
- I want to understand how I can leverage the unique features of Status in my DApp.
- I want to add my DApp to the Status store and optimise it for Status.
- I want to understand the research happening on Nimbus and how to contribute (will be split into it's own site when there is enough content, using the same theme).
- I want to understand the technical details of Status' protocols: how does Whisper work? how does X3DH key exchange and PFS work? What is different about `status-go`? How does LES and ULC work?
- How can I use SNT? From voting to Tribute to Talk to how to run a mailserver (this all needs to be detailed still).

### Requirements & Dependencies

Final design from Hazel and set up with Jakub.

### Security and Privacy Implications

None at the moment. Will follow up with @corpetty though.

## Dates

Final Design and Pipeline Setup
2018-09-28

Detailed explanation for CCs on blog
2018-09-29

Re-style omplete
2018-10-10

### Minimum Viable Product

Site that uses hexo.io to generate pages, is styled according to our designs, and has a slick build pipeline that anyone technical can easily contribute to. Some semblance of a structure, with enough room to evolve into what it really needs to be.

## Success Metrics

- 4-8 new contributions a month
- 2-4 updates a month to existing docs
- 5 tutorials fully written by November
- Technical spec for whisper complete and accessible
- Technical spec for PFS complete and accessible
- 3 clear Nimbus docs on what it is, what the state is now, and how to contribute
- Lots more comments like the one in slack on 2018-09-26 about the doc Julien shared being "exactly what I needed!"

## Supporting Role Communication

We'll need help from Michael and Jonny to get the really good docs out and communicated across the community, especially tutorials.

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

