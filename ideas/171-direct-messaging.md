---
id: 171-direct-messages
title: Direct messaging
status: Draft
created: 2018-04-28
category: core
contributors:
    - dshulyak
---

## Summary

in plain words this scheme proposes to establish single tcp connection between
two devices.

users that don't need to mantain deniability with selected friends will have an
option to trade that off for lower latency, higher reliability and higher
troughpout, with lower bandwith usage.

TODO maybe a diagram explaining how regular whisper traffic goes and how this
scheme will change that

## Product Overview & Description

Below is the detailed draft of the proposal, certain details such as exact code
that needs to be changed were avoided.

There are several prerequisites:
- one of the devices must have public endpoint or coordinate nat hole-punch.
  this device will act as initiator, and another device will connect to it
  TODO make a diagram explaining this
- to initiate such connection device will have to be connected to whisper network.
  details below

Such selected members must be trusted in the sense that they will have to:
- share public ip or nat endpoint, because connection will be *direct*
- disable expiry validation, e.g. it will be possible for such trusted
  members to send old envlopes (see below why is it also important part of this scheme)

Scheme for connection initiation (TODO diagram here) :
1. both devices are already added as contact
2. device A ensures that he has public ip or succesfully made a nat hole
   before performing next steps
3. device A sends its own enode (temporary public identity and public ip) to device B.
   TODO there is an alternative using discovery which is less efficient
4. device B checks locally if device A is in the list of "friends"
5. if false such message is simply ignored and device A can be even removed
   from contact list
6. if true device B adds received enode as trusted and initiates connection with
   device A by adding it as static peer
7. from now on all communication between device A and device B will be direct

What is direct and why?
1. single tcp connection, e.g. the best possible latency in the network
2. traffic is still encrypted, in a usual way asym or sym
3. whisper pow doesn't need to be computed
4. messages expiry mechanics are disabled and thus drop because of the time desync
   is not even possible

What about offline traffic?
every peer will store pending traffic for it's friend. example:
1. device A goes offline
2. device B sends 10 messages while device A is offline.
   this 10 messages stored on device B
3. device A goes online and receives all messages

i want to make a point that no additional storage is wasted as history
is usually stored on both devices.

and history is always safe when atleast one peer will have old device when
another peers connects with it.

## Benefits

1. get the best possible latency for messages in the network.
   e.g x2-5 reduction with current latency
2. no use of public infra for anything but initial connection negotiation
   no wasted money for communication with friends
3. 100% reliability
   all communication is happening over simple tcp connection
   thus if application protocol is reliable - there is no place for lost messages
4. keep the same or slightly lower cpu consumption
   pow computation will be disabled.
5. lower bandwith usage as there will be no duplicates in such communication
   TODO understanding why requires understanding of whisper routing

## Tradeoffs

1. This scheme can be used only between trusted peers.

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).