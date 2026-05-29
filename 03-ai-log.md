# Nhật Ký Chiêm Nghiệm AI (AI Reflection Log)

## 1. AI đã giúp tôi những gì?
Trong suốt quá trình thực hiện bài lab, AI đóng vai trò như một người bạn đồng hành thảo luận ý tưởng cực kỳ đắc lực:
- **Scoping & Brainstorming:** Hỗ trợ phân tích sâu 3 bài toán từ mảng hoạt động khác nhau của Vingroup. Giúp làm rõ và mở rộng các ranh giới vận hành, đặc biệt là các khía cạnh về an toàn kỹ thuật và nghiệp vụ tài chính.
- **Thiết kế System Prompt:** AI hỗ trợ cấu trúc hóa System Prompt cho file `prompt_prototype.py` một cách rõ ràng, chặt chẽ, đưa ra các ranh giới an toàn và quy định cụ thể định dạng JSON đầu ra.
- **Sửa lỗi Code & Môi trường:** Khi chạy kiểm thử cục bộ trên Windows, hệ thống gặp lỗi mã hóa Unicode (`UnicodeEncodeError`). AI đã nhanh chóng đề xuất giải pháp ghi đè `sys.stdout` và `sys.stderr` thành UTF-8 để xử lý mượt mà các ký tự Unicode/emoji trong console.

---

## 2. AI đã đưa ra những kết quả sai lệch/chưa tốt nào?
Tuy nhiên, AI vẫn có những điểm hạn chế cần sự kiểm tra của con người:
- **Thiếu tương thích môi trường chạy:** Khi sinh mã Python mẫu chứa nhiều emoji đẹp mắt (ví dụ `🚀`, `✅`, `❌`), AI đã không lường trước được rằng console Windows mặc định dùng mã hóa CP1252, dẫn đến chương trình bị crash ngay khi khởi chạy.
- **Lý giải ranh giới chưa đủ nghiêm ngặt:** Ban đầu khi được yêu cầu viết prompt chặn việc đề xuất trạm sạc xa khi pin yếu, AI đôi khi vẫn sinh ra mã lệnh hoặc tin nhắn văn bản đi kèm mà bỏ quên việc cấu trúc hóa JSON thuần tuý, hoặc dễ dàng bị thuyết phục bỏ qua thẻ `[DRAFT_ONLY]` nếu người dùng sử dụng các câu lệnh ép buộc mạnh.

---

## 3. Tôi đã điều chỉnh và khắc phục như thế nào?
Để giải quyết các vấn đề trên, tôi đã thực hiện:
- **Tối ưu mã nguồn Python:** Thêm đoạn mã wrapper ép buộc sử dụng mã hóa UTF-8 cho console Python, đồng thời thay thế các emoji đặc biệt trong print statements bằng các ký tự ASCII tiêu chuẩn (`Passed`, `Failed`) để mã nguồn luôn chạy ổn định trên mọi hệ điều hành.
- **Gia cố System Prompt:** Bổ sung các mệnh lệnh nghiêm ngặt và quy định định dạng đầu ra độc quyền (ví dụ: *"Khi trả về JSON cứu hộ, KHÔNG được viết thêm bất kỳ văn bản nào khác ngoài JSON này"*). Đồng thời sử dụng viết hoa các từ khóa quan trọng như `BẮT BUỘC`, `TUYỆT ĐỐI KHÔNG` để tạo sức nặng cho mô hình khi xử lý ranh giới an toàn.