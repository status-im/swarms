---
id: 142-recovery-compatibility
title: Wallet Recovery Compatibility
status: Active
created: 2018-04-04
category: core
lead-contributor: pilu
contributors:
    - pilu
    - antdanchenko
    - asemiankevich
    - flexsurfer
    - chadyj
    - jpbowen
exit-criteria: yes
success-metrics: yes
clear-roles: yes
future-iterations: yes
roles-needed:
---

## Meta

    Idea: #142
    Title: Wallet Compatibility
    Status: Draft
    Created: 2018-04-04
    Replaces (*optional): #94

## Summary

Users should be able to use `dapps` on their browser and continue to use them with the same account in Status, and vice versa.

## Swarm Participants

- Lead Contributor: @pilu
- Testing & Evaluation: @antdanchenko
- Testing & Evaluation: @asemiankevich
- Contributor: @flexsurfer
- Contributor: <!-- @username -->
- PM: @chadyj
- UX (if relevant): @jpbowen
<!-- - Contributor: @username -->

## Product Overview

Other wallets like MetaMask, Toshi, Cipher, etc., implements BIPs 39/32/44 like Status, and so they derive the keys starting from 12 mnemonic words.

Given that they use the same standards, users can start playing with a `dapp` with one of those apps, and continue with another one without problems. They can open one of the other apps, and use the same 12 mnemonic words to import their existing account (private key).
 
In Status, we implement the same standards to derive the keys starting from the 12 mnemonic words but using different constants, and we use the password added as an extra entropy in the generation of the seed.

This means that users can click on "Add existing account" and successfully "import" an account with the 12 mnemonic words that they generated in a different wallet software, but ending up with a different key and address.
Since the generation of the key is different, the account and address are not the ones that the user expected to import. 
Users won't be able to log in on `dapps` with the same they used previously, and won't be able to see the value and collectables they actually have in their wallet.

Impacts Idea #58-mainnet
Impacts Idea #80-onboarding

### Technical overview

The changes have been already implemented in [PR 858](https://github.com/status-im/status-go/pull/858), and they already went through the security audit.

**Changes:**

* update the BIP39 seed generation to use the salt `"mnemonic"` instead of `"status-im"` following [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki#from-mnemonic-to-seed).

* update the master key generation using the constant `"Bitcoin seed"` instead of `"status-im"`, following [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki#master-key-generation).

* remove the use of the password in the salt during the BIP39 seed generation (password is not removed from the app in general, and it's still required to encrypt the keys on the device).

### User stories

* As a user, I want to be able to use a `dapp` in Status, and then open the same `dapp` with the same account in a different Wall Software, using the 12 mnemonic words.

* As a user, I want to be able to use a `dapp` in an external app, and then using it in Status with the same account generated imported using the 12 mnemonic words.

### Security and Privacy Implications

The changes went already through the security audit.

### Minimum Viable Product

Goal Date: 2018-05-18

Description: users can import and export an account to and from Status. 

Testing Days required: <!-- Days required at the end of development for testing -->

## Success Metrics

* 5k daily active users (OKR 2.1 of Q2)
* 20% of users send a transaction (OKR 2.4 of Q2)

## Exit criteria

Users can use a single account/address for `dapps` and use it both in external apps and in Status.

## Supporting Role Communication

Once deployed, the generation of the keys will change. 
It will be impossible to re-import an account created previously. 

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
