# loud

> **A verifiable privacy L3 on Base, built on the OP Stack.**
> *Privacy you can verify. Loud by design.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Twitter](https://img.shields.io/twitter/follow/loudgg?style=social)](https://twitter.com/loudgg)

---

## What is loud?

**loud** is a privacy Layer 3 on Base that does something different: instead of hiding how it works, it makes its cryptography fully auditable and trustless.

Most privacy chains use **Groth16** — a proving system that requires a trusted setup ceremony. If that ceremony is compromised, the entire privacy guarantee collapses.

**loud uses PLONK** — a universal, trustless proving system. No trusted setup. No ceremony. Anyone can verify everything.

> *If privacy is a right, the system protecting it should be open.*

---

## Two modes, one core

| Mode | Description |
|------|-------------|
| **Full Privacy Chain** | Every transfer is a shielded note (Circom + PLONK). Fully private. Fully verifiable. |
| **Open L3 + Privacy Pool** | Transparent EVM with opt-in privacy. Compliance-compatible via Association Sets. |

---

## Why loud vs other privacy L3s?

| | loud | others |
|--|------|--------|
| Proving system | PLONK (trustless) | Groth16 (trusted setup) |
| Setup ceremony | ❌ None required | ✅ Required |
| Auditability | Full | Partial |
| Base L3 | ✅ | ✅ |
| Open source | ✅ | ✅ |

---

## Layout

```
packages/
  circuits/     Circom circuits + PLONK prover
  contracts/    Hardhat: pools, verifiers, bridges
  sdk/          TypeScript SDK for dApps
infra/
  op-stack/     Docker Compose: local L3 node
  explorer/     Blockscout block explorer
apps/
  web/          Next.js wallet UI
docs/
  architecture.md     System design & cryptographic core
  workflow.md         Development phases & roadmap
  privacy-design.md   ZK circuit design & PLONK rationale
```

---

## Quick start

```bash
pnpm install
pnpm setup    # compile circuits & contracts
pnpm dev      # start local stack
```

`pnpm dev` starts a local node, deploys the privacy core, copies circuit artifacts into the web app, and runs the wallet backend.

Run tests:
```bash
pnpm --filter @loud/sdk test
pnpm --filter @loud/circuits test
pnpm contracts:test
```

Run full L3 with explorer (Docker):
```bash
cd infra/op-stack && cp .env.example .env
cd infra/explorer && cp .env.example .env
docker compose up
```

---

## Security

> ⚠️ **loud is in active development. Do not use with real funds on mainnet yet.**
>
> Unlike Groth16-based systems, loud's PLONK setup requires no trusted ceremony — but the codebase has not yet undergone a full external audit. Audit is planned for Phase 6. See [docs/workflow.md](docs/workflow.md).

---

## Roadmap

- [x] Phase 1 — PLONK circuit design (Circom)
- [x] Phase 2 — Privacy Pool contracts (Hardhat)
- [x] Phase 3 — SDK + prover integration
- [ ] Phase 4 — OP Stack L3 deployment (Base Sepolia)
- [ ] Phase 5 — Next.js wallet UI
- [ ] Phase 6 — External audit
- [ ] Phase 7 — Mainnet launch

See [docs/workflow.md](docs/workflow.md) for full details.

---

## Links

- 🌐 Website: [loud.gg](https://loud.gg)
- 🐦 Twitter: [@loudgg](https://twitter.com/loudgg)
- 📄 Docs: [docs/](docs/)

---

## License

MIT — see [LICENSE](LICENSE)
