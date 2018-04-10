## Micropayment

### Existing Solutions

#### µRaiden

##### Concept

- Between two parties: *sender* (client) and *receiver* (service provider)
- Communication between sender and receiver via RESTful API
- Creation of channel and settling leads to µRaiden Smart Contract and a *deposit*
- Smart Contract enforces payment of deposit
- Signing payments with balance-proofs between sender and receiver allows off-chain transactions
- If deposit of sender gets low it can increase it
- Once channel gets closed deposit is payed to receiver based on balance-proofs and rest to sender
- Only two transactions for opening and closing
- Own ERC20 and ERC223 compliant token

##### Links

- https://raiden.network/micro.html
- https://github.com/raiden-network/microraiden
- https://microraiden.readthedocs.io/en/docs-develop/

#### SWAP

##### Concept

- Swarm Accounting Protocol
- Generic *peerwise* accounting
- Long-term exchange of data chunks balanced by data chunks preferred
- Relies on reputation system
- Open for payment systems with issue and receive function
- Issue results in a 3rd party proveable promise of payment
- Issued *cheques* will be accumulated in *cheque book*
- Only last one will be cashed in
- Peer decides how often to cash in
- Transactions costs motivate to minimize their number
- Trust to peers grows with good behavior
- SWAP^2 provides API to set triggers for automatic payments
- SWAP^3 reduces transaction cost by debt swap

##### Links

- https://github.com/ethersphere/swarm/wiki/Swap
- https://github.com/ethersphere/swarm/wiki/Swap-demo-instructions

#### Orchid

##### Concept

##### Links

- https://orchidprotocol.com/
