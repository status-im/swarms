# Tribute to Talk Specifications

There are two layers to TtT:
- Anti-spam 1:1 economic filtering. This is what we are building in the MVP.
- Monetization of a user’s time & attention with added features such as escrow, conversation time-out/limitations, etc.

The MVP will use a simple registry contract. For future iterations we will need use additional contracts. Research on contract options: https://notes.status.im/SGNQNVEATuChD7xXHybyWA 

## MVP
_Anti-spam 1:1 economic filtering_

_Goals:_ Deliver on white paper promise to SNT holders. Boost SNT utility. Provide basis for personal time/attention monetization through anti-spam 1:1 economic filtering.

### User Stories

_Summary:_ Anyone can set a “tribute to talk.” Others can pay this tribute via a normal wallet transaction in order to open up a conversation with that individual. Once they’ve paid the user tribute, they are added to their contacts. There is currently no way for a contact to be removed. This might be a blocker that we should tackle first.

_User A_
- As a user who values privacy, I would like to set a minimum required tribute to talk to me in order to prevent 1:1 spam. 
- I would like to change the tribute required to talk to me.
- I would like to remove the tribute required to talk to me. 

_A flows_<br>
<img src="https://github.com/status-im/swarms/blob/master/ideas/314-tribute-to-talk/mvp-user-a.png" width=350>

_User B_
- As a user looking to make new contacts, I would like to pay tribute so that I can message User A.

_B flows_<br>
<img src="https://github.com/status-im/swarms/blob/master/ideas/314-tribute-to-talk/mvp-user-b.png" width=350> 

### Feature Branding

Maintaining “Tribute to Talk” for naming to draw connection to white paper.

Treating this MVP as an early version of white paper Tribute to Talk (rather than separate feature).

### Open Questions
- Identifying TtT transactions in wallet history. Can we customize this?
- Is it a full wallet flow when setting/editing/removing a Tribute? Do we want to minimize this?
- How to handle `Learn More` screen (provided for in designs)
- How to mitigate the awkwardness of trying to contact someone you know, when they have a tribute set? Options: (1) Contact request feature (WIP) to circumvent TtT; (2) Refund TtT fee for someone I know. 

### Dependencies/Blockers
- `Remove from contacts` option would be helpful to remove people. Core team will not be able to work on this soon; if wanted, chat can own.
- ENS names should be supported by default in chat to boost feature usability. Why would I pay tribute to an anon name?

### Designs
[Figma link](https://www.figma.com/file/aS1ct66VQ6V0cio7vSqS8UoG/Chat?node-id=1319%3A13403 )
 
### Measurement & Tracking

- Number of Tributes set
- Number of accounts w/ Tribute set
- Avg. Tribute value (?)

## Contract Requirements

There are 3 functions:
- `set tribute`, which takes the tribute amount and sets it as tribute for the address
- `remove tribute`, which removes the tribute for the address
- `check tribute`, which takes an address and returns the tribute amount

### Potential Risks

1. JS client & NIM client must also recognize the Tribute registry so that people can’t skirt around the requirements of the contract/TtT settings (feature parity across clients). 
<br>_Mitigation:_ Discuss w/ other clients. It’s to the other client’s detriment not to implement TtT. If user on main client is using it, he/she won’t be able to exchange messages with clients that aren’t. The feature is easy to implement. 

2. Privacy risk: addresses with TtT set will be accessible from the registry contract. Hypothetically one could create a db from these addresses, and begin to pick out potential payments for TtT from other addresses.
<br>_Mitigation:_ Use ZK-SNARKS for payment privacy.

### Migration Strategy

The registry contract will be kept simple specifically to prevent us from needing to upgrade it in the future. When advanced features such as escrow are eventually built, they will be done with new contracts that leverage the existing registry.

## Future Iterations

### User Stories

_User A_
- As a user with a tribute set, I would like to review requests made to talk to me by people who have made deposits.
- I would like to respond to a message in order to accept the tribute.
- I would like to ‘ignore’ or ‘pass’ on a message to return the user’s SNT.
- I would like the option to “whitelist” people in my contacts so that they do not have to make a tribute to speak with me.
- I would like to forfeit a tribute made to me from people I may know, who are not yet in my contacts.
- I would like to close the conversation with someone who has paid tribute after a certain amount of messages/time. 

_User B_
- As a user who has requested to paid tribute to talk to User A, I would like the option to revoke my tribute if User A has not responded or if I’ve changed my mind.

