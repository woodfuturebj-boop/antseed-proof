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
```

The payment portal stays in the foreground. After funding, stop it with
`Ctrl+C` and confirm the deposit from that terminal, or keep it open and use a
second terminal:

```bash
antseed buyer balance
```

Then start the buyer with this provider pinned:

```bash
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

Before opening a paid session, run this read-only preflight. It checks the
installed CLI, signed peer catalog, and buyer balance without calling a model:

```bash
antseed --version
antseed network peer c50de6922b00677c93007c01924586de887ced7b
antseed buyer balance
```

Then choose a direct route and replace the message below with a task you actually
need completed. The model-prefix route pins this provider for one request without
replacing a saved connection. Do not send artificial traffic just to test the
route.

Current high-demand routes:

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
c50de6922b00677c93007c01924586de887ced7b@novaroute-code-audit-v1
```

```bash
curl http://127.0.0.1:8377/v1/chat/completions \
  -H "content-type: application/json" \
  -d '{"model":"c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6","messages":[{"role":"user","content":"REPLACE WITH YOUR REAL TASK"}]}'
```

Start with one of these current high-value services:

- `claude-opus-4.6` - first in AntSeed's latest official model-sales snapshot;
  signed live directory pricing
- `gpt-5.6-sol` - highest upstream dollar volume in the current market sample
- `gpt-5.6-sol-pro` - premium reasoning route
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

For any service above, inspect the stable NovaRoute AI
[seller profile](https://www.antfeed.org/sellers/0xc50de6922b00677c93007c01924586de887ced7b),
then search the exact service ID in the
[AntFeed service directory](https://www.antfeed.org/services) when a market
comparison is needed. Confirm the signed live price, then pin the peer before
the paid session.

[Official demand evidence: AntSeed Top models by sales](https://x.com/AntSeedAI/status/2081002378795377145).
[Official demand evidence: AntSeed Top models by token volume](https://x.com/AntSeedAI/status/2077010692012470320).
[Current exact-offer evidence](https://network.antseed.com/stats).

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

Cline can select **OpenAI Compatible** and use:

```text
Base URL: http://127.0.0.1:8377/v1
API Key: antseed-local
Model ID: c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
```

Entering the Base URL and API key may refresh Cline's free local model catalog.
It must not be followed by a synthetic verification prompt. See Cline's
[official OpenAI Compatible guide](https://docs.cline.bot/provider-config/openai-compatible).

Kilo Code can add a custom provider with these fields:

```text
Provider ID: antseed
Display name: NovaRoute AI
Provider API: OpenAI Compatible
Base URL: http://127.0.0.1:8377/v1
API Key: antseed-local
Model ID (manual): c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
```

Kilo may query the free local `/v1/models` catalog during setup. Keep the
manual peer-prefixed model ID and do not send a synthetic verification prompt.
See Kilo's [official guide](https://kilo.ai/docs/ai-providers/openai-compatible).

Zoo Code can select **OpenAI Compatible** and use:

```text
Base URL: http://127.0.0.1:8377/v1
API Key: antseed-local
Model ID (custom): c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
```

Zoo Code waits 250 ms after the Base URL or API key changes, then reads only
the free local `/v1/models` catalog. Select the custom peer-prefixed model ID,
use a service with native OpenAI tool calling, and do not send a synthetic
verification prompt. See Zoo Code's
[official guide](https://docs.zoocode.dev/providers/openai-compatible).

Goose can add a custom provider with these fields:

```text
Provider type: OpenAI Compatible
Display name: NovaRoute AI
API URL: http://127.0.0.1:8377/v1
Requires API key: off
Model: c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
Streaming: on
```

Goose may read only the free local `/v1/models` catalog for model discovery or
context metadata. Keep the peer-prefixed model, do not run the provider test,
and begin only with a real repository task. See Goose's
[official provider guide](https://goose-docs.ai/docs/getting-started/providers/#configure-custom-provider).

Cherry Studio can add a custom provider with these fields:

```text
Provider name: NovaRoute AI
Provider type: OpenAI
API key: antseed-local
API address: http://127.0.0.1:8377
Model ID (manual): c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
Provider: enabled
```

Cherry Studio appends `/v1` to the root API address. Adding a model manually
or listing models reads only the free local catalog. Do not click **Check** or
**Detect**: the official implementation sends a minimal inference probe. Keep
the peer-prefixed model, use a service with native OpenAI tool calling for MCP
work, and begin only with a real task. See Cherry Studio's
[official custom provider guide](https://docs.cherry-ai.com/docs/en-us/pre-basic/providers/zi-ding-yi-fu-wu-shang).

Chatbox can open a reviewed one-click import preview from the
[direct public buyer route](https://woodfuturebj-boop.github.io/?integration=chatbox#integrations).
The generated configuration contains:

```text
Provider ID: novaroute-antseed
Provider name: NovaRoute AI
API mode: OpenAI API Compatible
API key: antseed-local
API Host: http://127.0.0.1:8377
API Path: leave blank
Model ID: c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
Model type: Chat
Capability: Tool use
```

The official `chatbox://provider/import` flow shows these values read-only and
does not write settings until **Save**. Re-importing provider ID
`novaroute-antseed` shows an overwrite warning. Chatbox normalizes the blank
path to `/v1/chat/completions`, preserves the model ID, and passes native tools
to the OpenAI-compatible runtime. Do not click **Check** or **Test Model**:
those actions send separate text, vision, and tool inference probes. **Fetch**
only reads the free local `/v1/models` catalog and is not required. See the
[official provider guide](https://docs.chatboxai.app/en/guides/providers).

Jan supports OpenAI-compatible custom endpoints through the
[direct Jan buyer route](https://woodfuturebj-boop.github.io/?integration=jan#integrations):

```text
Settings > Model Providers > Add Provider
Provider name: NovaRoute AI
API format: OpenAI-compatible
Base URL: http://127.0.0.1:8377/v1
API key: antseed-local
Model ID: c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
Edit model > Tools: on > Save
```

Jan calls only the free local `{base_url}/models` endpoint while creating the
provider, refreshing models, or testing the placeholder key. The selected
model ID is preserved in Chat Completions. Custom-provider capabilities are
not inferred, so the **Tools** switch only saves a local capability flag; it
does not require a test prompt. Jan passes enabled MCP tools to the model at
runtime. Keep individual tool approvals enabled and start only with a real
task. See the [official custom endpoint guide](https://jan.ai/docs/desktop/remote-models/custom-endpoint)
and [official MCP guide](https://jan.ai/docs/desktop/mcp).

AnythingLLM Desktop can use the selected route through its
[direct Generic OpenAI panel](https://woodfuturebj-boop.github.io/?integration=anythingllm#integrations):

```text
Settings > AI Providers > LLM
LLM Provider: Generic OpenAI
Base URL: http://127.0.0.1:8377/v1
API Key: antseed-local
Selected Model: c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
Model context window: 8192
Max Tokens: 1024
```

The settings UI calls only the free local `/v1/models` catalog and preserves
the selected model ID. The current Generic OpenAI agent provider enables native
tool calling by default and sends tools only for a real agent request; no
setup inference probe is needed. Use the desktop app for this localhost path,
because Docker's `127.0.0.1` refers to the container itself. Open a workspace
and begin with a real task; use `@agent` only when that task needs tools. See
the [official Generic OpenAI guide](https://docs.anythingllm.com/setup/llm-configuration/cloud/openai-generic)
and [official agent overview](https://docs.anythingllm.com/agent/overview).

Do not use a test prompt. The first paid request must be the real task the user
already approved.

## Agent Path: AntFeed MCP Read-Only Discovery

This seller is indexed in AntFeed under wallet
`0xc50DE6922b00677c93007c01924586dE887ced7b`.

Open the [direct AntFeed seller profile](https://www.antfeed.org/sellers/0xc50de6922b00677c93007c01924586de887ced7b)
to inspect the address, aggregate history, and advertised services without
depending on directory ordering.

For a real code, Web3 transaction-safety, or release-readiness review, search
`novaroute-code-audit-v1` in the
[AntFeed service directory](https://www.antfeed.org/services), verify the
provider, then confirm the signed live price before considering a paid session.

Add this read-only discovery config to Claude Code, Claude Desktop, Cursor,
Cline, or another MCP host:

```json
{
  "mcpServers": {
    "antfeed": {
      "command": "npx",
      "args": ["-y", "@antfeed/mcp"],
      "env": {
        "ANTFEED_EXPLORER_URL": "https://www.antfeed.org"
      }
    }
  }
}
```

Use only `lookup` and `get_pricing`, then compare the result with the direct
peer lookup above. AntFeed MCP `0.2.5` expects local buyer endpoints at
`/health` and `/sessions`, but AntSeed CLI `0.1.136` does not expose them.
Do not call `create_session`; continue through the direct pinned buyer path in
this guide for the approved real workload.

Suggested agent instruction:

```text
Use AntFeed MCP to look up "NovaRoute AI". Verify
seller 0xc50DE6922b00677c93007c01924586dE887ced7b. For a real code, Web3
transaction-safety, or release-readiness review, inspect
novaroute-code-audit-v1 first. Otherwise inspect claude-opus-4.6,
minimax-m2.7, gpt-5.6-sol, and gpt-5.5 pricing. Compare the result
with the signed direct peer catalog, return the pinned model route, and do not
call create_session. Ask me to continue through the direct AntSeed buyer path.
```

Agents that can load repository skills can instead use the guarded
[`novaroute-antseed-buyer` skill](skills/novaroute-antseed-buyer/). It
performs read-only peer and price checks first and requires explicit user
confirmation before funding or a paid real workload.

## Help and Attribution

[Open the external buyer onboarding form](https://github.com/woodfuturebj-boop/antseed-proof/issues/new?template=beta.yml)
before or after installing a buyer. The buyer hash is optional until the buyer
exists. Never submit a peer private key, seed phrase, wallet credential, API key,
or complete environment file.

The operator permanently excludes its own buyer from demand, conversion, and
repeat-use statistics. Only independent external usage counts toward adoption.
