---
id: 306-core-dapp-team
title: Core Dapp Team
status: Active
created: 2018-05-01
category: core
lead-contributor: jeluard
contributors:
    - jeluard
    - flexsurfer
    - rachelhamlin
    - alwx
exit-criteria: no
success-metrics: no
clear-roles: yes
future-iterations: no
roles-needed:
---

The Core Dapp and Developer team is a product team that is focused on the dapp and developer experience of Status. It gets support and is enabled by the Mobile App team as well as Infra and P2P team.

DApps and Dev team is mostly focused on:

* improving DApps support in status
* providing tooling for DApps developers (documentation, HTTP API, JS API)
* offering Status extensions capacities

[Q4 2018 DApp/Dev strategy deck](https://docs.google.com/presentation/d/14FFmXzBh50jXxhZplVfSzR46jRKJBt74WpJtCv8mRas/edit#slide=id.g4235117b70_0_0)

[Weekly Sync Notes](https://docs.google.com/document/d/1S86RWNxLT-VV_xIJ02-NOHXnODVl-M33aDVyoiAEhdc/edit?usp=sharing)

## Work log

### 2018

### Week of Nov 12

* Added Voting DApp [#6702](https://github.com/status-im/status-react/pull/6702) (Julien)
* Improved playground IPFS usage [#92](https://github.com/status-im/pluto/issues/92) (Julien)
* Hooks name can have multiple segments [commit](https://github.com/status-im/pluto/commit/71db93d02862822e073e6561928777d5a7883397) (Julien)
* Published a WIP for wallet.settings hook [extensions.wallet.settings](https://github.com/status-im/status-react/tree/extensions.wallet.settings) (Julien)
* Discussed about extensions plans for Asia roadshow (Rachel, Andrey and Julien)
* Fixed and merged Granting profile access to a DApp [#6585] (Andrey)
* Investigated resolving ens in webview component and discussed with the core team (Andrey)
* Investigated extensions and started work on multi-extensions storage support [#6736] (Andrey)

### Week of Nov 5

* Fixed various extensions issues discovered during hackathon [#6610](https://github.com/status-im/status-react/pull/6610) [#6661](https://github.com/status-im/status-react/pull/6661) [#6668](https://github.com/status-im/status-react/pull/6668) (Julien)
* Added DApps [#6667](https://github.com/status-im/status-react/pull/6667) (Julien)
* Agreed with providers ring about next steps (Rachel, Andrey, Julien)
* Discussed with Embark team about EIP1102 strategies (backport to Embark3, delayed call to enable) (Rachel, Julien)
* Discussed ENS usernames reverse lookup strategies [#80](https://github.com/status-im/ens-usernames/issues/80) (Rachel, Julien)
* Investigated potential new wallet extension hook (Julien)
* Investigated how pluto works and moved registry out of it (Alex)
* Improved extension management — added functionality to allow editing and removing extensions + made UI for it (Alex)
* Worked on extensions data persistence (Alex) - not finished yet
* Introduced browser privacy mode [#6654] (Andrey)
* Fixed Cryptokitties [#6627] (Andrey)
* Display .eth or other domain rather than IPFS redirect [#6169] (Andrey)
* Granting profile access to a DApp gives access to any DApp with same host [#6585] (Andrey)

### Week of Oct 29

* Reorganized and edited [extensions documentation](https://github.com/status-im/status.im/tree/develop/source/extensions) (Julien, Rachel)
* Decided not to force EIP1102 until ~Nov 16—ENS DApp and Voting DApp will break because there are architectual changes needed in Embark to support the most recent implementation of EIP1102. OKR voting will run until Nov 16. Implication: DApps that switch to EIP1102 (per MetaMask timeline of Nov 2) will break inside Status unless `Development mode` and `Opt-in web3 provider access` are enabled in settings. (Julien, Rachel)

### September 17-28

#### Browser

* Implemented QR code scanner API
* Improved recovery flow
* Added UI to share deeplinks
* Added link to ENS DApp
* Added HTTP API docs
* Added chat link button in browser

#### Extensions

* Added simple [playground](https://status-im.github.io/pluto/try.html)
* Initiated contacts with MakerDAO and Kyber
* Started work on improving permissions support
