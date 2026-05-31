# Architecture

## Overview

loud is a privacy L3 built on the OP Stack, settling to Base. It uses a PLONK-based proving system (via Circom + SnarkJS) so no trusted setup ceremony is required.

## Cryptographic Core

### Why PLONK?

PLONK is a universal zk-SNARK that does not require a per-circuit trusted setup. This means:
- No multi-party ceremony that could be compromised
- Circuit upgrades do not invalidate past trust assumptions
- Anyone can independently verify the setup is sound

### Circuit Design

All circuits live in `packages/circuits/`. Each circuit:
1. Takes private inputs (note secret, nullifier)
2. Produces a public commitment + nullifier hash
3. Generates a PLONK proof verifiable on-chain

## Privacy Pool

The Privacy Pool contract (`packages/contracts/`) implements:
- Fixed-denomination deposits (prevents amount fingerprinting)
- Merkle tree of commitments
- On-chain PLONK verifier
- Association Set Provider interface (for compliance mode)

## L3 Stack

- **Sequencer**: OP Stack (single sequencer locally, decentralized roadmap)
- **Settlement**: Base Sepolia to Base mainnet
- **Explorer**: Blockscout
