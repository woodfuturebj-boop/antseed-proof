# Surplus Value Router

Public AntSeed verification proof and buyer connection guide for provider:

`c50de6922b00677c93007c01924586de887ced7b`

## Quick Connect

### AntStation Discover

Install the official [AntStation desktop app](https://github.com/AntSeed/antseed/releases/latest)
for macOS (Apple Silicon or Intel), Windows, or Linux,
fund the buyer with Base USDC, then open **Discover**. Search for `opus-4.7`
first, or search for `Surplus Value Router`; choose `Surplus Value Router | GPT/GLM/Claude`, select
the service you need, and start a real chat. Selecting the Discover result pins
both this provider and the service.

### CLI pin

CLI buyer auto-selection is disabled, so buyers must pin a peer explicitly.

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
c50de6922b00677c93007c01924586de887ced7b@opus-4.7
c50de6922b00677c93007c01924586de887ced7b@gpt-5.4
c50de6922b00677c93007c01924586de887ced7b@gpt-5.5
c50de6922b00677c93007c01924586de887ced7b@gpt-5.6-sol-pro
c50de6922b00677c93007c01924586de887ced7b@glm-5.2
c50de6922b00677c93007c01924586de887ced7b@kimi-k3
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.8
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
c50de6922b00677c93007c01924586de887ced7b@claude-sonnet-5
c50de6922b00677c93007c01924586de887ced7b@claude-fable-5
```

Copy-ready route pages:

- [`opus-4.7`](https://woodfuturebj-boop.github.io/routes/opus-4.7/) - published snapshot `$0.3061375` input / `$1.5306875` output per 1M tokens
- [`gpt-5.4`](https://woodfuturebj-boop.github.io/?model=gpt-5.4#first-workload)
- [`gpt-5.5`](https://woodfuturebj-boop.github.io/?model=gpt-5.5#first-workload)
- [`gpt-5.6-sol-pro`](https://woodfuturebj-boop.github.io/?model=gpt-5.6-sol-pro#first-workload)
- [`glm-5.2`](https://woodfuturebj-boop.github.io/?model=glm-5.2#first-workload)
- [`kimi-k3`](https://woodfuturebj-boop.github.io/?model=kimi-k3#first-workload)
- [`claude-opus-4.8`](https://woodfuturebj-boop.github.io/?model=claude-opus-4.8#first-workload)
- [`claude-opus-4.6`](https://woodfuturebj-boop.github.io/?model=claude-opus-4.6#first-workload)
- [`claude-sonnet-5`](https://woodfuturebj-boop.github.io/?model=claude-sonnet-5#first-workload)
- [`claude-fable-5`](https://woodfuturebj-boop.github.io/?model=claude-fable-5#first-workload)

## Provider

- Network display name: `Surplus Value Router | GPT/GLM/Claude`
- Agent ID: `56687`
- Seller wallet: `0xc50DE6922b00677c93007c01924586dE887ced7b`
- Settlement network: Base mainnet USDC
- Public endpoint: `192.220.28.51:6882`
- Verification domain: `https://woodfuturebj-boop.github.io`

## Featured Services

The beta onboarding page highlights ten services. The order below follows the
latest published AntSeed user-demand evidence and active adoption pricing:

- `claude-opus-4.6` - highest-user-demand route in the July 19 snapshot
- `opus-4.7` - second in the snapshot and the primary controlled adoption route
- `gpt-5.5` - subsidized high-demand adoption route
- `claude-opus-4.8` - high-demand frontier coding route
- `glm-5.2` - high-demand multilingual route
- `gpt-5.6-sol-pro` - high-demand rank-one reasoning route
- `claude-sonnet-5` - coding and agent route
- `gpt-5.4` - high-demand general route
- `kimi-k3` - agent and coding route
- `claude-fable-5` - long-form and coding route

[Demand evidence: AntSeed Top models by users, July 19](https://x.com/AntSeedAI/status/2078868465276874967).

The broader catalog remains advertised for compatibility. Featured status is an
onboarding and measurement decision, not a claim that other services were removed.

Run this to inspect the live catalog and current prices:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

The signed peer catalog is the source of truth. AntFeed refreshes its provider
directory hourly, and other discovery pages can cache older prices, so verify this command before
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
