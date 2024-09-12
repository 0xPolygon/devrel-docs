# CDK Overview

Polygon Chain Development Kit (CDK) is an innovative toolkit designed for
blockchain developers who want to create customizable layer 2 (L2) chains. It
empowers developers to launch new L2 chains that leverage Polygon's zkEVM
technology on Ethereum, with the option to use validium networks. In the future,
CDK will also support transitioning existing layer 1 chains into custom ZK-EVM
L2s.

## Key Features

CDK offers several key features that make it an attractive option for blockchain
developers:

1. Security: CDK utilizes cutting-edge zero-knowledge technology to build highly
   secure and scalable L2 chains.
2. Scalability: Chains built with CDK can process transactions much faster and
   at a lower cost compared to Ethereum, providing a superior user experience.
3. Modularity: The toolkit's components are designed to be easily customizable,
   allowing developers to tailor their L2 environment to specific needs.
4. Interoperability: Developers can choose to connect their chains to the
   [AggLayer](../agglayer/overview.md), enabling cross-chain transactions and
   access to a broader ecosystem of users and liquidity.
5. Sovereignty: Chain operators maintain full control over various aspects of
   their chain, including revenue, governance, security, and economic policies.

## Architecture and Components

CDK-built chains share a common high-level architecture, which includes
components for processing transactions, producing zero-knowledge proofs, and
interacting with Ethereum. The toolkit supports two main deployment modes:
rollup and validium, each with its own trade-offs in terms of security and
scalability.

## Bridging and Interoperability

CDK chains come with built-in bridging capabilities, allowing users to move
assets between the L2 chain and Ethereum. Developers can choose between a
standalone bridge or opt into the AggLayer's
[unified bridge](../agglayer/unified_liquidity.md) for enhanced interoperability
with other L2 chains.

## Customization Options

CDK offers various customization options, including the ability to create native
tokens, implement custom bridge solutions, and integrate with third-party data
availability solutions. Developers can also manage governance and economic
policies according to their specific requirements.

## Ecosystem Benefits

By leveraging CDK, developers can create sovereign and modular L2 chains that
benefit from the broader Polygon ecosystem. This includes access to unified
liquidity, optimized performance, and seamless asset transfers across different
chains, all while prioritizing user experience and data security.

For those interested in exploring CDK further, Polygon provides
[comprehensive technical documentation](https://docs.polygon.technology/cdk/)
to help developers understand and leverage the full potential of this
innovative toolkit. For hands on learning, stay tuned for the CDK tutorials.
