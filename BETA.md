# 24-Hour External Buyer Beta

Use a real AntSeed buyer and a real workload to connect to `Surplus Value Router`.
There is no reward for artificial traffic, self-trading, or test volume.

## Fastest Path: Direct Pin

```bash
npm install -g @antseed/cli
antseed buyer start
antseed payments
antseed buyer connection set --peer c50de6922b00677c93007c01924586de887ced7b
curl -s http://127.0.0.1:8377/v1/models | jq '.data[].id'
```

Start with one of these featured services:

- `opus-4.7`
- `opus-4.8`
- `claude-sonnet-5`
- `gpt-5.4`
- `glm-5.2`

Inspect the signed live catalog and pricing before use:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

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

Use `lookup` and `get_pricing` first. `create_session` can move buyer funds, so
review the seller, service, and deposit and keep host confirmation enabled.

Suggested agent instruction:

```text
Use AntFeed MCP to look up "Surplus Value Router". Verify seller
0xc50DE6922b00677c93007c01924586dE887ced7b, inspect opus-4.7 pricing,
and ask me before create_session.
```

## Help and Attribution

[Open the external buyer onboarding form](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
before or after installing a buyer. The buyer hash is optional until the buyer
exists. Never submit a peer private key, seed phrase, wallet credential, API key,
or complete environment file.

The operator permanently excludes its own buyer from demand, conversion, and
repeat-use statistics. Only independent external usage counts toward this beta.
