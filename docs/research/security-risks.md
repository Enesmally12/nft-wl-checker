# Security Requirements

## Core Principle

The WL checker should be a read-only verification system.

A user should NOT need to sign a transaction just to check eligibility.

## Major Threats

### 1. Fake Checkers

Attackers can create fake WL checkers that imitate legitimate projects.

### Protection

- Verify project domains
- Display official links
- Warn users about suspicious URLs
- Never request unnecessary wallet permissions

---

### 2. Malicious Wallet Connections

Basic eligibility checks should accept a wallet address without requiring wallet connection.

### Protection

Support:

`Enter wallet address → Check eligibility`

---

### 3. Merkle Verification Bugs

Incorrect proof verification can produce false eligibility.

### Protection

- Use audited libraries
- Test valid/invalid proofs
- Validate Merkle roots
- Include chain and contract information

---

### 4. Signature Replay

EIP-712 signatures must prevent replay attacks.

### Protection

Require:

- Chain ID
- Contract address
- Nonce
- Deadline

---

### 5. Stale Data

Eligibility data may become outdated.

### Protection

Every result should include:

- Checked timestamp
- Data source
- Snapshot block/date
- Freshness status

---

### 6. API Failure

Project APIs may become unavailable.

### Protection

Return:

`Unable to verify`

instead of:

`Not eligible`

---

### 7. False Negatives

Missing indexer data can incorrectly mark a user as ineligible.

### Protection

Use multiple data sources where possible.

---

### 8. Sybil Detection

Multiple wallets may belong to one user.

### Protection

Future feature:

- Funding-source analysis
- Wallet clustering
- Activity pattern analysis

Do NOT make Sybil detection part of the first MVP.

---

# Security Rules

1. No transaction required for checking.
2. No private keys.
3. No seed phrases.
4. No unnecessary wallet permissions.
5. Clearly identify verification source.
6. Clearly distinguish verified vs unverified results.
7. Never claim eligibility when verification failed.
8. Log verification failures.
9. Rate-limit public APIs.
10. Cache safe read-only data.
