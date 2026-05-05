# Smart Contract Security

## An Ninh Mã Nguồn — Ưu Tiên Hàng Đầu

### Nguyên Tắc Security-First
1. **Audit before deploy** — Không code nào lên mainnet mà chưa audit
2. **Defense in depth** — Nhiều lớp bảo vệ chồng lên nhau
3. **Minimal attack surface** — Smart contracts tối giản, modular
4. **Transparency** — Open source, verifiable on-chain

---

## Audit Strategy

| Phase | Audit Firm(s) | Scope |
|:---|:---|:---|
| **Pre-Testnet** | Internal security review | All contracts |
| **Pre-Mainnet #1** | Tier-1 auditor (e.g., Trail of Bits) | Core engine + token |
| **Pre-Mainnet #2** | Tier-1 auditor (e.g., OpenZeppelin) | Cross-chain + margin |
| **Pre-Mainnet #3** | Tier-1 auditor (e.g., Certora) | Formal verification |
| **Ongoing** | Bug bounty program | All deployed contracts |

---

## Security Features

| Feature | Implementation |
|:---|:---|
| **Timelock** | 48h delay trên mọi upgrades |
| **Multi-sig** | 3/5 → 5/9 multi-sig cho admin functions |
| **Emergency Pause** | Circuit breaker khi phát hiện anomaly |
| **Reentrancy Guard** | OpenZeppelin ReentrancyGuard trên mọi function |
| **Access Control** | Role-based, không có God Keys |
| **Formal Verification** | Mathematical proof cho critical paths |
| **Flash Loan Guard** | Protection against flash loan exploits |

---

## Bug Bounty Program

| Severity | Bounty |
|:---|:---|
| **Critical** (fund loss, consensus failure) | Up to $500,000 |
| **High** (temporary freeze, logic error) | Up to $50,000 |
| **Medium** (data leak, minor exploit) | Up to $10,000 |
| **Low** (UI bug, info disclosure) | Up to $1,000 |

Platform: Immunefi (hoặc tương đương)

---

> **Tiếp theo:** [Operational Security →](operational-security.md)
