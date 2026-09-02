# NFT Whitelist/Allowlist Ecosystem Research

## Executive Summary

The NFT whitelist ecosystem has evolved from simple wallet lists into multi-layer eligibility systems involving on-chain proofs, NFT/token ownership, snapshots, Discord roles, social activity, and project-specific APIs.

The major challenge is that eligibility data is fragmented across different chains, projects, and verification systems.

## Current Ecosystem

### Major Platforms

- Premint
- Atlas3
- Alphabot
- Ouellette
- Magic Eden
- GoldRush
- Project-specific eligibility checkers

### Chain Landscape

#### Ethereum
- Merkle allowlists
- EIP-712 signatures
- NFT/ERC20 ownership checks
- Snapshot-based eligibility

#### Base
- Similar EVM verification mechanisms to Ethereum
- Lower transaction costs
- Growing use of on-chain eligibility systems

#### Solana
- SPL/NFT ownership checks
- Collection-based eligibility
- Solana-specific APIs and indexers

#### Robinhood Chain
- Emerging ecosystem
- Requires dedicated research into available RPC/indexing infrastructure
- Eligibility mechanisms are still developing

## Major Eligibility Types

1. Merkle allowlists
2. EIP-712 signatures
3. NFT ownership
4. ERC20 balances
5. Snapshots
6. Wallet history
7. Mint history
8. Discord/social requirements
9. Project-specific APIs
10. Hybrid eligibility

## Major Market Gap

There is no single system that reliably checks NFT whitelist eligibility across multiple chains and multiple eligibility mechanisms.

Our system aims to solve this by creating a unified eligibility-checking layer.

## Important Constraints

- Some allowlists are private.
- Some projects only expose eligibility through APIs.
- Discord/social eligibility cannot always be independently verified.
- RPC and API providers have rate limits.
- Eligibility data can become stale.
- Different chains require different infrastructure.

## Architectural Implications

The system should:

1. Support multiple verification mechanisms.
2. Separate on-chain verification from off-chain verification.
3. Support multiple blockchain providers.
4. Cache expensive requests.
5. Handle rate limits.
6. Provide confidence/reliability levels.
7. Avoid requiring wallet transactions for basic checking.
8. Be extensible so new chains and verification methods can be added.
