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

`Meeting notes`: https://notes.status.im/weekly-chat-sync-agenda

## Research

`Timebox`: wrap by 21/12

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


## Specification

## Implementation

## Maintenance

## Copyright

Copyright and related rights waived via CC0.
