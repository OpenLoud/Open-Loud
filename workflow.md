# Development Workflow

## Phases

| Phase | Description | Status |
|-------|-------------|--------|
| 1 | PLONK circuit design | Done |
| 2 | Smart contracts (pools, verifiers) | Done |
| 3 | TypeScript SDK | Done |
| 4 | OP Stack L3 (Base Sepolia) | In Progress |
| 5 | Web wallet UI | In Progress |
| 6 | External security audit | Planned |
| 7 | Mainnet launch | Planned |

## Local Dev

```bash
pnpm install && pnpm setup && pnpm dev
```

## Testing

```bash
pnpm --filter @loud/circuits test
pnpm --filter @loud/sdk test
pnpm contracts:test
```
