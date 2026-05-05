# Smart Aggregation

## Tìm Giá Tốt Nhất Trên Mọi Chain, Mọi Nguồn

X18 Route là engine aggregation quét **200+ liquidity sources** trên **10+ chains** để đảm bảo người dùng luôn nhận được giá tốt nhất có thể.

---

## So Sánh Với Đối Thủ

| Feature | 1inch | Jupiter | X18ex |
|:---|:---:|:---:|:---:|
| EVM Aggregation | ✅ | ❌ | ✅ |
| Solana Aggregation | ❌ | ✅ | ✅ |
| Cross-chain routing | ✅ (Fusion+) | ❌ | ✅ |
| AI-powered routing | ❌ | ❌ | ✅ |
| Gasless execution | ✅ | ❌ | ✅ |
| MEV Protection | ✅ | Partial | ✅ |
| Integrated spot/perp | ❌ | ✅ | ✅ |

---

## Liquidity Sources

### DEX Protocols
Uniswap V2/V3/V4, SushiSwap, Curve, Balancer, PancakeSwap, Trader Joe, Velodrome, Aerodrome, Raydium, Orca, và 190+ protocols khác.

### Private Liquidity
- Professional market makers (RFQ system)
- OTC desks for large trades
- X18 native pools

### Cross-chain Sources
- Tất cả DEX trên mọi supported chain
- Bridge liquidity pools
- Resolver network fill capacity

---

## Intent-Based Execution

### Flow
```
1. User: "Buy 100 ETH with my USDC, best price"
         │
2. X18 Brain: Scan all sources, all chains
         │
3. Options presented:
   ├── Option A: 100% on Arbitrum — $250,050 — ⚡ 2s
   ├── Option B: 70% Arb + 30% Base — $249,800 — ⏱️ 15s
   └── Option C: AI Optimized — $249,650 — ⏱️ 8s ★ Recommended
         │
4. User selects → Resolver network executes
         │
5. Settlement → Tokens in user wallet
```

### Gasless Mode
- Người dùng KHÔNG cần giữ native token (ETH, BNB) cho gas
- Gas được trả bởi resolvers, tính vào giá swap
- Đặc biệt hữu ích cho cross-chain: không cần gas token trên chain đích

---

> **Tiếp theo:** [X18 Bot Platform →](bot-platform.md)
