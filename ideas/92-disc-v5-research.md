## Preamble

    Idea: #92-disc-v5-research
    Title: Research Ethereum Discovery V5 Protocol
    Status: In Progress
    Created: 2018-03-12

## Summary
Discovery protocol is essential for long-term scaling of the Status app. It will improve security of our cluster and reliability of the app and prepare it for the beta launch.

## Swarm Participants
- Lead Contributor: @adambabik
- Testing & Evaluation: @adambabik (unless someone else would like to take over)
- Contributor: @dshulyak
- Contributor: @themue

## Product Overview
Discovery protocol will allow us to dynamically change the number of server peers in our cluster and also distribute the peers among various providers and countries without rebuilding the app itself, hence improving security and reliability.

The biggest challenge may be increased CPU and network usage. This needs to be carefully measured and we may end up with proposing some protocol changes.

### Product Description
This is a research swarm. It must provide answers to the following questions:
- [ ] CPU/network increase usage. How does it change in absolute and relative values? How to reproduce the measurement?
- [ ] Can we turn on and off discovery protocol when the node is running?
- [ ] Can Discovery V5 protocol carry more information than protocol name and version? How can we distinguish Light Whisper nodes or Whisper nodes with MailServer capability? Notice that revealing this information (like Light Whisper node) may increase a chance to reveal the peer identity. The fact that we don’t want mobile phones to be each other peers raises this question.
- [ ] How to make sure that connecting to the cluster will be fast? When the app goes to the background, does it take significantly more time to find peers? Do we need to use cache? From the cluster perspective, how to autoscale cluster so that its free capacity is always high?
- [ ] How to make sure that there are always at least `N` peers with given capabilities? For instance, we always want to have at least `K` Whisper, `L` MailServer and `M` LES peers connected.

### Requirements & Dependencies
The discovery protocol should be testable locally with Docker, but for some more extensive tests, we will utilse a Docker Swarm cluster.

### Minimum Viable Product
Goal Date: 2018-04-08

Description:
1. All questions described in Product Description are researched and answered,
1. It's possible to start statusd and Status App with DiscV5 enabled instead of static nodes (switch between them with a flag would be great),
1. There is an automated way to collect CPI and network usage metrics in an isolated environment.

#### Exit criteria

1. Assess if DiscV5 is a viable protocol to replace static nodes.
1. If so, there is a list of issues that we should work on to further improve DiscV5 usage in the Status app and in the cluster (this may be realized as next iterations or a new swarm).

## Success Metrics
1. Connecting to the network for statusd/Status App via DiscV5 is successful in at least 99% of tries,
1. It's possible to discover minimal number of LES/2, Whisper and MailServer nodes via DiscV5 within 15 seconds without cache and in 5 seconds with cache,
1. Resources consumption (CPU and network ingress/egress) is not higher than 20% compared to static nodes.

## Links
* https://github.com/fjl/p2p-drafts

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

