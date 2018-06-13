---
id: 280-discoverable-trusted-server-nodes
title: Discoverable And Trusted Server Nodes
status: Draft
created: 2018-06-07
category: core
lead-contributor: adambabik
contributors:
    - richard-ramos (Smart Contract Developer)
exit-criteria: yes
success-metrics: yes
clear-roles: no
future-iterations: yes
roles-needed:
    - Go Developer
    - Clojure Developer
okrs:
    - "[PO]: Objective: Messaging is reliable"
    - "[P2]: KR: Cluster can handle 500 concurrent users"
---

## Summary
The idea here is to provide a way to make Mail Server nodes discoverable and trusted. This should work seamlessly for the end user.

## Product Overview
Currently, Mail Servers (and other planned server nodes like Push Notification servers) need to be hardcoded in the app code. It's possible to provide your own Mail Server in the app settings but that's not a scalable solution and it does not solve all issues.

The outcome of this swarm are decentralized and discoverable Mail Servers which will initially be managed and trusted by Status. The client will still accept user's custom Mail Servers.

In the next iterations, we may work on a solution to allow external providers to submit their own Mail Servers into the cluster and allow end users to accept these resources as trusted. The list of providers and their resource could be managed by [Token-Curated Registries](https://docs.google.com/document/d/1BWWC__-Kmso9b7yCI_R7ysoGFIT9D_sfjH3axQsmB6E), for instance.

## Product Description
The work in this swarm can be divided into three areas:
- (Infra) making Mail servers discoverable,
- (Smart Contract) writing a smart contract to keep track of trusted Mail Servers,
- (Client) mechanism of verifying whether a discovered Mail Server is trusted.

The smart contract should implement the complete interface that will allow managing providers and their resources. The client will have an option to decide which providers it trusts. Status will be a default provider and by default the app will trust it.

Due to the fact that all Mail Servers are supposed to be equal and independent (in other words, they should store the same messages, possibly in different order though), we will be able to remove all hardcoded Mail Server addresses from the client and rely only on discovered Mail Servers. This will allow Status to dynamically scale number of resources depending on the usage.

**Note** Important thing is that this solution should be flexible for other server nodes. It should be easy to introduce new resources, as long as a particular group of servers is discoverable, the client verifies them using a smart contract and can choose arbitrary one to continue.

## Requirements & Dependancies
1. (Optional) Before this swarm starts, https://github.com/status-im/status-go/issues/1006 should be resolved in order to avoid working on the same piece of code.

## Minimum Viable Product

Goal Date: TBD

1. [ ] A smart contract that keeps track of providers and Mail Servers,
1. [ ] Discoverable Mail Servers,
1. [ ] Requests for messages are securely encrypted to provide confidentiality,
    * As devp2p packets are encrypted and this is P2P communication, the question is should we additionally encrypt Whisper messages with a Mail Server's public key?
1. [ ] A client that collects discovered Mail Servers and verifies if they are trusted using the smart contract. Verified Mail Servers are added to the pool and a random one is selected to use.
    * We keep the option to add user's own Mail Server addresses.
1. [ ] Make sure this solution is flexible and can work with other server nodes.

## Iteration 1 (Optional, TBD)

Goal Date: TBD

1. [ ] Allow custom providers to register their Mail Servers (Status as a curator?),
1. [ ] Allow users of the app to select trusted providers
    * [ ] A new design of a screen needed.

## Success and exit criteria

1. Mail Servers are not hardcoded in the client but are discovered using Discovery V5 protocol and verified using a smart contract,
1. (Optional) External Mail Server providers can register themselves and users can decide if they trust their resources (a list of providers is curated by Status).

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
