# Intelligence Layer — X18 Brain

## AI-Native: Không Phải Tính Năng Phụ, Mà Là Core Engine

X18 Brain là lớp trí tuệ nhân tạo **tích hợp sâu** vào mọi hoạt động của nền tảng. Đây không phải chatbot hay AI wrapper — mà là một hệ thống ML/AI thực sự ảnh hưởng đến routing, risk, execution, và protection.

---

## Kiến Trúc X18 Brain

```
                    ┌─────────────────────┐
                    │    USER ACTIONS      │
                    │  (Swap, Trade, LP)   │
                    └──────────┬──────────┘
                               │
                    ┌──────────▼──────────┐
                    │    X18 BRAIN HUB     │
                    │   (Orchestrator)     │
                    └──┬───┬───┬───┬───┬──┘
                       │   │   │   │   │
          ┌────────────┘   │   │   │   └────────────┐
          │                │   │   │                │
    ┌─────▼─────┐   ┌─────▼───▼───▼─────┐   ┌─────▼─────┐
    │   Smart    │   │    Risk     MEV   │   │ Portfolio  │
    │  Router    │   │  Guardian  Shield │   │   Pilot    │
    │            │   │                   │   │            │
    │ • Path     │   │ • Position risk   │   │ • Auto     │
    │   finding  │   │ • Liq. warning    │   │   rebalance│
    │ • Gas      │   │ • Front-run       │   │ • Yield    │
    │   predict  │   │   detection       │   │   optimize │
    │ • Slippage │   │ • Sandwich        │   │ • Tax-loss │
    │   estimate │   │   prevention      │   │   harvest  │
    └────────────┘   └───────────────────┘   └────────────┘
          │                    │                     │
          └────────────────────┼─────────────────────┘
                               │
                    ┌──────────▼──────────┐
                    │   ML MODEL LAYER    │
                    │                     │
                    │ • Price Prediction   │
                    │ • Volatility Models  │
                    │ • Liquidity Scoring  │
                    │ • Sentiment Analysis │
                    │ • Pattern Detection  │
                    └─────────────────────┘
```

---

## Module 1: AI Smart Router

### Vấn Đề Hiện Tại
Các DEX aggregator như 1inch dùng thuật toán tĩnh (Dijkstra, BFS) để tìm đường swap. Chúng tối ưu **tại thời điểm hiện tại** nhưng không dự đoán được:
- Gas price sẽ thay đổi trong 10 giây tới
- Slippage thực tế khi order được submit
- Pool nào sẽ bị drain bởi MEV bot

### Giải Pháp X18
**ML-Powered Pathfinder** — một model được train trên hàng triệu transactions lịch sử:

| Feature | Mô tả |
|:---|:---|
| **Gas Price Prediction** | LSTM model dự đoán gas trong 30s-5min tới |
| **Slippage Estimation** | Random Forest model ước tính slippage thực tế |
| **Liquidity Depth Scoring** | Real-time scoring of pool health & depth |
| **Multi-chain Arbitrage** | Phát hiện price differences cross-chain |
| **Execution Timing** | Tìm thời điểm tối ưu để submit transaction |

### Ví Dụ Thực Tế
```
User: "Swap 50 ETH → USDC"

Traditional Router:
  → Uniswap V3: 100% → $125,000
  → Slippage: 0.8%
  → Gas: $15
  → Net: $123,985

X18 Brain Router:
  → 60% Uniswap V3 + 30% Curve + 10% Balancer
  → Cross-chain: 15% via Arbitrum pool (deeper liquidity)
  → Timing: Wait 12 seconds (gas drop predicted)
  → Slippage: 0.15%
  → Gas: $8
  → Net: $124,782

  💰 Savings: $797 (+0.64%)
```

---

## Module 2: Risk Guardian

### Real-time Risk Dashboard
Mỗi position và portfolio được monitored bởi Risk Guardian:

