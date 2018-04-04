## Preamble

    Idea: #95-les-service-model
    Title: Introduce LES Service Model
    Status: Draft
    Created: 2018-03-20

## Summary

Introduce the LES Service Model where LES clients can subscribe to higher quality services. Different
payment models will be available, negotiation between client and full node is done via auctions based
on demands and capacity.

This way full node service provide are able to monetize the services they provide. LES will make the
beginning, Whisper and Swarm may follow.

## Swarm Participants

- Lead Contributor: @themue
- Testing & Evaluation:
- Contributor: @jeka
- Contributor: @b00ris
- PM: @zsfelfoldi (external)
- UX (if relevant):

## Product Overview

Today all light clients are treated equal by the full nodes they connect. A future service model will introduce
the separation between free and payed services. As outlined by Felföldi Zsolt:

- LES will be available either as free or paid service,
- paid service can guarantee availability and short response times,
- client bandwidth demand fluctuates with time, good service quality requires reserve capacity,
- for-profit LES servers can still give away their extra capacity for free (with lower priority than paid service),
- free service is a good indicator of high bandwidth capacity and therefore the capability to provide good service, and
- paying clients will prefer servers which already gave them free service so free service can act as an advertisement.

See https://github.com/zsfelfoldi/ethereum-docs/blob/master/les/service_model.md.

Once the service model is introduced changes to Status app are needed:

- Migration from Infura to ULC
- Choice between free and paid LES service
- In case of paid LES service definition of demands for auction

For Status it also could become interesting to become a service provider offering payed full node services not only
for own clients. This business case has to be evaluated.

### Product Description

Parts of the introduction of the LES Service Model are:

- research, definition, and implementation of connection management system of paying clients for full nodes,
- research, definition, and implementation of auctioning,
- research, definition, and implementation of payment methods and models,
- documentation.

### Minimum Viable Product

Goal Date: TBD (before end of Q2/2018)

Description:

- [ ] New Ultra Light Client Mode is added to LES
- [ ] Ability for user to choose between free and standard payed priority service
- [ ] Negotiation about subscription between client and full node by performing an auction
- [ ] Booking of micropayment fees for subscribed standard payed priority service

Outline of MVP and next milestones is currently under discussion with Zsolt.

## Success Metrics

TBD

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

