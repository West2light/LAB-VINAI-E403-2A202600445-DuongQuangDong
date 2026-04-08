# UX exercise — MoMo Moni AI

## Sản phẩm: MoMo — Moni AI Assistant (Phân loại & Quản lý chi tiêu)

---

## 4 paths

### 1. AI đúng
- **Scenario:** User hỏi: *"Chi tiêu tháng này của tôi?"*
- **Hệ thống:** Hiểu đúng intent, trả về tổng chi tiêu và breakdown theo category/thời gian.
- **User thấy:** Thông tin rõ ràng, đúng nhu cầu, tin tưởng vào AI.
- **Vấn đề (As-is):** Không có confirm, không biết AI lấy data từ đâu, không biết có thiếu dữ liệu không.
- 👉 **Nhận xét:** Trải nghiệm mượt nhưng thiếu explainability → trust chưa mạnh.

### 2. AI không chắc (🔥 Weakest path)
- **Scenario:** User hỏi mơ hồ: *"Chi tiêu gần đây?"* hoặc *"Tôi tiêu nhiều không?"*
- **Hệ thống hiện tại:** Vẫn trả lời ngay, không hỏi lại, không làm rõ thời gian/phạm vi.
- **User thấy:** Câu trả lời chung chung, không chắc có đúng ý mình không.
- **Vấn đề (As-is):** Không có clarifying question hay options (tuần/tháng/năm). AI "giả vờ chắc chắn".
- 👉 **Nhận xét:** Đây là điểm yếu nhất, gây sai hiểu và giảm trust.

### 3. AI sai
- **Scenario:** User hỏi: *"Chi tiêu từ 1/1/2024 đến nay"*. AI chỉ trả lời gần đây (24 tháng/năm gần nhất).
- **Hệ thống:** Không hiểu đúng yêu cầu, không báo "tôi không chắc".
- **User thấy:** Kết quả không khớp nhưng không rõ sai ở đâu. Phải hỏi lại hoặc tự xem thủ công.
- **Vấn đề (As-is):** Không có feedback "AI có thể sai", không có nút sửa nhanh.
- 👉 **Nhận xét:** Sai nhưng không minh bạch + khó sửa.

### 4. User mất niềm tin
- **Scenario:** AI trả lời sai nhiều lần, không đúng nhu cầu.
- **User hành động:** Tự đi xem lịch sử giao dịch, không dùng AI nữa.
- **Hệ thống:** Không có gợi ý chuyển sang manual, không có support rõ ràng. Chỉ có nút gọi tổng đài ẩn.
- **Vấn đề (As-is):** Exit không rõ ràng, không có cách "cứu trust".
- 👉 **Nhận xét:** User "silent drop" AI.

---

## ⚖️ Tổng kết & Insight

- **Best path:** Khi AI đúng → mượt, nhanh.
- **Worst path:** **Path 2 — Khi AI không chắc**. Vì không có clarification/confidence, dẫn đến sai và mất trust.
- **Insight cốt lõi:** 
> "Moni hoạt động tốt khi câu hỏi rõ ràng, nhưng thiếu cơ chế xử lý khi AI không chắc, dẫn đến việc AI trả lời sai nhưng vẫn tỏ ra tự tin, làm giảm niềm tin của người dùng."

---

## 🔍 Phân tích gap marketing vs thực tế

- **Marketing:** Quảng cáo Moni là "Trợ lý tài chính thông minh", "Tự động phân loại chi tiêu 100%", giúp người dùng thảnh thơi không cần ghi chép.
- **Thực tế:** 
    - Auto-tag chỉ chính xác với các giao dịch phổ biến (Circle K, Highland). Các giao dịch chuyển tiền cá nhân hoặc mua sắm online phức tạp thường bị tag vào "Khác" hoặc sai lệch.
    - AI thiếu khả năng "hỏi lại" (clarification) — một đặc điểm quan trọng của một "trợ lý" thực thụ.
- **Gap lớn nhất:** Marketing tạo kỳ vọng về một AI hoàn hảo (automation), trong khi thực tế sản phẩm đang ở mức Augmentation nhưng lại thiếu các công cụ để User hỗ trợ AI (feedback loop).

---

## 🎨 Sketch (As-is & To-be)

### 🟥 AS-IS (Hiện tại - Chỗ gãy cần khoanh tròn)
```text
User hỏi: "Chi tiêu gần đây?"
        ↓
AI hiểu mơ hồ (không chắc)
        ↓
AI vẫn trả lời luôn (Giả vờ chắc chắn)
        ↓
Hiển thị 1 kết quả duy nhất (vd: tháng này)
        ↓
User hoang mang: "Có đúng ý không? Có thiếu data không?"
        ↓
→ 🔴 Chỗ gãy: Không hỏi lại, không có lựa chọn, không có confidence state.
```

### 🟩 TO-BE (Đề xuất cải thiện)
```text
User hỏi: "Chi tiêu gần đây?"
        ↓
AI detect: intent chưa rõ (low confidence)
        ↓
AI hỏi lại (Clarification):
"Bạn muốn xem trong khoảng nào?"
[7 ngày] [30 ngày] [Tháng này] [Tùy chọn]
        ↓
User chọn (1 tap)
        ↓
AI trả lời đúng context + Hiển thị Breakdown rõ ràng
        ↓
✨ (Optional - Data Flywheel):
"Bạn thường xem 30 ngày → lần sau mình dùng mặc định này nhé"
```

---

## ✨ Điểm nhấn cải tiến (Ghi chú cho Sketch)

- **➕ Thêm:** Clarifying question (hỏi lại), Quick options (buttons), Confidence state (ngầm hoặc hiện).
- **➖ Bớt:** AI tự động trả lời khi chưa chắc chắn.
- **🔄 Đổi:** Từ **AI quyết định** → **AI + User cùng quyết định**.

---

## 🚀 Câu chốt & Bonus Insight

> "Thay vì đoán, AI nên hỏi lại khi không chắc — chỉ cần 1 tap là đủ để tăng độ chính xác và build trust."

> "Thiết kế này giúp đóng vòng data flywheel bằng cách đưa user vào loop, thay vì chỉ thu thập dữ liệu thụ động."
