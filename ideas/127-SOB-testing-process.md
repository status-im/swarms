"Improve OpenBounty Testing and make it easy to contribute"


## Preamble

    Idea: 127
    Title: Improve OpenBounty Testing and make it easy to contribute
    Status: In Progress
    Created: 2018-04-02

## Summary
- make QA process in SOB team easy to understand and support; 
- in order  to reduce time spent on regression testing automate main use cases;

## Swarm Participants

- Lead Contributor:@churik
- Testing & Evaluation: @annadanchenko 
- Contributor: @asemiankevich 

## Product Overview

Full and transparent QA process in Status Open Bounty team will help to involve new people into the testing process more quickly (if needed) and provide developers with more info about what was tested in particular PR or in `develop` branch. Ideally process should be integrated with TestRail, but initially, a smoke checklist should be defined and then automated.

All regression test cases should be automated eventually in order to reduce time for SOB testing and to find issues faster.
In future would be nice to integrate GitHub pull requests with automation testing thus after PR will be built and deployed,  it will trigger end-to-end tests and publish test results in PR comment.
Hence this idea is a placeholder for current and future iterations of improving QA process in SOB team.

### Minimum Viable Product v1

Goal Date: 2018-06-29
Actions needed for MVP v1 will pass:
#### Documentation 
- [ ] Tutorial video or docs about QA process in SOB team
- [ ] Basic use cases (smoke checklist) are defined in TestRail
#### Involment
- [ ]  one more QA can test SOB
#### End-to-end test (1 full walkthrough test for SOB)
- [ ] automate PR creating
- [ ] define function for PR merging
- [ ] define function for SNT transfer 
- [ ] define function for signing transaction and payout confirmation
