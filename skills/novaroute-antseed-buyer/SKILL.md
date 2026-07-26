---
name: novaroute-antseed-buyer
description: Connect an existing AntSeed buyer to the verified NovaRoute AI peer for a user-approved real workload, with explicit pricing and payment checks.
---

# NovaRoute AntSeed Buyer

Use this skill when a user explicitly asks to route a real AI workload through
NovaRoute AI on AntSeed.

## Fixed identity

- Peer ID: `c50de6922b00677c93007c01924586de887ced7b`
- Public endpoint: `149.28.69.249:6882`
- Website: `https://woodfuturebj-boop.github.io/`
- Settlement: Base mainnet USDC

The signed peer catalog is authoritative. Cached websites and AntFeed can lag.

## Safety rules

1. Never request, read, print, or store a private key, seed phrase, API key,
   wallet credential, or complete environment file.
2. Never self-buy, create test inference, fabricate traffic, or submit a paid
   request merely to check that routing works.
3. Use only a concrete workload the user already needs completed.
4. Before any paid request, show the selected peer, service, signed live price,
   Base mainnet settlement, and proposed deposit or spend cap. Require explicit
   user confirmation.
5. Do not fund, deposit, withdraw, sign, or send a transaction on the user's
   behalf without that confirmation. Prefer the official `antseed payments`
   flow instead of constructing transactions.

## Read-only verification

Run these first:

```bash
antseed --version
antseed network peer c50de6922b00677c93007c01924586de887ced7b
antseed buyer status
antseed buyer balance
```

These checks do not call a model or open a paid inference session. Confirm that
the peer is reachable, the required service is listed, and its current signed
input and output prices are acceptable to the user.

For a real code, Web3 transaction-safety, or release-readiness review, start
with the differentiated `novaroute-code-audit-v1` service. For general-purpose
work, start with `claude-opus-4.6`: it ranks first in AntSeed's latest official
model-sales snapshot and exposes signed live directory pricing.
Other current high-intent choices include `gpt-5.6-sol`, `gpt-5.6-sol-pro`,
`gpt-5.5`, and `minimax-m2.7`. The MiniMax
route ranks eighth in AntSeed's official token-volume snapshot; always confirm
an exact service comparison at `https://www.antfeed.org/services/<service-id>`,
then confirm its signed live price before a real request.

The public AntFeed service page at
`https://www.antfeed.org/services/novaroute-code-audit-v1` is a read-only
comparison surface. Use it only as corroborating discovery evidence; the
signed peer catalog remains authoritative for the current paid price.

## Pin an existing buyer

If the buyer proxy is already running, switch it without a restart:

```bash
antseed buyer connection set --peer c50de6922b00677c93007c01924586de887ced7b
```

If the buyer is not running, ask the user to start it in a separate foreground
terminal with the peer pinned:

```bash
antseed buyer start --peer c50de6922b00677c93007c01924586de887ced7b
```

When finished, use `Ctrl+C` and wait for
`Disconnected. All channels finalized.`. Never force-kill the buyer.

## Per-request pin

For clients that support custom headers, preserve the normal service name and
pin only this request:

```text
x-antseed-pin-peer: c50de6922b00677c93007c01924586de887ced7b
```

The equivalent model prefix is:

```text
c50de6922b00677c93007c01924586de887ced7b@<service-id>
```

Do not send either form until the user has supplied and approved a real task.

## Coding-agent paths

After the buyer is funded, running, pinned, and explicitly approved:

```bash
# Codex
antseed codex --model claude-opus-4.6

# OpenCode
antseed opencode --model claude-opus-4.6

# Aider
export OPENAI_API_BASE=http://127.0.0.1:8377/v1
export OPENAI_API_KEY=antseed-local
aider --model openai/c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6
```

For Continue, add an OpenAI provider in `config.yaml` with
`apiBase: http://127.0.0.1:8377/v1`, `apiKey: antseed-local`, and model
`c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`.

For Cline, select **OpenAI Compatible** and enter base URL
`http://127.0.0.1:8377/v1`, API key `antseed-local`, and model ID
`c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`. Cline may refresh
the free local model catalog while these fields are entered. Do not send a
synthetic verification prompt after configuration.

