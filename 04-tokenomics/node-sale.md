# Chương Trình Bán Node Ban Đầu

## X18 Node Sale — Gia Tăng Tài Sản Từ Ngày Đầu

Chương trình bán Node ban đầu cho phép người dùng **đầu tư sớm** vào hệ sinh thái X18ex, nhận quyền lợi đặc biệt, và bắt đầu mining $X18 tokens trước khi nền tảng chính thức ra mắt.

---

## Tổng Quan Chương Trình

| Thông tin | Chi tiết |
|:---|:---|
| **Thời gian bán** | **3 tháng** (đồng hồ đếm ngược trong dashboard) |
| **Giá tham chiếu $X18** | **$1.00 / token** |
| **Loại Node** | 3 gói: $1K, $5K, $10K |
| **Tổng số Node** | **2,300 gói** (hữu hạn, không phát sinh thêm) |
| **Sau khi hết hạn** | Node dừng hoạt động, không có gói nào phát sinh |
| **Node chưa bán hết** | **Đốt hoàn toàn** (burn) — tăng scarcity |

---

## Các Gói Node

```
╔══════════════════════════════════════════════════════════════════════════╗
║                      X18 NODE PACKAGES                                 ║
╠══════════════════════════════════════════════════════════════════════════╣
║                                                                        ║
║  ┌─────────────────────┐  ┌─────────────────────┐  ┌─────────────────┐ ║
║  │    🥉 GÓI $1K      │  │    🥈 GÓI $5K       │  │   🥇 GÓI $10K  │ ║
║  │                     │  │                      │  │                 │ ║
║  │  Giá: $1,000        │  │  Giá: $5,000         │  │  Giá: $10,000  │ ║
║  │  X18 Token: 1,000   │  │  X18 Token: 5,000    │  │  X18 Token:    │ ║
║  │                     │  │                      │  │  10,000        │ ║
║  │  Số lượng: 1,000 gói│  │  Số lượng: 1,000 gói │  │  Số lượng:     │ ║
║  │                     │  │                      │  │  300 gói       │ ║
║  │  Quyền lợi: V1     │  │  Quyền lợi: V2      │  │  Quyền lợi: V3 │ ║
║  │  Mining: 8%/tháng   │  │  Mining: 9%/tháng    │  │  Mining:        │ ║
║  │  Bonus: 0%          │  │  Bonus: 5%           │  │  10%/tháng     │ ║
║  │                     │  │                      │  │  Bonus: 10%    │ ║
║  └─────────────────────┘  └─────────────────────┘  └─────────────────┘ ║
║                                                                        ║
╚══════════════════════════════════════════════════════════════════════════╝
```

### Bảng Chi Tiết Quyền Lợi

| Thông tin | 🥉 Gói $1K | 🥈 Gói $5K | 🥇 Gói $10K |
|:---|:---:|:---:|:---:|
| **Giá mua** | $1,000 | $5,000 | $10,000 |
| **$X18 Token nhận được** | 1,000 | 5,000 | 10,000 |
| **Số lượng gói** | 1,000 gói | 1,000 gói | 300 gói |
| **Cấp quyền lợi** | V1 | V2 | V3 |
| **Mining rate** | 8% / tháng | 9% / tháng | 10% / tháng |
| **Bonus khi mua** | 0% | +5% (+250 X18) | +10% (+1,000 X18) |
| **Tổng X18 nhận** | 1,000 | **5,250** | **11,000** |

---

## Cơ Chế Hoạt Động

### 1. Mua Node
```
User mua gói Node ($1K / $5K / $10K)
         │
         ▼
X18 Tokens được phân bổ cho user
         │
         ▼
Toàn bộ tokens bị LOCK ❌
(Không thể rút, bán, hay chuyển)
         │
         ▼
Mining bắt đầu tự động ⛏️
```

### 2. Mining & Unlock
```
Mỗi tháng, user nhận mining rewards:
         │
         ├── Gói $1K:  8% × 1,000 =   80 X18/tháng
         ├── Gói $5K:  9% × 5,250 =  472.5 X18/tháng
         └── Gói $10K: 10% × 11,000 = 1,100 X18/tháng
         │
         ▼
Rewards được unlock và có thể:
  ✅ Giữ (HODL)
  ✅ Trade trên X18 DEX
  ✅ Stake để earn thêm
  ✅ Sử dụng trong X18 Game
```

### 3. Token Lock & Release
> **Quan trọng**: Toàn bộ $X18 Token khi mua gói ban đầu sẽ bị **LOCK** và chỉ trả % mỗi tháng thông qua cơ chế mining. Đây là thiết kế nhằm:
> - **Bảo vệ giá token** — Tránh dump ngay sau khi mua
> - **Cam kết dài hạn** — Incentivize holders giữ và tham gia ecosystem
> - **Phân phối đều** — Token được unlock dần, không gây áp lực sell

