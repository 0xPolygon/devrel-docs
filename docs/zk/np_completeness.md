# NP-Completeness

NP-completeness is a concept from computational complexity theory, which is a
field that studies the difficulty of solving different computational problems.
To explain it in a way that avoids heavy math jargon, though still rigorous,
let's break it down step by step.

Key Concepts:

 1. **Decision Problems**: These are problems that have a simple "yes" or "no"
    answer. For example, "Is there a subset of numbers that adds up to a target
    value?"
 2. **P ([Polynomial time](./polynomial_time.md)):** A class of decision
    problems that can be solved quickly (in polynomial time) by a computer.
    "Quickly" here means that the time it takes to solve the problem scales
    reasonably as the problem gets bigger (e.g., finding a path in a graph).
 3. **NP (Nondeterministic Polynomial time):** A class of problems for which, if
    someone gives you a solution, you can verify that it's correct quickly (in
    polynomial time). You might not be able to solve the problem quickly, but if
    you had a solution, checking if it's right is fast. For example, given a
    solution to a Sudoku puzzle, it's easy to check if it's correct, even though
    solving the puzzle might take a lot of time.
 4. **NP-complete:** These are the hardest problems in NP. If you can solve an
    NP-complete problem quickly (in polynomial time), then you could solve all
    NP problems quickly. Think of NP-complete problems as a "core" or
    "representative" set of the most difficult problems that still fit into the
    NP class.

Example of an NP-complete problem: The traveling salesman problem—finding the
shortest route that visits a list of cities exactly once. It's easy to check if
a proposed route is the shortest, but finding that route in the first place is
tough.

## Why NP-completeness is important

NP-complete problems are important because they define the boundary between
problems that are "easily solvable" and those that seem to be hard. Many
cryptographic proofs, like Zero-Knowledge (ZK) and systems like SNARKs and
STARKs, build on the fact that certain NP-complete problems are hard to solve,
which provides security in cryptographic systems.

## Connection to ZK proofs

ZK proofs often deal with NP problems because we want to verify that someone
knows a solution to a problem without revealing what the solution is. These
proofs take advantage of the fact that while solving an NP-complete problem
might be hard, verifying a solution is easy.

For example, in a ZK proof, you might want to prove you know the solution to an
NP-complete problem without revealing the solution itself, but instead just
prove you can verify it efficiently.

## Putting it together with STARKs/SNARKs

- SNARKs and STARKs are cryptographic tools that allow for verifying
  computations efficiently without needing to go through the entire computation
  process again.
- They are designed to handle NP-complete problems in a way that allows proof
  without direct computation, which ties back to the hardness of solving these
  problems while taking advantage of the ease of verification.

To sum up, NP-completeness is about problems where verifying a solution is easy,
but finding the solution is hard. In cryptography, we often use the fact that
some problems are NP-complete to make systems secure, since solving the problem
is hard, but checking the solution is easy, which is a key idea in
Zero-Knowledge proofs, SNARKs, and STARKs.
