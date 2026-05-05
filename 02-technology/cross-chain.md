# Cross-Chain Infrastructure

## Chain Abstraction: Người Dùng Không Cần Biết Chain

X18ex triển khai kiến trúc **Chain Abstraction** — người dùng chỉ thấy assets và markets, không cần quan tâm chúng nằm trên chain nào.

---

## Intent-Based Cross-Chain Protocol

```
┌──────────────────────────────────────────────────────┐
│                  USER EXPERIENCE                     │
│                                                      │
│  "Swap 10 ETH → USDC at best price"                │
│  (User doesn't know ETH is on Arbitrum,             │
│   best USDC pool is on Base)                        │
│                                                      │
└─────────────────────┬────────────────────────────────┘
                      │
┌─────────────────────▼────────────────────────────────┐
│              X18 INTENT RESOLVER                     │
│                                                      │
│  1. Parse user intent                                │
│  2. Scan liquidity: Ethereum, Arbitrum, Base, BSC    │
│  3. Calculate: direct swap vs cross-chain route      │
│  4. Factor: gas, slippage, bridge risk, speed        │
│  5. Present best option to user                      │
│                                                      │
│  Result: Split 70% Arbitrum + 30% Base               │
│  Savings: 0.4% better vs single-chain                │
│                                                      │
└─────────────────────┬────────────────────────────────┘
                      │
┌─────────────────────▼────────────────────────────────┐
│           RESOLVER NETWORK (Execution)               │
│                                                      │
│  Professional market makers compete to fill          │
│  the intent at or better than quoted price.          │
│                                                      │
│  • Dutch auction mechanism                           │
│  • Staked $X18 as collateral                         │
│  • Slashing for failed fills                         │
│                                                      │
└─────────────────────┬────────────────────────────────┘
                      │
┌─────────────────────▼────────────────────────────────┐
│             SETTLEMENT & VERIFICATION                │
│                                                      │
│  On-chain escrow contracts on both chains            │
│  Atomic settlement: both sides or neither            │
│  No custodial risk, no bridge token exposure         │
│                                                      │
└──────────────────────────────────────────────────────┘
```

---

## Supported Chains

### Ngày 1 — Launch Chains

| Chain | Type | TVL | Lý do |
|:---|:---|:---|:---|
| **Ethereum** | L1 | $100B+ | Liquidity king, institutional trust |
| **Arbitrum** | L2 | $15B+ | DeFi hub, low gas, fast |
| **Base** | L2 | $10B+ | Coinbase ecosystem, retail growth |
| **BSC** | L1 | $8B+ | Massive volume, low cost |
| **Polygon** | L2 | $5B+ | Enterprise adoption |

### Tháng 6-12 — Expansion

| Chain | Type | Lý do |
|:---|:---|:---|
| **Solana** | L1 (non-EVM) | Speed champion, growing DeFi |
| **Avalanche** | L1 | Institutional DeFi, subnets |
| **Optimism** | L2 | Superchain ecosystem |

### Năm 2 — Full Coverage
Sei, Mantle, Blast, zkSync, Scroll, Linea, Aptos, Sui

---

## Unified Liquidity Pool

Thay vì mỗi chain có liquidity riêng biệt, X18ex tạo **Unified Liquidity Layer**:

```
Traditional:
  ETH/USDC on Arbitrum: $50M liquidity
  ETH/USDC on Base:     $20M liquidity
  ETH/USDC on BSC:      $30M liquidity
  → User on Arbitrum chỉ access $50M

X18ex Unified:
  ETH/USDC across all chains: $100M unified liquidity
  → User on ANY chain access toàn bộ $100M
  → Slippage giảm 3-5x cho large trades
```

---

## Security Model

### Không Dùng Traditional Bridge

X18ex **KHÔNG** dùng lock-and-mint bridge truyền thống (nguồn gốc của >$2.5B bị hack). Thay vào đó:

| Traditional Bridge | X18 Cross-Chain |
|:---|:---|
| Lock tokens on Chain A | Intent signed by user |
| Mint wrapped tokens on Chain B | Resolvers fill on target chain |
| ❌ Wrapped tokens = custodial risk | ✅ Native tokens, no wrapping |
| ❌ Bridge contract = honeypot | ✅ Escrow with atomic settlement |
| ❌ Single point of failure | ✅ Distributed resolver network |

### Fallback & Safety

- **Timeout Protection**: Nếu fill không hoàn tất trong 10 phút → auto-refund
- **Resolver Insurance**: Resolvers stake $X18 → slashed nếu failed fill
- **Multi-sig Escrow**: Escrow contracts được audit, multi-sig upgradeable

---

> **Tiếp theo:** [MEV Protection & Security →](mev-protection.md)
