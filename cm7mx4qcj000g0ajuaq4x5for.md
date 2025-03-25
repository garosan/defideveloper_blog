---
title: "Understanding Morpho: A New Approach to Decentralized Lending"
datePublished: Thu Feb 27 2025 05:43:10 GMT+0000 (Coordinated Universal Time)
cuid: cm7mx4qcj000g0ajuaq4x5for
slug: understanding-morpho-a-new-approach-to-decentralized-lending
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1740594980320/39b0bb13-6288-412b-a1b1-3313a57b603d.png
tags: web3, blockchain-development, defi, defi-lending

---

I've recently started collaborating on a DeFi project that was developed during a hackathon and utilizes Morpho. Before this, I had no prior knowledge of Morpho, so I had to dive into its documentation to understand how this lending protocol operates. After a few hours of research, I became fascinated with what I was learning and decided to create a series of articles to explore Morpho's mechanics and how it differentiates itself from other lending protocols like AAVE and Compound. I will analyze every concept of their documentation that will help us understand better lending primitives and explain it with examples and code. Let’s dive into it!

## What is Morpho?

Morpho follows this paradigm of having a ‘Labs’ as a regular entity that built the original tech, a DAO and a protocol. Morpho Labs was co-founded by Paul Frambot, Merlin Egalite, Julien Thomas, and Mathis Gontier Delauney. Frambot, the CEO, secured a $1 million seed round during his final year as an engineering student, followed by a $20 million investment from Andreessen Horowitz and Variant. The protocol launched on Ethereum mainnet in July 2022.

From their docs, Morpho showcases 6 main products or topics:

* Morpho
    
* Morpho Vaults
    
* Bundlers
    
* Public Allocator
    
* Rewards
    
* Morpho Optimizers (deprecated)
    

Let’s take a look at the main product: the Morpho protocol. Morpho is a decentralized lending and borrowing protocol designed to be more efficient and flexible than traditional DeFi lending platforms. In Morpho you can deploy a minimal and isolated lending market by specifying:

* One collateral asset
    
* One loan asset
    
* A Liquidation Loan-To-Value (LLTV)
    
* An Interest Rate Model (IRM)
    
* An oracle
    

We will see what all these means through the series.

Unlike traditional lending protocols that require governance approval for asset listings and parameter changes, Morpho allows for permissionless market creation. Anyone can create a market with different collateral tokens, borrowable tokens, and oracles, and for the LLTV and IRM you have to choose between the options pre-approved by the Morpho DAO governance.

The following LLTVs have been DAO-approved: \[0%; 38.5%; 62.5%; 77.0%; 86.0%; 91.5%; 94.5%; 96.5%; 98%\].

The only **Interest Rate Model (IRM)** that has been DAO-approved is the *AdaptiveCurveIRM*, which we will cover in another article.

In Morpho, markets are named in the following format:

`CollateralAsset/LoanAsset (LLTV, ORACLE, IRM)`

so a market named `wstETH/WETH (94.5%, ChainlinkOracle, AdaptiveCurveIRM)` is very simple to read: the collateral asset is `wstETH`, the asset to loan is `WETH`, the LLTV is 94.5%, the oracle to be used is from Chainlink and the interest rate model that will be used is `AdaptiveCurveIRM`. Simple.

### Key Features of Morpho

* **Overcollateralized lending**: Borrowers must provide more collateral than the value of their borrowed assets.
    
* **Immutable protocol**: Once deployed, Morpho will function in perpetuity without governance interference, provided the blockchain where it is deployed keeps functioning.
    
* **Permissionless market creation**: Each market has fixed parameters, ensuring stability and predictability.
    
* **Externalized risk management**: Users, rather than protocol governance, determine risk exposure.
    
* **Oracle-agnostic pricing**: Rather than being oracle-less, Morpho allows market creators to choose their preferred price oracle.
    

## Governance and Risk Management

Traditional platforms centralize risk management through governance voting. For example, AAVE token holders vote on whether an asset like SHIB can be used as collateral and determine its risk parameters. This approach limits scalability and forces users into a single risk model.

Morpho decentralizes risk management, allowing users to create and interact with any deployed market. This enables:

* Customizable risk profiles
    
* Greater asset diversity
    
* Scalable and autonomous lending markets
    

For example, Morpho Labs created Morpho Vaults, which is a product built on top of Morpho which facilitates the creation of lending vaults on top of Morpho markets. This is how they work in a nutshell:

* A "Vault" is a smart contract that aggregates funds from multiple lenders.
    
* A "Curator" manages the vault’s risk parameters and strategy.
    
* The Vault then supplies funds across different Morpho markets in an optimized way.
    

This allows passive lenders to supply their assets and forget about assessing which markets have the appropriate collateral, LLTV, oracle, and IRM, the vault does it on their behalf.

In the following articles we will keep dissecting key Morpho concepts like understanding how their liquidation mechanism works, how they interest rate model works and, much more.

## Conclusion

Morpho is a very interesting DeFi lego which introduces a new paradigm in decentralized lending by enabling immutable, permissionless markets with user-controlled risk management. Unlike traditional lending platforms like AAVE and Compound, Morpho removes governance bottlenecks and empowers users with greater flexibility. Many more products can be built on top of this like their Morpho Vaults, flash loans and more. We will cover more of these topics in upcoming articles. Keep building 🚀