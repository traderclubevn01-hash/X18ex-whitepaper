# Architecture Overview

## Kiến Trúc Tổng Quan X18ex

X18ex được thiết kế theo kiến trúc **5 tầng** (Five-Layer Stack) — mỗi tầng giải quyết một nhóm vấn đề cụ thể và hoạt động độc lập nhưng kết nối chặt chẽ.

---

## Sơ Đồ Kiến Trúc

```
╔══════════════════════════════════════════════════════════════════╗
║                    🌍 ECOSYSTEM LAYER                          ║
║  ┌──────────────┐  ┌──────────────┐  ┌──────────────────────┐  ║
║  │   Plugin     │  │  Developer   │  │     X18 DAO          │  ║
║  │ Marketplace  │  │  Community   │  │   Governance         │  ║
║  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘  ║
╠═════════╪══════════════════╪═════════════════════╪══════════════╣
║         │          📱 APPLICATION LAYER          │              ║
║  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────┴───────────┐  ║
║  │   Web3       │  │   Mobile     │  │   Bot Dashboard      │  ║
║  │  Terminal    │  │     App      │  │   & API Portal       │  ║
║  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘  ║
╠═════════╪══════════════════╪═════════════════════╪══════════════╣
║         │          🔌 INTEGRATION LAYER          │              ║
║  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────┴───────────┐  ║
║  │  REST API    │  │  WebSocket   │  │   Webhook &          │  ║
║  │  Gateway     │  │   Feeds      │  │   Event System       │  ║
║  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘  ║
║  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────┴───────────┐  ║
║  │  Wallet      │  │  Cross-chain │  │   Account            │  ║
║  │ Abstraction  │  │   Bridge     │  │   Abstraction        │  ║
║  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘  ║
╠═════════╪══════════════════╪═════════════════════╪══════════════╣
║         │          🧠 INTELLIGENCE LAYER         │              ║
║  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────┴───────────┐  ║
║  │  AI Smart    │  │   Risk       │  │   MEV Protection     │  ║
║  │  Routing     │  │  Guardian    │  │      Shield          │  ║
║  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘  ║
║  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────┴───────────┐  ║
║  │  Portfolio   │  │  Market      │  │   Liquidation        │  ║
║  │   Pilot      │  │  Sentiment   │  │     Shield           │  ║
║  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘  ║
╠═════════╪══════════════════╪═════════════════════╪══════════════╣
║         │          ⚡ PROTOCOL LAYER              │              ║
║  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────┴───────────┐  ║
║  │  Hybrid      │  │ Perpetuals   │  │   Lending &          │  ║
║  │ Order Book   │  │   Engine     │  │   Borrowing          │  ║
║  │   + AMM      │  │              │  │                      │  ║
║  └──────┬───────┘  └──────┬───────┘  └──────────┬───────────┘  ║
║  ┌──────┴───────┐  ┌──────┴───────┐  ┌──────────┴───────────┐  ║
║  │  Liquidity   │  │  Settlement  │  │   Plugin Hook        │  ║
║  │    Pools     │  │    Layer     │  │     Engine            │  ║
║  └──────────────┘  └──────────────┘  └──────────────────────┘  ║
╠══════════════════════════════════════════════════════════════════╣
║                   ⛓️ MULTI-CHAIN SUBSTRATE                     ║
║  ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐     ║
║  │ETH │ │ARB │ │BASE│ │BSC │ │POL │ │SOL │ │AVAX│ │OP  │     ║
║  └────┘ └────┘ └────┘ └────┘ └────┘ └────┘ └────┘ └────┘     ║
╚══════════════════════════════════════════════════════════════════╝
```

---

## Mô Tả Từng Tầng

### ⚡ Tầng 1: Protocol Layer — "The Foundation"

Tầng nền tảng nơi mọi logic giao dịch xảy ra on-chain.

| Component | Chức năng | Công nghệ tham chiếu |
|:---|:---|:---|
| **Hybrid Order Book + AMM** | Kết hợp tốc độ CLOB với thanh khoản AMM | Vertex Protocol + Uniswap v4 |
| **Perpetuals Engine** | Hợp đồng tương lai vĩnh viễn, leverage tới 50x | Hyperliquid + dYdX |
| **Lending & Borrowing** | Cho vay/mượn tích hợp trong margin | Aave + Vertex |
| **Liquidity Pools** | Concentrated liquidity + custom curves | Uniswap v4 Hooks |
| **Settlement Layer** | On-chain settlement đảm bảo transparency | Ethereum L1/L2 |
| **Plugin Hook Engine** | Mở rộng chức năng qua smart contract plugins | Uniswap v4 Hooks |

