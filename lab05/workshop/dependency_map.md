NOW: Hội thoại vai trò
Vấn đề: Người học tiếng trung đang bị stuck ở việc giao tiếp thoải mái, và bắt được các tình huống đặt thù trong ngôn ngữ
Đang làm : Đang phát triển bộ dữ liệu chi tiết về các tình huống đặt thù trong giao tiếp tiếng trung, đặt biệt ở các lĩnh vực thương mại, kinh doanh và đàm phán + fine-tuning, RAG (Retrieval-Augmented Generation)model, VAD (Voice Activity Detection). Dự kiến 4.5 tháng. 

# 3 external dependencies: 
1. Sự thay đổi đột ngột về Policy hoặc Pricing của LLM API (OpenAI/Azure/Anthropic)
2. Sự bất ổn của hạ tầng kết nối quốc tế (Cáp quang biển) tại Việt Nam
3. Rào cản bản quyền và pháp lý về dữ liệu học thuật/thương mại

## Dependency 
### Sự thay đổi đột ngột về Policy hoặc Pricing của LLM API (OpenAI/Azure/Anthropic)
1. Worst-case scenario: Nếu nhà cung cấp thắt chặc việc nạp dữ liệu vào mô hình thì nguồn dữ liệu của ứng dụng sẽ không đầy đủ -> chất lượng output giảm nghiêm trọng. 
2. Plan B : chuyển sagn LLM3 và Qwen 2, Tự triển khai Fine-tuning trên hạ tầng riêng hoặc thuê GPU cloud linh hoạt để toàn quyền sở hữu dữ liệu huấn luyện.
3. Cost: 
Nhân lực: Cần thêm khoảng 2-4 tuần để AI Engineer cấu hình lại Pipeline từ API sang Local Model.  

Hạ tầng: Thuê GPU (như NVIDIA A100/H100) trên các nền tảng như RunPod hoặc Lambda Labs với giá khoảng $1.5 – $4.0/giờ trong giai đoạn huấn luyện.

### Sự bất ổn của hạ tầng kết nối quốc tế (Cáp quang biển) tại Việt Nam
1. Worst-case scenario: đường truyền bị ảnh hưởng thì từ 2-3s độ trễ sẽ tăng lên 10-15s, tệ hơn sẽ bị đứng ứng dụng khi mất kết nối hoàn toàn với máy chủ AI ở nước ngoài.
2. Plan B:
Thuê máy chủ GPU tại Việt Nam (ví dụ: VNG Cloud, Viettel IDC) để đặt các mô hình STT (Whisper) và TTS. Việc xử lý âm thanh ngay trong nước sẽ giảm thiểu ảnh hưởng khi đứt cáp.  Sử dụng cơ chế Hybrid Architecture: Các tác vụ nặng về ngôn ngữ vẫn gọi API quốc tế (nếu cáp ổn), nhưng khi gặp sự cố, hệ thống tự động chuyển sang mô hình "nhẹ" hơn chạy tại server Việt Nam để duy trì hội thoại cơ bản. 
3. Cost : 
Hạ tầng: Thuê Server GPU tại VN có chi phí cao hơn quốc tế, dao động khoảng 10,000,000 - 25,000,000 VNĐ/tháng tùy cấu hình.  

Kỹ thuật: Team cần dành 1-2 tuần để xây dựng logic tự động chuyển đổi (Failover mechanism) giữa hai hạ tầng.

### Rào cản bản quyền và pháp lý về dữ liệu học thuật/thương mại
1. Worst-case scenario: Nếu có vấn đề pháp lý, hoặc không rõ ràng thì sẽ ngăn chặn nền tảng được public tại appstore, googleplay. 
2. Plan B : 
Dữ liệu tổng hợp (Synthetic Data): Sử dụng LLM cao cấp để "tự tạo" ra các kịch bản hội thoại mới dựa trên cấu trúc của tài liệu gốc, thay vì sao chép trực tiếp, để đảm bảo tính nguyên bản (Originality).  

