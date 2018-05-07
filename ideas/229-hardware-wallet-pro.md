---
id: 229-hardware-wallet-pro
title: Hardware Wallet Pro
status: Active
created: 2018-05-01
category: core
lead-contributor: bitgamma
contributors:
    jarradh
    naghdy
exit-criteria: true
success-metrics: true
clear-roles: true
future-iteration: true
roles-needed:
    - QA
    - UXR
---

## Preamble

    Idea: 229-hardware-wallet-pro
    Title: Hardware Wallet Pro
    Status: In Progress
    Created: 2018-05-01

## Summary

We currently have a Javacard based hardware wallet implementation. This is a simple and inexpensive hardware wallet with good security. The main limitations of this solution are

1. Requires a SmartCard reader on the host
2. Transaction data (amount, address) is displayed on the possibly compromised host device, the card has no screen
3. The seed is currently partially generated off-card because of JavaCard limitations
4. Limited API does not allow much room in terms of additional features. We already stretch the limit of what JavaCard can do by a far amount with our hardware wallet, which means that clever tricks and workarounds had to be implemented in a few cases.

The proposal is to create a Pro version of the hardware wallet not based on the JavaCard platform and removing these limitations. This Pro version will have a significantly higher cost that then JavaCard one, since it will be a more complex device.

## Swarm Participants

- Lead Contributor: @bitgamma
- Contributor: @jarradh
- Contributor: @naghdy
- QA: TBD
- UX: TBD

## Product Overview
The product will be a HD hardware wallet with its own screen and input buttons used to display and confirm transactions. The seed will be generated on card and mnemonics will be displayed on the card screen as to never reach the mobile device. Communication with mobile/desktop clients will happen through BLE. The device will be powered by its own rechargeable battery (inductive charger). Ideally, the physical size will match that of a standard smart card.

### Security and Privacy Implications
As with any hardware wallet security is a prime concern. The device must be engineered to cope at least with the following threats

1. Data sniffing - this can be solved by encrypting the communication with the client device
2. Data injection - communication with the client device must be authenticated
3. User impersonation - beside possessing the card, the user must be authenticated by a PIN (the "something you know" factor)
4. Tampering of the software - Firmware must be either non-upgradable (less flexible, makes it impossible to fix existing bugs) or the upgrade procedure must be implemented in a secure way
5. Tampering of the hardware - It should be cost prohibitive to tamper with the hardware to read data or write malicious data. With the correct production techniques the device will be destroyed by disassembling.

## Success Metrics

The project is composed o 4 major steps. Although these are described sequentially, at some point it might be possible to run some of them in parallel. Phase 3 especially can be started when the software is still being finalized but there is a solid understanding of which components are needed and how they are to be wired.

### Phase 1
Goal Date: Start of Q4 2018
Description: A prototype should be built using an STM32 Nucleo development board with a Bluetooth shield. This will allow writing most of the firmware. During this phase the UI must be designed. This means the design of a custom segment-based LCD and the design of how the user will interact with the device.

### Phase 2
Goal Date: End Q4 2018

Description: At the beginning of Q4, the new STM32WB chip will be available. This component integrates a bluetooth stack and a STM32L4 core in a single chip while also providing hw-accelerated encryption and key management. The firmware must be ported to this platform, which will be the platform used by the actual product

### Phase 3
Goal Date: end of Q1 to middle of Q2 2019

Description: In this phase the final product design, PCB design and BOM must be finalized and a manufacturer must be chosen and contracted.

### Phase 4
Goal Date: TBD

Description: Stock, distribution and launch. It is early to define a date because it very much depends from the manufacturer lead times and commercial strategy (we might want to tie product launch might to a specific conference or event)

## Exit criteria

This swarm will be deemed successful and be closed after reaching Phase 4.

## Copyright

Copyright and related rights waived
via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
