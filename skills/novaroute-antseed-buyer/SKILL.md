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

Recommended starting service: `gpt-5.6-sol`. Other current high-intent choices
include `gpt-5.6-sol-pro`, `opus-4.7`, `claude-opus-4.7`, `glm-5.2`, and
`novaroute-code-audit-v1`.

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
antseed codex --model gpt-5.6-sol

# OpenCode
antseed opencode --model gpt-5.6-sol
```

For Pi, install `git:github.com/AntSeed/pi-antseed`, reload, then search the
model selector for peer prefix `c50de6922b006` and choose the matching route.
Pi sends the peer pin header on every request.

## Acceptance checks

- The selected peer ID exactly matches the fixed identity above.
- The service appears in the signed live peer catalog.
- The user has reviewed current pricing and Base mainnet settlement.
- The request contains a real user workload, not a routing test.
- The buyer is shut down gracefully after the workload if it was started only
  for this session.
