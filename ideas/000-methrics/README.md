---
id: 000-methrics
title: Methrics
status: draft
created: 2018-05-17
category: research
lead-contributor:
contributors:
    -
    -
    -
exit-criteria: no
success-metrics: no
clear-roles: no
future-iteration: no
roles-needed:
    - QA
    - PM
    - UXR
    - Clojure dev
    - Go dev
    - Contracts dev
    - Designer
    - Community
---

## Preamble

    Idea: 000-methrics
    Title: Methrics
    Status: Draft
    Created: 2018-05-17
    Requires:
    Replaces:

## Summary

A decentralized and anonymized approach to application metrics

## Swarm Participants

TODO

- Lead Contributor:
- Evaluator (defaults to lead contributor):
- Contributor:
- Contributor:
- QA:
- PM (required for user-facing):
- UXD/R (required for user-facing swarms): @patrick, @hester

## Product Overview

Striking the balance between delivering a beautiful app and respecting the privacy of the user remains a task fraught with difficult tradeoffs.

One such tradeoff is the collection of application metrics from users as they use the application - in that process, people have little insight into what is being collected and how it may be used, within or outside of its intended purpose.

The decentralized open metrics idea is an experiment to explore fully transparent metrics collection where the data is available to the user and to anyone else as it's being collected, with minimal leakage outside of its stated scope.

Metrics are generally not limited to data that is explicitly generated for the purpose of tracking, but also include other traces that the user might leave behind as they navigate the application, such as transactions and dapp assets hosted on web sites, and part of the product idea is to explore ways to expose and break down these trails for the user such that they become accessible and understandable.

To explore as part of this project is how to ensure that data retention laws such as GDPR are accounted for.

### User Stories

* I want to understand what trails I leave behind when using the application, including blockchain transactions and dapp interactions, and how these may be combined
* I want to contribute to the development of Status anonymously by letting the application collect tracking data
* I want to limit specific types of data that Status collects when I use the application
* I want to export the data conveniently for my own analysis
* I want meaningful information that I can make sense of, opposed to datapoints

### Requirements & Dependencies

* Current tracking examples
  * [Example mixpanel data](https://gist.github.com/chadyj/fb95dec5e557116d3715cb8facf6dae1#file-metrics-export-json)

### Security and Privacy Implications

Guideline: if not a primary necessity for application to            perform its tasks, should it be there?

The security and privacy implications of enabling tracking in any application are significant - there are many things that can go wrong when creating a corpus of behavioral data, specially when valuable assets are involved.

* Reliance on vendor
  * IP address disclosure
  * Vendor incentives to collect more than stated
  * Vendor may be hacked or bought out, transferring the data to another entity
* Radical openness
  * If we're uncomfortable exposing our data publically we should not be collecting it
* Risks
  * Unintended leakage of data
  * Correlation between tracking data and other events
    * Liability for status in case of fallout from such correlations
  * Doxing / deanonymization
  * No way of turning off, once decentralized
* Filtering
  * Allowing user to selectively share data - for example, chat ok but transaction not
* Community
  * Community members might prefer that data is not fully public    but only available to trusted parties

### Related products

* [statsd](https://codeascraft.com/2011/02/15/measure-anything-measure-everything/) - metrics collection with a centralized server
* [mixpanel](https://mixpanel.com) - Product analytics
* [supermax](https://www.supermax.cool/) - Blockchain/smart contract log visualizer
* [shiny](http://shiny.rstudio.com/) - Data analysis in R
* [thegraph](http://www.thegraph.com/) - A decentralized query protocol for blockchains

### Background information

* [Slack discussion on privacy](https://status-im.slack.com/archives/C9R0TSTM2/p1523263085000070)

## Dates

TODO
Scope - months?

### Minimum Viable Product

### Iteration 1

* Anonymous data collection and storage
  * Send metrics over whisper? Good for anonymity, dogfooding protocol
* Documentation / FAQ
* Community engagement and validation of the idea
* Build connections to renowned privacy advocates who might vouch for the approach

### Iteration 2

* Coverage for a broad range of current mixpanel statistics,
  such as Daily Active Users (TODO: list them)
* Own data is discoverable by user, if possible
  * TODO: if it's very anonymous, can we actually make this distiction?

### Iteration 3

* Data exploration support
  * Custom front-end or pre-loaded panels in existing analyis platform like mixpanel, graphana, jupyter, Shiny/Rstudio?
  * Help user understand public traces such as blockchain transactions and tracable dapp requests (malicious dapps?)

## Success Metrics

* X% users are comfortable downloading the application, even though it contains tracking
  * we can measure with surveys and in-person UXR testing
  * TODO: how to not lose out on / measure privacy sensitive minority
* X% of users opted in/out of tracking
* 90% of users who do opt in to metrics tracking understand what is being tracked
* 90% of users who opt in know where to go to see aggregated data exploration
* Collected data used to drive at least 3 significant UX improvements
* Broader recognition from community that Status sets the standard for data usage transparency and security (TODO: measure?)

## Exit criteria

* Status app no longer connects to mixpanel or similar third parties
* Status app supports publishing a broad range of events and metrics
* Dashboards launched for data exploration
* Source data can be exported in machine-readable format

## Supporting Role Communication

* Community manager - It might not be clear enough what the limit is of what we are collecting and 'public data' might give an allergic reaction altogether. Organize a session with some active community managers to discuss a mock of a public dashboard and get their feedback to see what FAQ we need to include.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
