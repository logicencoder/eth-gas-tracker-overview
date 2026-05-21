# Ethereum Gas Tracker — Product Overview (Public)

End-to-end description of the **Ethereum Gas Live** product: realtime fees, analytics, and indexable guides on [LogicEncoder.com](https://logicencoder.com/ethereum-gas-tracker/).

Documentation only — no private source code.

![Ethereum Gas Tracker](assets/eth-gas-tracker-overview.png)

---

## What problem it solves

Ethereum wallets show one suggested fee. In practice, costs depend on **congestion**, **transaction type** (transfer vs swap vs NFT), and **timing**. Users routinely:

- Overpay during spikes  
- Underpay and stall confirmations  
- Miss cheaper hours because they never see historical context  

This product continuously reads chain data and presents **three intentional tiers**, stress metrics, history, and send-timing guidance in one interface—on the web and via the same engine behind topic-specific URLs.

---

## Product components

| Layer | Role | Public repo |
|-------|------|-------------|
| **Backend** | Geth/RPC ingestion, SQLite, WebSocket, REST, SEO HTML/SSR data | [eth-gas-live-backend-overview-public](https://github.com/logicencoder/eth-gas-live-backend-overview-public) |
| **WordPress plugin** | Public site shell, SEO templates, admin Mission Control | [eth-gas-live-plugin-overview-public](https://github.com/logicencoder/eth-gas-live-plugin-overview-public) |
| **Legacy standalone** | Older local-only tree | Superseded by backend private repo on `main` |

Private implementation: `eth-gas-live-backend-private`, `eth-gas-live-plugin-private`.

---

## Core capabilities (accurate to production)

### 1. Realtime fee tiers

**Base Route**, **Standard Way**, **Faster Inclusion** — each with GWEI, ETH, USD, priority breakdown, and confirmation estimate. Updates on new blocks via WebSocket (REST fallback).

### 2. Network stress (not mempool size)

Live UI emphasizes metrics that are **measurable from blocks**:

- Tx/min estimate  
- IPI (Inclusion Pressure Index) 0–100  
- Spike score 0–100  
- Fee competition (tip spread)  
- Block utilization and block speed pressure  
- Status labels (e.g. normal / high / spike)  

A dedicated SEO page `/ethereum-mempool-tracker/` discusses **network load and throughput** with live IPI and tx/min—it does **not** promise a global pending-transaction count.

### 3. History and analytics

- Charts: 1h → 30d, smoothing options  
- Heatmap (localized timezone on the public site)  
- Rolling averages (1h–30d)  
- Statistics API: percentiles, volatility, best/worst hours  
- Faster-tier live percentiles P50–P85  

### 4. Decision support

- **Gas Intelligence Hub** — insight text, 24h best/worst hour, send-now vs wait  
- **Fee calculator** — presets + custom gas limit  
- **18 featured action estimates** (transfer, token ops, DEX swap, NFT, bridge, lending, staking, governance, deploy, etc.)  
- **Session alerts** with optional notifications  

### 5. Indexable content cluster

Eleven topic paths plus the live tracker hub; content filled with live placeholders so Google and users see **current** fees and stress scores. Hub navigation in the SPA lists nine quick links (calculator, best time, history, …) without a separate “mempool size” tab.

### 6. Operations

Backend exposes health/monitoring JSON; WordPress admin **Mission Control** charts runtime, WebSocket clients, fetch/push success, and database size.

---

## Live URLs (LogicEncoder)

| Page | URL |
|------|-----|
| Main tracker | https://logicencoder.com/ethereum-gas-tracker/ |
| Fees today | https://logicencoder.com/ethereum-gas-fees-today/ |
| Why fees high | https://logicencoder.com/why-are-ethereum-gas-fees-high/ |
| Best time to send | https://logicencoder.com/best-time-to-send-ethereum/ |
| Calculator | https://logicencoder.com/ethereum-gas-calculator/ |
| Network load | https://logicencoder.com/ethereum-mempool-tracker/ |

---

## Who should use this overview

- **Employers / clients** — scope and depth of a shipped crypto infra + UX product  
- **Partners** — understand surfaces before API or branding discussions  
- **Users** — what the live site does without reading code  

---

## Disclosure

Intentionally excludes implementation secrets (RPC wiring, deploy hosts, keys). For technical depth, see private repositories after access is granted.
