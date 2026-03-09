<div align="center">

# Mythic Mini

[![Network](https://img.shields.io/badge/network-mythic%20l2-39FF14?style=flat-square)](https://mythic.sh)
[![Built by](https://img.shields.io/badge/built%20by-MythicLabs-7B2FFF?style=flat-square)](https://mythiclabs.io)
[![License: BUSL-1.1](https://img.shields.io/badge/license-BUSL--1.1-39FF14?style=flat-square)](./LICENSE)
[![Firedancer](https://img.shields.io/badge/firedancer-v0.812-black?style=flat-square)](https://github.com/firedancer-io/firedancer)

**Run a lightweight Mythic L2 RPC node on modest hardware. Powered by Firedancer.**

[Install](https://mythic.sh/install) · [Documentation](https://mythic.sh/docs/validators) · [Network Status](https://mythic.sh/tokenomics)

</div>

---

## Quick Start

```bash
curl -sSf mythic.sh/install | sudo bash
```

Or force the mini tier:

```bash
MYTHIC_TIER=mini curl -sSf mythic.sh/install | sudo bash
```

## Requirements

| Resource | Minimum |
|----------|---------|
| OS | Ubuntu 22.04+ |
| CPU | 8 cores |
| RAM | 32GB |
| Storage | 500GB SSD |
| Network | 100Mbps+, public IP |

## What Is Mini Tier?

Mini is the lightest way to participate in the Mythic L2 network:

- **RPC-only** -- serves blockchain queries, no full transaction history
- **Lean tile layout** -- 10 Firedancer tiles instead of 15+
- **Small ledger** -- 10M slot limit keeps disk usage under control
- **Snapshot sync** -- fetches genesis and snapshots from bootstrap node

This is ideal for developers, hobbyists, and anyone who wants to run an RPC endpoint without enterprise hardware.

## Configuration

Config is placed at `/etc/mythic/config.toml`:

```toml
[consensus]
  snapshot_fetch      = true
  genesis_fetch       = true

[rpc]
  port                = 8899
  full_api            = true
  transaction_history = false

[tiles]
  layout = "1 net, 1 quic, 1 verify, 1 dedup, 1 pack, 1 bank, 1 poh, 1 shred, 1 store, 1 sign"
```

Full config template: [`mythic-mini.toml`](./mythic-mini.toml)

## Usage

```bash
# Start
sudo systemctl start mythic-validator

# Status
sudo systemctl status mythic-validator

# Logs
journalctl -u mythic-validator -f
```

## Upgrade Path

Ready for more? Upgrade to the standard validator tier for full transaction history and staking rewards:

```bash
MYTHIC_TIER=validator curl -sSf mythic.sh/install | sudo bash
```

See [mythic-validator](https://github.com/MythicFoundation/mythic-validator) for standard tier requirements.

## Mythic CLI

```bash
curl -sSf mythic.sh/cli | bash
mythic validator status
```

## Other Tiers

| Tier | Repo | Hardware |
|------|------|----------|
| **Mini** | You are here | 8+ cores, 32GB RAM |
| Validator | [mythic-validator](https://github.com/MythicFoundation/mythic-validator) | 32+ cores, 128GB RAM |
| AI | [mythic-ai-validator](https://github.com/MythicFoundation/mythic-ai-validator) | 48+ cores, 256GB RAM, GPU |

## License

[Business Source License 1.1](./LICENSE) -- converts to MIT on February 1, 2028.
