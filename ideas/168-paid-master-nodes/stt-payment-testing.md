# Getting and sending STT, proof of payment

Some notes for initial payment MVP and testing thereof.

## How do I get STT?

- Be on Ropsten
- Advanced settings -> Development mode
- Chat with console and use `/faucet <StatusFaucet>` to get ETH
- > For STT simply send a transaction (can be 0 ether) with Gas limit 105000 (you need to set the value manually!) to the following address: 0x34358C45FbA99ef9b78cB501584E8cBFa6f85Cef (https://wiki.status.im/Testing_FAQ_(core_team))
- You should have 1000 STT

## Sending and getting proof of payment

Send STT tx to <some address> (friend, mail server) with default gas and:
:status-im.ui.screens.wallet.send.events/transaction-completed
:response -> :id/:hash => 0x1734f4ff6840ec92b589ca7fc2adbee3c8bcb16b4bffe9954496e00f9d27eeb1

Shows up here: https://ropsten.etherscan.io/tx/0x1734f4ff6840ec92b589ca7fc2adbee3c8bcb16b4bffe9954496e00f9d27eeb1

Can probably be queried in a more trustless way, but requires further
investigation. Depends on what services are running on mail server.

## Requesting funds?
Limitation: can't currently request funds in STT. Also coupled with chat, etc.
Easier to just pop up tx screen. Prefilled.

## Payment for MVP

Navigate to `:wallet-send-transaction` with:
- recipient
- STT
- amount
- gas price filled in / default

You send it, and once you get tx completed you have hash id. This can be sent to
mail server who can verify it and accept it. This means you paid and it is up to
mail server to respect in a way. You send this tx id to mail server. It responds
with some OK message.

(Ideally funds are locked so you don't send payment and it doesn't respect it,
but this is a later iteration).

## Problem re proof of payment

If you send tx id, you have enode, but this should be verified with address. So
ideally you'd sign tx with your account. Iteration 1? Separate dock.
