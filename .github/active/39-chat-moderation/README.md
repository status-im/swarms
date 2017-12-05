## Preamble

    Idea: <to be assigned>
    Title: Chat moderation
    Status: Draft
    Created: 2017-11-23
    Related: https://github.com/status-im/ideas/issues/15

## Summary

Moderation of public chat groups.

## Vision

Users must have greater control over the content in their chat feeds to ensure a positive experience. We can give users that control by providing them with a suite of moderation tools. Our moderation tools will enable users to define their own content rules or subscribe to a moderation provider to do it for them. A marketplace will ultimately exist where users can choose from a range of moderation providers.

## Swarm Participants

- Lead Contributor: @james
- Testing & Evaluation:
- Contributor: @themue
- Contributor:
- UX (if relevant):

## Requirements

## Goals & Implementation Plan

### Minimum Viable Product

Goal Date:

### Description

The MVP provides users with basic moderation tools so that they can block users, filter posts with certain phrases, and reduce spam.

### User Stories 

#### Blocking a user

User A enters a public group chat. User B sends a message that User A dislikes. User A blocks User B. All messages from User B no longer show up in any chat feeds of User A.

#### Reducing spam

User A enters a public group chat. User A discovers that messages in the chat feed are low quality (spam). User A adjusts the required SNT burn value until the quality of the chat feed improves.

#### Filter unwanted content

User A does not want to view any messages that contain the phrase x. User A updates their moderation rules to ignore any messages that contain the phrase x. Messages that contain the phrase x no longer appear in any chat feeds of User A.

#### Advanced filtering with smart contracts

User A is a power user. User A configures their moderation rules to include the address of a smart contract that implements a standard rules interface. The smart contract will be called to evaluate new messages as they are received.

### Requirements

- A format / schema for moderation rules must be defined.
- A standard rules interface for smart contracts must be defined.
- A smart contract that must:
  - Allow a caller to burn any ERC20 token.
  - Allow a caller to label burn amounts.
  - Return burn amounts given a token address, user address, and an optional label.
- A moderation settings UI must exist where the user may configure:
  - Blocked users.
  - Filtered phrases.
  - The address of a smart contract to call.
  - Burn amount required.
- UserA must be able to block a UserB from UserB's profile.
- Messages are evaluated against the moderation rules before they are rendered, aborting render where necessary.
- Moderation rules must persist between sessions.
- Chat group settings UI must:
  - Display the user's burn amount for that channel.
  - Allow users to burn tokens for that channel.

### Iteration 1

Goal Date:

### Description

Users can subscribe to moderation providers. 

### User Stories 

### Requirements

TBD

### Iteration 2

Goal Date:

### Description

A moderation marketplace.

### User Stories 

### Requirements

TBD

### Iteration 1..N

Goal Date:

## Supporting Role Communication

## Post-Mortem

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
