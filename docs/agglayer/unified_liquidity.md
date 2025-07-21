# Unified Liquidity

As more and more L2s appear, followed by their own L3s and beyond, the
fragmentation of liquidity across chains becomes a problem. Coupled with a
multitude of bridges each using their own unique wrapper for a bridged token,
and the liquidity is sometimes fragmented even on the same chain, compounding
the problem.

The aim is to provide a single source of liquidity for all chains connected to
the Agglayer. This is done through the Unified Bridge, which allows users to
deposit and withdraw liquidity from any chain connected to the Agglayer.

So how does Unified Liquidity work in practice?

Let's look at an example using AggToken, a hypothetical token that is bridged
across multiple chains.

As with the [Day in the Life of an Agglayer Transaction](ditl.md), we have to
make some assumptions.

- Assumption 1: Alistair uses Zigil, an Agglayer superwallet.
- Assumption 2: The issuer of AggToken accepts the Unified Bridge as canonical.

Alistair wants to buy 10000 AggTokens. 30000 AggTokens are in the LP on
AlistairChain, 20000 on Bobchain, and 50000 on Ethereum. Buying 10000 in any of
these chains would cause quite a bit of slippage due to limited liquidity depth
and would expose Alistair to sandwich attacks, but buying a smaller amount three
times would open Alistair up to arbitrage where others could quickly profit from
the price difference he caused.

Zigil can cleverly calculate the best way to buy 10000 AggTokens with minimal
slippage and arbitrage risk totals. Let's say that due to the LP setups in the
DEXes on these chains, Zigil can buy 1000 AggTokens on AlistairChain, 1000 on
Bobchain, and 8000 on Ethereum. Zigil will buy 10000 AggTokens in three
transactions, one on each chain, but submitted at once to the a sequencer that
works with Agglayer which will make sure the bundle is executed atomically.

In a step by step manner, the Agglayer sequencer will:

1. Receive the bundle of transactions from Zigil.
2. Validate the local exit proof for each chain included in the bundle, and the
   chains' pessimistic proofs.
3. Aggregate the proofs and at the same time submit the transactions to the
   chain mempools and make sure they are executed.
4. Show Alistair a single balance of 10000 AggTokens, but the actual balance
   will be 1000 + 1000 + 8000 on three different chains.

Now what happens when Alistair decides to send 9000 AggTokens to a vault on BobChain?

1. Zigil will make sure Alistair still has this balance total.
2. Zigil will calculate the best way to send these tokens. Since the vault is on
   BobChain, Zigil will send 8000 from Ethereum to BobChain, and then 9000 on
   BobChain to a BobChain vault.
3. Once the chain proofs are all verified and validated, Zigil (or another
   entity, like the target chain or the dapp which monitors the cross chain
   transactions to pick up the claiming process on the target chain) will make
   sure the bundled transactions are executed in the correct order, again
   atomically. First, the 8000 AggTokens on Ethereum will be burnt, and then
   minted on BobChain. The minted tokens will then be sent to Bob. Then the
   whole balance of 9000 tokens will be sent to the BobChain vault. These are 3
   transactions on 2 chains, all bundled together and executed and proven one by
   one.
4. First, the proof that an 8k burn on Ethereum will be successful is generated.
   Then, the proof that the 8k mint on BobChain will succeed is generated, and
   depends on the previous proof. Finally, the proof of the previous two
   transactions is generated as a prerequisite for the 9k transfer to the
   BobChain vault, which will generate its own proof of success. These proofs
   are then aggregated and submitted to the settler for settlement on Ethereum,
   while they are executing on the individual chains to actually change the
   state.
5. After everything is done and Zigil becomes aware of the proofs being settled,
   Zigil shows Bob a 9k vault balance, and 1k AlistairChain balance of
   AggTokens.