---

## Đồng Hồ Đếm Ngược

Chương trình bán Node có **đồng hồ đếm ngược** hiển thị trong dashboard mỗi user:

```
╔═══════════════════════════════════════════════════════╗
║              ⏱️ NODE SALE COUNTDOWN                   ║
╠═══════════════════════════════════════════════════════╣
║                                                       ║
║              67 NGÀY : 14 GIỜ : 32 PHÚT              ║
║                                                       ║
║  ┌─────────────────────────────────────────────────┐  ║
║  │ Gói $1K   ████████████░░░░░░  680/1,000 đã bán │  ║
║  │ Gói $5K   ██████████████░░░░  720/1,000 đã bán │  ║
║  │ Gói $10K  █████████████████░  255/300 đã bán   │  ║
║  └─────────────────────────────────────────────────┘  ║
║                                                       ║
║  📊 Tổng đã bán: 1,655 / 2,300 (71.9%)               ║
║                                                       ║
║  🔥 Node chưa bán sau 3 tháng → BURN vĩnh viễn       ║
║                                                       ║
║            [ Mua Node Ngay ]                          ║
╚═══════════════════════════════════════════════════════╝
```

---

## Quyền Lợi Theo Cấp (V1, V2, V3)

| Quyền lợi | V1 (Gói $1K) | V2 (Gói $5K) | V3 (Gói $10K) |
|:---|:---:|:---:|:---:|
| Mining $X18 monthly | ✅ 8% | ✅ 9% | ✅ 10% |
| Fee discount trên DEX | 10% | 25% | 40% |
| AI Premium access | ❌ | ✅ Basic | ✅ Full |
| Bot API Pro tier | ❌ | ✅ | ✅ |
| X18 Game VIP | ❌ | ✅ Silver | ✅ Gold |
| Governance voting | ✅ 1x | ✅ 1.5x | ✅ 2x |
| Private community access | ❌ | ✅ | ✅ |
| Priority support | ❌ | ❌ | ✅ |
| Early access to new features | ❌ | ✅ | ✅ |
| Exclusive airdrops | ❌ | ❌ | ✅ |

---

## Cơ Chế Đốt Node Chưa Bán

### Burn = Tăng Scarcity

Sau 3 tháng, tất cả gói Node **chưa bán** sẽ bị đốt hoàn toàn:

```
Ví dụ: Nếu chỉ bán được 1,800 / 2,300 gói:

Gói chưa bán: 500 gói
Token tương ứng: ~2,000,000 $X18 (ước tính)
         │
         ▼
🔥 BURN vĩnh viễn — Token không bao giờ tồn tại
         │
         ▼
Total Supply giảm từ 18,000,000 → ~16,000,000
         │
         ▼
💎 Scarcity tăng → Giá trị token tăng cho holders
```

> **Cam kết**: Không có cơ chế nào để mint lại những token đã burn. Smart contract đảm bảo tính bất biến.

---

## Tại Sao Nên Mua Node Sớm?

### 1. Giá Tham Chiếu $1
Giá ước tính $X18 tại giai đoạn bán Node là **$1.00/token**. Khi nền tảng mainnet launch và volume tăng, giá token sẽ được xác định bởi thị trường — tiềm năng upside đáng kể.

### 2. Mining Rewards
Node holders bắt đầu earn $X18 **ngay lập tức** thông qua mining, trước khi DEX mainnet ra mắt.

### 3. Early Adopter Benefits
Quyền lợi V1/V2/V3 là **vĩnh viễn** — fee discounts, AI access, và governance power không mất đi sau chương trình.

### 4. Burn Scarcity
Node chưa bán bị burn → supply thực tế thấp hơn 18M → favorable cho holders.

---

## Lưu Ý Quan Trọng

> ⚠️ **Disclaimer**
> - Cộng thêm % khi mua là quyền lợi người dùng nhận thêm % token khi mua gói
> - Toàn bộ $X18 Token khi mua gói ban đầu sẽ bị **LOCK** và chỉ trả % mỗi tháng
> - Số lượng các gói là **hữu hạn**, không phải vô hạn
> - Số lượng gói có bộ đếm để xem còn bao nhiêu gói tương ứng
> - Nếu không bán hết trong 3 tháng, token tương ứng sẽ **đốt hoàn toàn**
> - Node sẽ dừng hoạt động sau kỳ hạn và không có gói nào phát sinh thêm

---

> **Tiếp theo:** [Deflationary Mechanics →](deflationary.md)
