---
id: 172-topic-democracy
title: µTopic Democracy
status: In Progress
created: 2018-04-15
category: core
lead-contributor: Ricardo Guilherme Schmidt <3esmit.stateofus.eth>
contributors:
    - Jarrad Hope <jarrad.stateofus.eth>
exit-criteria: yes
success-metrics: yes
clear-roles: no
future-iterations: no
roles-needed:
    - PM
    - Design
    - StatusIM dev
    - Embark dev
okrs:
   - "[P2]: SNT is a powerful utility in Status"
---

# Swarm proposal

A democracy where you can specify delegate for carbon-voting proposals with specific multilevel governance delegation topics, or fallback to default delegate if none set.

## Communication
`status channel`: [#172-topic-democracy](https://get.status.im/chat/public/172-topic-democracy)
`sync frequency`: Weekly Sync

## Summary and Goal(s)

This product intend replace authority centralized control for contracts with a democracy based on a token.
Developers would be able to spawn democracy contracts to take decisions on the control of contracts used in the Dapps they are developing.  
The product would enhance security and continuance of this subsystems as the control would be up to token holders.

For a democracy where every member understands basic about every subject required for senstive actions inside the network is utopic. 
Every subsystem decisions would be democratic for the users of the platform, because a optional voting capability would be given to token owners, where they could set their delegate, or vote by themselfs.

Users wouldn't have to set specific delegates for each topic, they would be able to set their trusted in a root topic, which would be make that delegate claim the influence at any sub level which don't have a specialized delegate set. 
This relationship between child-parent creates a trust network, which is a common set of trust nominations by users in a network.  

When users don't vote and don't delegate, their influence might be delegated to a default delegate, if that specific delegation have a default.
The default delegate will be defined by the developer of the governed sub system, as they usually are the most understanded in the issue, or issues in general, regarding their subsystem.

### User Story

Contributor Julien is swarm leader of #313-sticker-market. 
This project deploys a smart contract with settings that can be defined by its controller.
- Being a onlyOwner is against Status Principle of Decentralization.
- Developers need control over the smart contract for development roadmap.
- Don’t knows exactly what is the consensus for many parameters.
SNT Holders funded the development of Status. 
- Don’t want to trust a onlyOwner for decisions on Status Network Contracts
- Wants to engage with decisions and polls by voting or selecting a delegate
- Are happy if they can control the ecosystem around the token they hold.

### Product Description

- Users should be able to participate on decisions or delegate their influence. _Important to democracy._
- Votes are counted as MiniMeToken balance of user at block voting end. _Important to not double tabulating without locking token transfers_ 
- Voting or delegating must not cause direct risks to users balances. _Important to don't cause barriers into democracy process_
- Users that delegates must be able to vote differently then their delegate. _Important to don't cause barriers into setting a delegate._
- Delegates should be able to delegate influence delegated to them, as a delegation chain. _Important to inflience get into experts._
- The execution of proposals should be subject of two proposals, first asking for it's approval, and second asking for it's veto.  _Important to prevent a big delegate changing decision at last moment._
- Approval Proposal uses a "Executive Delegation" and Veto Proposal uses a "Veto Delegation". _Important to prevent bribe of delegates._
- Specifics topics have their specific delegation chain, which if unset by user should fallback to parent topic definition. _Important to influence get into specialists of the topic._
- Users that didnt defined any delegate would be claimable by default delegate. _Important to don't cause slowness into development roadmaps._
- Users could be able to create their own sub democracies and choose their trust network (or create a new one) for controlling the decisions of tokens that contract hold. 
- User's democracy would be able to have any default delegate choosen by its creator.

### [MVP] Basic liquid democracy with binary proposals

Description: Topic Democracy for contracts control
- Developers can create democracy to own system contracts;
- Developers can create subtopics to specific functions on their contract;
- Users can request approval for execution of state changes;
- Users can set delegates;
- Users can vote;
- Volunteers can include other votes signatures
- Delegates can claim influence;
- Volunteers can tabulate votes;
- Proposal can be executed by Democracy contract;
- Users can request opinion as poll to trust network;

### [2ºi] Complex proposals and elections. 

Description: Election Proposal enable an Approval proposal to contain an elected variable based on other proposal.
- Upgrade current SNT (Opinion) Voting Dapp to become completely gasless. 
- Users can easily approve a high majority and tercerize a complex decision based on an election.
- Price variables could be elected as a weighted math mean.

### [3ºi] Multiple delegations

Description: Users can delegate to multiple delegates with different priorities.
- Lessens power of default delegate on sub democracies
- Allow smarter choices

## Success Metrics

Sub-democracies controlling sub-systems with intelligent outcomes. 
At least one sub-system should be sucessfully operated democratically by SNT holders or it's choosen delegates. (wonderfully work)
The partial success might be having only sub-systems operated democratically by Default Delegates. (no user engagement, but works) 
Another success metric would be the popularization of µTopic Democracy as means to control several aspects of Status, such as public chats (using SNT), group chats (using membership as token), public token list order and curation, and any aspect requiring democracy. 

## Exit criteria

Working platform for developers spawn sub-democracies controlled by SNT holders for controlling their syb-systems (e.g. ENS Usernames, Sticker Market, Tribute to Talk). 

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