Hợp tác (Partnership): Ký kết thỏa thuận sử dụng nội dung với 1-2 trung tâm tiếng Trung hoặc chuyên gia đàm phán tại Việt Nam để có "giấy thông hành" bản quyền hợp pháp.
3. Cost : 
Phí bản quyền: Có thể chi trả theo hình thức Revenue Share (chia sẻ doanh thu 5-10%) hoặc trả phí một lần cho bộ dữ liệu (dao động 20,000,000 - 50,000,000 VNĐ).  

Pháp lý: Chi phí tư vấn luật sư hoặc dịch vụ đăng ký bản quyền/SHTT tại Việt Nam khoảng 5,000,000 - 15,000,000 VNĐ.


# Critical Path
# Critical Path — Giai đoạn NOW (Hội thoại vai trò)
> Lộ trình 4.5 tháng · Team 3 người · Mục tiêu: Public MVP

---

## Sơ đồ tổng quan

```
                            ┌─────────────┐
                            │  BẮT ĐẦU   │
                            └──────┬──────┘
                                   │
                    ╔══════════════▼══════════════╗  ⚠ RỦI RO CAO
                    ║  Legal-01: Rà soát &        ║
                    ║  Viết lại Synthetic Data    ║  Tuần 1–4
                    ║  Bắt buộc trước mọi bước AI ║
                    ╚══════════════╤══════════════╝
                                  │
              ┌───────────────────┴───────────────────┐
              │ (song song)                           │ (đường găng)
              ▼                                       ▼
  ┌───────────────────────┐           ╔═══════════════════════╗
  │ Data-01: Thu thập     │           ║ Data-02: Tiền xử lý & ║
  │ kịch bản thô          │           ║ chuẩn hóa dữ liệu     ║  Tuần 5–6
  │ Song song · Tuần 1–3  │           ║ Phụ thuộc Legal-01    ║
  └───────────┬───────────┘           ╚═══════════╤═══════════╝
              │                                   │
              │                    ┌──────────────┘
              │                    │
              │       ╔════════════▼════════════╗
              │       ║ AI-01: Fine-tuning Model ║
              │       ║ Tuần 7–12               ║  ◀─── M2 (Tháng 3.0)
              │       ║ Nhiệm vụ nặng nhất       ║       Model >80% ✓
              │       ╚════════════╤════════════╝
              │                   │
    ┌─────────┘         ┌─────────┘
    │ (merge vào)       │
    ▼                   ▼
┌──────────────┐  ╔═══════════════════════════╗
│ AI-02: RAG   │  ║ Tech-01: Pipeline         ║
│ Cần Data-02  │─▶║ Streaming STT→LLM→TTS     ║  Tuần 13–16
│ sạch         │  ║ Độ trễ mục tiêu <3–5s     ║  ◀─── M3 (Tháng 4.0)
└──────────────┘  ╚═══════════════╤═══════════╝       Latency <5s ✓
┌──────────────┐                  │
│ AI-03: VAD   │                  │
│ Nhận diện    │─▶                │
│ khoảng lặng  │  ╔═══════════════▼═══════════╗
└──────────────┘  ║ Tech-02: Failover Hybrid  ║
┌──────────────┐  ║ Cloud ↔ Local Server VN   ║  Tuần 17–18
│ App-01: UI   │  ║ Đảm bảo ổn định hạ tầng   ║
│ Mobile       │─▶╚═══════════════╤═══════════╝
│ Song song    │                  │
└──────────────┘  ╔═══════════════▼═══════════╗
                  ║ Test-01: Kiểm thử         ║
                  ║ End-to-End & Fix Bugs     ║  Tuần 19–20
                  ║ Đo phản xạ <3s            ║
                  ╚═══════════════╤═══════════╝
                                  │
                    ┌─────────────▼─────────────┐
                    │       PUBLIC MVP 🚀        │
                    └───────────────────────────┘
```

**Chú thích:** `╔═══╗` = Đường găng (critical) &nbsp;|&nbsp; `┌───┐` = Song song (non-critical) &nbsp;|&nbsp; `⚠` = Rủi ro cao

