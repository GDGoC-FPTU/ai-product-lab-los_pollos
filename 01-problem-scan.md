
# 🔍 Phase 1 — SCAN (Cá nhân, 20 min)

Hãy sử dụng **4 Lenses** dưới đây để quét qua hoạt động vận hành của các công ty thành viên Vingroup. Ghi lại **ít nhất 5 bài toán/bottleneck** thực tế.

### 4 Lenses tìm bài toán AI cho Vingroup:
1. **Lặp lại (Repetitive):** Tác vụ lặp đi lặp lại nhiều lần hằng ngày. (Ví dụ: So khớp hóa đơn sạc điện tại VinFast, route lại chuyến taxi tại Xanh SM).
2. **Tốn thời gian (Time-consuming):** Tác vụ ngốn thời gian xử lý thủ công của nhân viên. (Ví dụ: Soạn thảo phản hồi đánh giá 1-star của cư dân Vinhomes).
3. **AI có thể tốt hơn (AI-upgrade):** Dịch vụ khách hàng hiện tại còn chậm hoặc phản hồi rập khuôn. (Ví dụ: Chatbot CSKH Vinpearl hỗ trợ đặt vé vui chơi).
4. **Pain từ người khác (Stakeholder Pain):** Bottleneck khiến khách hàng hoặc nhân viên thực địa phàn nàn. (Ví dụ: Tài xế Xanh SM phàn nàn về việc hệ thống gợi ý điểm đón khách không chính xác).

> [!TIP]
> **🤖 AI Prompts — Partner brainstorm:**
> Hãy sử dụng prompt sau để brainstorm các bài toán thực tế nếu bạn chưa có ý tưởng:
> *"Tôi là AI Engineer tại Vin Smart Future (Vingroup). Tôi đang tìm kiếm các pain point vận hành cụ thể có thể tối ưu bằng AI cho mảng [Chọn một: VinFast / Xanh SM / Vinhomes / Vinmec]. Hãy gợi ý cho tôi 5 quy trình nghiệp vụ thủ công, tốn nhiều thời gian và gây rò rỉ hiệu suất kèm con số thống kê ước tính về tổn thất."*

### 📝 List bài toán của tôi:
| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | GreenSM | Lặp lại | Kiểm định chất lượng dịch vụ tài xế qua hình ảnh và phản hồi |
| 2 | GreenSM | Tốn thời gian | Xử lý khiếu nại hoàn tiền và tranh chấp chuyến đi |
| 3 | GreenSM | Lặp lại | Đối soát và phê duyệt bồi hoàn chi phí sửa chữa/bảo dưỡng đội xe |
| 4 | Vinhomes | Tốn thời gian | Tổng hợp, phân loại và soạn thảo phản hồi cá nhân hoá hàng nghìn ý kiến/khiếu nại của cư dân Vinhomes hằng ngày |
| 5 | VinFast | Stakeholder pain | Kỹ sư vận hành phàn nàn vì mất quá nhiều thời gian phân tích thủ công file log dữ liệu khổng lồ từ xe điện gửi về để tìm nguyên nhân lỗi (lỗi sạc, phần mềm,...) |

---

# 🃏 Phase 2 — QUICK-ASSESS (Cá nhân, 30 min)

Chọn **top 3 bài toán** từ danh sách trên và hoàn thiện **3 Quick Problem Cards** dưới đây (10 phút/card).

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #01                                     │
│                                                             │
│ Bài toán (1 câu): Xử lý khiếu nại hoàn tiền và tranh chấp chuyến đi của khách hàng  │
│ Công ty thành viên: [ ] VinFast  [X] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Tổng đài viên (CSKH) & Khách hàng │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Nhận khiếu nại ──> 2. Tra cứu GPS / Lịch sử Chat/App ──> 3. Đối chiếu giải trình tài xế  ──> 4. Ra quyết định                   │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 3 (⏱ 25 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Tại bước 2 & 3 AI sẽ chỉ nhảy vào các case phức tạp (Edge cases), nơi tài xế và khách hàng chửi bới nhau trong Lịch sử Chat bằng tiếng lóng, mỉa mai hoặc phân tích sắc thái cảm xúc (dùng Sentiment Analysis) còn lại dùng Rule-based để lấy GPS so với Lộ trình chuẩn (nếu lệch nhiều quá X% thì hoàn tiền chênh lệch), hoặc kiểm tra lúc tài xế bấm "đã đến điểm đón" so với toạ độ khách hàng đặt (để xác định lỗi của tài xế hay không),... │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm từ 25 phút xuống dưới 5 phút và đồng thời Giữ nguyên hoặc giảm tỷ lệ gian lận hoàn tiền │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [X] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #02                                     │
│                                                             │
│ Bài toán (1 câu): Tổng hợp, phân loại và soạn thảo phản hồi ý kiến/khiếu nại của cư dân trên app Vinhomes Resident.  │
│ Công ty thành viên: [ ] VinFast  [ ] Xanh SM  [X] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Ban quản lý (BQL) toà nhà/khu dân cư │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Đọc feedback trên app ──> 2. Phân loại nhóm lỗi ──> Chuyển kỹ thuật/vệ sinh/xử lý  ──> 4. Soạn văn bản trả lời                 │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 2 & 4 (⏱ 8 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Tự động phân loại ở bước 2 (dùng rule-based để gắn tag và chuyển cho bộ phận tương ứng - ví dụ như có keywords "rác", "bẩn" thì gắn tag [Vệ sinh]) và tự động soạn thảo phản hồi ở bước 4 dựa trên bộ quy chuẩn phát ngôn của Vinhomes. │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Tăng tỉ lệ hài lòng của cư dân lên sau khi áp dụng AI vào (đo bằng %) │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```

```
┌─────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #03                                     │
│                                                             │
│ Bài toán (1 câu): Phân tích file log dữ liệu khổng lồ từ xe điện để tìm nguyên nhân lỗi hệ thống  │
│ Công ty thành viên: [X] VinFast  [ ] Xanh SM  [ ] Vinhomes  │
│                     [ ] Vinmec   [ ] Khác (Ghi rõ)________  │
│                                                             │
│ Ai đang đau (Actor)? Kỹ sư vận hành (QA/R&D Engineer) │
│                                                             │
│ Workflow thủ công hiện tại (3-5 bước):                      │
│   1. Tiếp nhận ticket báo lỗi ──> 2. Trích xuất file log từng xe ──> 3. Dò lỗi thủ công qua hàng nghìn dòng code/thông số ──> 4. Xác định cấu phần lỗi -> 5. Lên phương án sửa chữa │
│                                                             │
│ Bước nào tốn thời gian/lỗi nhất? Bước 3 (⏱ 180 phút/lượt)      │
│ AI có thể nhảy vào hỗ trợ ở bước nào? Bước 3 (Tự động quét, phát hiện bất thường và khoanh vùng dòng log gây lỗi) │
│                                                             │
│ Đo thành công bằng gì (Metric có số)? Giảm thời gian chẩn đoán lỗi xe từ 3 tiếng xuống dưới 20 phút và đồng thời làm tăng tí lệ (%) chính xác của của vùng lỗi phần mềm │
│   VD: "Giảm thời gian soạn phản hồi từ 10 min ──> under 2 min"│
│                                                             │
│ Quick Architecture: [ ] No AI  [ ] Rule  [X] LLM  [ ] Agent │
└─────────────────────────────────────────────────────────────┘
```