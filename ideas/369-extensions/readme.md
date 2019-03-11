# Extensions Swarm

---
id: #369-extensions
title: Extensions
status: research
lead-contributor: Julien/Rachel
contributors:
    - Andrey
    - Julien
    - Nastya
    - Rachel
    - Hester
budget:
- actual: ?
- estimate: ?
- currency: USD
---

## Summary and Goals

Extensions proved to resonate in the Status developer community and thus we'd like to bring them out of alpha. 

Currently extensions lack polish, developer-friendly tooling and several key features. Let's make this happen!

Swarm phases:

1. Out of alpha
2. Improve developer experience 
3. Advanced features

## Contributors

- Andrey
- Julien
- Nastya
- Rachel
- Hester

(+ Janitor swarm) 

## Communication

`status channel`: [#369-extensions](https://get.status.im/chat/public/369-extensions)

`sync schedule`: biweekly sprint planning, ad hoc meetings as needed

`Pivotal project:` https://www.pivotaltracker.com/projects/??

`Meeting notes:` https://notes.status.im/extensions-meeting-notes

`Research notes:` https://notes.status.im/extensions-research

## Scope 

### Out of alpha

Extensions are currently only enabled when `dev mode` is turned on.

This makes extensions difficult to discover and install.

In order to surface extensions more visibly to users, we should first cover off on the following:

**1. Improved security modeling
2. Stronger syntax validation & error handling in development
3. User experience of discovery, installation, etc.** 

The main factor preventing extensions from being available by default is the missing security/privacy model.

This requires at minimum:

* Implementing `permissions` support
* Defining permissions per primitive
* Defining and implementing permissions/extensions UI
* Eventual per primitives, contextual UI considerations (e.g. event to send chat message on behalf of a user)
* Prevent any extension from crashing Status at runtime (stronger syntax validation)

Additional features that should also be considered:

* Per extension app-db persistence
* Unbreakable installation and error reporting (requires more metadata per primitive)
* Smooth installation experience and user journey
* Merge latest pluto improvements

### Improve developer experience

Developers are currently slowed by the process of deploying and testing extensions. 

The following options are considered to make the whole experience smoother:

**1. Improved editor
2. Simplified deployment**

Ultimately a developer would have high level tooling allowing them to simply create an extension from primitives while being confident it is functional.

Once satisfied, it is more seamless to deploy and test hands-on.

Finally it can be published and made available to status users.

#### Improved editor

There are both near term and long term changes enviosioned for the editor. 

In the near term, the following improvements can be introduced:

1. Merging the current extensions playground with Fiddle
2. Adding visual feedback to the editor
3. Adding traces to the editor for event tracking
4. Support for events that are currently mobile only, written for web  

Long term, creation of an extension could be done conveniently from within Status desktop. 

In a scenario where desktop reuses the same UI as mobile, this is the most efficient way of develping and testing an extension.

A simple figma style interface could offer:

* High level UI components palette access, with documentation and example usage
* Drag and drop UI definition
* Real-time extension preview in a realistic phone style UI

Everything is tracable:

* Query changes and payload
* Events and payload
* Runtime errors (e.g. invalid runtime destructuring)

Everything is manipulable:

* Query data mocks can be crafted and dispatched
* Events can be triggered with custom payload per components
* Specific components can be mocked

At all times, extension preview and source are in sync. With a click it can be tested in desktop directly.

The extension preview can be flipped to source access for advanced users.

#### Simplified Deployment

An extension could be seamlessly pushed to a paired device or any device in dev mode, provided the right URL.

Once the extension is modified in the editor, it can be pushed and updated without down time.

Once ready for prime time, a click deploys an extension on IPFS, updates an eventual ENS name and creates an extension URL (available as a QR code too).

This extension will be available forever, published permissionlessly and easily installable by anyone.

### Advanced features

Potential features that could be added at some point, worth considering from an architectural perspective.

#### More hooks

Extensions are as useful as the hooks are available in Status. 

Hooks to consider:

* Web injection (https://discuss.status.im/t/extensions-to-enhance-old-web/1085)
* More chat hooks (chat message wrapper -no access to message-, chat message modifier)
* More wallet hooks

#### Lightweight extension container

Status can be used as an extension container.

After scanning a QR code, Status is started (and eventually installed) and displays the extension only.

Specific lighter version of Status could be created to ensure fast startup (e.g. android go apps).

#### Custom Status

A default extension accessible via ENS could be used as global status configuration.

It would be loaded during bootstrap and would allow global configuration.

#### Deeper Status integration

See [ENS related ideas](https://discuss.status.im/t/extensions-ens-integration/1082)

#### Dependencies

Over time extension specific logic will be made available as extensions. Relying on this logic via dependency removes the need to duplicate work and allows to easily combine crypto primitives.

#### Versioning

An extension owner might want to make changes to an existing extension. It should be easy for related extension users to be notified of those updates and install them.

The extension developer can also easily browse the history of changes [visually](https://githistory.xyz/status-im/status-react/blob/develop/src/status_im/core.cljs) so that it is trivial to spot them.

#### Remote code

While verstaile, local data based events and queries can't accomodate all scenarios.

Alowing developer to provide custom JavaScript logic solves this issue. Specific attention have to be paid to security and user awareness.

#### Discovery

Extension can be exchanged via Whisper between contacts.

#### Better URL

Follow EIP1577 style standard to support easily any storage mechanism (IPFS, SWARM).

## Implementation

Implementation details will follow once research is completed.

## Copyright

Copyright and related rights waived via CC0.