---

## Danh sách nhiệm vụ chi tiết

### 🔴 Đường găng (bắt buộc theo thứ tự)

| ID | Nhiệm vụ | Tuần | Phụ thuộc | Ghi chú |
|---|---|---|---|---|
| Legal-01 | Rà soát bản quyền & viết lại Synthetic Data | 1–4 | — | ⚠ Nút chặn toàn bộ pha AI |
| Data-02 | Tiền xử lý & chuẩn hóa dữ liệu Fine-tuning | 5–6 | Legal-01 | RAG cần dữ liệu sạch |
| AI-01 | Fine-tuning Model (thuật ngữ Business Chinese) | 7–12 | Data-02 | Nhiệm vụ nặng nhất, nhiều lần lặp |
| Tech-01 | Pipeline Streaming (STT → LLM → TTS) | 13–16 | AI-01, AI-02 | Tối ưu độ trễ <3–5s |
| Tech-02 | Failover Logic Cloud ↔ Local Server VN | 17–18 | Tech-01 | Chống mất kết nối cáp quang biển |
| Test-01 | Kiểm thử End-to-End & Fix Bugs | 19–20 | Tech-02 | Đo phản xạ <3s |

### 🟢 Song song (không ảnh hưởng ngày launch)

| ID | Nhiệm vụ | Chạy cùng | Merge vào |
|---|---|---|---|
| Data-01 | Thu thập & phân loại kịch bản thô | Legal-01 (T1–3) | AI-02 (làm input RAG) |
| AI-02 | Xây dựng hệ thống RAG (Vector DB) | AI-01 (T7–12) | Tech-01 |
| AI-03 | Tích hợp VAD (nhận diện khoảng lặng) | AI-01 (T7–12) | Tech-01 |
| App-01 | Phát triển giao diện UI Mobile | Toàn bộ dự án | Tech-02 |

---

## Milestones

| Milestone | Thời điểm | Nội dung | Tiêu chí đạt |
|---|---|---|---|
| **M1** | Tháng 1.5 | Legal-Clean Dataset hoàn tất | Dữ liệu sạch về pháp lý, sẵn sàng fine-tune |
| **M2** | Tháng 3.0 | Model Fine-tune đạt chuẩn | Độ chính xác thuật ngữ kinh doanh > 80% |
| **M3** | Tháng 4.0 | Pipeline Streaming ổn định | Độ trễ phản hồi < 3–5s trên hạ tầng Hybrid |

---

## Ràng buộc phụ thuộc

```
Legal-01  ──────────────────▶  AI-01
          (Dữ liệu phải sạch bản quyền trước khi fine-tune
           để tránh phải làm lại từ đầu)

Data-02   ──────────────────▶  AI-02
          (RAG cần corpus đã chuẩn hóa để truy xuất chính xác)

AI-01
  +       ──────────────────▶  Tech-01
AI-02     (Cần cả "bộ não" fine-tune lẫn knowledge base RAG
           trước khi tối ưu pipeline thực tế)

Tech-01   ──────────────────▶  Tech-02
          (Cần pipeline ổn định trước khi thiết lập failover)
```

---

## Lưu ý cho Product Lead

> **⚠ Điểm giám sát ưu tiên #1:** `Legal-01` (Tuần 1–4)
> Nếu bước này kéo dài quá 4 tuần, toàn bộ pha AI phía sau bị đóng băng.
> Đây là vị trí cần theo dõi sát nhất trong tháng đầu tiên.

- **App-01** (UI Mobile) chạy song song và thường hoàn thành sớm — không gây áp lực lên ngày ra mắt trừ khi có thay đổi thiết kế lớn.
- **AI-01** là nhiệm vụ tốn nhiều thời gian nhất và có nguy cơ trễ nếu chất lượng dữ liệu từ Data-02 chưa đạt.
- **Tech-02** nên được chuẩn bị hạ tầng từ sớm (song song với Tech-01) để không thành điểm nghẽn cuối cùng trước launch.