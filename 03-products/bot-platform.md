# X18 Bot Platform

## Bot-First Architecture: Built for Developers from Day One

Over **60% of volume** on leading DEXs comes from bots and automated strategies. X18ex does not consider bot integration as a secondary feature — it is a **core pillar** of the platform.

---

## Developer Portal

### Overview
```
┌─────────────────────────────────────────────────────────────┐
│                   X18 DEVELOPER PORTAL                      │
│                                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌────────────┐  │
│  │ API Keys │  │ Usage    │  │ Error    │  │ Webhook    │  │
│  │ Manage   │  │ Analytics│  │ Logs     │  │ Config     │  │
│  └──────────┘  └──────────┘  └──────────┘  └────────────┘  │
│                                                             │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌────────────┐  │
│  │ SDK      │  │ Sandbox  │  │ Strategy │  │ Backtest   │  │
│  │ Docs     │  │ Testing  │  │ Templates│  │ Engine     │  │
│  └──────────┘  └──────────┘  └──────────┘  └────────────┘  │
│                                                             │
│  Rate Limits: 1,000 req/min (Free) │ 10,000 (Pro $X18)     │
│  WebSocket Streams: 50 (Free) │ 500 (Pro)                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## APIs

### REST API v2
```
Base URL: https://api.x18ex.com/v2/

Endpoints:
├── /markets          — List all trading pairs
├── /orderbook/{pair} — Real-time order book
├── /trades/{pair}    — Recent trades
├── /ticker           — 24h price statistics
├── /account/balances — Portfolio balances (auth)
├── /orders           — Create/cancel orders (auth)
├── /positions        — Perpetual positions (auth)
├── /history          — Trade history (auth)
└── /ai/route         — AI-powered trade routing (auth)
```

### WebSocket Feeds
```
ws://stream.x18ex.com/v2/

Channels:
├── orderbook@{pair}   — Live order book updates
├── trades@{pair}      — Real-time trade stream
├── ticker@{pair}      — Price ticker updates
├── account            — Balance & position changes
├── fills              — Order fill notifications
└── liquidations       — Market liquidation events
```

### Webhook System
```json
{
  "event": "order.filled",
  "data": {
    "orderId": "x18_ord_abc123",
    "pair": "ETH/USDC",
    "side": "buy",
    "price": 2500.00,
    "amount": 10.0,
    "fee": 0.025,
    "timestamp": "2026-09-15T10:30:00Z"
  }
}
```

Events: `order.filled`, `order.cancelled`, `position.liquidated`, `position.warning`, `price.alert`, `strategy.signal`

---

## SDKs

| Language | Status | Primary Use Case |
|:---|:---|:---|
| **Python** | ✅ Production | Quant trading, data analysis, ML strategies |
| **TypeScript/JavaScript** | ✅ Production | Web bots, dApp integrations |
| **Rust** | ✅ Production | High-frequency trading, low-latency |
| **Go** | 🔄 Beta | Microservices, backend integrations |

### Code Example (Python SDK)
```python
from x18ex import Client

client = Client(api_key="your_key", secret="your_secret")

# Get best route for swap
route = client.ai_route(
    from_token="ETH",
    to_token="USDC",
    amount=10.0,
    chain="auto"  # AI selects optimal chain
)
print(f"Best price: {route.price}, savings: {route.savings_pct}%")

# Execute
tx = client.execute_route(route, slippage=0.5)
print(f"Tx hash: {tx.hash}")
```

---

## Strategy Templates

### Pre-built Strategies (1-click deploy)

| Strategy | Description | Risk |
|:---|:---|:---:|
| **Grid Trading** | Buy low, sell high within a range | 🟢 Low |
| **DCA Bot** | Automatic dollar-cost averaging | 🟢 Low |
| **TWAP Executor** | Split large orders over time | 🟢 Low |
| **Arbitrage Scanner** | Cross-DEX/cross-chain price differences | 🟡 Medium |
| **Momentum Rider** | Follow trend based on indicators | 🟡 Medium |
| **Sniper Bot** | Early entry into new listings | 🔴 High |
| **Liquidation Hunter** | Identify and execute liquidation opportunities | 🔴 High |

### Custom Strategy Builder
- **X18Script** — Simple Domain-Specific Language:
```
WHEN price("ETH/USDC") crosses_above SMA(50)
AND volume > avg_volume * 2
AND rsi < 70
THEN buy("ETH/USDC", amount=portfolio.balance * 0.1, type="limit", offset=-0.5%)
```

---

## Strategy Marketplace

### Operating Model
- Developers publish strategies on the marketplace
- Users subscribe (free or paid in $X18)
- Revenue sharing: **70% creator / 20% protocol / 10% burn**
- Transparent performance tracking: PnL, drawdown, Sharpe ratio

### Backtesting Engine
- Test strategies on **3 years of historical data**
- Simulate gas costs, slippage, MEV impact
- Monte Carlo simulations for risk assessment

### Paper Trading Mode
- Real-time market data, zero real money
- Test strategies before live deployment
- Leaderboard for paper trading

---

## Bot Performance Leaderboard

```
╔═══════════════════════════════════════════════════════════════╗
║                   🏆 BOT LEADERBOARD                        ║
╠═══════════════════════════════════════════════════════════════╣
║  #  │ Strategy         │ 30d Return │ Sharpe │ Max DD │ Subs ║
║  1  │ AlphaGrid Pro    │ +18.5%     │ 2.8    │ -4.2%  │ 1.2K ║
║  2  │ MomentumX        │ +15.2%     │ 2.3    │ -7.1%  │ 890  ║
║  3  │ CrossArb v3      │ +12.8%     │ 3.1    │ -2.1%  │ 2.3K ║
║  4  │ DCA Master       │ +8.4%      │ 1.9    │ -3.5%  │ 5.6K ║
║  5  │ SmartDIP         │ +7.2%      │ 1.7    │ -5.8%  │ 3.1K ║
╚═══════════════════════════════════════════════════════════════╝
```

---

> **Next:** [AI Trading Assistant →](ai-assistant.md)