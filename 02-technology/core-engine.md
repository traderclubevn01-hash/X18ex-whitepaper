# X18 Core Engine

## Hybrid Order Book + AMM Trading Engine

X18 Core là trái tim của toàn bộ nền tảng — engine giao dịch kết hợp **Central Limit Order Book (CLOB)** với **Automated Market Maker (AMM)** để đạt cả tốc độ và depth of liquidity.

---

## Tại Sao Hybrid?

| Mô hình | Ưu điểm | Nhược điểm |
|:---|:---|:---|
| **Pure AMM** (Uniswap) | Thanh khoản tự động, permissionless | Slippage cao, impermanent loss |
| **Pure Order Book** (Hyperliquid) | Tốc độ cao, precision | Cần market makers, liquidity cold start |
| **Hybrid** (X18ex) | ✅ Tốc độ + thanh khoản + permissionless | Phức tạp hơn để xây dựng |

---

## Kiến Trúc Core Engine

```
┌──────────────────────────────────────────────────────────┐
│                    X18 CORE ENGINE                       │
│                                                          │
│  ┌─────────────────┐         ┌─────────────────────┐    │
│  │   CLOB Engine   │◄───────►│   AMM Engine        │    │
│  │  (Off-chain     │         │  (On-chain           │    │
│  │   Sequencer)    │         │   Concentrated LP)   │    │
│  │                 │         │                      │    │
│  │ • Limit Orders  │         │ • Passive Liquidity  │    │
│  │ • Market Orders │         │ • Custom Curves      │    │
│  │ • Stop Orders   │         │ • Auto-rebalance     │    │
│  │ • TWAP/VWAP     │         │ • Range Orders       │    │
│  └────────┬────────┘         └──────────┬───────────┘    │
│           │                             │                │
│           ▼                             ▼                │
│  ┌──────────────────────────────────────────────────┐    │
│  │              UNIFIED MATCHING ENGINE              │    │
│  │                                                   │    │
│  │  Best price from CLOB or AMM → auto-route         │    │
│  │  Smart order splitting across both engines         │    │
│  └────────────────────┬──────────────────────────────┘    │
│                       │                                   │
│                       ▼                                   │
│  ┌──────────────────────────────────────────────────┐    │
│  │              ON-CHAIN SETTLEMENT                  │    │
│  │                                                   │    │
│  │  • Atomic settlement on target chain              │    │
│  │  • Flash Accounting (EIP-1153)                    │    │
│  │  • Netting & batch settlement                     │    │
│  └──────────────────────────────────────────────────┘    │
└──────────────────────────────────────────────────────────┘
```

---

## Order Types Hỗ Trợ

### Basic Orders
| Order Type | Mô tả |
|:---|:---|
| **Market Order** | Thực hiện ngay ở giá tốt nhất hiện tại |
| **Limit Order** | Đặt giá mong muốn, chờ khớp |
| **Stop-Loss** | Tự động bán khi giá xuống mức chỉ định |
| **Take-Profit** | Tự động chốt lời khi giá đạt mục tiêu |

### Advanced Orders
| Order Type | Mô tả |
|:---|:---|
| **TWAP** | Time-Weighted Average Price — chia nhỏ theo thời gian |
| **VWAP** | Volume-Weighted Average Price — chia nhỏ theo volume |
| **Trailing Stop** | Stop-loss di chuyển theo giá |
| **OCO** | One-Cancels-Other — 2 lệnh liên kết |
| **Iceberg** | Ẩn size lệnh lớn, hiển thị từng phần nhỏ |

### AI-Enhanced Orders (X18 Exclusive)
| Order Type | Mô tả |
|:---|:---|
| **Smart Execute** | AI chọn timing, splitting, routing tối ưu |
| **Intent Order** | Nêu ý định ("Buy 10 ETH at best price across all chains"), AI xử lý |
| **Predictive Stop** | AI dự đoán volatility spike → tự động điều chỉnh stop |

---

## Cross-Margin System

X18ex triển khai hệ thống **Unified Cross-Margin** — tất cả positions, spot balances, và lending deposits được tính chung làm collateral:

```
┌─────────────────────────────────────────┐
│         UNIFIED MARGIN ACCOUNT          │
│                                         │
│  Spot: 10 ETH ($25,000)                │
│  Perp: Long BTC 2x ($20,000)           │
│  Lending: 5,000 USDC deposited         │
│  ────────────────────────────           │
│  Total Margin: $50,000                  │
│  Used Margin:  $20,000 (Perp)           │
│  Free Margin:  $30,000                  │
│  Health Factor: 2.50 ✅                 │
│                                         │
│  💡 Unrealized profit from ETH spot     │
│     offsets BTC perp margin requirement │
└─────────────────────────────────────────┘
```

**Lợi ích:**
- Capital efficiency tăng **2-3x** so với isolated margin
- Giảm rủi ro liquidation vì portfolio netting
- Một tài khoản cho mọi hoạt động

---

## Performance Targets

| Metric | Target | So sánh |
|:---|:---|:---|
| **Order Latency** | <50ms | Hyperliquid: ~100ms |
| **Orders/Second** | 100,000+ | Hyperliquid: 200K |
| **Settlement Finality** | <2 seconds (L2) | dYdX: ~1s |
| **Uptime** | 99.99% | Industry: 99.9% |
| **Gas Optimization** | 40% less than avg | Via Flash Accounting |

---

## Plugin Hook System

Lấy cảm hứng từ Uniswap v4 Hooks, X18ex cho phép developers gắn custom logic vào lifecycle của pool:

### Hook Points
```
beforeInitialize → afterInitialize
beforeSwap → afterSwap
beforeAddLiquidity → afterAddLiquidity
beforeRemoveLiquidity → afterRemoveLiquidity
beforeSettle → afterSettle
```

### Plugin Use Cases
- **Dynamic Fee Plugin** — Phí thay đổi theo volatility
- **TWAMM Plugin** — Time-Weighted AMM cho large orders
- **KYC Gate Plugin** — Pools chỉ cho verified users
- **Yield Optimizer Plugin** — Auto-compound LP rewards
- **Notification Plugin** — Custom alerts khi điều kiện đạt

---

> **Tiếp theo:** [Intelligence Layer — X18 Brain →](intelligence-layer.md)
