<!-- Please Review https://docs.google.com/document/d/1CaFM2ZXGOKf05_LXMPJeNNy5qJOdAq91EF2Gn2QUBFI/edit# for more details -->
<!-- in PR the document should be named as`DEV#1-title.md` -->

## Preamble

    Idea: 96
    Title: Tribute to Talk
    Status: Draft
    Created: 2018-03-20
    Requires (*optional): TBD


## Summary
<!-- "If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the Idea. -->
Economics-based anti-spam filter, in our case for receiving messages and “cold” contact requests from users.


## Swarm Participants
<!-- Each contributor pledges to the idea with their FOCUS value. (hours per week) -->
<!-- Here all roles in swarm are defined and filled, one of the contributors should responsibility of the Idea as Lead. -->

<!-- Testing/Evaluation support role is also mandatory to check in on specified Goal dates or earlier. -->

<!-- Lead Contributor is the Owner of the Idea. If required, they can get support from a PM, but should be responsible for end to end execution of the Idea. This includes ensuring appropriate resources are allocated, setting realistic timelines and milestones, and any post-launch metrics or bug fixes that are attributed to the Idea -->
<!-- A swarm requires at minimum 3 contributors and 1 evaluator/tester -->
<!-- 'Contributor' should be replaced with a descriptive role type. -->
- Lead Contributor: @richard-ramos
- Testing & Evaluation: <!-- @username -->
- Contributor: <!-- @username -->
- Contributor: <!-- @username -->
- PM:  @rachelhamlin
- UX (if relevant): <!-- @username -->
<!-- - Contributor: @username -->

## Product Overview
<!-- A short (~200 word) description and motivation of the Idea. Without clear explanation the Idea should not proceed. Can include User Stories -->
<!-- Testing/Evaluation role accepts responsbility to checkin at Goal dates, -->
<!-- forces discussion to continue implementation or recommend disband and post-mortem. -->
This enables stakeholders to set a minimum amount of SNT that a Status stakeholder must deposit in order for someone outside of their network to contact him directly. If the recipient replies the deposit is forfeited to the recipient.

**SNT Utility**

SNT is deposited, and transferred from stakeholders to recipients upon receiving a reply from the recipient.

Example use-cases

- Stakeholder A, a professional, would like to reach out to a high profile figure in the same industry, but would otherwise have no means of receiving a response.
- Stakeholder B, an artist and celebrity wishes to spend some time chatting with fans, and also desires a means of monetizing their fan base.
- Stakeholder C, a freelancer, provides photography tutorials, and has a means of generating revenue.

### Product Description
<!-- What functionality are you adding? What will this look like from a user perspective? Why is this important? -->
Any Status user can enable Tribute to Talk and set a minimum required deposit for other users to stake in order to send them a message. Users requiring a tribute can whitelist their full contact list, or specific contacts.

If User A requires a minimum 200 SNT deposit, User B will not be able to open a new chat with User A until they deposit at least 200 SNT. Once deposited, User B can send their message.

If User A responds to User B’s message, the deposit is transferred to User A, and a conversation is opened.

If User A does not respond or User B changes their mind, User B can cancel or withdraw the request. The request will also time out automatically if User A does not respond in some number of days. In any case where User A does not respond, the deposit is returned to User B.

If User A rejects User B’s request, User B’s deposit is returned. User B will have to wait some amount of time before they are able to send a new request to User A.

In the future, User A might have the option to respond to User B but waive the deposit. User B might have the option to make a tribute to User A without requiring a response. 


### Requirements & Dependencies
<!-- Are there bugs or feature requests in other repositories that are part of this Idea? -->
<!-- There is no approval unless the idea requires to be reviewed by supporting organelles (Financial, Hiring, or Design). -->
<!-- The Swarm must develop a fully fleshed out Requirements document for the idea to proceed, to the satisfaction of participants. -->

### Minimum Viable Product
<!-- Mandatory, completes the Idea in the fastest route possible, can be hacky, needed to feel progress. See https://imgur.com/a/HVlw3 -->
Goal Date: TBD <!-- Date for evaluation in ISO 8601 (yyyy-mm-dd) format --> 

Description: <!-- Description of Deliverables-->
For the initial delivery, these are the minimum features proposed.
- [ ] UI for recipients to set Tribute to Talk with required minimum deposit for any new chat
- [ ] UI for requesters to send minimum SNT deposit and their message to users with Tribute to Talk enabled
- [ ] UI for requesters to cancel a request and withdraw deposit
- [ ] UI for recipient to respond to or reject new requests 
- [ ] Deposit is transferred from requester to recipient when recipient responds
- [ ] Deposit is returned to requester if rejected or withdrawn

Next milestones and deliverables would be determined discussing and prioritizing features of the product description

## Dates
Goal Date: TBD <!-- Date for evaluation in ISO 8601 (yyyy-mm-dd) format --> 

Description: TBD <!-- Description of Deliverables-->

Testing Days required: TBD <!-- Days required at the end of development for testing -->

## Exit Criteria
Any user can set up Tribute to Talk and require a deposit minimum to be contacted. Other users can put down a deposit to message them. New requests can be responded to, rejected or withdrawn. The deposit is transferred when a recipient responds, and sent back if they reject or the requester withdraws.

## Success Metrics
<!-- Assuming the idea ships, what would success look like? What are the most important metrics that you would move? -->
Initial emphasis is on TtT working as expected and producing no bugs for critical events. 

- Message requests are delivered 100% reliably from requester to recipient.
- Message responses by recipients are successfully recognized in all instances, both accepted and rejected.
- Transfer or return of deposit to either recipient or requester is successful.


## Supporting Role Communication
<!-- Once Requirements and Goals are fleshed out, then it should be communicated to supporting organelles if required -->
TBD

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
