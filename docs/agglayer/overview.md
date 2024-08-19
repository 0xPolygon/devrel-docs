# AggLayer Overview

The AggLayer is an in-development interoperability protocol that allows for
trustless, cross-chain token transfers and message-passing, as well as more
complex operations. The safety of the AggLayer is provided by ZK proofs.

The AggLayer currently connects chains built with
[Polygon CDK](https://docs.polygon.technology/cdk/), a developer toolkit for
designing ZK-powered Layer 2s. The long term goal for the protocol is to be
flexible enough to provide interoperability among a growing range of blockchain
architectures, including L2s, appchains, and non-EVM chains.

## Components

The AggLayer is composed of the following components:

- AggLayer Service ([Rust](https://github.com/AggLayer/agglayer-rs) and
  [Go](https://github.com/AggLayer/agglayer-go) version (deprecated in favor of
  Rust))
- Unified Bridge
- Polygon CDK chains

The AggLayer Service is designed to receive ZK proofs from various CDK chains
and verify their validity before sending them to the L1 for final settlement.

Each part of the AggLayer Service is also composed of a number of sub-services
and components:

- a _sequencer_, currently run by Polygon Labs and temporarily centralized, is
  used to order the transactions submitted by the chains in a way that is valid
  to the L1 taking into consideration the interdependencies between the chains.
- a _prover_ will prove that these transactions are valid, per rules provided by
  the authenticator.
- an _authenticator_ is a component which authenticates the
  [pessimistic proofs](pessimistic_proof.md) submitted by a chain. The
  authenticator is provided for each chain by that chain, such that a chain will
  "tell" the AggLayer what's required to consider it as "progressing" to the
  next state. Each chain decides what this state transition condition is - is it
  a compiled set of signatures from some EOAs, or a full proof, or ZK-Proof
  showing that some validators signed off on a block, etc. The authenticator
  serves the role of a _verifier_.
- an _aggregator_ is a component which aggregates the proofs submitted by the
  provers into a single proof.
- a _settler_ sends the aggregated proof to the L1 for final settlement.
