# zkEVM Overview

Polygon zkEVM is a Layer 2 scaling solution for Ethereum that leverages
zero-knowledge technology to provide fast and secure transaction validation with
rapid finality.

!!! info

    To learn about zkEVM's technical details, architecture, and how to deploy
    its parts, please see the
    [zkEVM technical docs](https://docs.polygon.technology/zkEVM/).

As an EVM-equivalent solution, it supports
[most Ethereum EIPs](https://docs.polygon.technology/zkEVM/architecture/protocol/etrog-upgrade/#eips-support),
[precompiles and opcodes](https://docs.polygon.technology/zkEVM/architecture/protocol/etrog-upgrade/#zkevm-is-almost-type-2),
allowing developers to seamlessly deploy existing Ethereum smart contracts and
use familiar tools in a more cost-effective environment.

The zkEVM network achieves its security by inheriting from Ethereum while
implementing additional measures. These include a multi-signature admin
contract, a timelock mechanism for upgrades, and a Security Council for
emergency interventions. All transaction data and validity proofs are posted on
Ethereum, ensuring full data availability and enabling users to reconstruct the
complete state of the rollup if necessary.

Efficiency is a core focus of Polygon zkEVM. The network employs various
strategies to maximize performance, such as off-chain computation with on-chain
data and proof storage, an efficient bridge implementation using Merkle roots,
and a specialized zkProver component. The zkProver utilizes advanced
cryptographic techniques, including a custom zero-knowledge assembly language
(zkASM) and a combination of zk-STARKs and zk-SNARKs, to significantly reduce
gas costs and improve overall efficiency.I will

Developers and users can connect to the fully-audited Polygon zkEVM mainnet or
its testnet (Cardona) using the
[provided RPC URLs and chain IDs](https://docs.polygon.technology/zkEVM/get-started/json-rpc/).
With its combination of Ethereum compatibility, enhanced scalability, and robust
security measures, Polygon zkEVM offers a powerful solution for those seeking to
build and deploy decentralized applications with lower costs and higher
throughput.
