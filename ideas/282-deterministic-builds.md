---
id: 282-deterministic-builds
title: Deterministic Mobile App Builds
status: In Progress
created: 2018-09-01
category: infra
lead-contributor: jakubgs
contributors:
  - corpetty
  - adambabik
  - mandrigin
  - divan
  - cammellos
  - yenda
  - rasom
exit-criteria: yes
success-metrics: yes
clear-roles: yes
future-iterations: yes
roles-needed:
---

## Preamble

    Idea: #282-deterministic-builds
    Title: Deterministic Mobile App Builds
    Status: In Progress
    Created: 2018-09-01

The purpose of achieving deterministic builds is encuring security of Status software. Deterministic builds depend on ensuring stable inputs, ensuring stable outputs, and capturing as little of the build environment as possible.

In simple terms, deterministic builds mean the same commit generates exactly the same software package(s) regardless of where and when it is built. This is achieved by controlling all possible variables in a build, which includes controlling your build environment as well.

## Objectives

- status-go builds are deterministic
- status-react builds are deterministic

## Key Results

- Anyone can build a commit on their own machines and verify the result by comparing against our builds
- We can upload Android builds to F-Droid which requires deterministic builds

## Timeline / Checkpoints

Time is given since start of swarm.

* __1 month__
  - All major blockers are identified for major build steps
    - Dependencies
    - Compilation
    - Packaging
* __3 months__
  - All dependencies are contolled and versioned
  - Env controlling solution is chosen and implemented(vm, nix, docker)
* __4 months__
  - Remaining blockers are cleared
  - CI is configured to build in a deterministic way
  - Instructions to check build vailidty are published for anyone to use

# Exit Criteria

- All Status mobile and desktop app builds are deterministic

## What exactly we going to do?

- Verify all of our dependencies are frozen and versioned (`Gemfile.lock`)
- Verify we depend on no resources pulled from internet during build
- Make sure we initialize all variables in an explicit way
- Verify the build output does not depend on build system time/locale/encoding
- Eliminate timestamp related changes (use `SOURCE_DATE_EPOCH`)
- Use [gitan-builder](https://github.com/devrandom/gitian-builder) or [Nix](https://nixos.org/nix/) to have a controlled build environment
- Configure deterministic builds to run on Jenkins