```
╔═══════════════════════════════════════════╗
║           RISK GUARDIAN DASHBOARD         ║
╠═══════════════════════════════════════════╣
║                                           ║
║  Portfolio Health:  ██████████░░  83%     ║
║  Risk Level:        🟡 MODERATE           ║
║                                           ║
║  Positions:                               ║
║  ├─ ETH Long 5x    Risk: 🔴 HIGH         ║
║  │  └─ Liq. Price: $2,150 (12% away)     ║
║  ├─ BTC Perp 2x    Risk: 🟢 LOW          ║
║  │  └─ Liq. Price: $48,000 (35% away)    ║
║  └─ SOL Spot       Risk: 🟢 SAFE         ║
║                                           ║
║  ⚠️ ALERT: ETH volatility spike predicted ║
║     in next 2 hours. Consider reducing    ║
║     leverage or adding collateral.        ║
║                                           ║
║  🤖 AI Suggestion:                        ║
║     Add 2,000 USDC collateral to improve  ║
║     health factor from 1.2 → 1.8         ║
║     [Accept] [Customize] [Dismiss]        ║
║                                           ║
╚═══════════════════════════════════════════╝
```

### Risk Scoring Model
| Factor | Weight | Data Source |
|:---|:---:|:---|
| Leverage ratio | 25% | On-chain position data |
| Distance to liquidation | 25% | Real-time price feed |
| Market volatility | 20% | Historical + implied vol |
| Correlation risk | 15% | Cross-asset correlation matrix |
| Liquidity risk | 15% | Pool depth & withdrawal patterns |

---

## Module 3: MEV Protection Shield

### MEV Attack Types Chống Được

| Attack | Phương pháp bảo vệ |
|:---|:---|
| **Front-running** | Private mempool + commit-reveal scheme |
| **Sandwich Attack** | Deadline enforcement + slippage bounds |
| **Back-running** | Randomized execution timing |
| **JIT Liquidity** | Detection & warning system |
| **Time-bandit** | Multiple block confirmation |

### Cơ Chế Hoạt Động
```
1. User submits trade intent (signed, encrypted)
         │
2. X18 Brain analyzes MEV risk score
         │
3. If risk HIGH:
   ├── Route through private mempool
   ├── Apply commit-reveal (2-phase execution)
   └── Set tight deadline & slippage bounds
         │
4. If risk LOW:
   └── Direct execution with standard protection
         │
5. Post-trade MEV audit log (transparent)
```

---

## Module 4: Liquidation Shield

### Dự Đoán Thay Vì Phản Ứng

Hầu hết DEX chỉ **liquidate** khi đã quá muộn. X18 Brain **dự đoán** nguy cơ liquidation **trước 15 phút** và đưa ra các hành động phòng ngừa:

| Cấp độ | Trigger | Hành động |
|:---|:---|:---|
| 🟡 **Warning** | Health < 1.5 + vol spike predicted | Push notification + email |
| 🟠 **Critical** | Health < 1.2 | Auto-suggest: add collateral hoặc reduce position |
| 🔴 **Emergency** | Health < 1.05 (nếu user bật auto-protect) | Auto-partial-close 20% position để restore health |

**Opt-in Auto-Protect**: Người dùng có thể bật/tắt. Khi bật, AI tự động bảo vệ position thay vì để liquidation engine xử lý (tiết kiệm penalty fee).

---

## Module 5: Portfolio Pilot

### AI Portfolio Optimization
- **Auto-Rebalance** — Tự cân bằng portfolio theo target allocation
- **Yield Routing** — Tự tìm và chuyển liquidity đến pool có yield tốt nhất
- **Tax-Loss Harvesting** — Tự động realize loss để tối ưu thuế (opt-in)
- **Correlation Analysis** — Cảnh báo khi portfolio quá tập trung vào 1 sector

---

## Privacy & Data

> **Cam kết**: X18 Brain KHÔNG bao giờ lưu trữ private keys, seed phrases, hoặc giao dịch cá nhân. Tất cả AI models chạy trên aggregated, anonymized data. Người dùng có toàn quyền opt-in/opt-out mọi AI feature.

---

> **Tiếp theo:** [Cross-Chain Infrastructure →](cross-chain.md)
