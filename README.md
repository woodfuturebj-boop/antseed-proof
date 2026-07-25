# NovaRoute AI

Public AntSeed verification proof and buyer connection guide for provider:

`c50de6922b00677c93007c01924586de887ced7b`

## Quick Connect

### AntStation Discover

Install the official [AntStation desktop app](https://github.com/AntSeed/antseed/releases/latest)
for macOS (Apple Silicon or Intel), Windows, or Linux,
fund the buyer with Base USDC, then open **Discover**. Search the exact provider
name `NovaRoute AI` first, choose it, select the service you need, and start a
real chat. Selecting the Discover result pins both this provider and the
service. Service-name searches such as `claude-opus-4.6` are broader and can return
several peers.

### CLI pinned startup

CLI buyer auto-selection is disabled, so buyers must pin a peer explicitly.

```bash
antseed buyer start --peer c50de6922b00677c93007c01924586de887ced7b
```

For a buyer proxy that is already running, switch the session pin without a
restart:

```bash
antseed buyer connection set --peer c50de6922b00677c93007c01924586de887ced7b
```

Per-request routing also works:

```text
x-antseed-pin-peer: c50de6922b00677c93007c01924586de887ced7b
```

For a single real workload without replacing a saved connection, use one of the
current high-demand direct routes:

```text
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
c50de6922b00677c93007c01924586de887ced7b@gpt-5.4
c50de6922b00677c93007c01924586de887ced7b@gpt-5.5
c50de6922b00677c93007c01924586de887ced7b@gpt-5.6-sol-pro
c50de6922b00677c93007c01924586de887ced7b@gpt-5.6-terra
c50de6922b00677c93007c01924586de887ced7b@gpt-5.6-sol
c50de6922b00677c93007c01924586de887ced7b@gemini-3-5-flash
c50de6922b00677c93007c01924586de887ced7b@glm-5.2
c50de6922b00677c93007c01924586de887ced7b@minimax-m2.7
c50de6922b00677c93007c01924586de887ced7b@kimi-k3
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4-8-fast
c50de6922b00677c93007c01924586de887ced7b@claude-sonnet-5
c50de6922b00677c93007c01924586de887ced7b@claude-fable-5
```

Copy-ready route pages:

- [`claude-opus-4.6`](https://woodfuturebj-boop.github.io/routes/claude-opus-4.6/) - first in AntSeed's latest official model-sales snapshot; inspect signed live pricing before use
- [`gpt-5.4`](https://woodfuturebj-boop.github.io/?model=gpt-5.4#first-workload)
- [`gpt-5.5`](https://woodfuturebj-boop.github.io/?model=gpt-5.5#first-workload)
- [`gpt-5.6-sol`](https://woodfuturebj-boop.github.io/routes/gpt-5.6-sol/) - highest upstream dollar volume in the current sample; inspect signed live pricing before use
- [`gpt-5.6-sol-pro`](https://woodfuturebj-boop.github.io/?model=gpt-5.6-sol-pro#first-workload)
- [`gpt-5.6-terra`](https://woodfuturebj-boop.github.io/routes/gpt-5.6-terra/) - current-demand rank-one route; inspect signed live pricing before use
- [`gemini-3-5-flash`](https://woodfuturebj-boop.github.io/routes/gemini-3-5-flash/) - current-demand rank-one route; inspect signed live pricing before use
- [`glm-5.2`](https://woodfuturebj-boop.github.io/?model=glm-5.2#first-workload)
- [`minimax-m2.7`](https://woodfuturebj-boop.github.io/routes/minimax-m2.7/) - eighth in AntSeed's official token-volume snapshot; inspect signed live pricing before use
- [`kimi-k3`](https://woodfuturebj-boop.github.io/?model=kimi-k3#first-workload)
- [`claude-opus-4-8-fast`](https://woodfuturebj-boop.github.io/routes/claude-opus-4-8-fast/) - fast route; inspect signed live pricing before use
- [`claude-sonnet-5`](https://woodfuturebj-boop.github.io/?model=claude-sonnet-5#first-workload)
- [`claude-fable-5`](https://woodfuturebj-boop.github.io/?model=claude-fable-5#first-workload)

## Provider

- Network display name: `NovaRoute AI`
- Agent ID: `56687`
- Seller wallet: `0xc50DE6922b00677c93007c01924586dE887ced7b`
- Settlement network: Base mainnet USDC
- Public endpoint: `149.28.69.249:6882`
- Verification domain: `https://woodfuturebj-boop.github.io`

## Featured Services

The buyer page prioritizes current high-value services. The order below combines
AntSeed's latest official sales snapshot with signed live pricing:

- `claude-opus-4.6` - first in the latest official model-sales snapshot; signed live directory pricing
- `gpt-5.6-sol` - highest upstream dollar volume in the current market sample; exact rank one
- `gpt-5.6-sol-pro` - second-highest current reasoning volume; exact rank one
- `claude-sonnet-5` - high-value coding demand; exact rank one
- `claude-fable-5` - high-value long-form demand; exact rank one
- `kimi-k3` - agent and coding demand; exact rank one
- `glm-5.2` - highest request count in the current upstream sample
- `minimax-m2.7` - eighth in AntSeed's official token-volume snapshot
- `gpt-5.5` - strong request demand with signed live directory pricing
- `gpt-5.4` - general reasoning demand; exact rank one

[Official demand evidence: AntSeed Top models by sales](https://x.com/AntSeedAI/status/2081002378795377145).
[Official demand evidence: AntSeed Top models by token volume](https://x.com/AntSeedAI/status/2077010692012470320).
[Current exact-offer evidence](https://network.antseed.com/stats).

The broader catalog remains advertised for compatibility. Featured status is an
onboarding and measurement decision, not a claim that other services were removed.

Run this to inspect the live catalog and current prices:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

The signed peer catalog is the source of truth. AntFeed refreshes its provider
directory hourly, and other discovery pages can cache older prices, so verify this command before
funding or creating a paid session.

For AntFeed MCP, use local buyer URL `http://localhost:8377` with the CLI buyer
or `http://localhost:8378` with AntStation Desktop. The
[external buyer guide](BETA.md#agent-path-antfeed-mcp) includes the guarded
Claude Code, Claude Desktop, Cursor, and Cline setup path. The
[direct seller profile](https://www.antfeed.org/sellers/0xc50de6922b00677c93007c01924586de887ced7b)
bypasses directory ordering for read-only inspection.
The [audit-service comparison](https://www.antfeed.org/services/novaroute-code-audit-v1)
opens the specialist route directly for provider and price review.

## Operating Policy

- Surplus-backed OpenAI-compatible provider.
- Prices are monitored against upstream raw cost.
- No private keys, API keys, or credentials are stored in this repository.
- No self-trading or fake traffic.

## Beta and Support

- [24-hour external buyer guide](BETA.md)
- [Guarded buyer skill for agents](skills/novaroute-antseed-buyer/SKILL.md)
- [Beta overview and acceptance criteria](https://github.com/woodfuturebj-boop/antseed-proof/issues/1)
- [External buyer beta](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
- [Connection support](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=support.yml)

Never include private keys, seed phrases, API keys, wallet credentials, or complete
environment files in an issue.
