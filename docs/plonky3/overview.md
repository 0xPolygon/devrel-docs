# Polygon Plonky3 Overview

## What is Plonky3 and How does it work?

[Plonky3](https://github.com/Plonky3/Plonky3) is a toolkit for implementing polynomial IOPs (PIOPs), such as PLONK and STARKs, allowing developers to configure a variety of to-spec implementations from a single ZK proving system. 

Polygon Plonky3 supports several finite fields and hash functions. Currently, the only supported polynomial commitment scheme is FRI, but future releases will support several, including Brakedown.

## Understand Plonky3

Plonky3 is a toolkit for designing a custom ZK proving implementation that can then be used to power application-optimized zkVMs and zkEVMs. 

In the same way an AI dev uses Pytorch and Tensorflow for building AI models, Polygon Plonky3 provides the same flexibility for building ZK proving systems. Polygon Plonky3 enables simple builds, such as the Fibonacci sequence prover in this repo that requires only one AIR Scripts, to complex systems, such as SP1 from Succinct labs with multiple AIR scripts for different components of a single zkVM. 

## How does Plonky3 work?

Here's a TLDR version:

1. Define the computation using Algebraic Intermediate Representation (AIR).
2. Generate a trace of the computation based on the AIR.
3. Utilize efficient finite field implementations for arithmetic operations.
4. Apply Generalized Vector Commitment Schemes to create succinct representations of large vectors or polynomials.
5. Use polynomial commitment schemes like Circle PCS for compact polynomial representations.
6. Perform fast polynomial operations using FFTs and related algorithms.
7. Implement the FRI (Fast Reed-Solomon IOP) protocol to prove properties about committed polynomials.
8. Employ a challenger mechanism with the Fiat-Shamir heuristic for non-interactive proofs.
9. The unified STARK prover combines all components to generate the proof.
10. The verifier uses the same components to efficiently check the proof's validity.

Plonky3's modular design allows for easy customization and optimization of different components, making it adaptable to various use cases and performance requirements.

#### "Seems very complicated, I don't understand half of the steps."
_Don't worry, These are the underlying workflow of Plonky3 based ZK system, if you are builders who are using Plonky3, your main job is at Step 1 and Step 2, the rest is just configuration!_

## Outline
- [Overview](./overview.md)
- Concepts:
  - [Fields](./concepts/fields.md)
  - [Hash Functions](./concepts/hash_functions.md)
  - [Polynomial Commitment Schemes](./concepts/pcs.md)
  - [FRI](./concepts/fri.md)
- Examples:
  - [Fibonacci Sequence](./examples/fibonacci.md)
  - [Range Check](./examples/range_check.md)
  - [Merkle Tree](./examples/merkle_tree.md)
- zkVMs Step by Step Guide
- zkML Step by Step Guide