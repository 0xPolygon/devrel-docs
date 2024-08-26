# Pessimistic Proofs

The Pessimistic Proof is a novel cryptographic primitive that allows a
blockchain to prove that it isn't doing anything wrong. In the case of AggLayer,
we use it to prove that the AggLayer-connected chain in question is not
withdrawing more funds than have been deposited into its contract on the L1.

Per the [official post](https://polygon.technology/blog/introducing-the-pessimistic-proof-for-the-agglayer-zk-security-for-cross-chain-interoperability):

Through the Pessimistic Proof, the AggLayer makes three checks:

- Chain updates have been done correctly;
- Chains have done their internal accounting correctly—meaning they didn’t try
  to withdraw tokens they didn’t have; and
- All of the chains together do all of the internal accounting together, correctly.

Each chain connected to the AggLayer maintains a local exit tree, which tracks
all withdrawals from that chain. Using the root of each chain’s local exit tree,
the AggLayer can build a global view of all withdrawals from all chains on the
unified bridge; this is called the “global exit tree.”

Because the global exit tree is committed to the L1, the AggLayer must know that
all local exit trees are valid, too, to ensure that the next global exit tree is
also valid.

In other words, the AggLayer needs to know that the cumulative state of all
connected chains checks out.

To ensure this cryptographically, the AggLayer generates a pessimistic proof,
which requires three inputs from each chain:

- The chain’s local exit tree, as of its most recent update
- The list of new withdrawals included in the current update
- The chain’s expected new local exit root

Using inputs 1 and 2, the AggLayer computes the new local exit root, compares it
with the chain’s expected local exit root, and generates a proof that answers
the question: Did the local exit root update properly?

Using the pessimistic proof, the AggLayer is able to compute how many tokens of
each type were withdrawn from each chain. These values are then summed across
all chains, leaving a single view of the total balances available for each token
on the AggLayer.

If a chain is found to have negative balance at the end of the checking process,
its invalid state cannot be verified on the L1 which prevents it from settling
there.

It should be noted that a chain can still be hacked or brought down - the
AggLayer does not secure against this. However, it does ensure that the chain is
not cheating the whole system by withdrawing more funds than were deposited.