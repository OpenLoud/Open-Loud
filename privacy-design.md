# Privacy Design

## Core Principle

loud's privacy is mathematically verifiable. We use PLONK so that:
1. No trusted ceremony is needed
2. The proof system itself is auditable
3. Privacy guarantees do not depend on any single party

## Note Scheme

Each shielded note contains:
- `secret`: random 31-byte field element
- `nullifier`: hash(secret, index)
- `commitment`: hash(amount, secret)

## Compliance Mode

In Open L3 + Privacy Pool mode:
- Withdrawals include an Association Set proof
- An Association Set Provider can verify a withdrawal is clean
- The user identity is never revealed, only set membership

## Audit Plan

External audit is planned for Phase 6 before mainnet.