For Kilo Code, add a custom provider with ID `antseed`, display name
`NovaRoute AI`, provider API **OpenAI Compatible**, base URL
`http://127.0.0.1:8377/v1`, API key `antseed-local`, and manually add model ID
`c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`. Kilo may query
the free local `/v1/models` catalog; retain the manual peer-prefixed ID and do
not use a synthetic verification prompt.

For Zoo Code, select **OpenAI Compatible**, enter base URL
`http://127.0.0.1:8377/v1` and API key `antseed-local`, then choose custom model
ID `c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`. Zoo Code reads
only the free local `/v1/models` catalog during setup. Retain the peer-prefixed
ID, use a service with native OpenAI tool calling, and do not send a synthetic
verification prompt.

For Goose, add a custom **OpenAI Compatible** provider with API URL
`http://127.0.0.1:8377/v1`, API-key requirement disabled, streaming enabled,
and model `c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`. Goose may
read only the free local `/v1/models` catalog for discovery or context
metadata. Retain the peer prefix, skip the provider test, and begin only with
a real repository task.

For Cherry Studio, add a custom **OpenAI** provider with API address
`http://127.0.0.1:8377`, API key `antseed-local`, and manually add model
`c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`. Cherry Studio
appends `/v1` to this root address. Adding or listing models reads only the
free local catalog, but **Check** or **Detect** sends a paid inference probe.
Do not use either check. Retain the peer prefix, choose a service with native
OpenAI tool calling for MCP-backed work, and begin only with a real task.

For Chatbox, use the route-specific `chatbox://provider/import` preview on the
public buyer page. It imports provider ID `novaroute-antseed`, API host
`http://127.0.0.1:8377`, API key `antseed-local`, and model
`c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6` with model type
**Chat** and **Tool use** enabled. Review the read-only preview and choose
**Save**; an existing provider with the same ID triggers an overwrite warning.
Do not click **Check** or **Test Model**, which send paid text, vision, and tool
probes. **Fetch** only reads the free local `/v1/models` catalog and is not
required. Begin only with a real task.

For Jan, add an **OpenAI-compatible** custom provider named `NovaRoute AI`
with base URL `http://127.0.0.1:8377/v1`, API key `antseed-local`, and model
`c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`. Provider
creation, model refresh, and key testing read only the free local `/v1/models`
catalog. Jan does not infer custom-model capabilities, so edit the model,
enable **Tools**, and save the local capability flag without sending a test
prompt. Keep individual MCP tool approvals enabled and begin only with a real
task.

For AnythingLLM Desktop, select **Generic OpenAI** with base URL
`http://127.0.0.1:8377/v1`, API key `antseed-local`, model
`c50de6922b00677c93007c01924586de887ced7b@claude-opus-4.6`, context window
`8192`, and max tokens `1024`. Setup reads only the free local `/v1/models`
catalog. The runtime preserves the model ID and supports native agent tools.
Do not use this localhost configuration in Docker, and do not send a test
prompt. Begin only with a real workspace task; use `@agent` only when that
task needs tools.

These commands configure a route. Run them only for a concrete workload the
user has approved; do not send a verification or test prompt.

For Pi, install `git:github.com/AntSeed/pi-antseed`, reload, then search the
model selector for peer prefix `c50de6922b006` and choose the matching route.
Pi sends the peer pin header on every request.

## AntFeed MCP path

Use AntFeed MCP `0.2.5` only for the read-only `lookup` and `get_pricing`
tools. Its transaction bridge expects `/health` and `/sessions`, which AntSeed
CLI `0.1.136` does not expose. Do not call `create_session` with the CLI buyer.
After discovery, verify the exact peer, service, and current signed price, then
continue through the direct pinned buyer path above for the user's approved
real workload.

## Acceptance checks

- The selected peer ID exactly matches the fixed identity above.
- The service appears in the signed live peer catalog.
- The user has reviewed current pricing and Base mainnet settlement.
- The request contains a real user workload, not a routing test.
- The buyer is shut down gracefully after the workload if it was started only
  for this session.
