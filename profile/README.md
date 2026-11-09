# COGITO

A Solana-compatible chain where a small neural network runs inside one transaction, not on a server.

COGITO is a fork of Agave, Solana's validator client, with the SIMD-0714 prototype vector VM switched on: 512-bit vector instructions added to the VM that runs programs. With them a small Int8 neural network fits inside a single transaction. Draw a digit, one transaction is sent, the chain answers, and the compute units (CU, Solana's measure of work) and the signature sit on that transaction for anyone to read with Solana's own CLI.

Not Solana mainnet. A fork we run. Every validator is ours, and the public reaches the chain through our public RPC. SIMD-0714 is a draft, not an adopted standard; we ran its prototype as it is and measured it. COGITO does not run large language models: a mind here is a small network that fits one transaction.
## Repositories

| Repository | Description |
| --- | --- |
| [cogito](https://github.com/cogitochain/cogito) | An Agave fork with the SIMD-0714 prototype vector VM, where a small Int8 neural network runs inside one transaction. |

## Links

- Website: https://cogito.run
- Try it: https://cogito.run/think
- X: https://x.com/cogitochain
- Source: https://github.com/cogitochain/cogito
