---
id: #314-tribute-to-talk
title: Tribute to Talk
status: research
lead-contributor: Eric/Rachel
contributors:
    - Eric
    - Vitaliy
    - Tetiana
    - Hester
    - Richard
    - Rachel
budget:
- actual: xxx
- estimate: yyy
- currency: ETH
---


TtT Swarm Proposal
=

## Summary and Goals

The Tribute to Talk swarm will deliver SNT based anti-spam mechanisms in accordance with the white paper.

It allows individuals to monetize their time and attention by setting minimum required deposits to message them.

## Contributors

- Eric 
- Vitaliy 
- Maciej
- Richard
- Tetiana 

(+ Janitor swarm)

## Communication

`status channel`: #314-tribute-to-talk
`sync schedule`: weekly, during core chat sync

`Pivotal link`: https://www.pivotaltracker.com/projects/2231830

`Meeting notes`: https://notes.status.im/weekly-chat-sync-agenda

`Research notes`: [Research notes](research.md)


## Research

`Timebox`: wrap by 21/12/18

`Previous work`:
An initial version of Tribute to Talk was partially developed and designed back in April/May. 

The existing smart contract documentation is [here](https://github.com/status-im/contracts/blob/096-tribute-to-talk/TributeToTalk.md#deciding-the-outcome-of-a-chat-request). Written by Richard Ramos (@rramos).

The previous designs were shared in these [github issues](https://github.com/orgs/status-im/projects/27).

Ongoing design exploration [available here](https://www.figma.com/file/aS1ct66VQ6V0cio7vSqS8UoG/Chat?node-id=1319%3A13403)

Changes to the smart contract may be required in order to meet specs defined in this swarm.

`Potential user stories for MVP`:
- As an influential person, I want to set a minimum required deposit to speak with me on Status.
- I want to review incoming requests from people who have made deposits.
- I want to read the sender's message before accepting or ignoring their request. 
- I want to receive payment from the sender when I respond to their request. 
- I want the option to close the line of communication again afterward.
- I want the option to waive the deposit and still accept the message.
--
- As a fan of some influential person, I want to offer an SNT deposit in order to message that person.
- I want to be notified when the person has accepted my message and sent a reply.
- I want to receive my SNT back if the person does not respond to my message.


`Research questions`:
- Is this feature comparable to any other anti-spam mechanisms? Will people understand the concept? What UX references are relevant?
- What features does the current smart contract support?
- Do we need to conduct an audit on the contract before launch?
- Identifiy incompatibilies with other features/issues—e.g. inability to remove contacts once added, overlap with core issues, etc. 

## Latest

**2/1/19**
- First version of UI is complete and design reviewed
- Changes required here: https://github.com/status-im/status-react/pull/7304#issuecomment-459337181

**Update 7/1/19**<br>
*Top line: The Tribute to Talk MVP will deliver 1:1 spam prevention. The contract will manage tribute settings only. There will be no escrow; payment will be handled through a normal SNT transaction. There are constraints that force this decision, but it's also the simplest possible implementation.* 

User A = Person sending tribute<br>
User B = Person accepting/rejecting chat request

[Eric]
So far we have discussed 2 different options:
- contract 1 is a very simple contract that is only used as a index of tributes required to contact users. The tribute is payed with a regular transaction which is slightly better for privacy but requires A to pay before talking to B without an escrow. I don't think there would be a need for a security audit for this one because the contract itself doesn't handle any value.

- contract 2 is more complex and acts as an escrow. B needs to accept the tribute to be paid. However this just look like an additional step in the UX flow that doesn't really bring any guarantees because it can't be proven that the B actually replied or provided a meaninful reply.

[Continued here](https://notes.status.im/SGNQNVEATuChD7xXHybyWA?edit)


## Specification

[Read spec](https://github.com/status-im/swarms/blob/master/ideas/314-tribute-to-talk/specs.md)

## Implementation

## Maintenance

## Copyright

Copyright and related rights waived via CC0.
