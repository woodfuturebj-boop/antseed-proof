# 24-Hour External Buyer Beta

Use a real AntSeed buyer and a real workload to connect to `Surplus Value Router`.
There is no reward for artificial traffic, self-trading, or test volume.

## Fastest Path: AntStation Discover

1. Install the official [AntStation desktop app](https://github.com/AntSeed/antseed/releases/latest).
2. Fund the buyer with Base USDC.
3. Open **Discover** and search for `opus-4.7` first, or search for `Surplus Value Router`.
4. Choose `Surplus Value Router | GPT/GLM/Claude`, select a service, and start a real chat.

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

```bash
curl http://127.0.0.1:8377/v1/chat/completions \
  -H "content-type: application/json" \
  -d '{"model":"c50de6922b00677c93007c01924586de887ced7b@opus-4.7","messages":[{"role":"user","content":"REPLACE WITH YOUR REAL TASK"}]}'
```

Start with one of these featured services:

- `opus-4.7` - primary controlled adoption route; published snapshot `$0.3061375` input / `$1.5306875` output per 1M tokens
- `claude-opus-4.6` - highest-user-demand route in the July 19 snapshot
- `gpt-5.5` - subsidized high-demand rank-one adoption route
- `claude-opus-4.8` - current high-demand frontier coding route
- `glm-5.2` - current high-demand multilingual route
- `gpt-5.6-sol-pro` - high-demand rank-one reasoning route
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
Use AntFeed MCP to look up "Surplus Value Router | GPT/GLM/Claude". Verify
seller 0xc50DE6922b00677c93007c01924586dE887ced7b, inspect opus-4.7 first,
then gpt-5.5, claude-opus-4.6, and glm-5.2 pricing, compare it with
the signed direct peer catalog, and ask me before create_session.
```

## Help and Attribution

[Open the external buyer onboarding form](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
before or after installing a buyer. The buyer hash is optional until the buyer
exists. Never submit a peer private key, seed phrase, wallet credential, API key,
or complete environment file.

The operator permanently excludes its own buyer from demand, conversion, and
repeat-use statistics. Only independent external usage counts toward this beta.
