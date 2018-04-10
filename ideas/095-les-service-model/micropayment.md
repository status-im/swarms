## Micropayment

### Existing Solutions

#### µRaiden

##### Concept

- Between two parties: sender (client) and receiver (service provider)
- Communication between sender and receiver via RESTful API
- Creation of channel and settling leads to µRaiden Smart Contract and a deposit
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

#### Links

- https://github.com/ethersphere/swarm/wiki/Swap
