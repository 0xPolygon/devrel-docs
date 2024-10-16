# Miden overview

Miden is a rollup for high-throughput and private applications. It features
private accounts, a hybrid account/UTXO state model using
[Notes](./note_features.md) (which themselves have
[different types](./note_types.md)) and local transaction execution with proof
generation. It inherits Ethereum's security and decentralization, with the added
benefit of privacy and high throughput.

!!! info

    To learn about Miden's technical details, architecture, and how to deploy
    its parts, please see the
    [Miden technical docs](https://docs.polygon.technology/miden/).

Miden's design makes it intuitive for developers who may wish to build private
applications in DeFi, Gaming, prediction markets, governance, and more. Here are
some examples:

## Private DeFi trading

A decentralized exchange could leverage Miden's private notes to enable
confidential trading. Users could create private notes containing their trade
orders, including asset amounts and desired exchange rates. The note's script
would define the conditions for execution, such as price limits. When it finds
matching orders, the transaction kernel would execute privately, swapping assets
between parties without revealing trade details to the network.

## Confidential voting system

Miden's private notes allow implementing a transparent yet confidential voting
system. Each eligible voter would receive a private note containing their voting
rights. The note's script would ensure that each user can only vote once. Voters
cast votes as private transactions, with the results tallied by the network
without revealing individual votes. This system would provide verifiable
integrity while preventing vote buying or coercion.

## Privacy-preserving gaming

A blockchain-based game could use Miden's hybrid account/UTXO model to manage
in-game assets and actions. Private notes store players' inventories and
progress, while public notes store global game state. Note scripts implement the
game logic, allowing for complex interactions and trades between players without
revealing sensitive information about their game state to others.

## Confidential supply chain management

Businesses could use Miden to track their supply chain while maintaining
confidentiality. A private note represents each step in the supply chain,
containing information about the product, its origin, and current status. The
note's script could enforce business rules and regulatory compliance. Partners
could selectively share information using encrypted notes, allowing for
transparency where needed while keeping sensitive details private.

## Private prediction markets

A prediction market platform could leverage Miden's privacy features to create
markets where participants can place bets without revealing their positions.
Each bet is a private note, with the note's script defining the conditions for
winning. The market's aggregated data is then made public through a separate
mechanism, while individual bets remain confidential. This would prevent
front-running and market manipulation while still providing valuable
crowd-sourced predictions.
