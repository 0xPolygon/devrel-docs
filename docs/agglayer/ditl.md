# A Day in the Life of an Agglayer Transaction

These are Alistair and Bob.

![Alistair and Bob introduced](../images/ditl_agg_1.png)

Alistair is a blockchain user. He has 100 USDT on Polygon PoS and wants to send
50 to Bob on SwaderChain.

Here we need to declare some assumptions before going further:

1. There exists a cool new wallet we'll call Zigil. All our users' interactions
   will be happening through the UI of this amazing new wallet.
2. The Polygon PoS chain and SwaderChain trust each other (defined when a chain
   joins the Agglayer) on the pre-confirmation stage level (Pragmatism). To
   learn more about different trust levels between chains, please read
   [Trust Levels Between Agglayer Chains](trust.md).
3. Tokens we want to interact with have already accepted their Agglayer version
   (their Unified-Bridge version) as canonical. Thus, when talking about
   "sending USDT", we are referring to USDT in the Agglayer ecosystem, and not
   wUSDT, axl.USDT, or any other wrapped or synthetic derivation.

Polygon PoS is the originator of the transaction, when Alistair attempts to send
50 USDT.

![Alistair attempts to send 50 USDT](../images/ditl_agg_2.png)

Since the chains technically do not see each other, we need a relayer. This is
where Agglayer comes in, which both Polygon PoS and SwaderChain are a part of.

![The Agglayer connects many chains](../images/ditl_agg_3.png)

The Agglayer can connect as many chains as will join it. There is no upper
limit. Due to the [Agglayer's architecture](overview.md), the 50 USDT message
will be traveling through several layers. Let's follow it along!

Once Alistair attempts to send 50 USDT, Zigil will first check if Alistair
has enough balance to send 50 USDT.

## Local Exit and Balance Trees

Even if Alistair has enough balance, to perform a valid cross chain transfer,
Zigil must make sure that the Local Balance Tree of Polygon PoS proves that the
chain has at least 50 USDT available for withdrawal, i.e. that Polygon PoS will
not be withdrawing more funds than have been deposited into it.

All Agglayer chains will periodically automatically generate a Local Balance
Tree of withdrawals and a Local Exit Tree for their state. These are submitted
to the Agglayer which authenticates them using an _authenticator_ provided by
each chain, to generate proof that the Tree of a chain is correct.

More info about trees can be found in the
[Local Exit and Balance Trees](lbt_vs_let.md) page.

Zigil uses this proof's validity to make sure that Polygon PoS has at least 50
USDT available for _burning_ (withdrawal).

## Reading State

Zigil will now read the L1 state of the Agglayer contracts, which for each token
contain a tuple of chain or rollup ID that the token originates from and its
contract address on that chain.

| Token | OriginChain | Address         |
|-------|-------------|-----------------|
| USDT  | Ethereum    | 0xSomeAddress   |
| POL   | Polygon POS | 0x0             |
| ETH   | Ethereum    | 0x0             |
| LINK  | Ethereum    | 0xSomeAddress|
| RMRK  | Moonbeam    | 0xSomeMoonbeamAddress|
| FREN  | Base    | 0xSomeBaseAddress|

The contracts will also note the withdrawable balance per each connected chain,
if non-zero.

| Chain        | Token | Balance |
|--------------|-------|---------|
| Polygon PoS  | USDT  | 20000   |
| Polygon PoS  | LINK  | 3000    |
| zkEVM        | USDT  | 10000   |
| SwaderChain  | USDT  | 0       |
| SwaderChain  | RMRK  | 100000  |
| SwaderChain  | FREN  | 40000   |
| BobChain     | USDT  | 200     |

The mainnet contracts are basically a "list" of all chains and their balances
for particular tokens. This is Agglayer's primary protection against
chain-hack-spillover, as explained on the
[Pessimistic Proof](pessimistic_proof.md) page.

At this point, Zigil knows that Polygon PoS has at least 50 USDT and that at
least this much belongs to Alistair.

In the UI, it will allow Alistair to send 50 USDT. But how does it _send_ to
another chain? Surely a blockchain isn't aware of another blockchain's assets or
its recipients?

Indeed, this is exactly why we need a unifying wallet to abstract away the need
to individually interact with each chain. So what does Zigil actually do now?

## Generating Intent

The _intent_ is for 50 USDT to arrive in Bob's wallet on SwaderChain. As such,
Zigil will create a batch of steps to be executed:

1. Burn 50 USDT on Polygon PoS in favor of the Agglayer, with a reference note
   to the next step.
2. Mint 50 USDT on SwaderChain in favor of Bob, with a reference note to the
   previous step.
3. Batch these two steps into a single transaction for inclusion in the Agglayer.

With the intent now clear, we need proofs that these steps are valid for them to
execute.

## Authenticator, Prover, Aggregator, and Settler

An authenticator is a component which authenticates the block production of a
chain and the exit tree submitted by the chain.

Each chain provides its own authenticator to the Agglayer, such that the
Agglayer can run checks against it. If a block and the chain's Pessimistic Proof
are authenticated with the Prover, the Aggregator will aggregate them into a
single proof. This proof is then sent to the Settler (in this case a tool called
Ethereman) which will send it to the L1 for final settlement.

In the phase before settling but after verifying proofs, the state of the chains
is still in the Agglayer. In [pragmatism](trust.md), this is the state that is
used. At this point, since SwaderChain has a pragmatic view of Polygon PoS, it
will use the state of Polygon PoS as it was when the block was produced. It will
not wait for the L1 to confirm the state transition, because the proofs alone
are enough to confirm that the state transition is valid.

## Minting and Burning

The Agglayer does not execute transactions. It only verifies the chain Trees and
aggregates the proofs of their validity. The actual execution of the transaction
is done by the sequencer, or some application that is trusted to do so.

The batch is now unpacked and executed, making the following
state transitions:

1. Burn 50 USDT on Polygon PoS
2. Reduce Polygon PoS's withdrawable USDT balance by 50
3. Issue certificate about the validity of this state transition
4. Once authenticator verifies the certificate, it means all the transferred
   assets can now be "safely" claimed on destination chains
5. Mint 50 USDT on SwaderChain, claim in Bob's name
6. Increase SwaderChain's withdrawable USDT balance by 50

After these steps, both chains will again be generating a Local Exit Tree and
Local Balance Tree of withdrawals to be submitted to the Agglayer as Pessimistic
Proofs. This is again done to secure the unified bridge from hack spillovers.
