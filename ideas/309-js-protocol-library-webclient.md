---
id: 309-js-library
title: Build a status protocol JS library & example web client for status
status: draft
created: 2018-10-15
category: multi-category
lead-contributor: iurimatias (Iuri Matias)
contributors:
    - Richard Ramos
    - Barry G
exit-criteria: no
success-metrics: 
    - js library that is easy to reuse to implement custom clients for status
    - proof of concept web chat client 
clear-roles: no
future-iteration: yes
roles-needed:
    - JS or TS developers (nodejs, react, redux)
    - Frontend developers (css, bootstrap)
---

## Preamble

Idea: 309
Title: Build a status protocol JS library & example web client for status
Status: Draft
Created: 2018-10-15

## Summary

We need to make it easier for devs & 3rd parties to build their own chat clients & applications on top of the status protocol.
We also need different/new client implementations which just like in the case of Ethereum itself, helps out flush the protocol and define it better. Arguably It also helps decentralization as users are not necessarily dependant on one client implementation.

### Swarm Participants

- Contributor: [@iurimatias](https://github.com/iurimatias)
- Contributor: [@richard-ramos](https://github.com/richard-ramos)
- Contributor: [@bgits](https://github.com/bgits)

### Technical solution

- JS library that abstracts protocol, so developer can:
-- connect to (a) network
-- listen & send messages to a channel or another user
-- is allowed to specify his own (sub)-app protocol
- Webapp client
-- serverless app, connects to local geth node (initial solution)
-- implements similar UI & functionality to existing status desktop

### Technologies to use

- nodejs + webpack (to build library for both node and browser)
- react
- redux

### Milestones

* 1. poc script that listens & display messages on the command line connected to a configured geth node.
* 2. NodeJS library to listen to & send messages to custom channels.
* 3. poc WebUI to listen to & send messages to custom channels.

### Dates

To start after Devcon.

### relevant work

- https://github.com/trazyn/weweChat
- https://github.com/noman-land/matrix-whisper-bridge

