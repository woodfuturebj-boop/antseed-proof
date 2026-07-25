# External Buyer Connection Guide

Use a real AntSeed buyer and a real workload to connect to `NovaRoute AI`.
Artificial traffic, self-trading, and test volume are not accepted.

## Fastest Path: AntStation Discover

1. Install the official [AntStation desktop app](https://github.com/AntSeed/antseed/releases/latest) for macOS (Apple Silicon or Intel), Windows, or Linux.
2. Fund the buyer with Base USDC.
3. Open **Discover** and search the exact provider name `NovaRoute AI` first.
4. Choose `NovaRoute AI`, select a service, and start a real chat.

Selecting the Discover result pins both this provider and the service. Verify
the displayed provider and live price before funding a session.
Service-name searches such as `claude-opus-4.6` are useful fallbacks but can return
several peers; the exact provider name narrows the directory directly.

## CLI Path: Direct Pin

```bash
npm install -g @antseed/cli
antseed payments
antseed buyer start --peer c50de6922b00677c93007c01924586de887ced7b
```

If the buyer proxy is already running, pin this peer without restarting it:

```bash
antseed buyer connection set --peer c50de6922b00677c93007c01924586de887ced7b
```

When the foreground buyer workload is finished, press `Ctrl+C` and wait for
`Disconnected. All channels finalized.` before closing the terminal. Do not
force-kill the buyer process; graceful shutdown lets AntSeed finalize the
payment channel normally and release unused deposit.

Then choose a direct route and replace the message below with a task you actually
need completed. The model-prefix route pins this provider for one request without
replacing a saved connection. Do not send artificial traffic just to test the
route.

Current high-demand routes:

```text
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
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
c50de6922b00677c93007c01924586de887ced7b@minimax-m2.7
c50de6922b00677c93007c01924586de887ced7b@kimi-k3
c50de6922b00677c93007c01924586de887ced7b@claude-opus-4-8-fast
c50de6922b00677c93007c01924586de887ced7b@claude-sonnet-5
c50de6922b00677c93007c01924586de887ced7b@claude-fable-5
c50de6922b00677c93007c01924586de887ced7b@novaroute-code-audit-v1
```

```bash
curl http://127.0.0.1:8377/v1/chat/completions \
  -H "content-type: application/json" \
  -d '{"model":"c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6","messages":[{"role":"user","content":"REPLACE WITH YOUR REAL TASK"}]}'
```

Start with one of these current high-value services:

- `claude-opus-4.6` - first in AntSeed's latest official model-sales snapshot;
  lowest-priced indexed exact offer
- `gpt-5.6-sol` - highest upstream dollar volume in the current market sample
- `gpt-5.6-sol-pro` - premium reasoning route
- `claude-opus-4.7` - canonical Opus 4.7 alias
- `opus-4.7` - official demand-name alias for the same upstream route
- `claude-opus-4-7` - compatibility alias for the same upstream route
- `gpt-5.5` - general and coding route
- `claude-opus-4-8-fast` - fast Opus route
- `glm-5.2` - multilingual route
- `minimax-m2.7` - eighth in AntSeed's official token-volume snapshot
- `gpt-5.6-terra` - general reasoning route
- `gemini-3-5-flash` - fast Gemini route
- `claude-sonnet-5` - coding and agent route
- `gpt-5.4` - current high-demand general route
- `kimi-k3` - agent and coding route
- `claude-fable-5` - current long-form and coding route
- `novaroute-code-audit-v1` - differentiated read-only code, Web3
  transaction-safety, and release-readiness review agent

[Official demand evidence: AntSeed Top models by sales](https://x.com/AntSeedAI/status/2081002378795377145).
[Official demand evidence: AntSeed Top models by token volume](https://x.com/AntSeedAI/status/2077010692012470320).
[Current exact-offer evidence](https://network.antseed.com/stats).

Inspect the signed live catalog and pricing before use:

```bash
antseed network peer c50de6922b00677c93007c01924586de887ced7b
```

Use this signed peer catalog as the source of truth. AntFeed refreshes its
provider directory hourly, and other discovery surfaces may also cache an older price snapshot. If a cached listing
differs, do not create a paid session until the direct peer lookup is reviewed.

## Coding Tool Paths

After the buyer is funded, running, pinned, and the user has approved a real
task:

```bash
antseed codex --model claude-opus-4.6
antseed opencode --model claude-opus-4.6

export OPENAI_API_BASE=http://127.0.0.1:8377/v1
export OPENAI_API_KEY=antseed-local
aider --model openai/c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
```

Continue can use this `config.yaml` model entry:

```yaml
name: NovaRoute AI
version: 1.0.0
schema: v1

models:
  - name: NovaRoute AI - claude-opus-4.6
    provider: openai
    model: c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
    apiBase: http://127.0.0.1:8377/v1
    apiKey: antseed-local
    roles:
      - chat
      - edit
      - apply
```

Do not use a test prompt. The first paid request must be the real task the user
already approved.

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
        "ANTSEED_BUYER_STRICT": "1",
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
seller 0xc50DE6922b00677c93007c01924586dE887ced7b. For a real code, Web3
transaction-safety, or release-readiness review, inspect
novaroute-code-audit-v1 first. Otherwise inspect claude-opus-4.6,
minimax-m2.7, gpt-5.6-sol, opus-4.7, and gpt-5.5 pricing. Compare the result
with the signed direct peer catalog, and ask me before create_session.
```

Agents that can load repository skills can instead use the guarded
[`novaroute-antseed-buyer` skill](skills/novaroute-antseed-buyer/SKILL.md). It
performs read-only peer and price checks first and requires explicit user
confirmation before funding or a paid real workload.

## Help and Attribution

[Open the external buyer onboarding form](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
before or after installing a buyer. The buyer hash is optional until the buyer
exists. Never submit a peer private key, seed phrase, wallet credential, API key,
or complete environment file.

The operator permanently excludes its own buyer from demand, conversion, and
repeat-use statistics. Only independent external usage counts toward adoption.
