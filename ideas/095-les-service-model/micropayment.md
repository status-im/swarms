## Micropayment

### Existing Solutions

#### Raiden

##### Concept

- Off-chain solution for ERC20-compliant token transfers on Ethereum
- Transfer of tokens without global consensus
- Previously setup on-chain deposits and *balance proofs*
- Payment channels for bidirectional transfers between two participants as long as deposit isn't exceeded
- Transfers require no fees
- Funds can be added to existing channels
- Blockchain isn't involved during transfers, only for channel creation and potential closing
- As binding as on-chain due to smart contract containing tokens only accessable to both participants
- Closing leads to payments to both participants based on balance
- *Network* of channels with routing allow transfers between all peers, secured by *hash-locks*
- Scaling with the number of peers
- RESTful API

##### Links

- https://raiden.network/
- http://raiden-network.readthedocs.io/en/stable/
- https://medium.com/@raiden_network/

#### µRaiden

##### Concept

- Like Raiden but only between two parties: *sender* (client) and *receiver* (service provider)
- Designed for 1:N solutions
- Creation of channel and settling leads to µRaiden Smart Contract and a *deposit*
- Smart Contract enforces payment of deposit
- Signing payments with balance-proofs between sender and receiver allows off-chain transactions
- Once channel gets closed deposit is payed to receiver based on *balance proofs* and rest to sender
- Typically only two on-chain transactions for opening and closing
- If deposit of sender gets low it can increase it with an on-chain transaction
- Own ERC20 and ERC223 compliant token
- RESTful API

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
