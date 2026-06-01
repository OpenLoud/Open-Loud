<p align="center">
  <img src="banner.png" alt="Open Loud" width="600"/>
</p>

<h1 align="center">Open Loud</h1>

<p align="center">
  <b>A verifiable privacy L3 on Base, built on the OP Stack.</b><br/>
  <i>Privacy you can verify. Loud by design.</i>
</p>

<p align="center">
  X <a href="https://twitter.com/OpenLoudgg">@OpenLoudgg</a> · <a href="https://openloud.org">openloud.gg</a>
</p>

---

A **verifiable privacy L3 on Base**, built on the OP Stack. Open Loud ships in two profiles that share one cryptographic core:

- **Full privacy chain** — every transfer is a shielded UTXO note (Circom + PLONK). No trusted setup. Fully verifiable.
- **Open L3 + Privacy Pool** — a transparent EVM L3 with an opt-in, *compliance-compatible* Privacy Pool (fixed denomination + Association Sets, so withdrawals are "unlockable" by an Association Set Provider).

It runs locally with a single sequencer via Docker Compose and deploys to Base Sepolia / mainnet by swapping the settlement endpoint and keys.

## Why PLONK, not Groth16?

Most privacy chains use **Groth16** — a proving system that requires a trusted setup ceremony. If that ceremony is compromised, every privacy guarantee collapses.

**Open Loud uses PLONK** — a universal, trustless proving system:

| | Open Loud (PLONK) | Others (Groth16) |
|--|---|---|
| Trusted setup | ❌ None required | ✅ Required |
| Ceremony risk | None | Single point of failure |
| Auditability | Full — verify yourself | Partial |
| Circuit upgrades | No new ceremony needed | New ceremony per circuit |

> *If privacy is a right, the system protecting it should be open.*

## Layout

```
packages/
  circuits/     Circom circuits + PLONK prover (no trusted setup)
  contracts/    Hardhat: pools, verifiers, bridges
  sdk/          TypeScript: notes, Merkle tree, proof generation
infra/
  op-stack/     Docker Compose single-sequencer L3
  explorer/     Blockscout
apps/
  web/          Next.js UI (deposit / withdraw / verify)
docs/
  workflow.md         phased build plan
  architecture.md     system architecture & cryptographic core
  privacy-design.md   ZK circuit design & PLONK rationale
```

## Quick start

```bash
pnpm install
pnpm setup    # compile circuits + deploy contracts
pnpm dev      # local chain + deploy + wallet backend
```

`pnpm dev` is the turn-key local stack: it starts a local node, deploys the privacy core, copies circuit artifacts into the web app, and runs the wallet backend. Then:

```bash
node apps/web/scripts/demo-deposit.mjs
curl http://localhost:3000/api/pool/leaves
```

Run the full verification gate directly:

```bash
pnpm --filter @loud/sdk test        # 9/9 passing
pnpm --filter @loud/circuits test   # 4/4 passing
pnpm contracts:test                 # 10/10 passing
```

Real L3 + explorer (Docker; chain boot is optional — see each README):

```bash
cd infra/op-stack && cp .env.example .env
cd infra/explorer && cp .env.example .env
docker compose up
```

> Status: privacy core **done & verified**; full stack scaffolded & turn-key. See [docs/workflow.md](docs/workflow.md).

## Security

> ⚠️ The setup shipped for development is single-contributor and **must not** secure real funds. Mainnet requires an external audit (Phase 6). See [docs/privacy-design.md](docs/privacy-design.md).

