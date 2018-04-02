


<!-- Please Review https://docs.google.com/document/d/1CaFM2ZXGOKf05_LXMPJeNNy5qJOdAq91EF2Gn2QUBFI/edit# for more details -->
<!-- in PR the document should be named as`DEV#1-title.md` -->

## Preamble

    Idea: <to be assigned>
    Title: make testing process in SOB transparent and easy to contribute in 
    Status: In Progress
    Created: 2018-04-02

## Summary
- make QA process in SOB team easy to understand and support for newcomers; 
- in order  to reduce time spent on regression testing automate main usecases;

## Swarm Participants
<!-- Each contributor pledges to the idea with their FOCUS value. (hours per week) -->
<!-- Here all roles in swarm are defined and filled, one of the contributors should responsibility of the Idea as Lead. -->

<!-- Testing/Evaluation support role is also mandatory to check in on specified Goal dates or earlier. -->

<!-- Lead Contributor is the Owner of the Idea. If required, they can get support from a PM, but should be responsible for end to end execution of the Idea. This includes ensuring appropriate resources are allocated, setting realistic timelines and milestones, and any post-launch metrics or bug fixes that are attributed to the Idea -->
<!-- A swarm requires at minimum 3 contributors and 1 evaluator/tester -->
<!-- 'Contributor' should be replaced with a descriptive role type. -->
- Lead Contributor:@churik
- Testing & Evaluation: @annadanchenko 
- Contributor: @asemiankevich 

## Product Overview
<!-- A short (~200 word) description and motivation of the Idea. Without clear explanation the Idea should not proceed. Can include User Stories -->
<!-- Testing/Evaluation role accepts responsbility to checkin at Goal dates, -->
<!-- forces discussion to continue implementation or recommend disband and post-mortem. -->
Full and transparent QA process in Status Open Bounty team  will help to involve new people into testing process more quickly (if needed) and provide developers with more info about what was tested in particular PR or in `develop` branch. Ideally process should be integrated with TestRail, but initially smoke check list should be defined and than automated.
Hence this idea is placeholder for current and future iterations of improving QA process in SOB team.


### Requirements & Dependencies
<!-- Are there bugs or feature requests in other repositories that are part of this Idea? -->
<!-- There is no approval unless the idea requires to be reviewed by supporting organelles (Financial, Hiring, or Design). -->
<!-- The Swarm must develop a fully fleshed out Requirements document for the idea to proceed, to the satisfaction of participants. -->
For now blocker for 1 full-walkthrough autotest are:
- Jenkins doesn't recognize  xml reports and looks for them in wrong place after last refactoring. Problem is still investigating.

### Minimum Viable Product v1

<!-- Mandatory, completes the Idea in the fastest route possible, can be hacky, needed to feel progress. See https://imgur.com/a/HVlw3 -->
Goal Date: 2018-29-06
Actions needed for MVP v1 passed:
#### Documentation 
- [ ] Tutorial video or docs about QA process in SOB team
- [ ] Basic use cases (smoke check list) are defined in TestRail
#### Involment
- [ ]  one more QA can test SOB
#### End-to-end test (1 full walkthrough test for SOB)
- [ ] automate creating PR 
- [ ] define function for merging PR
- [ ] define function for SNT transfer 
- [ ] define function for signing transaction and confirming payment

