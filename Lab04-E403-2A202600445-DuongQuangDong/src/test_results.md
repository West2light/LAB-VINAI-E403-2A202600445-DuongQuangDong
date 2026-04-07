# BÁO CÁO KẾT QUẢ THỬ NGHIỆM TRAVELBUDDY AGENT

**Sinh viên:** Dương Quang Đông  
**MSSV:** 2A202600445

---

## 📋 TỔNG QUAN CÁC TEST CASES

| STT | Kịch bản Test                   | Mục tiêu                                     |    Kết quả    |
| :-: | :------------------------------ | :------------------------------------------- | :-----------: |
|  1  | Chào hỏi & Chưa rõ điểm đến     | Kiểm tra khả năng dẫn dắt của Agent          | ✅ Thành công |
|  2  | Tìm kiếm chuyến bay đơn lẻ      | Kiểm tra Single Tool Call (`search_flights`) | ✅ Thành công |
|  3  | Lên kế hoạch trọn gói (Chained) | Kiểm tra Multi-step Tool Chaining & Budget   | ✅ Thành công |
|  4  | Thiếu thông tin điểm đến        | Kiểm tra khả năng hỏi lại (Clarification)    | ✅ Thành công |
|  5  | Yêu cầu ngoài phạm vi hỗ trợ    | Kiểm tra Guardrails (Từ chối đúng quy định)  | ✅ Thành công |

---

## 🔍 CHI TIẾT CÁC KỊCH BẢN

### 1️⃣ Test 1: Chào hỏi & Chưa rõ điểm đến

**User:** "Xin chào! Tôi đang muốn đi du lịch nhưng chưa biết đi đâu."

**Hành động của Agent:**
- `---> Trả lời trực tiếp`

**Kết quả:**
> **TravelBuddy:** Chào bạn! Thật tuyệt khi nghe bạn muốn đi du lịch. Để mình giúp bạn chọn điểm đến phù hợp, bạn có thể cho mình biết một số thông tin sau không?
>
> 1. Bạn muốn đi trong khoảng thời gian nào?
> 2. Bạn thích những hoạt động gì (biển, núi, văn hóa, ẩm thực...)?
> 3. Ngân sách dự kiến cho chuyến đi khoảng bao nhiêu?
>
> Với những thông tin này, mình sẽ tìm ra những gợi ý hoàn hảo cho bạn!

---

### 2️⃣ Test 2: Single Tool Call

**User:** "Tìm giúp tôi chuyến bay từ Hà Nội đi Đà Nẵng"

**Hành động của Agent:**
- `---> Gọi tool: search_flights({'origin': 'Hà Nội', 'destination': 'Đà Nẵng'})`
- `---> Trả lời trực tiếp`

**Kết quả:**
> **TravelBuddy:** Dưới đây là một số lựa chọn chuyến bay từ Hà Nội đi Đà Nẵng:
>
> #### ✈️ Danh sách chuyến bay:
> 1. **Vietnam Airlines** | 06:00 - 07:20 | **1.450.000đ** (economy)
> 2. **Vietnam Airlines** | 14:00 - 15:20 | **2.800.000đ** (business)
> 3. **VietJet Air** | 08:30 - 09:50 | **890.000đ** (economy)
> 4. **Bamboo Airways** | 11:00 - 12:20 | **1.200.000đ** (economy)
>
> Bạn có muốn mình tìm thêm khách sạn tại Đà Nẵng phù hợp với ngân sách của bạn không?

---

### 3️⃣ Test 3: Multi-Step Tool Chaining (Tư vấn trọn gói)

**User:** "Tôi đang ở Hà Nội, muốn đi Phú Quốc 2 đêm, budget 5 triệu. Tư vấn giúp!"

**Hành động của Agent:**
- `---> Gọi tool: search_flights({'origin': 'Hà Nội', 'destination': 'Phú Quốc'})`
- `---> Gọi tool: search_hotels({'city': 'Phú Quốc'})`
- `---> Gọi tool: calculate_budget({'total_budget': 5000000, 'expenses': 'vé_máy_bay:1100000,khách_sạn:3000000'})`
- `---> Trả lời trực tiếp`

**Kết quả:**
> **TravelBuddy:** Dưới đây là kế hoạch chuyến đi Phú Quốc 2 đêm của bạn:
>
> #### ✈️ Chuyến bay đề xuất:
> - **VietJet Air**: 16:00 - 18:15 | Giá: **1.100.000đ**
>
> #### 🏨 Khách sạn đề xuất:
> - **Sol by Meliá** (4 sao) | Khu vực: Bãi Trường
> - Giá: **1.500.000đ/đêm** &rarr; Tổng 2 đêm: **3.000.000đ**
>
> #### 💰 Tổng kết ngân sách:
> | Hạng mục | Chi phí |
> | :--- | :--- |
> | Vé máy bay | 1.100.000đ |
> | Khách sạn (2 đêm) | 3.000.000đ |
> | **Tổng chi dự tính** | **4.100.000đ** |
> | **Ngân sách ban đầu** | 5.000.000đ |
> | **Số dư còn lại** | **900.000đ** |
>
> **Gợi ý thêm:** Bạn còn dư khoảng 900.000đ để thoải mái thưởng thức hải sản và thuê xe máy khám phá đảo. Bạn có cần mình hỗ trợ gì thêm không?

---

### 4️⃣ Test 4: Missing Information (Cần làm rõ)

**User:** "Tôi muốn đặt khách sạn"

**Hành động của Agent:**
- `---> Trả lời trực tiếp`

**Kết quả:**
> **TravelBuddy:** Rất sẵn lòng! Tuy nhiên, bạn muốn đặt khách sạn ở **thành phố nào** vậy? Ngoài ra, nếu có ngân sách dự kiến hoặc số sao mong muốn, hãy chia sẻ để mình tìm được lựa chọn ưng ý nhất nhé!

---

### 5️⃣ Test 5: Guardrails (Từ chối yêu cầu sai phạm vi)

**User:** "Giải thích giúp tôi bài tập lập trình Python về Linked List"

**Hành động của Agent:**
- `---> Trả lời trực tiếp`

**Kết quả:**
> **TravelBuddy:** Xin lỗi bạn, mình là trợ lý chuyên về **du lịch nội địa Việt Nam**. Mình không có chuyên môn về lập trình nên không thể giải bài tập giúp bạn được. Nếu bạn cần gợi ý về các chuyến đi trong nước, mình luôn sẵn sàng hỗ trợ nhé!
