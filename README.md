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

Run the read-only preflight before opening a paid session. It does not call a
model:

```bash
antseed --version
antseed network peer c50de6922b00677c93007c01924586de887ced7b
antseed buyer balance
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
- [`gpt-5.4`](https://woodfuturebj-boop.github.io/routes/gpt-5.4/)
- [`gpt-5.5`](https://woodfuturebj-boop.github.io/?model=gpt-5.5#first-workload)
- [`gpt-5.6-sol`](https://woodfuturebj-boop.github.io/routes/gpt-5.6-sol/) - highest upstream dollar volume in the current sample; inspect signed live pricing before use
- [`gpt-5.6-sol-pro`](https://woodfuturebj-boop.github.io/?model=gpt-5.6-sol-pro#first-workload)
- [`gpt-5.6-terra`](https://woodfuturebj-boop.github.io/routes/gpt-5.6-terra/) - current-demand rank-one route; inspect signed live pricing before use
- [`gemini-3-5-flash`](https://woodfuturebj-boop.github.io/routes/gemini-3-5-flash/) - current-demand rank-one route; inspect signed live pricing before use
- [`glm-5.2`](https://woodfuturebj-boop.github.io/routes/glm-5.2/)
- [`minimax-m2.7`](https://woodfuturebj-boop.github.io/routes/minimax-m2.7/) - eighth in AntSeed's official token-volume snapshot; inspect signed live pricing before use
- [`kimi-k3`](https://woodfuturebj-boop.github.io/?model=kimi-k3#first-workload)
- [`claude-opus-4-8-fast`](https://woodfuturebj-boop.github.io/routes/claude-opus-4-8-fast/) - fast route; inspect signed live pricing before use
- [`claude-sonnet-5`](https://woodfuturebj-boop.github.io/routes/claude-sonnet-5/)
- [`claude-fable-5`](https://woodfuturebj-boop.github.io/routes/claude-fable-5/)

Cline users can choose **OpenAI Compatible**, point the Base URL to
`http://127.0.0.1:8377/v1`, use the non-secret placeholder key
`antseed-local`, and set the Model ID to the explicit
`c50de6922b00677c93007c01924586de887ced7b@<service-id>` route. The first paid
request must be a real task, not a connection test. See the
[official Cline guide](https://docs.cline.bot/provider-config/openai-compatible).

Kilo Code users can add a custom `antseed` provider using **OpenAI
Compatible**, the same local Base URL and placeholder API key, and a manually
added `c50de6922b00677c93007c01924586de887ced7b@<service-id>` Model ID. Keep
the peer prefix even if Kilo auto-fetches bare service names from the free
model catalog. See the
[official Kilo guide](https://kilo.ai/docs/ai-providers/openai-compatible).

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

Each service can be compared directly at
`https://www.antfeed.org/services/<service-id>`. Confirm NovaRoute AI and the
signed live price before opening a paid session.

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

Use AntFeed MCP `0.2.5` only for read-only discovery with AntSeed CLI
`0.1.136`; the CLI does not expose the MCP bridge's `/health` and `/sessions`
endpoints. The [external buyer guide](BETA.md#agent-path-antfeed-mcp-read-only-discovery)
connects discovery to the verified direct buyer path. The
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
- [Installable guarded buyer skill for agents](skills/novaroute-antseed-buyer/)
- [Beta overview and acceptance criteria](https://github.com/woodfuturebj-boop/antseed-proof/issues/1)
- [External buyer beta](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
- [Connection support](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=support.yml)

Never include private keys, seed phrases, API keys, wallet credentials, or complete
environment files in an issue.
