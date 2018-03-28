<!-- Please Review https://docs.google.com/document/d/1CaFM2ZXGOKf05_LXMPJeNNy5qJOdAq91EF2Gn2QUBFI/edit# for more details -->
<!-- in PR the document should be named as`DEV#1-title.md` -->

## Preamble

    Idea: 83
    Title: Energy Efficient Status
    Status: In Progress
    Created: 2018-02-19


## Summary
A specific issue about the energy efficiency of different parts of Status (`status-go`, `status-react`, `desktop` (when running on a laptop battery).


## Swarm Participants
<!-- Each contributor pledges to the idea with their FOCUS value. (hours per week) -->
<!-- Here all roles in swarm are defined and filled, one of the contributors should responsibility of the Idea as Lead. -->

<!-- Testing/Evaluation support role is also mandatory to check in on specified Goal dates or earlier. -->

<!-- Lead Contributor is the Owner of the Idea. If required, they can get support from a PM, but should be responsible for end to end execution of the Idea. This includes ensuring appropriate resources are allocated, setting realistic timelines and milestones, and any post-launch metrics or bug fixes that are attributed to the Idea -->
<!-- A swarm requires at minimum 3 contributors and 1 evaluator/tester -->
<!-- 'Contributor' should be replaced with a descriptive role type. -->
- Lead Contributor: @mandrigin (~25h)
- Contributor (Go): @feuGeneA 
- Contributor (QA): @lukaszfryc (~10h/week)
<!-- - Contributor: @username -->

## Product Overview
Energy consumption is a crucial part of the mobile experience, and even though it is related to performance, it is worth having a separate.
The end goal is:
- to provide a toolkit and guidelines to test energy efficiency of different parts of an app on different platforms;
- using this toolkit to fix the top battery drainers;
- notice regressions early by having tests in place.

### Goals

1. Create a BoK for Energy efficiency testing: https://github.com/orgs/status-im/projects/18
a. test apps are created for both Android and iOS
b. test cases are written and tools are created to measure the energy efficiency of both Status client (status-react+status-go) and tests apps (status-go exclusively).
c. tests are run on a regular basis
d. (stretch goal) tests are automated for both platforms

2. Fix obvious issues with energy consumption
https://github.com/orgs/status-im/projects/17


## Exit criteria
- We have test cases and tools to check the energy efficiency of `status-go` and `status-react` independently;
- We can notice regressions/improvements caused, e.g. by updating the version of `go-ethereum` or new features of Status;
- Top energy draining issues are identified and fixed.

## Success Metrics
KR: 
(1) foreground energy consumption is < 120% of the apps in a similar class (messengers) 
(2) background energy consumption is < 120% of the apps in a similar class (messengers)


## MVP(s)
MVP1 (docs & process): Create and integrate energy efficiency testing as a part of the release process (date: *Mar, 30*)
MVP2 (development): Create a low-power background mode for status-go (date: *Mar, 30*)


## Supporting Role Communication
<!-- Once Requirements and Goals are fleshed out, then it should be communicated to supporting organelles if required -->

## Useful Links
https://github.com/dgryski/go-perfbook

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
