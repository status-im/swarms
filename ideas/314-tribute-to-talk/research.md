Tribute to Talk Research
===

*Top line: The Tribute to Talk MVP will deliver 1:1 spam prevention. The contract will manage tribute settings only. There will be no escrow; payment will be handled through a normal SNT transaction. There are constraints that force this decision, but it's also the simplest possible implementation.* 

User A = Person sending tribute
User B = Person accepting/rejecting chat request

[Eric]
So far we have discussed 2 different options:
- contract 1 is a very simple contract that is only used as a index of tributes required to contact users. The tribute is payed with a regular transaction which is slightly better for privacy but requires A to pay before talking to B without an escrow. I don't think there would be a need for a security audit for this one because the contract itself doesn't handle any value.

- contract 2 is more complex and acts as an escrow. B needs to accept the tribute to be paid. However this just look like an additional step in the UX flow that doesn't really bring any guarantees because it can't be proven that the B actually replied or provided a meaninful reply.


# [Contract 1: TTT with regular transactions](https://github.com/status-im/contracts/blob/314-tribute-to-talk/contracts/communication/MessageTribute.sol)
- Is the tribute treated as a deposit and held in escrow? How does the contract handle it?
No, the tribute is payed with a regular transaction
The contract is only used to set a TTT and check what the tribute is to contact a user
A sends a regular SNT transaction to B (can be more than the TTT to hide the fact that it is a tribute)

- What if User B ignores or rejects a request? How can User A get their money back? Does this happen automatically after a certain amount of time?
A doesn't get their money back, nothing happens

- Can we build in a cancelation action for User A?
No

- Is User A added to User B's contacts once User B accepts the tribute?
Yes but there is no accepting the tribute, if a tribute has been payed B sees A messages otherwise they are not bisible

- Is it required that User B send a reply to accept the tribute? Can it be required? 
No, can't be required

- What if User B wants to end the conversation? How can they limit the amount of contact? 
We could have a built-in message type that would inform A that he needs to pay a tribute again to end the conversation
B can increase his TTT to limit the amount of contacts.



# [Contract 2: TTT through contract](https://github.com/status-im/contracts/tree/096-tribute-to-talk/contracts/communication/MessageTribute.sol)
- Is the tribute treated as a deposit and held in escrow? How does the contract handle it?
No. Contract only deals with signed messages, and transfer is performed once the receiver receives a requestor signed message

- What if User B ignores or rejects a request? How can User A get their money back? Does this happen automatically after a certain amount of time?
A could get their money back as the contract helds the money until B calls receiveTribute but I don't think the contract supports cancellation
There could also be an expiration for the TTT after which the tribute is returned to A without a response from B

Funds transfer are performed only when the receiver invoke `grantAudience` within a time limit. The receiver has the option to accept the request and optionally waive the fee. This contract version also requires that the requestor sets an allowance of SNT for the fee amount in order for the trasnfer to be successful. There's no cancelation mechanism.

- Can we build in a cancelation action for User A?
yes but the contract does not supports it right now

- Is User A added to User B's contacts once User B accepts the tribute?
yes

- Is it required that User B send a reply to accept the tribute? Can it be required? 
no we can only require that user B calls `grantAudience` but there is no way to tell if he actually gave a reply without arbitrage

- What if User B wants to end the conversation? How can they limit the amount of contact? 



# [Contract 3: TTT through contract autoaccepting fee](https://github.com/status-im/contracts/blob/096-tribute-to-talk-autoaccept/contracts/communication/MessageTribute.sol)
- Is the tribute treated as a deposit and held in escrow? How does the contract handle it?
No. Fee is sent immediatly to the receiver

- What if User B ignores or rejects a request? How can User A get their money back? Does this happen automatically after a certain amount of time?
User A will not get back his funds. The function `payTribute` will transfer the funds immediatly, and User B can then decide if he replies back or not.

- Can we build in a cancelation action for User A?
Cancellation in the UI would be possible for User A while they're still deciding whether to send the tribute or not. Once the fee is sent, there's no cancelation possible.

- Is User A added to User B's contacts once User B accepts the tribute?
yes

- Is it required that User B send a reply to accept the tribute? Can it be required? 
No

- What if User B wants to end the conversation? How can they limit the amount of contact? 



# [Contract 4: TTT through contract, allowing receiving/rejecting requests](https://github.com/status-im/contracts/blob/314-tribute-to-talk-rejectable/contracts/communication/MessageTribute.sol)
- Is the tribute treated as a deposit and held in escrow? How does the contract handle it?
No, The contract has functions for users to request/send SNT. A uses `sendTribute` and B uses `receiveTribute`

- What if User B ignores or rejects a request? How can User A get their money back? Does this happen automatically after a certain amount of time?
Transfers are done only when valid signed messages are received. 

- Can we build in a cancelation action for User A?
Could be if the agreement between parties is managed via offchain communication, before sending the signed messages

- Is User A added to User B's contacts once User B accepts the tribute?
yes

- Is it required that User B send a reply to accept the tribute? Can it be required? 
No

- What if User B wants to end the conversation? How can they limit the amount of contact? 


# Design exploration
Prototype exploring what TtT might look like. Flow might change depending on the selected contract going forward:
https://www.dropbox.com/s/xi1k6bjo46h98us/TtT.mp4?dl=0
