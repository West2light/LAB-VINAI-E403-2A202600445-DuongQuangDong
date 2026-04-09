# Individual reflection - Duong Quang Dong (2A202600445)

## 1. Role

Product canvas owner + prototype developer. Phụ trách xây dựng AI Product Canvas, visualize canvas bằng HTML/CSS, và hỗ trợ phần kỹ thuật cho logging, prompt test, debug, version control.

## 2. Đóng góp cụ thể

- Viết AI Product Canvas cho bài toán chatbot Vinmec hỗ trợ mẹ bầu tìm hiểu gói thai sản, bảo hiểm và chi phí dịch vụ.
- Làm phần visualize canvas product bằng HTML/CSS để nhóm có bản demo rõ ràng và dễ theo dõi các thành phần của sản phẩm.
- Xây dựng/chỉnh sửa chức năng trong `tools.py` để log User Feedback, phục vụ vòng lặp học hỏi và cải thiện chất lượng chatbot.
- Test prompt và debug để cải thiện cách bot trả lời các câu hỏi về chính sách, giá, và tình huống ngoài phạm vi.
- Viết docs mô tả cấu trúc thư mục và hướng dẫn cài đặt prototype để dễ handoff và giúp các thành viên khác chạy lại hệ thống nhanh hơn.
- Làm việc với GitHub và version controller để đồng bộ và quản lý mã nguồn.

## 3. SPEC mạnh/yếu

- Mạnh nhất: SPEC xác định khá rõ user, pain point, và vai trò của AI trong bài toán Vinmec. Định hướng precision-first cũng hợp lý vì đây là bài toán liên quan đến chi phí, chính sách, và độ tin cậy thông tin, nên việc ưu tiên đúng hơn đầy đủ là rất quan trọng.
- Yếu nhất: Phần liên kết từ SPEC sang prototype và prompt test chưa thực sự sâu. Canvas và logic sản phẩm đã có, nhưng chưa biến thành một flow hoàn chỉnh từ UI -> tool calling -> feedback review, và bộ test prompt cũng chưa đủ đa dạng để kiểm tra tốt các trường hợp mơ hồ, sai intent, và handoff.

## 4. Đóng góp khác

- Hỗ trợ debug các vấn đề phát sinh trong quá trình test prompt và tích hợp chức năng.
- Viết tài liệu để chuẩn hóa cách tổ chức source code và cách setup prototype, giúp nhóm dễ onboarding và giảm lỗi khi chạy môi trường.
- Chuẩn hóa quá trình lưu version bằng GitHub để dễ theo dõi thay đổi và tránh mất code khi làm nhóm.
- Bổ sung logging feedback để sau này có thể dùng dữ liệu thật từ user cho việc review và cập nhật knowledge base.

## 5. Điều học được

Hôm nay mình học rõ hơn rằng product canvas không chỉ để "viết cho đủ spec" mà nó giúp định hình rất rõ mình sẽ xây cái gì trong prototype. Khi từ canvas đi sang HTML/CSS visualize và sang `tools.py`, mình thấy rõ mỗi ô trong spec đều cần một biểu hiện cụ thể trong sản phẩm: user feedback phải được log, AI sai phải có đường recover, và prompt không thể viết chung chung.

Mình cũng học thêm về cách prompt, debug, và logging liên quan trực tiếp đến nhau. Prompt test cho thấy nếu không có cơ chế feedback và log thì rất khó biết bot đang sai ở đâu, sai vì dữ liệu, prompt, hay do user hỏi mơ hồ.

## 6. Nếu làm lại

Sẽ chia việc thành từng vòng rõ hơn ngay từ đầu: canvas -> prompt test sớm -> prototype UI -> logging/feedback -> debug. Hôm nay có lúc làm song song nhiều thứ nên dễ bị chuyển ngữ cảnh, dẫn đến việc debug và test prompt chưa thực sự hệ thống.

Sẽ chuẩn bị bộ test prompt có cấu trúc sớm hơn, gồm happy path, low-confidence, failure, và correction path. Nếu làm vậy sớm, phần prompt và tools sẽ ổn hơn, và prototype cũng bám sát spec hơn ngay từ vòng đầu.

## 7. AI giúp gì / AI sai gì

- **Giúp:** AI hỗ trợ brainstorm câu chữ và cấu trúc cho Product Canvas, một số core trong project như prompt, tools, gợi ý cách trình bày để visualize canvas bằng HTML/CSS, và hỗ trợ debug nhanh những lỗi nhỏ trong quá trình code/test. AI cũng hiệu quả khi dùng để test nhanh nhiều cách đặt prompt và xem phản hồi của hệ thống trong các tình huống khác nhau.
- **Sai/mislead:** AI dễ đề nghị các hướng mở rộng nghe hợp lý nhưng vượt scope hackathon, hoặc viết prompt/logic quá đẹp trên lý thuyết nhưng khó tích hợp vào flow thật.
- **Bài học:** Dùng AI tốt nhất khi mình đã có problem framing rõ, scope rõ, và dùng nó như công cụ tăng tốc. Nếu không giữ scope chặt, AI rất dễ đẩy mình sang các nhánh không cần thiết.
