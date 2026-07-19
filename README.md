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

For a single real workload without replacing a saved connection, use one of the
current high-demand direct routes:

```text
c50de6922b00677c93007c01924586de887ced7b@gpt-5.4
c50de6922b00677c93007c01924586de887ced7b@glm-5.2
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.8
c50de6922b00677c93007c01924586de887ced7b@gemini-3.1-pro-preview
c50de6922b00677c93007c01924586de887ced7b@claude-fable-5
```

Copy-ready route pages:

- [`gpt-5.4`](https://woodfuturebj-boop.github.io/?model=gpt-5.4#first-workload)
- [`glm-5.2`](https://woodfuturebj-boop.github.io/?model=glm-5.2#first-workload)
- [`claude-opus-4.8`](https://woodfuturebj-boop.github.io/?model=claude-opus-4.8#first-workload)
- [`gemini-3.1-pro-preview`](https://woodfuturebj-boop.github.io/?model=gemini-3.1-pro-preview#first-workload)
- [`claude-fable-5`](https://woodfuturebj-boop.github.io/?model=claude-fable-5#first-workload)

## Provider

- Network display name: `Surplus Value Router | GPT/GLM/Claude`
- Agent ID: `56687`
- Seller wallet: `0xc50DE6922b00677c93007c01924586dE887ced7b`
- Settlement network: Base mainnet USDC
- Public endpoint: `192.220.28.51:6882`
- Verification domain: `https://woodfuturebj-boop.github.io`

## Featured Services

The beta onboarding page highlights eight services. Five have current demand
signals and active rank-one pricing experiments:

- `gpt-5.4` - high-demand general route
- `glm-5.2` - high-demand multilingual route
- `claude-opus-4.8` - high-demand frontier coding route
- `gemini-3.1-pro-preview` - Gemini reasoning route
- `claude-fable-5` - long-form and coding route

Additional featured routes:

- `minimax-m2.7`
- `opus-4.7`
- `claude-sonnet-5`

The broader catalog remains advertised for compatibility. Featured status is an
onboarding and measurement decision, not a claim that other services were removed.

Run this to inspect the live catalog and current prices:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

The signed peer catalog is the source of truth. Default discovery pages and
third-party directories can cache older prices, so verify this command before
funding or creating a paid session.

## Operating Policy

- Surplus-backed OpenAI-compatible provider.
- Prices are monitored against upstream raw cost.
- No private keys, API keys, or credentials are stored in this repository.
- No self-trading or fake traffic.

## Beta and Support

- [24-hour external buyer guide](BETA.md)
- [Beta overview and acceptance criteria](https://github.com/woodfuturebj-boop/antseed-proof/issues/1)
- [External buyer beta](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
- [Connection support](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=support.yml)

Never include private keys, seed phrases, API keys, wallet credentials, or complete
environment files in an issue.
