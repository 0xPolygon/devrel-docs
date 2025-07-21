# Exit Tree vs Balance Tree

In both cases we're talking about Merkle Trees, data structures for secure
verification of data in large content pools. Merkle Trees hash information at
the leaf level (data input level, in a manner of speaking) and then use a hash
function to hash these data, further hashing the hashes in pairs until a single
hash is obtained. This hash is the Merkle root of the tree.

The Local Exit Tree is used for a rollup chain's state proofs. ZK proofs and
fraud proofs both work with Local Exit Trees. "Local" refers to the fact that
the tree is built from the chain's current state, while "Exit" refers to the
fact that the tree is used to exit funds from the chain.

Another Merkle tree whose leaves are then the roots of the various exit trees is
called the global exit tree. The root of the global exit tree is the single
source of state-truth communicated between rollups. The GER is stored on the
mainnet settling the rollups.

The Local Balance Tree is for accounting outgoing balances.
[Pessimistic proof](./pessimistic_proof.md) uses the LBT to match with the
global exit root and L2 balances. The LBT is tracked and maintained by the
Agglayer for now, because the Agglayer currently generates the pessimistic
proof. Later on, the chains will generate their own pessimistic proofs and LBTs
and submit them to the Agglayer.
