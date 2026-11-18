<p align="center"><a href="https://cogito.run"><img src="assets/banner.png" width="100%" alt="COGITO"></a></p>

<p align="center">
  <a href="https://cogito.run"><img src="https://img.shields.io/badge/site-cogito.run-111111?style=flat-square" alt="Site"></a>
  <a href="https://cogito.run/think"><img src="https://img.shields.io/badge/try-think-111111?style=flat-square" alt="Try it"></a>
  <a href="https://x.com/cogitochain"><img src="https://img.shields.io/badge/X-cogitochain-111111?style=flat-square" alt="X"></a>
  <a href="https://github.com/cogitochain/cogito"><img src="https://img.shields.io/badge/source-cogito-111111?style=flat-square" alt="Source"></a>
  <a href="https://github.com/cogitochain/cogito#license"><img src="https://img.shields.io/badge/licenses-MIT%20%2F%20Apache%202.0-111111?style=flat-square" alt="Source licences"></a>
  <a href="https://github.com/anza-xyz/agave"><img src="https://img.shields.io/badge/engine-Agave%20fork-111111?style=flat-square" alt="Agave fork"></a>
</p>

# COGITO

A Solana-compatible chain where a small neural network runs inside one transaction, not on a server.

COGITO is a fork of Agave, Solana's validator client, with the SIMD-0714 prototype vector VM switched on: 512-bit vector instructions added to the VM that runs programs. With them a small Int8 neural network fits inside a single transaction. Draw a digit, one transaction is sent, the chain answers, and the compute units (CU, Solana's measure of work) and the signature sit on that transaction for anyone to read with Solana's own CLI at https://rpc.cogito.run. The node keeps only the newest few hours of transactions, so read a fresh thought; the site keeps its own record of each one.

Not Solana mainnet. A fork we run. Every validator is ours, and the public reaches the chain through our public RPC. SIMD-0714 is a draft, not an adopted standard; we ran its prototype as it is and measured it. COGITO does not run large language models: a mind here is a small network that fits one transaction.

The digit network takes 1,700 compute units as a vector program (1,850 for the whole transaction as the site sends it) and 349,958 as its scalar twin, with the same weights and the same answer, on our network of 4 validators in 3 emulated locations on one server (the whitepaper's Measured table lists every condition). The public repository rebuilds both digit programs byte for byte and runs their checks; our measuring scripts are not public, and any thought on the network can be read with the stock CLI.

## Token and chain

- $COGITO is an SPL token on Solana mainnet. CA: `Cogito6Ss5vhwAqjkrB5jVRr3GXwtmseJqZm9CyUy4di` ([Solscan](https://solscan.io/token/Cogito6Ss5vhwAqjkrB5jVRr3GXwtmseJqZm9CyUy4di))
- The plan is for $COGITO to become this chain's gas and stake, with holders' balances at a stated slot carried into the chain; no date is set yet. Today the chain runs on test gas from a faucet, and no wallet is needed to send a thought.
- Every thought is a transaction on the COGITO chain with its compute units on it.

## What a thought is

- **a thought**: one transaction that runs a neural network once.
- **a mind**: one neural-network program deployed on the chain.
- **think**: to send that transaction.
- **the bench**: where the old way and the new way run side by side on the same input and are measured.

## How it works

1. The engine is Agave with the SIMD-0714 prototype vector VM. Every validator needs AVX-512; without it the engine does not start.
2. A mind is an Int8 network, 256 inputs, 128 hidden, 16 outputs, written as machine code that uses the vector instructions. Each mind has a scalar twin with the same weights on today's instruction set.
3. In the browser a drawing becomes 256 bytes. The browser makes a throwaway key, receives test gas from the faucet and sends one transaction to the mind.
4. The chain runs the network inside that transaction and returns the answer. The answer, the compute units, the signature and an explorer link appear in place.
5. Anyone reads the same number with the stock Solana CLI by pointing `solana confirm -v <signature>` at the RPC URL shown on the site.

## Repositories

| Repository | Description |
| --- | --- |
| [cogito](https://github.com/cogitochain/cogito) | An Agave fork with the SIMD-0714 prototype vector VM, where a small Int8 neural network runs inside one transaction. |

## Links

- Website: https://cogito.run
- Try it: https://cogito.run/think
- X: https://x.com/cogitochain
- Source: https://github.com/cogitochain/cogito
