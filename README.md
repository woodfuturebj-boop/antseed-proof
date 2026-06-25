# Surplus Value Router

Public AntSeed verification proof and buyer connection guide for provider:

`c50de6922b00677c93007c01924586de887ced7b`

## Quick Connect

AntSeed buyer auto-selection is disabled, so buyers must pin a peer explicitly.

```bash
antseed buyer connection set --peer c50de6922b00677c93007c01924586de887ced7b
```

Per-request routing also works:

```bash
curl -H "x-antseed-pin-peer: c50de6922b00677c93007c01924586de887ced7b" http://127.0.0.1:8377/v1/models
```

Model-prefix routing:

```text
c50de6922b00677c93007c01924586de887ced7b@gpt-5.4
```

## Provider

- Display name: `Surplus Value Router`
- Agent ID: `56687`
- Seller wallet: `0xc50DE6922b00677c93007c01924586dE887ced7b`
- Settlement network: Base mainnet USDC
- Public endpoint: `192.220.28.51:6882`
- Verification domain: `https://woodfuturebj-boop.github.io`

## Primary Services

The live service list is published through AntSeed metadata. Current primary services include:

- `gpt-5.4`
- `gpt-5.4-mini`
- `gpt-5.2-codex`
- `gpt-5.3-codex`
- `opus-4.7`
- `opus-4.8`
- `glm-5`
- `glm-5.1`
- `grok-4.3`

Run this to inspect the live catalog and current prices:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

## Operating Policy

- Surplus-backed OpenAI-compatible provider.
- Prices are monitored against upstream raw cost.
- No private keys, API keys, or credentials are stored in this repository.
- No self-trading or fake traffic.
