---
id: 307-breaking-whisper
title: Breaking Whisper
status: Draft
created: 2018-09-24
category: swarm / SITG experiment
lead-contributor: corpetty
contributors:
exit-criteria: no
success-metrics: yes
clear-roles: yes
future-iterations: yes
---

## Preamble
    Idea: 307-breaking-whisper
    Title: SITG Experiment #2: Breaking Whisper
    Status: Draft
    Created: 2018-09-24

## Summary
1) Understanding the limits of whisper (with and without optimizations)

## Swarm Participants
- Lead Contributor: @corpetty 
- Commited Contributors: 
- Suggested Contributors (??): 
  * Ivan: @divan
  * Jakub: @jacob
  * Jacek: @arnetheduck
  * Mark: @easye
  * Adam: @adamb

## Overview
Approach finding the limits of whisper from a rigorous academic approach.  See [this](https://hackmd.io/B-W4T1SzSgCAbYS2CfoIPg) for details.  We will be using the Skin In The Game (SITG) model for incentivizing the work here.  See [this](https://hackmd.io/eqS67u1QSfmZQ3IsgywFkQ) for more details on SITG.

### Description
The concept is simple: We use whisper as a fundamental backbone to Status' communication, but we don't know how much of a load that backbone can support.  Since this information does not exist, and there doesn't seem to be other people in the community focused on providing it, we must do it ourselves.

This endeavor outlines the process of systematically and rigorously evaluating the limitations, strengths, and weaknesses of Whisper as a communications protocol.  It is then planned to use the results of this study to reason about future improvements of whisper and their prioritization, as well as what whisper's long term role within Status will be. 

In an attempt to streamline and incentivize this process, as well as experiment with primitives of a DAO, we will be encapsulating this project with the SITG experiments, which are outlined in the above HackMD docs. 

### Requirements & Dependencies
- Whisper Simulator and metrics

## [Milestones](#milestones)
### Milestone 1: Simulation engine completion and metrics definition.
Goal Date: 2018-
Description: 
* Completion of [whispervis](https://github.com/status-im/whispervis) and the required stats as laid out in Product Overview HackMD doc.
* The simulation aspect is not as important as the ability to run multiple tests with different parameters changed in a quick manner

Contributors: 
* @divan ??
* @adamb ??
* @arnetheduck ??

### Milestone 2: Perform theoretical tests.
Goal Date: 2018-
Description:
* Systematically perform and record all tests with regards to relevant parameter changes

Contributors: 
* @corpetty 

### Milestone 3: Results aggregation and data analysis.
Goal Date: 2018-
Description:
* Gather and scrub all data for uniformity
* Plot relevant plots as per HackMD doc in Product Overview
* Decide which results are best ported to experimental model
  * practicality
  * value of information for comparison
* This should provide preliminary data on theoretical limit of naive whisper scaling
  * Publish a blog about current progress, current insights, proposed next steps

Contributors: 
* @easye ??

### Milestone 4: Beta fleet preparation.
Goal Date: 2018-
Description:
* Complete description of cluster setup specifications
* Make sure we are tracking the same metrics on the cluster as the theoretical model
* Note typical usage / remove standard usage
* Development of methodology for stress testing Beta fleet in the similar manner as Theoretical model. 

Contributors: 
* @jacob ??

### Milestone 5: Perform beta fleet stress test.
Goal Date: 2018-
* Systematically apply methodology from previous milestone to actual experimental cluster
* Collect and store relevent performance metrics
* Publish a blog about initial experimental results and thoughts

### Milestone 6: Comparison Analysis
Goal Date: 2018-
* Compare theoretical vs experimental tests data
* Plot and create indicator of how accurate theory is to experiment
* brainstorm on
  * problems with theoretical model and experimental setup
  * improvements with communication scaling and their implementation details with experimental/theoretical frameworks

### Milestone 7: Paper write-up and publish
Goal Date: 2018-
* Write up the entire process / analysis / results / and conclusions for ourselves and the public. 
* Portal for community feedback

Contributors: 
* Someone from peopleops for portal ??

## Success Metrics
* Compeleted paper on whisper scaling, both theoretical and experimental
* Enough information to make a case on how Status uses Whisper, what userbase / message load it breaks at, and what improvements to test to judge viability of Whisper in the future

Contributors: 
* @easye ??

## Future Iterations
* Implementation of said scaling improvements
* Incorporation of other protocols into the simulator 
  * pss, etc
* Clear roadmap on what a scaling study looks like for future improvements / other protocols


```
Legend:
?? - suggested contributor
```