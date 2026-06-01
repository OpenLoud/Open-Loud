# @loud/sdk

TypeScript SDK for integrating Open Loud privacy into dApps.

## Install

```bash
npm install @loud/sdk

import { LoudClient } from '@loud/sdk'

const client = new LoudClient({ rpc: 'https://rpc.openloud.gg' })
const proof = await client.prove({ secret, amount })
await client.withdraw({ proof, recipient })