### 🧠 Tầng 2: Intelligence Layer — "The Brain"

Tầng AI tạo nên sự khác biệt cốt lõi — không ai khác có.

| Component | Chức năng |
|:---|:---|
| **AI Smart Routing** | ML model quét 200+ liquidity sources, dự đoán slippage & gas |
| **Risk Guardian** | Real-time risk scoring cho mọi trade và position |
| **MEV Protection Shield** | AI phát hiện và ngăn chặn MEV attacks |
| **Portfolio Pilot** | AI tự động rebalance và optimize portfolio |
| **Market Sentiment** | NLP phân tích social feeds → trading signals |
| **Liquidation Shield** | Dự đoán liquidation risk 15 phút trước, auto-hedge |

### 🔌 Tầng 3: Integration Layer — "The Connectors"

Tầng kết nối giữa protocol và ứng dụng.

| Component | Chức năng |
|:---|:---|
| **REST API Gateway** | Full trading, data, account management API |
| **WebSocket Feeds** | Real-time orderbook, trades, positions, alerts |
| **Webhook System** | Push notifications cho events: fills, liquidations |
| **Wallet Abstraction** | Kết nối mọi wallet type: EOA, Smart Account, MPC |
| **Cross-chain Bridge** | Intent-based bridging an toàn, không custodial |
| **Account Abstraction** | Gasless transactions, session keys, social login |

### 📱 Tầng 4: Application Layer — "The Interface"

Tầng giao diện người dùng.

| Component | Chức năng |
|:---|:---|
| **Web3 Trading Terminal** | Full-featured trading interface, TradingView charts |
| **Mobile App** | iOS/Android native app |
| **Bot Dashboard** | API key management, strategy deployment, performance analytics |

### 🌍 Tầng 5: Ecosystem Layer — "The Community"

Tầng hệ sinh thái mở.

| Component | Chức năng |
|:---|:---|
| **Plugin Marketplace** | Mua/bán/chia sẻ plugins |
| **Developer Community** | Grants, hackathons, documentation |
| **X18 DAO** | Governance, treasury, proposals |

---

## Multi-Chain Substrate

X18ex hỗ trợ multi-chain từ ngày đầu thông qua kiến trúc **Chain Abstraction**:

### Phase 1 — Launch Chains
| Chain | Type | Lý do |
|:---|:---|:---|
| **Ethereum** | L1 | Liquidity sâu nhất, institutional trust |
| **Arbitrum** | L2 | Low gas, fast, DeFi ecosystem mạnh |
| **Base** | L2 | Coinbase ecosystem, retail onboarding |
| **BSC** | L1 | Volume lớn, chi phí thấp |

### Phase 2 — Expansion Chains
| Chain | Type | Lý do |
|:---|:---|:---|
| **Polygon** | L2 | Massive user base, enterprise |
| **Solana** | L1 | Tốc độ cao nhất, non-EVM diversity |
| **Avalanche** | L1 | Institutional DeFi, subnets |
| **Optimism** | L2 | Superchain ecosystem |

### Phase 3 — Full Coverage
- Sei, Mantle, Blast, zkSync, Scroll, Linea
- Non-EVM: Aptos, Sui (research phase)

---

## Triết Lý Kiến Trúc

### Modular, Không Monolithic
Mỗi module có thể nâng cấp độc lập. Upgrade perpetuals engine không ảnh hưởng spot trading.

### Open Core, Plugin Extensions
Core protocol là open-source. Extensions qua plugin marketplace cho phép innovation từ community.

### On-chain Settlement, Off-chain Speed
Order matching off-chain cho tốc độ. Settlement on-chain cho transparency và security.

### AI-Enhanced, Not AI-Dependent
AI tối ưu mọi thứ nhưng protocol vẫn hoạt động hoàn hảo nếu AI layer offline. Không có single point of failure.

---

> **Tiếp theo:** [X18 Core Engine →](core-engine.md)
