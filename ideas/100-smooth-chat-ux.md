<!-- Please Review https://docs.google.com/document/d/1CaFM2ZXGOKf05_LXMPJeNNy5qJOdAq91EF2Gn2QUBFI/edit# for more details -->
<!-- in PR the document should be named as`DEV#1-title.md` -->

## Preamble

    Idea: UX 100
    Title: Smooth chat UX
    Status: Draft
    Created: date created on 2018-03-23


## Summary
<!-- "If you can't explain it simply, you don't understand it well enough." Provide a simplified and layman-accessible explanation of the Idea. -->

The main goal of this UX swarm is to "smooth the edges" of our chat experience for our upcoming launch. Our current chat implementation works, but it is still not optimal. Two of the core OKR's (Use Status every day and message is reliable) depends heavily on a good and smooth chat experience.

The UX issues are split between 3 groups, starting with the low effort tasks/high payoff moving to big effort/high payoff (v1, v2, v3). Although its scope can seem ambitious at first, the idea is to have deliverables once in two weeks. Those deliverables will contain all the necessary documentation necessary for implementation. More designers are welcome to join as we go, as well as developers, QA's PM's.

## Swarm Participants
<!-- Each contributor pledges to the idea with their FOCUS value. (hours per week) -->
<!-- Here all roles in swarm are defined and filled, one of the contributors should responsibility of the Idea as Lead. -->

<!-- Testing/Evaluation support role is also mandatory to check in on specified Goal dates or earlier. -->

<!-- Lead Contributor is the Owner of the Idea. If required, they can get support from a PM, but should be responsible for end to end execution of the Idea. This includes ensuring appropriate resources are allocated, setting realistic timelines and milestones, and any post-launch metrics or bug fixes that are attributed to the Idea -->
<!-- A swarm requires at minimum 3 contributors and 1 evaluator/tester -->
<!-- 'Contributor' should be replaced with a descriptive role type. -->
- Lead Contributor: @ricardosaavedra
- Testing & Evaluation: <!-- @username -->
- Contributor: <!-- @username -->
- Contributor: <!-- @username -->
- PM: <!--- @username -->
- UX (if relevant): <!-- @username -->
<!-- - Contributor: @username -->

## Workflow and day-to-day activities
<!-- A short (~200 word) description and motivation of the Idea. Without clear explanation the Idea should not proceed. Can include User Stories -->
<!-- Testing/Evaluation role accepts responsbility to checkin at Goal dates, -->
<!-- forces discussion to continue implementation or recommend disband and post-mortem. -->
Every beginning of a new cycle (you can call it sprint if you'd like), we will decide together what to focus on for the upcoming two weeks as well as discussing current problems, technical challenges and the best solutions (trade-off between implementation cost and UX).
As ideas and design solutions start to emerge, we will get together to validate/critique the proposed solutions until we arrive at a group consensus.


### Product Description
<!-- What functionality are you adding? What will this look like from a user perspective? Why is this important? -->

**V1 - quick fixes**
- Chat view / message status
- Chat view / last seen 
- Chat view / user page 
- Chat view / minior UI fixes 
- Chat view / message space optimization
- Chat view / timestamps
- Chat view / adding/blocking new contact flow
- Keyboard / use cases behaviors
- Keyboard / maximum message width
- Keyboard / fixing console position
- Offline states and error handling 

**V2 - group chat improvements**

- Group chat view / chat metadata
- Group chat view / message space optimization 
- Group chat / timestamps
- Group chat / seen by logic and documentation
- Group chat / grouping messages 
- Group chat view / top bar behavior

**V3 - more engaging and visually clear home screen**

- Home screen / starting a new chat flow
- Home screen / visual consistency fixes
- Home screen / search function 
- Home screen / loading messages experience

For more details about each one of those fixes, please visit: https://docs.google.com/document/d/1AyU9mWMG1MxNPPBr1kidIl7eMJzPhbUjJjUNBBxZpg8/edit

### Team & Dependencies
<!-- Are there bugs or feature requests in other repositories that are part of this Idea? -->
<!-- There is no approval unless the idea requires to be reviewed by supporting organelles (Financial, Hiring, or Design). -->
<!-- The Swarm must develop a fully fleshed out Requirements document for the idea to proceed, to the satisfaction of participants. -->
Ideally, we would have at least 2 developers (Whisper, Clojure) in the team acting as a stakeholder in the process.

Even though you won't be implementing those designs directly, you should act as if you were, so that what comes out of this process isn't a wishfull thinking of our collective imagination; bearing no relationship with reality (time constraints and limited resources). 

<!--### Minimum Viable Product-->
<!-- Mandatory, completes the Idea in the fastest route possible, can be hacky, needed to feel progress. See https://imgur.com/a/HVlw3 -->
Goal Date: <!-- Date for evaluation in ISO 8601 (yyyy-mm-dd) format --> 

### UX swarm, what's new: <!-- Description of Deliverables-->

The idea behind the UX swarm to be able to work on the solutions (together) ahead of time; compared to how swarms have been working in the past. With this initiative we wish to achieve:

- transparency about UX process; everyone is involved and welcome to join at any point
- more collaboration between developers and designers 
- be able to outsource some of the work (more bounties)
- more time to fail, and try different solutions
- better documentation and chance to validate assumptions (user testing)


## Dates
Goal Date:  <!-- Date for evaluation in ISO 8601 (yyyy-mm-dd) format --> 

Description: <!-- Description of Deliverables-->

Testing Days required: <!-- Days required at the end of development for testing -->

## Success Metrics

- average of 10 messages a day by each active user 
- messaging experience feels good: 90% of surveyed users feel like the messaging experience is solid enough compared to new apps
- 80% of users that installed the app used the messaging feature in their first week (simple and inviting)


<!-- ## Supporting Role Communication-->
<!-- Once Requirements and Goals are fleshed out, then it should be communicated to supporting organelles if required -->

<!-- ## Copyright-->
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
