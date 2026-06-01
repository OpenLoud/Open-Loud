# Architecture

## Overview

loud is a privacy L3 built on the OP Stack, settling to Base. It uses a PLONK-based proving system (via Circom + SnarkJS) so no trusted setup ceremony is required.

## Why PLONK?

PLONK is a universal zk-SNARK that does not require a per-circuit trusted setup. This means:
- No multi-party ceremony that could be compromised
- Circuit upgrades do not invalidate past trust assumptions
- Anyone can independently verify the setup is sound

## Privacy Pool

The Privacy Pool contract implements:
- Fixed-denomination deposits
- Merkle tree of commitments
- On-chain PLONK verifier
- Association Set Provider interface

## L3 Stack

- Sequencer: OP Stack
- Settlement: Base Sepolia to Base mainnet
- Explorer: Blockscout
