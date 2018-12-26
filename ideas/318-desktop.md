---
id: 318-desktop
title: Desktop
status: research
lead-contributor: Volodymyr
contributors:
    - Volodymyr
budget:
- actual: xxx
- estimate: yyy
- currency: ETH/USD/SNT
---

# Desktop Swarm proposal

## Summary and Goal(s)

Messenger apps expected to be present on all widely used platforms - ios, android, mac, windows, linux.

Status desktop app currently extensively used by Status company for communications.
It is implemented with the help of [react-native-desktop](https://github.com/status-im/react-native-desktop) project that is a Qt-based port of `react-native` to desktop platforms: mac, windows, linux.

So Desktop swarm has two goals in mind:
1. Providing well-polished communication tool for Status company itself and the community
2. Feature parity with mobile application
For initial scope focus is on the first goal.

Additional tasks for the swarm is maintaining `react-native-desktop` project to fit Status desktop needs and publishing Status desktop releases.

## Communication
`status channel (same as swarm id)`: [#318-desktop](https://get.status.im/chat/public/318-desktop)

`sync frequency`: Weekly Sync

`meeting notes`: https://notes.status.im/IVQ6ZK6iRw6LfF-4y4WJmw

## Research

`Timebox: 21/12`

`Research questions:`

 * **what features we already planned or were talking about? How they priority changes now?**
  * ~~[Allow standard keyboard shortcuts](https://github.com/status-im/status-react/issues/6272)~~
  * ~~Publishing at platform's official marketplaces~~
  * ~~[Fix memory leaks](https://github.com/status-im/status-react/issues/5271)~~
  * ~~Improve CPU usage~~
  * ~~windows uwp support~~
  * ~~markdown support in chat~~
  * ~~text selection among multiple messages~~
  * ~~[show connection stats inside the app](https://github.com/status-im/status-react/issues/6568)~~
  * ~~[add log level settings](https://github.com/status-im/status-react/issues/5848)~~
  * ~~[use peer counts to detect online\offline state](https://github.com/status-im/status-react/issues/6961)~~
  * ~~[No new messages after going back from sleep](https://github.com/status-im/status-react/issues/6396)~~
  * ~~[Security and privacy review](Desktop security and privacy review)~~
  * ~~[Context menu in input fields](https://github.com/status-im/status-react/issues/6571)~~
  * ~~[Add design for menus](https://github.com/status-im/status-react/issues/4434)~~
  * ~~[Fix scroll stuttering](https://github.com/status-im/status-react/issues/6570)~~
  * ~~[Add dev mode and network switching](https://github.com/status-im/status-react/issues/6477)~~
  * ~~[UI fixes for bubble-less chat area](https://github.com/status-im/status-react/issues/6506)~~
  * ~~[Fix group chats creation](https://github.com/status-im/status-react/issues/6607)~~
  * ~~[Confirmation dialog on logout](https://github.com/status-im/status-react/issues/4977)~~
  * ~~[Custom url support on linux](https://github.com/status-im/status-react/issues/6394)~~
  * ~~[Add custom mailserver](https://github.com/status-im/status-react/issues/6110)~~
  * ~~[Edit profile picture](https://github.com/status-im/status-react/issues/5456)~~
  * ~~[Remove code duplication in Jenkinsfiles](https://github.com/status-im/status-react/issues/5424)~~
  * ~~[Persist scroll position after navigation through the app](https://github.com/status-im/status-react/issues/5852)~~
  * ~~[Add jenkins job for e2e tests](https://github.com/status-im/status-react/issues/5859)~~
  * ~~[Apply onboarding designs](https://github.com/status-im/status-react/issues/4418)~~
 * **what existing desktop issues affect its usability most (in functionality or UI)**?  
 * ~~**how many users outside of Status we have? (optional)**~~
 * **how can we get user feedback about desktop**
  * [make a poll within Status](https://goo.gl/forms/AAzNNfCTGjL8hcEl1)
 * **what features mostly anticipated by users?**
  * mentions
  * image/links previews
  * pinned channels
  * mark all messages in a channel as unread
  * channel (chat where only creator can write and others can read). That would be great for announcing things company-wide
  * persisting chat list and settings between full reinstalls
 * **what ui/ux input needed**
 * **what should be done in `react-native-desktop` to support status desktop tasks**
  * ~~[Get rid of ubuntu-server and embed js engine in react-native-desktop](https://github.com/status-im/status-react/issues/6175)~~
  * ~~[File open dialog](https://github.com/status-im/react-native-desktop/issues/377)~~
  * ~~[Fix remote js debugging](https://github.com/status-im/react-native-desktop/issues/392)~~
  * ~~Improve UI responsiveness (needs clarification on existing issues)~~
 * **what should be done in `react-native-desktop` to make its maintenance easier**
  * ~~port to react-native 0.57. That will give us a possibility to make it an [out-of-tree](https://facebook.github.io/react-native/docs/out-of-tree-platforms) platform and facilitate future upgrades.~~
    * PR with updated version [already in react-native-desktop](https://github.com/status-im/react-native-desktop/pull/422)
    * [PR for testing it with status-react](https://github.com/status-im/status-react/pull/6983)
    * PR for mobile [in progress](https://github.com/status-im/status-react/pull/6951)
  * ~~More documentation/tutorials for external contributors~~
 * **what tasks can be done without involving Clojure/Go resources**


 `Research output structure:`
 When questions above answered we can create:
 - prioritized list of most important tasks to do for boosting communication experience
 - user stories
 - bounties


 `Research output:`

 **Prioritized list of tasks:**

 * **TODO**
    * High
      * [Fix memory leaks](https://github.com/status-im/status-react/issues/5271)      
      * [Fix scroll stuttering](https://github.com/status-im/status-react/issues/6570)
      * [Get rid of ubuntu-server and embed js engine in react-native-desktop](https://github.com/status-im/status-react/issues/6175)
      * [port to react-native 0.57](https://github.com/status-im/react-native-desktop/pull/422)          

    * Medium
      * [Support building react-native-desktop with msvc](https://github.com/status-im/react-native-desktop/issues/222)  
      * Add emoji panel
      * [Fix remote js debugging](https://github.com/status-im/react-native-desktop/issues/392)      
      * [UI fixes for bubble-less chat area](https://github.com/status-im/status-react/issues/6506)      
      * [Security and privacy review](Desktop security and privacy review)
      * [Add design for menus](https://github.com/status-im/status-react/issues/4434)
      * [Confirmation dialog on logout](https://github.com/status-im/status-react/issues/4977)
      * [File open dialog](https://github.com/status-im/react-native-desktop/issues/377)      
      * [Edit profile picture](https://github.com/status-im/status-react/issues/5456) (depends on file open dialog implementation in react-native-desktop)
      * [Persist scroll position after navigation through the app](https://github.com/status-im/status-react/issues/5852)
      * [Add jenkins job for e2e tests](https://github.com/status-im/status-react/issues/5859)
      * [Apply onboarding designs](https://github.com/status-im/status-react/issues/4418)
      * Improve UI responsiveness (needs clarification on existing issues)
      * Image/links preview      
      * mark all messages in a channel as unread
      * [Allow standard keyboard shortcuts](https://github.com/status-im/status-react/issues/6272)
      * markdown support in chat
      * text selection among multiple messages
      * More documentation/tutorials in react-native-desktop for external contributors
      * [Custom url support on linux](https://github.com/status-im/status-react/issues/6394)
      * Mentions

    * Low
      * Pinned channels
      * [Fix group chats creation](https://github.com/status-im/status-react/issues/6607)
      * [Remove code duplication in Jenkinsfiles](https://github.com/status-im/status-react/issues/5424)
      * [Improve CPU usage on resize](https://github.com/status-im/status-react/issues/5151)
      * [Add custom mailserver](https://github.com/status-im/status-react/issues/6110)
      * [Add dev mode and network switching](https://github.com/status-im/status-react/issues/6477)
      * [Context menu in input fields](https://github.com/status-im/status-react/issues/6571)

 * **Needs input from other teams (most probably)**
  * channels (public chat where only creator can write and others can read). That would be great for announcing things company-wide
  * persisting chat list and settings between full reinstalls

 * **Postponed**
  * windows uwp support
  * Publishing at platform's official marketplaces


 **User stories:**

 **Bounties:**


## Specification

> do after `Research`

(required)
`timebox specification (approx)`

(optional)
`user stories`, `architecture`, `designs`, `PoC`

## Implementation

(required)
`timebox implementation (approx)`

> do after `Specification`

> All swarm contributors should test and break the implementation, especially developers

(required)
`document progress`

(optional)
`townhall demo`

## Maintenance

`lead-contributor`,`post-mortems`

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
