## Preamble

    Idea: 132
    Title: Seamless Login
    Status: Draft
    Created: 2018-05-04


## Summary

When a user opens Status or taps on a push notification they should be able to start using the app quickly without any interruptions, and also have control over authentication preferences.

## Swarm Participants
- Lead Contributor: @alwx
- Testing & Evaluation: @asemiankevich
- PM: @chadyj
- UX: @andmironov @jpbowen @hesterbruikman


## Product Overview

Status frequently logs out users when the app is in the background and forces users to log in again when opening the app. Being repeatedly and unexpectedly logged out has led to frustration and complaints (see Instabug and internal reports) which negatively impact the user experience and potentially contributes to churn. Also, users are encouraged to have complex passwords but this can be cumbersome to enter.

By reducing friction around the critical point of returning to the app users can spend more time in Status which will help DAU and retention (Q2 OKR).

This idea seeks to make logging in seamless through both technical and UX methods.


### Product Description

From a users perspective, the user will not repeatedly be logged out when using Status. This will be the default behavior. Since authentication preference is personal, there will be security/login settings so that a user can customize their desired level of control. For example, a user can specify never to be logged out, or choose to log in every time.

When we do ask users to login we want this to be as smooth as possible, and this can be achieved with the (optional) use of device security features such as Touch ID or a pin code. Instead of a password prompt, a user can simply use their fingerprint or look into the phone. This will be set up during onboarding and toggled in settings.

Note, that all transactions require authentication, so even if the phone was lost or stolen a third party couldn’t transfer funds. This idea does not cover the transaction flow.


### Iteration 1

During onboarding give users the option to setup seamless authentication (if their device supports it) and use the device/OS conventions to enable, or skip. There will be a setting to manage this preference.

## Iteration 2

Goal Date:

Take seamless login further and fix the root cause of the log outs by restoring from crashes. See [#2869](https://github.com/status-im/status-react/issues/2869#issuecomment-376098196) for some preliminary exploration.

This iteration is completed when users don’t have to type their password after a crash.


## Success Metrics

- A user does not need to login after several hours of intermittent use on Android and iOS, as well as logins persistent across upgrades (can it be automated in tests?)
- UXR validates workflow on real devices with real users
- 90% of surveyed users are satisfied with the frequency of login requests from Status app
- 0 password related issues in Instabug


## Exit criteria

When Iteration 1 and 2 are complete the success metrics should be evaluated. If the results are successful this swarm can be closed. If work is needed a third iteration can be done to address shortcomings.

## Supporting Role Communication

- Core
- Marketing
- Test team

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
