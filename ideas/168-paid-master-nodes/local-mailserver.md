# How to run and use mail server locally

## status-go

Just some notes:

```
make statusgo
./build/bin/statusd -shh -datadir=paid-data-mailserver -shh.mailserver -shh.passwordfile=wnode-data-mailserver/password.txt -listenaddr=127.0.0.1:30303 -log=DEBUG -ipc
```

Verify peers are connected separately:

```
geth attach ~/git/status-go/paid-data-mailserver/geth.ipc
admin.peers
```

## Clojure side

Add local mail server to `constants.cljs` where address is RLPx in print out above, e.g:

```
"paid" {:id      "paid"
        :name    "Status testnet mailserver paid, experimental"
        :address
        "enode://9f0a55f116aedb40d4036d9a385d505d9c183fd708ef1aa2f883895df97864f758eee911c26c86732ae13a57664a076de2527189f983ee24dda2a4cb5f5db777@127.0.0.1:30303"}
```

Connect to it, might need to switch networks and login/logout etc to trigger
requestMessages`. Make sure networks match. Check logs for `offline inbox` to
see flow. Can switch offline server in advanced settings.

If there are issues with peers, and mail server has peers, then going into CLJS repl and:

```
(require 'status-im.transport.inbox)
(status-im.transport.inbox/add-peer "enode://987c40d5761678f030d80de13a2f8a0150da651e5d2c430b96e4f8c2c544389918c7bd820d2d6a5610afb96dcedf8ebb0b941859a0cdbd7dddbbd13994dcbe52@[::]:30303" println println)
(status-im.transport.inbox/fetch-peers println println)
```

can help with debugging.

## Notes

Note that this above flow only modifies the 'server' side of mail server and UI
side of client. If you want to modify status-go node on client side you need to
make sure status-go is built and linked properly in the app. See
https://github.com/status-im/status-react/blob/develop/scripts/bundle-status-go.sh
