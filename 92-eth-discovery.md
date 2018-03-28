## Preamble

    Idea: #92-disc-v5-research
    Title: Research Ethereum discovery protocol
    Status: Draft
    Created: 2018-03-12

## Summary
Discovery protocol is essential for long-term scaling of the Status app. It will improve security and reliability of the app and prepare it for the beta launch. 

## Swarm Participants
- Lead Contributor: @adambabik
- Testing & Evaluation: TBD
- Contributor: @dshulyak
- Contributor: TBD

## Product Overview
Discovery protocol will allow us to dynamically change the number of peers in our cluster and also distribute the peers among various providers and countries without rebuilding the app itself, hence improving security and reliability.

The biggest challenge may be increased CPU and network usage. This needs to be carefully measured as it may lead to proposing some discovery protocol changes for light nodes.

### Product Description
This is a research swarm. It must provide answers to the following questions:
- [ ] CPU/network increase usage. How does it change in absolute and relative values? How to reproduce the measurement?
- [ ] Can we turn on and off discovery protocol when the node is running?
- [ ] Can Discovery V5 protocol carry more information than protocol name and version? How can we distinguish Light Whisper nodes or Whisper nodes with MailServer capability? Notice that revealing this information (like Light Whisper node) may increase a chance to reveal the peer identity. The fact that we don’t want mobile phones to be each other peers raises this question.
- [ ] How to make sure that connecting to the cluster will be fast? This is more a cluster question, i.e. how to autoscale cluster so that it can quickly connect new peers.
- [ ] How to make sure that there are always at least N peers with given protocol support. For instance, we always want to have at least some Whisper and some LES peers connected. Also, we want to always have at least one Whisper peer with MailServer support.

### Requirements & Dependencies
The discovery protocol should be testable locally with Docker, but for some more extensive tests, we may utilize a public cluster.

### Minimum Viable Product
Goal Date: TBD

Description: 
1. All questions described in Product Description are researched and answered,
1. It's possible to start statusd and Status App with DiscV5 instead of static nodes (switch between them with a flag would be great),
1. There is an automated way to run performance and resources consumption tests within an isolated environment.

## Success Metrics
1. It's possible to start statusd/Status App with bootnodes and DiscV5 enabled,
1. It's possible to discover LES/2, Whisper and MailServer nodes via DiscV5 (nodes with the same protocol but different capabilities),
1. Resources consumption is not higher than 20% compared to static nodes.

## Links
* https://github.com/fjl/p2p-drafts

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

