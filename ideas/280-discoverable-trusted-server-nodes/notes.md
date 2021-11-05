Discoverable And Trusted Server Nodes
=====================================

## Proposed Workflow

1. Mail Server registers itself with a topic `mailserver` in Discovery V5 pool,
1. A client subscribes to Discovery V5 for peers registered with `mailserver` topic,
1. A client verifies that a found Mail Server is trusted using a smart contract,
1.1. If so, the selected Mail Server is cached and used to retrieve historic messages,
1.2. Otherwise, it's discarded and the client waits for new candidates.

### What does happen when a previously trusted Mail Server is not trusted anymore?

(when a previously trusted Mail Server got removed from the smart contract registry)

We can use smart contract events to observe that in order not to check if a given Mail Server is trusted whenever the historic messages are requested ([discussion](https://github.com/status-im/ideas/pull/280/files?utf8=%E2%9C%93&diff=unified#r194015066)).

## Token-Curated Registries

[Detailed Specification](https://docs.google.com/document/d/1BWWC__-Kmso9b7yCI_R7ysoGFIT9D_sfjH3axQsmB6E)

This concept overlaps in many aspects with the smart contract that is needed to be designed for this swarm. TCRs can be used as a solution or inspiration to design the smart contract.

## Q&A

### Q: What consistency level do Mail Servers provide?

Each Mail Server is independent and stores its own log of historic messages. It means there is no sync between them and the consistency is not maintained or even verified. In particular:
- stored messages might be in a different order on each Mail Server,
- if a given Mail Server was down for longer than TTL of some messages, those messages could be lost on a given server.
