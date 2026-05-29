# Phase 1 — SCAN & Phase 2 — QUICK-ASSESS

This file contains the individual scoping efforts for Phase 1 and Phase 2 of the AI Product Scoping Lab.

---

# 🔍 Phase 1 — SCAN

Dưới đây là danh sách 5 bài toán thực tế đã quét qua hoạt động vận hành của các công ty thành viên Vingroup sử dụng **4 Lenses**:

| # | Subsidiary (VinFast/Xanh SM...) | Lens | Mô tả ngắn bài toán |
|---|----------------------------------|------|---------------------|
| 1 | VinFast | Lặp lại | Đối chiếu hàng trăm nghìn giao dịch sạc xe giữa ứng dụng VinFast với hóa đơn từ hệ thống tài chính |
| 2 | Vinhomes | Tốn thời gian | Cư dân nộp hồ sơ sửa nhà, kỹ sư tòa nhà phải lật từng trang bản vẽ CAD/PDF để đối chiếu thủ công với quy định an toàn, chịu lực và PCCC |
| 3 | Vinpearl / VinWonders | AI-upgrade | Hệ thống trả lời theo kịch bản cứng, không hiểu được ngữ cảnh phức tạp khi khách hàng hỏi về combo nghỉ dưỡng |
| 4 | Vinmec | Pain từ người khác | Bác sĩ tốn quá nhiều thời gian nhập liệu hồ sơ bệnh án điện tử (EHR) sau mỗi ca khám |
| 5 | VinFast | Lặp lại | So khớp ba bước (3-way matching) giữa Đơn đặt hàng (PO), Phiếu nhập kho (GRN) và Hóa đơn (Invoice) từ hàng nghìn nhà cung cấp linh kiện toàn cầu |

---

# 🃏 Phase 2 — QUICK-ASSESS

Dưới đây là 3 Quick Problem Cards được đánh giá nhanh dựa trên danh sách SCAN ở trên:

```text
┌────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #1                                              │
│                                                                    │
│ Bài toán (1 câu): Đối chiếu thủ công khối lượng lớn giao           │
│ dịch sạc xe điện giữa ứng dụng VinFast với hóa đơn từ hệ           │
│ thống tài chính│                                                   │
│ Công ty thành viên: [x] VinFast                                    │
│                                                                    │
│ Ai đang đau (Actor)? Nhân viên kế toán/tài chính                   │
│                                                                    │
│ Workflow thủ công hiện tại (3-5 bước):                             │
│   1. Xuất file Excel giao dịch từ Backend App VinFast              |
│   ─> 2. Xuất dữ liệu hóa đơn/sao kê từ ERP & Cổng thanh toán.      |
│   ─> 3. Dùng hàm VLOOKUP/Index-Match để so khớp mã giao dịch.      |
│   ─> 4. Tìm và xử lý thủ công các ca lệch tiền/lỗi hệ thống.       |
│                                                                    │
│ Bước nào tốn thời gian/lỗi nhất? bước 3 và 4 (2-3 giờ/lượt)        │
│ AI có thể nhảy vào hỗ trợ ở bước nào? bước 3 và 4                  │
│ (Đối soát tự động và tự động phân loại, gắn nhãn                   |
│ nguyên nhân lệch tiền)                                             |
│                                                                    │
│ Đo thành công bằng gì (Metric có số)? ______________________       │
│   * Tỷ lệ sai sót: >98%                                            │
│   * Giảm thời gian so khớp từ 2 giờ/ngày ──> 15 phút/ngày          │
│                                                                    │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent        │
└────────────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #2                                              │
│                                                                    │
│ Bài toán (1 câu): Bác sĩ tốn quá nhiều thời gian nhập liệu hồ      │
│ sơ bệnh án điện tử (EHR) sau mỗi ca khám                           |
│                                                                    │
│ Công ty thành viên: [x] Vinmec                                     │
│                                                                    │
│ Ai đang đau (Actor)? Bác sĩ khám bệnh tại các chuyên khoa          │
│                                                                    │
│ Workflow thủ công hiện tại (3-5 bước):                             │
│   1. Bác sĩ hỏi bệnh, khám lâm sàng và trao đổi với bệnh nhân.     |
│   ─> 2. Ghi chú nhanh các triệu chứng chính ra nháp hoặc nhớ.      |
│   ─> 3. Gõ máy tính để nhập triệu chứng, tiền sử vào EHR.          |
│   ─> 4. Tóm tắt chẩn đoán, gõ phác đồ điều trị và kê đơn thuốc.    |
│                                                                    │
│ Bước nào tốn thời gian/lỗi nhất? bước 3 và 4 (12 phút/lượt)        │
│ AI có thể nhảy vào hỗ trợ ở bước nào? bước 3 và 4                  │
│ (Nghe cuộc hội thoại ở Bước 1, tự động cấu trúc hóa thành văn bản  |
│   EHR)                                                             │
│                                                                    │
│ Đo thành công bằng gì (Metric có số)? ______________________       │
│   * Giảm thời gian nhập liệu EHR từ 12 phút/lượt ──> 2 phút/lượt   │
│   * Tăng thời gian tương tác mắt trực tiếp với bệnh nhân > 70%     │
│                                                                    │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent        │
└────────────────────────────────────────────────────────────────────┘

┌────────────────────────────────────────────────────────────────────┐
│ QUICK PROBLEM CARD #3                                              │
│                                                                    │
│ Bài toán (1 câu): So khớp ba bước (3-way matching) giữa Đơn đặt    │
│ hàng (PO), Phiếu nhập kho (GRN) và Hóa đơn (Invoice) từ hàng       │
│ nghìn nhà cung cấp linh kiện toàn cầu                              │
│                                                                    │
│ Công ty thành viên: [x] VinFast                                    │
│                                                                    │
│ Ai đang đau (Actor)? Nhân viên kế toán/tài chính                   │
│                                                                    │
│ Workflow thủ công hiện tại (3-5 bước):                             │
│   1. Nhận Hóa đơn (PDF/Ảnh) từ NCC qua email và tải lên ERP.       |
│   ─> 2. Tra cứu Đơn đặt hàng (PO) tương ứng trên hệ thống SAP.     |
│   ─> 3.Tra cứu Phiếu nhập kho (GRN) kiểm đếm tại Hải Phòng.        |
│   ─> 4. So khớp thủ công từng dòng (Line-item): Mã, Số lượng, Đơn  |
│   giá, Thuế, Đơn vị tính (Pcs/Box/Kg), Loại ngoại tệ.              │
│                                                                    │
│ Bước nào tốn thời gian/lỗi nhất? bước 4 (45 phút/bộ chứng từ)      |
│ AI có thể nhảy vào hỗ trợ ở bước nào? bước 4                       |
│ (So khớp tự động Line-item và gắn cờ các trường lệch)              |
│                                                                    │
│ Đo thành công bằng gì (Metric có số)? ______________________       │
│   * Tỷ lệ tự động hóa quy trình (Straight-Through Processing):     |
│       Đạt > 85% bộ chứng từ chuẩn không cần con người can thiệp.   |
│   * Giảm thời gian so khớp từ 45 phút ──> dưới 3 phút              |
│                                                                    │
│ Quick Architecture: [ ] No AI  [ ] Rule  [ ] LLM  [x] Agent        │
└────────────────────────────────────────────────────────────────────┘
```
