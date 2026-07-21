# AntSeed Provider Attestation

Provider: NovaRoute AI

This repository is controlled by the GitHub account that publishes the AntSeed GitHub verification proof for the provider below.

## Identity

- AntSeed peer ID: `c50de6922b00677c93007c01924586de887ced7b`
- On-chain agent ID: `56687`
- Seller wallet: `0xc50DE6922b00677c93007c01924586dE887ced7b`
- Settlement chain: Base mainnet
- Settlement asset: USDC

## Public Proofs

- GitHub proof file: `antseed.json`
- Domain proof site: `https://woodfuturebj-boop.github.io`
- Domain proof file: `https://woodfuturebj-boop.github.io/.well-known/antseed.json`

## Operating Notes

- The provider is configured as an OpenAI-compatible AntSeed seller.
- The upstream is Surplus Intelligence.
- Current advertised services are managed by local price guard automation.
- Buyers must explicitly pin this peer because AntSeed buyer auto-selection is disabled by default:
  `antseed buyer connection set --peer c50de6922b00677c93007c01924586de887ced7b`
- No private keys, API keys, or credentials are committed to this repository.
