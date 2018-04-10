# Bountify all

## Problem

We have a lot of issues in various Status repositories. These could to a large
extent be solved by the larger community, as well as incentivized according to
priority by core contributors.

Additionally, there's no reward for putting bounties on issues, which leads to
an uphill battle in terms of bounty growth (see Andy's slides Town Hall).

## Solution

Create a swarm that will put a bounty on all outstanding issues and give
bountifier/issue creator a reward (finder's fee) for doing so, assuming the
issue gets solved.

The finder's fee can be ad hoc in inital implementation, and if proven
successful it can be encoded in a SOB contract.

There are five objections for putting a bounty on all issues as far as I
can see:

1. Issue is not well-defined enough

Then it should be closed.

2. Issue requires privileged access

OK exception - mark with label 'closed-flow' and move on.

3. Cost

Currently we have around 500 issues in status-react. Assuming they are all good
issues, and they get rewarded an average of $100 _if solved_, that's $50k. This
isn't an unreasonable amount, assuming we actually solve these issues.

Additionally, we can put an artificial growth limit on this. So first week 20 issues,
next week 22, etc.

4. Pervese incentives

This is only true for core contributors, and we aren't currently operating in a
byzantine environment. So this can be solved simply by a basic honor system, and
simple soft rules like not solving bounties you yourself put up.

5. Effort involved

The finder's fee of 10% (or 5% for issue creator 5% for bounty creator)
hopefully solves this issue. This is the hypothesis this swarm would test.

## Future work

1. Automatically put bounties on all new issues, given some conditions

2. Instead of spitballing bounty size, use issue size and priority to determine
   bounty size. E.g. a matrix where bounty size can be 1*3=3 (small, high prio),
   3*3=9 (big, high prio).
