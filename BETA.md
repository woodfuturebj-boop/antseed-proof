# 24-Hour External Buyer Beta

Use a real AntSeed buyer and a real workload to connect to `NovaRoute AI`.
There is no reward for artificial traffic, self-trading, or test volume.

## Fastest Path: AntStation Discover

1. Install the official [AntStation desktop app](https://github.com/AntSeed/antseed/releases/latest) for macOS (Apple Silicon or Intel), Windows, or Linux.
2. Fund the buyer with Base USDC.
3. Open **Discover** and search for `opus-4.7`, `claude-opus-4.7`, or `claude-opus-4-7` first. These exact service names use the same high-demand upstream route. You can also search for `NovaRoute AI`.
4. Choose `NovaRoute AI`, select a service, and start a real chat.

Selecting the Discover result pins both this provider and the service. Verify
the displayed provider and live price before funding a session.

## CLI Path: Direct Pin

```bash
npm install -g @antseed/cli
antseed buyer start
antseed payments
antseed buyer connection set --peer c50de6922b00677c93007c01924586de887ced7b
curl -s http://127.0.0.1:8377/v1/models | jq '.data[].id'
```

Then choose a direct route and replace the message below with a task you actually
need completed. The model-prefix route pins this provider for one request without
replacing a saved connection. Do not send artificial traffic just to test the
route.

Current high-demand routes:

```text
c50de6922b00677c93007c01924586de887ced7b@opus-4.7
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.7
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4-7
c50de6922b00677c93007c01924586de887ced7b@gpt-5.4
c50de6922b00677c93007c01924586de887ced7b@gpt-5.5
c50de6922b00677c93007c01924586de887ced7b@gpt-5.6-sol-pro
c50de6922b00677c93007c01924586de887ced7b@gpt-5.6-terra
c50de6922b00677c93007c01924586de887ced7b@gpt-5.6-sol
c50de6922b00677c93007c01924586de887ced7b@gemini-3-5-flash
c50de6922b00677c93007c01924586de887ced7b@glm-5.2
c50de6922b00677c93007c01924586de887ced7b@kimi-k3
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4-8-fast
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.8
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
c50de6922b00677c93007c01924586de887ced7b@claude-sonnet-5
c50de6922b00677c93007c01924586de887ced7b@claude-fable-5
```

```bash
curl http://127.0.0.1:8377/v1/chat/completions \
  -H "content-type: application/json" \
  -d '{"model":"c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.7","messages":[{"role":"user","content":"REPLACE WITH YOUR REAL TASK"}]}'
```

Start with one of these featured services:

- `claude-opus-4.7` - canonical alias for the same high-demand Opus 4.7 upstream; published snapshot `$0.495` input / `$2.475` output per 1M tokens
- `opus-4.7` - official demand-name route; published snapshot `$0.3061375` input / `$1.5306875` output per 1M tokens
- `claude-opus-4-7` - compatibility alias; published snapshot `$0.495` input / `$2.475` output per 1M tokens
- `claude-opus-4.6` - highest-user-demand route in the July 19 snapshot
- `gpt-5.5` - published high-demand rank-one route
- `claude-opus-4-8-fast` - current paid-demand rank-one route; published snapshot `$1.50` input / `$7.50` output per 1M tokens
- `claude-opus-4.8` - current high-demand frontier coding route
- `glm-5.2` - current high-demand multilingual route
- `gpt-5.6-sol-pro` - high-demand rank-one reasoning route
- `gpt-5.6-terra` - current-demand rank-one route; published snapshot `$0.05` input / `$0.30` output per 1M tokens
- `gpt-5.6-sol` - current-demand rank-one route; published snapshot `$0.10` input / `$0.60` output per 1M tokens
- `gemini-3-5-flash` - current-demand rank-one route; published snapshot `$0.104013` input / `$0.624073` output per 1M tokens
- `claude-sonnet-5` - coding and agent route
- `gpt-5.4` - current high-demand general route
- `kimi-k3` - agent and coding route
- `claude-fable-5` - current long-form and coding route

[Demand evidence: AntSeed Top models by users, July 19](https://x.com/AntSeedAI/status/2078868465276874967).

Inspect the signed live catalog and pricing before use:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

Use this signed peer catalog as the source of truth. AntFeed refreshes its
provider directory hourly, and other discovery surfaces may also cache an older price snapshot. If a cached listing
differs, do not create a paid session until the direct peer lookup is reviewed.

## Agent Path: AntFeed MCP

This seller is indexed in AntFeed under wallet
`0xc50DE6922b00677c93007c01924586dE887ced7b`.

```json
{
  "mcpServers": {
    "antfeed": {
      "command": "npx",
      "args": ["-y", "@antfeed/mcp"],
      "env": {
        "ANTFEED_EXPLORER_URL": "https://www.antfeed.org",
        "ANTSEED_BUYER_URL": "http://localhost:8377",
        "ANTSEED_MAX_DEPOSIT_USDC": "10"
      }
    }
  }
}
```

Use `lookup` and `get_pricing` first. Compare the result with the direct peer
lookup above. `create_session` can move buyer funds, so review the seller,
service, and deposit and keep host confirmation enabled.

Suggested agent instruction:

```text
Use AntFeed MCP to look up "NovaRoute AI". Verify
seller 0xc50DE6922b00677c93007c01924586dE887ced7b, inspect claude-opus-4-8-fast first,
then claude-opus-4.7, opus-4.7, gpt-5.5, and glm-5.2 pricing, compare it with
the signed direct peer catalog, and ask me before create_session.
```

## Help and Attribution

[Open the external buyer onboarding form](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
before or after installing a buyer. The buyer hash is optional until the buyer
exists. Never submit a peer private key, seed phrase, wallet credential, API key,
or complete environment file.

The operator permanently excludes its own buyer from demand, conversion, and
repeat-use statistics. Only independent external usage counts toward this beta.
