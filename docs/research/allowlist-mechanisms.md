# NFT Allowlist Verification Mechanisms

## Purpose

This document defines the different mechanisms NFT projects can use to determine whether a wallet is eligible.

Our checker must identify which mechanism a project uses and select the appropriate verification backend.

---

## 1. Merkle Allowlist

### Description

A project stores a Merkle root on-chain and provides eligible wallets with Merkle proofs.

### Required Data

- Contract address
- Merkle root
- Wallet address
- Merkle proof
- Allocation
- Mint price
- Chain ID

### Verification

Fully on-chain.

### Reliability

Very High.

### Backend Required

- RPC provider
- ABI/contract interaction
- Merkle proof verification

### Priority

P0 — Build first.

---

## 2. EIP-712 Signature

### Description

The project signs eligibility data for each wallet.

### Required Data

- Contract address
- Signer address
- Wallet address
- Signature
- Nonce
- Deadline
- Chain ID
- Allocation

### Verification

Cryptographic signature verification.

### Reliability

Very High.

### Priority

P0.

---

## 3. NFT Ownership

### Description

Eligibility depends on holding a specific NFT.

Example:

`Hold ≥ 1 Azuki`

### Required Data

- NFT contract
- Wallet address
- Required balance
- Optional token ID
- Optional snapshot block

### Verification

On-chain `balanceOf()` / `ownerOf()`.

### Reliability

High for real-time ownership.

### Priority

P0.

---

## 4. ERC20 Balance

### Description

Eligibility depends on holding a minimum token balance.

### Required Data

- Token contract
- Wallet address
- Minimum balance
- Optional snapshot block

### Verification

On-chain `balanceOf()`.

### Reliability

High for real-time checks.

### Priority

P1.

---

## 5. Snapshot Eligibility

### Description

Eligibility depends on wallet state at a specific block.

### Required Data

- Snapshot block
- Contract address
- Eligibility criteria
- Snapshot data

### Verification

Depends on whether snapshot data is public and verifiable.

### Reliability

Medium.

### Priority

P1.

---

## 6. Wallet History

Examples:

- Wallet older than 6 months
- 100+ transactions
- Traded $10,000+
- Used specific protocols

### Verification

Requires blockchain indexing.

### Reliability

Medium.

### Infrastructure

- Indexer
- Blockchain RPC
- Database

### Priority

P2.

---

## 7. Mint History

Examples:

- Minted from Project X
- Minted 5 NFTs
- Participated in previous collection

### Verification

Requires historical blockchain data.

### Priority

P2.

---

## 8. Discord/Social Eligibility

Examples:

- Discord OG role
- Discord level
- Twitter engagement
- Completed social tasks

### Verification

Off-chain.

### Reliability

Low-Medium.

### Infrastructure

- Discord API
- Project API
- Social APIs

### Priority

P2/P3.

---

## 9. Project-Specific API

Some projects expose an endpoint that directly returns eligibility.

Example:

GET /eligibility?wallet=0x...

### Reliability

Low-Medium.

### Problem

There is no universal API standard.

### Priority

P2.

---

## 10. Hybrid Eligibility

Projects can combine multiple requirements.

Example:

NFT holder AND Discord role

OR

NFT holder OR OG role

The verification engine must support logical operators:

- AND
- OR
- NOT
- thresholds
- tiers

### Priority

P1.

---

# Verification Priority

| Mechanism | Verification | Reliability | Priority |
|---|---|---|---|
| Merkle | On-chain | Very High | P0 |
| EIP-712 | Cryptographic | Very High | P0 |
| NFT ownership | On-chain | High | P0 |
| ERC20 balance | On-chain | High | P1 |
| Snapshot | Hybrid | Medium | P1 |
| Hybrid rules | Mixed | Depends | P1 |
| Wallet history | Indexed | Medium | P2 |
| Mint history | Indexed | Medium | P2 |
| Project API | Off-chain | Low-Medium | P2 |
| Discord/Social | Off-chain | Low-Medium | P3 |
