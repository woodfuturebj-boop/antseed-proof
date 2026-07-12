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

## Featured Services

The first beta onboarding page highlights five services:

- `opus-4.7`
- `opus-4.8`
- `claude-sonnet-5`
- `gpt-5.4`
- `glm-5.2`

The broader catalog remains advertised for compatibility. Featured status is an
onboarding and measurement decision, not a claim that other services were removed.

Run this to inspect the live catalog and current prices:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

## Operating Policy

- Surplus-backed OpenAI-compatible provider.
- Prices are monitored against upstream raw cost.
- No private keys, API keys, or credentials are stored in this repository.
- No self-trading or fake traffic.

## Beta and Support

- [External buyer beta](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
- [Connection support](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=support.yml)

Never include private keys, seed phrases, API keys, wallet credentials, or complete
environment files in an issue.
