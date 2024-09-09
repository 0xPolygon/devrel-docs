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
  to the L1 taking into consideration the interdependencies between the chains,
  as in, where the burning happens vs where the minting and claiming happens.
- a _prover_ will prove that these transactions are valid, per rules provided by
  the authenticator. While the prover is a component of the AggLayer as a whole,
  it is run by the chains, not the AggLayer itself.
- an _authenticator_ is a component which authenticates the
  [pessimistic proofs](pessimistic_proof.md) submitted by a chain. The
  authenticator is provided for each chain by that chain, such that a chain will
  "tell" the AggLayer what's required to consider it as "progressing" to the
  next state. Each chain decides what this state transition condition is - is it
  a compiled set of signatures from some EOAs, or a full proof, or ZK-Proof
  showing that some validators signed off on a block, etc. The authenticator
  serves the role of a _verifier_. The authenticator, in simple terms, helps the
  AggLayer understand if it can accept the Pessimistic Proof provided by the
  chain.
- an _aggregator_ is a component which aggregates the proofs submitted by the
  provers into a single proof.
- a _settler_ sends the aggregated proof to the L1 for final settlement.
- AggSender - a component which communicates bridge updates from the chain to
  the AggLayer.

## Joining the AggLayer

Technically, any chain can join the AggLayer.

A chain sets its own authenticator which can be an execution proof, proof of
consensus, signature check, or anything else. So really, any SYSTEM can join the
AggLayer (not necessarily only chains) using Pessimistic Proofs, but how secure
that connection is depends on the authenticator.

As an example, zkEVM will be using execution proofs - the most secure version at
this time. Non-EVM (or non blockchain) systems will need their own
implementation of the AggLayer's data structures and messaging format (LxLy,
Local Exit Tree etc.), and some authenticator to use (probably JTMB).

There are four main things that a chain needs:

- bridge contracts
- native [local exit tree](lbt_vs_let.md) implementation (data structure that
  tracks withdrawals for the AggLayer)
- AggSender equivalent: component that implements the functionality of
  communicating bridge updates from the chain to the AggLayer
- oracle equivalent: component that submits the L1 GER information to the chain.

Most of these needs will be covered by the
[CDK](https://docs.polygon.technology/cdk/).
