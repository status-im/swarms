---
id: 276-fast-discovery
title: 'Fast discovery'
status: Draft
created: 2018-06-22
category: core
lead-contributor: dshulyak
contributors:
    - dshulyak
exit-criteria: yes
success-metrics: yes
clear-roles: yes
future-iteration: no
roles-needed:
    - 'Go Developer'
okrs:
    - '[PO]: Objective: Messaging is reliable'
---

## Preamble

    Idea: #276-fast-discovery
    Title: Fast discovery
    Status: draft
    Created: 2018-06-22

## Summary

Previously we added support for discovery v5 in status client.
While it allows us to discover peers in under 5 seconds, and consumes on average 50kb of traffic (sum of inbound and outound).
This picture completely changes with more concurrent clients. If 100 clients joins simultaneously discovery becomes
very slow and not reliable. For instance it can consume as much as 2mb in 10s while not finding required number of peers.

## Swarm Participants

- Lead Contributor: dshulyak

## Product Overview

We will implement protocol that takes into consideration problems mentioned in summary of this document.

Statusd process will register both in discovery v5 and rendevouz (defined in this spec) discovery protocol.
This way we will also preserve backward compatibility with beta release.

### Compatibility with ethereum network

We want to allow other peers to register in status network, and those peers are not necessarily running.
our software (for example they can run wnode provided in go-ethereum repository). To make it possible we
can go two ways:

1. Convince them to use new discovery protocol in addition to original discovery based on kademlia.
This is preferred way, but might be hard to achieve.
2. Implement a proxy that will search for target topics and create enodes for every node with particular
topic.

### User Stories

Devices will be able to connect with new peers without spending noticeable amount of time and traffic.

### Requirements & Dependencies

No.

### Security and Privacy Implications

Same properties.

## Protocol implementation.

### Protocol

https://github.com/libp2p/specs/blob/4059338ff0f90835ed953e1eb4c2beb703cc04d9/rendezvous/README.md

For details please see that spec. but essentially it just implements 3 RPC call.
1. discover peers
2. register peer for a particular topic
3. unregister peer (under consideration. we will need to )

### Peer definition

We need to share more information than public key of the peer and information
for ip connection. There is a format suitable for sharing any
key=value information. You can learn more about ENRs here:

https://github.com/ethereum/EIPs/blob/master/EIPS/eip-778.md

One of the goals is to advertise provider signature.
For details see discoverable mail server swarm.

### Transport layer

We are free in the choice of the transport. I suggest to use go-stream-muxer
for negotiating connection type (https://github.com/libp2p/go-stream-muxer).
With a preference towards rlp stream over tcp connection.

### Storage layer

In the end we will want to persist peers and remove them after ttl. But
considering that our ttl will be low enough, maybe 5m-10m, we can keep them
in memory in first iteration.

Peer will have to be removed from storage (disk/memory) after ttl.

Storage layer will have to support two types of queries:
1. get N random peers from database that registered with topic X
2. purge peers that are older than now - ttl

Again, in first iteration we can just loop over all rows in whichever store.
But better to select store that allows to make queries based on 2 primary indexes
(in our case topic and ttl).

### Peer validation

Basic validation will have to ensure that ENR object is signed by the key
provided in ENR (signature is a part of ENR).

## Dates

### Iteration 1

2018-07-05

1. Implement transport layer
2. Implement protocol primitives.

### Iteration 2

2018-07-12

1. Implement protocol using primitives and transport.
2. Implement persistance layer.
3. Implement fast discovery server (bootnode).

### Iteration 3

2018-07-19

1. Integrate fast discovery client into status-go.
2. Write new scale test using status-scale framework. 200 concurrent nodes should be
able to discover 5 peers in under 5 seconds (dirty time) and spending no more than ~3kb of traffic.

## Success Metrics

1. Latency for discovering 10 peers will be under 1s (without counting rtt)
2. Low traffic overhead. ideally there will be almost no overhead,
so if 1 peer is 300b of data (dictated by ENR), bunch of 10 peers, in theory, will be ~3kb + some protocol meta information.

## Exit criteria

1. Discovery for mobile devices works as described in success metrics.

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
