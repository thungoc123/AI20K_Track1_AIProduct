# NguyenThiNgocThu_Milestone1_InvestorPackage

## Trang 1: Cover + Twitter Pitch

### Twitter Pitch

**Bọn em là ChinTalk AI. Bọn em giúp người đi làm VN giải quyết việc giỏi ngữ pháp nhưng "câm" giao tiếp bằng AI Partner có độ trễ <2s, dùng engine Qwen-2 hiểu sâu sắc thái bản địa.**

- Pilot 100 user: 85% phản xạ dưới 3s không dịch nhẩm. LTV/CAC = 4.5x, payback 5 tháng.
- Gọi $150K Seed để đạt 10K paid users trong 12 tháng.

---

## Trang 2-5: Pitch Memo + Market + PRD

### Pitch Memo (ChinTalk AI)
1. THE PROBLEM
Người đi làm (22-40 tuổi) tại Việt Nam thường xuyên rơi vào trạng thái "câm" khi giao tiếp thực tế với đối tác Trung Quốc dù có nền tảng ngữ pháp tốt. Tần suất lặp lại hàng ngày này gây rào cản lớn trong việc thăng tiến và gây thiệt hại trực tiếp đến hiệu quả đàm phán, giao thương.

2. THE INSIGHT
Phần lớn thị trường nhầm lẫn rằng người học cần thêm "kiến thức", nhưng thực tế họ chỉ cần "phản xạ không áp lực" để phá vỡ rào cản tâm lý ngại nói sai. Việc phân tích dữ liệu từ dự án Moni trước đây giúp tôi nhận ra rằng sự đứt gãy trong trải nghiệm người dùng thường đến từ việc thiếu tích hợp các tín hiệu mục tiêu thực tế vào quá trình luyện tập.

3. THE SOLUTION
Sản phẩm: Một AI Speaking Partner di động tập trung duy nhất vào việc luyện phản xạ nói tự nhiên thông qua các kịch bản hội thoại công việc thực tế.

Differentiator: Khác với ChatGPT, chúng tôi sử dụng engine AI nội địa Trung Quốc để giải mã chính xác các hàm ý, từ lóng và sắc thái biểu đạt đặc thù trong kinh doanh.

AI giúp như thế nào: AI đóng vai trò một người bạn không phán xét, phản hồi dưới 2 giây để người dùng hình thành phản xạ nói mà không cần dịch nhẩm trong đầu.

4. WHY NOW
Các mô hình ngôn ngữ lớn (LLM) như Qwen-2 hiện nay đã đạt đến độ chín muồi về khả năng hiểu tiếng Trung bản địa với chi phí API tối ưu. Đồng thời, hành vi người dùng đã dịch chuyển sang học tập linh hoạt (mobile-first) trong các khung giờ vụn vặt thay vì đến trung tâm truyền thống.

5. TRACTION / PROOF
Pilot: Đã thử nghiệm trên 100 người dùng đi làm, đạt 85% tỷ lệ phản xạ dưới 3 giây ngay trong tuần đầu tiên.

Aha moment: Người dùng nhận ra sự thay đổi khi có thể đối đáp các câu chứa hàm ý phức tạp mà không bị ngắt quãng.

Kinh tế: Dự kiến LTV/CAC đạt 4.5x với thời gian hoàn vốn (payback) trong vòng 5 tháng dựa trên mô hình SaaS.

6. THE ASK
Chúng tôi đang tìm kiếm $150,000 (Vòng Seed) để hoàn thiện hạ tầng kỹ thuật và tối ưu hóa Data Flywheel. Mục tiêu trong 12 tháng tới là đạt mốc 10.000 người dùng trả phí và chiếm lĩnh phân khúc luyện nói tiếng Trung cho người đi làm tại Việt Nam.

---

### Market Analysis + PRD (trích từ PRD_skeleton_draft.md)

#### 1. Problem Statement
Người đi làm (22–40 tuổi) học tiếng Trung tại Việt Nam, có nền tảng ngữ pháp/từ vựng nhưng "câm" khi giao tiếp thực tế, do thiếu môi trường luyện nói không áp lực. Điều này khiến họ không đạt hiệu quả sử dụng tiếng Trung trong công việc hoặc giao thương.

#### 2. Target User
Người đi làm (22–40 tuổi) học tiếng Trung tại Việt Nam, tranh thủ thời gian rảnh (giờ nghỉ trưa, sau khi con cái đi ngủ), mong muốn phản xạ tự nhiên, không cần dịch nhẩm, phát âm chuẩn hơn.

#### 3. User Stories
- As a busy office worker learning Chinese, I want to practice speaking with an always-available, non-judgmental partner, so that I can improve my pronunciation and fluency without feeling embarrassed.
- As a Vietnamese professional, I want to fit short speaking practice sessions into my fragmented schedule, so that I can gradually build natural reflexes for real-life conversations.

#### 4. MVP Scope
**In-Scope:**
- Có thể nghe được người dùng nói và bắt đầu được cuộc trò chuyện trôi chảy theo một chủ đề cụ thể.

**Out-of-Scope:**
- AI sàng lọc ra những lỗi của người dùng khi nói chuyện và recommend họ theo hướng tốt hơn.

**Non-Goals:**
- Dạy kiến thức về tiếng Trung.
- Phổ cập nội dung hay đa dạng các nội dung như đọc/viết.

#### 5. Success Metrics
- Tỷ lệ người dùng trả lời tiếng Trung dưới 3 giây mà không cần dịch nhẩm trong đầu.
- Số lần luyện nói/ngày.
- Mức độ tự tin khi giao tiếp thực tế (qua khảo sát hoặc phản hồi).

#### 6. Dependencies & Constraints
**Kỹ thuật & Công nghệ:**
- STT Engine: Cần API nhận diện giọng nói tiếng Trung độ trễ thấp, nhận tốt giọng Việt (Whisper, Google STT, iFlytek).
- TTS Engine: Giọng đọc AI tự nhiên, phù hợp hội thoại (Azure, ElevenLabs).
- LLM: Phản hồi giữ ngữ cảnh, dùng từ vựng business Chinese.
- Độ trễ toàn hệ thống (STT→LLM→TTS) không vượt 2 giây.

**Dữ liệu & Nội dung:**
- Bộ kịch bản hội thoại thực tế công việc tại Việt Nam.
- Cơ sở dữ liệu âm thanh phát âm chuẩn (Pinyin, Tones).

---

## Trang 6-7: Financial + Unit Economics

**[Chưa có file chi tiết về Financial Model, Unit Economics, LTV, CAC, Payback. Cần bổ sung file Excel và nội dung chi tiết.]**

---

## Trang 8: Roadmap + OKRs

**[Chưa có file Roadmap, OKRs. Cần bổ sung nội dung chi tiết cho phần này.]**

---

## Trang 9: Dependency + Critical Path

**[Chưa có file Dependency Map, Critical Path. Cần bổ sung nội dung chi tiết cho phần này.]**

---

## Phụ lục
- Link file Excel chi tiết Day 18: [Chưa có file]
- Link file PRD đầy đủ Day 17: [lab02/PRD_skeleton_draft.md]

---

*Ghi chú: Các phần thiếu sẽ được liệt kê chi tiết trong file TasksToComplete.md*
