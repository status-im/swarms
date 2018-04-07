## Preamble

    Idea: 73
    Title: Gas Abstraction
    Status: In Progress
    Created: 2018-02-01
    Requires: #145

## Summary

Enable Status users to pay gas fee with any token that is valueable to society. 
Users would sign a message request to contracts which will use user's balance of selected token to refund proportional used gas to a incentivezed ETH owner to include that message in a transction.p

## Swarm Participants

- Lead Contributor:  @3esmit
- UX: @alexvandesande 
- Contributor/Testing: @iurimatias 
- Contributor/Testing: @richard-ramos 

## Product Overview

A barrier for user adoption to blockchain through Status would be the need of holding two tokens for paying fees, ether gas for moving the [SNT](https://etherscan.io/address/0x744d70fdbe2ba4cf95131626614a1763df805b9e#readContract) fee from user balance to decentralized service provider. 

The product solve this by emulating a gas abstraction by adding "Gas Relayer Actor" in top of smart contracts as: [Identity](https://github.com/status-im/contracts/blob/73-economic-abstraction/contracts/identity/Identity.sol)[GasRelay](https://github.com/status-im/contracts/blob/73-economic-abstraction/contracts/identity/IdentityGasRelay.sol), MultiSigWallet, [SNTController](https://github.com/status-im/contracts/blob/73-economic-abstraction/contracts/status/SNTController.sol#L82) (updated from SNTPlaceHolder). 

- Allows SNT holder to broadcast ethereum signed messages to anyone with ETH to validate them in the GasRelay smart contracts, and offering a refund of gas used in a gas price set in SNT. 
- Whoever have ether could verify if the gas price worth the SNT gas price offered.
- This becomes a micro trade of ETH->SNT.
- Allow user to use any token they want (even ETH, or ETH stored in Identity).

### Product Description

Gas Relay node: Status Destkop extension or an independent node can include messages by making automatic transactions calls to smart contracts to earn tokens being offered as gas price refund.
Fundamental pivot. 

Identity Gas Relay adaptor: include terms for accepting ethereum signed messages representing authorization to call by/for Identity owner offering a gas price refund.
Important for gas abstraction.

SNT Controller Gas Relay adaptor: include terms for accepting ethereum signed messages to IdentityGasRelay facotory and for moving the tokens from there using SNT.
Important for accounts that never held ether, just SNT.

### Requirements & Dependancies

Idea [#145](https://github.com/status-im/ideas/pull/145) is important to seamless and safe integration of gas abstraction for any type of call.
Implemention of [EIP#191](https://github.com/ethereum/EIPs/issues/191) is somewhat important, specially for making signature verification slightly gas cheaper.

### Minimum Viable Product

Goal Date:
Description:
- Users can call EVM by paying gas in a selected token.
- Users can join gas abstraction by SNTController terms
- Users can earn tokens by including other's messages

#### Identity Gas Relay

Goal Date:
Description: 
- Gas Relay Node that recieve whisper messages from Identity owners, 
- Identity User Interface with Gas Relayed option of calls

#### SNT Gas Relayer

Goal Date:
Description: 
- Gas Relay Node implements watching messages for SNTController 
- User interface for creating Identity+ENS register (pay gas in SNT)
- Moving SNT to other address from SNTController terms (paying gas in SNT)

## Success Metrics

Users are able to use Ethereum Virtual Machine and Status Network with only ever holding SNT.

## Supporting Role Communication

## Copyright
Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
