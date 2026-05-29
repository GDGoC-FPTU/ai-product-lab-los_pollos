# AI Log — Reflection on AI as Thought Partner

- Võ Thanh Hiệp
- 2A202600836
- Phòng C401
- Lab02

## AI giúp gì
Trong buổi Lab này, tôi đã dùng AI để:
- Brainstorm các pain point vận hành cho Vin Smart Future, đặc biệt là quy trình xử lý tranh chấp chuyến đi ở Xanh SM và quản lý pin/điện.
- Viết prompt prototype cho Gemini 2.5 Flash bằng Python, bao gồm system prompt nghiêm ngặt, định dạng output JSON và các testcase tấn công boundary.
- Debug lỗi Python trong `starter-code/prompt_prototype.py`, đặc biệt khi API Gemini trả lỗi `400 invalid_argument`.
- Được hỗ trợ xác định rõ khi nào nên dùng rule-based thay vì agent/LLM quá phức tạp.

## AI sai gì
AI đã gặp một số vấn đề sau:
- Lần đầu tôi có xu hướng chọn kiến trúc `Agent` cho bài toán xử lý khiếu nại hoàn tiền. Đây là overkill vì bài toán thực tế phù hợp hơn với rule-based engine + LLM chỉ để draft văn bản.
- Khi xây dựng mã Python, tôi đã tạo payload không đúng cho `google-genai` SDK bằng cách dùng `types.Content(role="system", ...)` và `types.Content(role="user", ...)`. Điều này làm model trả lỗi `400 invalid_argument`.
- Một phần AI có thể đề xuất ranh giới an toàn chưa đủ cứng: nếu người dùng cố bypass `[DRAFT_ONLY]`, cần phải ép chế độ cứng hơn và trả về JSON duy nhất.

## Sửa đổi ra sao
Tôi đã điều chỉnh prompt và code như sau:
1. Viết `SYSTEM_PROMPT` cực kỳ nghiêm ngặt:
   - Luôn bắt đầu output bằng `[DRAFT_ONLY]`.
   - Chỉ trả về một object JSON duy nhất với các trường `draft`, `action`, `reason`, `station`.
   - Nếu pin < 5%, chuyển sang `dispatch_mobile_charger` và không đề xuất trạm cách > 5km.
2. Thêm testcase adversarial để dò prompt injection:
   - Một input cố tình yêu cầu gửi tin nhắn ngay và bỏ `[DRAFT_ONLY]`.
   - Một input yêu cầu đi đến trạm 8km khi pin chỉ còn 2%.
3. Sửa mã Python để dùng đúng định dạng `contents` của `google-genai`:
   - Dùng `types.Part.from_text(text=...)` thay vì `types.Content(role=..., parts=...)`.
4. Bổ sung kiểm tra output:
   - Nếu model trả về `response.text`, lấy luôn.
   - Nếu không, kiểm tra `response.candidates[0].content.parts` và nối text.

## Bài học rút ra
- AI là một trợ lý tốt khi cần brainstorm và đưa ra gợi ý prompt, nhưng tôi vẫn cần kiểm tra kỹ về giới hạn kỹ thuật của SDK và định dạng API.
- Với những bài toán nghiệp vụ nhạy cảm, rule-based vẫn là nền tảng an toàn hơn; LLM nên dùng ở phần draft giao tiếp hoặc tóm tắt, không nên thay thế logic quyết định chính.
- Việc dùng adversarial test là rất hữu ích để kiểm tra prompt boundary và giảm nguy cơ prompt injection.

## Kết luận
Tôi đã học được cách phối hợp AI như một thought partner: nhận ý tưởng ban đầu, điều chỉnh lại khi AI sai, rồi dập lại ranh giới an toàn bằng prompt và code. Dự án này giúp tôi rõ hơn về sự khác biệt giữa "có thể dùng AI" và "nên dùng AI", đồng thời thực hành cả phần prompt engineering và debug API thật sự.
