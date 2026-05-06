
| Tính năng             | Mục tiêu giải quyết         | Độ ưu tiên        |
|-----------------------|-----------------------------|-------------------|
| Hội thoại vai trò     | Ngữ cảnh thực tế           | Cao              |
| Gợi ý phản xạ         | Phản hồi < 3 giây           | Cao              |
| Hội thoại rảnh tay    | Tận dụng thời gian rảnh    | Trung            |
| Tiếp nối hội thoại    | Lịch trình bận rộn         | Trung            |
| Quản lý độ trễ        | Trải nghiệm người dùng     | Cao (Kỹ thuật)    |



**Giả sử:** 200 user active  
**Team:** 3 người

### Thông số RICE cho từng tính năng

| Tính năng              | Reach (R) | Impact (I) | Confidence (C) | Effort (E)         |
|------------------------|-----------|------------|----------------|--------------------|
| Hội thoại vai trò      | 200       | 3          | 100            | 4.5 (3m x 1.5)     |
| Gợi ý phản xạ          | 180       | 2          | 80             | 1.5 (1m x 1.5)     |
| Hội thoại rảnh tay     | 60        | 1          | 50             | 2.25 (1.5m x 1.5)  |
| Quản lý độ trễ         | 200       | 2          | 50             | 3                  |

**Ghi chú:**
- Reach: Số lượng người dùng bị ảnh hưởng
- Impact: Mức độ tác động (1-3)
- Confidence: Độ tin cậy (%)
- Effort: Công sức (tháng, đã nhân hệ số)

​
 
Tính cho từng tính năng:

Hội thoại vai trò: (200 × 3 × 100) / 4.5 = 13,333.33
Gợi ý phản xạ: (180 × 2 × 80) / 1.5 = 19,200
Hội thoại rảnh tay: (60 × 1 × 50) / 2.25 = 1,333.33
Quản lý độ trễ: (200 × 2 × 50) / 3 = 6,666.67

## Bảng RICE Score (từ cao xuống thấp)

| Tính năng            | RICE Score  |
|----------------------|------------|
| Gợi ý phản xạ        | 19,200     |
| Hội thoại vai trò    | 13,333.33  |
| Quản lý độ trễ       | 6,666.67   |
| Hội thoại rảnh tay   | 1,333.33   |

high value - high effort: 
# Tài liệu Phân tích Ưu tiên Tính năng - Dự án AI Học Tiếng Trung

## 1. Ma trận Value vs. Effort (Dựa trên mô hình Quick Wins)

| | **Effort: LOW** | **Effort: HIGH** |
| :--- | :--- | :--- |
| **Value: HIGH** | **[QUICK WINS]**<br>Làm ngay — lấy đà<br>• **Gợi ý từ khóa & Cấu trúc (Think in Chinese)** | **[STRATEGIC BETS]**<br>Đầu tư dài hạn = moat (lợi thế)<br>• **Hội thoại ngắt lời (Interruptible)** |
| **Value: LOW** | **[FILL-INS]**<br>Làm khi rảnh<br>•  **Lưu trạng thái hội thoại** | **[NON-STARTERS]**<br>VỨT vào sọt rác<br>• **Tối ưu độ trễ tuyệt đối < 1s (giai đoạn đầu)** |

---

## 2. Chi tiết 5 tính năng quan trọng

### 1. AI Conversation Persona (Hội thoại theo vai trò)
* **Phân loại:** Quick Win (Thiên về Content/Prompt)
* **Mô tả:** Giả lập đối tác, đồng nghiệp, khách hàng Trung Quốc.

### 2. "Think in Chinese" Mode (Gợi ý từ khóa & Cấu trúc)
* **Phân loại:** Quick Win
* **Mô tả:** Hiển thị 3-5 từ khóa gợi ý để người dùng phản xạ dưới 3 giây.
* **Effort:** ~1 tháng (Team 3 người).

### 3. Voice-First Interruptible Dialogue (Hội thoại ngắt lời)
* **Phân loại:** Strategic Bet
* **Mô tả:** AI tự nhận diện giọng nói và dừng lại khi bị ngắt lời.
* **Effort:** ~1.5 tháng (Kỹ thuật streaming/VAD phức tạp).

### 4. Fragmented Progress Sync (Tiếp nối hội thoại)
* **Phân loại:** Fill-ins
* **Mô tả:** Lưu ngữ cảnh để người dùng bận rộn có thể học tiếp bất cứ lúc nào.

### 5. Adaptive Latency Management (Quản lý độ trễ)
* **Phân loại:** Strategic Bet
* **Mô tả:** Tối ưu luồng dữ liệu để phản hồi đạt mức < 3s (khi đã ổn định mức 6s).
* **RICE Score:** ~333.

---
*Tài liệu được thiết kế cho Product Lead dự án App tiếng Trung.*