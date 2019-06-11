---
id: #386-nim-ewasm
title: Nim Based Smart Contract Language targeting EWASM
status: research
lead-contributor: Jacques
contributors:
    - Jacques

budget:
- actual: to be determined
- estimate: 300
- currency: ETH
---

# Swarm proposal

Ethereum 2.0 will introduce a new Virtual Machine for writing smart contracts, based on WebAssembly (WASM). This swarm will deliver a Nim based smart contract language to allow developers to write smart contracts in Nim, with minimal boilerplate.

## Summary and Goal(s)

## Communication

`status channel (same as swarm id)`: [#386-nim-ewasm-dsl](https://gitter.im/status-im/nimbus)
* Weekly Sync
13:30 UTC every Wednesday
Call Link: https://meet.google.com/zsw-cues-jjg

## Timeline

* 2 months: Research and PoC
* 2 months: Development and tooling
* 2 months: Documenation and testing


eWasm nim kick off point:

- https://ewasm.readthedocs.io
- https://discuss.status.im/t/wrc20-and-nim-the-ewasm-token-challenge/1167
- https://github.com/jacqueswww/nim-eth-contracts
- https://github.com/status-im/nim-eth-contracts

Using existing eWASM compiler tookit in above repositories. Establish what a clean Nim - ethereum smart contract would look like.

## Specification

The ethereum smart contract language will aim to have the following features:

- Concept of public & private (exported & local) method.
- Tooling
    - ABI encoding & decoding
        - Parameter Return Type decoder & encoder for public functions.
        - Start off with 64-Bit based if standardised at time of implementation.
            - WRC20 as reference point (https://gist.github.com/axic/16158c5c88fbc7b1d09dfa8c658bc363)
    - ABI JSON generating with Ethereum specific types (e.g. `uint256` and `map()`).
- Strict ruleset for allowing only subset of Nim to be used.
    - Emphasis on readibility and verifiability.
    - Minimisation of "footguns".
- Standard library and macros
    - Emitting of Log Events.
    - Specific syntax to store in the global scope of the contract (self/this).
    - Basic arithmetic support for Ethereum specific types.
    - Overflow protection (to be determined).
    - Must be able to write at minimum Token (ERC20) or NFT (ERC721) with DSL.
    - eWASM internal functions must be abstracted away (no direct interface with CallData, Storage and similar "ethereum" exposed functions).
- Web3 Test suite against Ewasm chain/client (to be determined).

### Milestones

- Defining principles for the Language
- Simple tooling for nim contract development
    - ABI encoding/decoding
    - Deployment tools
    - Development environment / Framework
- Townhall demo
- WRC202 / ERC20 Token Contract running on ewasm testnet



## Implementation


## Maintenance

- Jacques

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).