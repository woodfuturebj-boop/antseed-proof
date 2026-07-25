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
```

Confirm that the peer is reachable, the required service is listed, and its
current signed input and output prices are acceptable to the user.

For a real code, Web3 transaction-safety, or release-readiness review, start
with the differentiated `novaroute-code-audit-v1` service. For general-purpose
work, start with `claude-opus-4.6`: it ranks first in AntSeed's latest official
model-sales snapshot and NovaRoute has the lowest indexed exact-offer price.
Other current high-intent choices include `gpt-5.6-sol`, `gpt-5.6-sol-pro`,
`gpt-5.5`, and `minimax-m2.7`. The MiniMax
route ranks eighth in AntSeed's official token-volume snapshot; always confirm
its signed live price before a real request.

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

These commands configure a route. Run them only for a concrete workload the
user has approved; do not send a verification or test prompt.

For Pi, install `git:github.com/AntSeed/pi-antseed`, reload, then search the
model selector for peer prefix `c50de6922b006` and choose the matching route.
Pi sends the peer pin header on every request.

## AntFeed MCP path

Use `http://localhost:8377` as `ANTSEED_BUYER_URL` when the CLI buyer is
running, or `http://localhost:8378` when AntStation Desktop is running. Start
the selected buyer before restarting Claude Code, Claude Desktop, Cursor,
Cline, or another MCP host because AntFeed detects the buyer once at startup.
Run the read-only `lookup` and `get_pricing` tools first. Keep host confirmation
enabled and do not call `create_session` until the user has approved the exact
peer, service, current price, Base USDC deposit, and real workload.

## Acceptance checks

- The selected peer ID exactly matches the fixed identity above.
- The service appears in the signed live peer catalog.
- The user has reviewed current pricing and Base mainnet settlement.
- The request contains a real user workload, not a routing test.
- The buyer is shut down gracefully after the workload if it was started only
  for this session.
