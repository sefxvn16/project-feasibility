# project-feasibility

[English](README.md) | **Tiếng Việt**

Skill cho trợ lý AI để dựng và phân tích mô hình hiệu quả tài chính dự án (dòng tiền, NPV, IRR, Payback, phân tích độ nhạy, kết luận đầu tư) cho **quyết định nội bộ sơ bộ** về một dự án cụ thể: đầu tư mới, thương vụ M&A hoặc hợp tác kinh doanh. Trọng tâm là kỷ luật giả định: mọi dữ liệu đầu vào đều gắn nhãn, công việc đi qua ba pha có điểm dừng sau mỗi pha, và không được chỉnh giả định để kết quả đẹp hơn.

## Skill làm gì

Một mô hình khả thi có thể trông hợp lý ở kết quả cuối dù một giả định ban đầu đã sai. Chiều ngược lại cũng có: âm thầm chỉnh input cho tới khi NPV vừa ý. Skill chống cả hai bằng ba quy tắc.

**1. Mỗi nhận định mang đúng một nhãn**

- **Fact**: có nguồn, quan sát hoặc công bố được.
- **Estimate**: luôn ở dạng khoảng, không chốt số đơn lẻ.
- **Assumption**: giả định nội bộ, chỉ dùng khi không có Fact hoặc Estimate đủ tin cậy.

**2. Pipeline ba pha một chiều, dừng sau mỗi pha**

| Pha | Làm | Không làm |
|---|---|---|
| **F1 — Data & Assumptions** | Gắn nhãn dữ liệu, đánh giá độ tin cậy, ghi khoảng trống và rủi ro ngoài mô hình | Tính toán, đánh giá, kết luận |
| **F2 — Modeling & Calculation** | Theo file mẫu của bạn, hoặc đề xuất cơ cấu file để duyệt trước; dựng mô hình truy vết được (tách input / công thức / kết quả), tính NPV, IRR, Payback | Tạo hay đổi giả định, phân tích độ nhạy, diễn giải |
| **F3 — Analysis & Decision** | Độ nhạy, hòa vốn, so sánh kịch bản, kết luận | Đổi input hay công thức, bỏ kịch bản xấu, cam kết lợi nhuận |

Sau mỗi pha, skill trình bày kết quả và chờ người dùng xác nhận mới sang pha tiếp. Muốn đổi giả định thì quay về F1, nêu lý do và ghi ảnh hưởng tới các pha sau.

**Quy định về file mô hình (F2)**

- Nếu bạn đưa file mẫu, mô hình dựng theo mẫu đó. Không có mẫu thì skill đề xuất trước danh sách sheet, nội dung từng sheet, các dòng và cột chính, và chỉ dựng file khi bạn đồng ý.
- Không có công thức ẩn: mọi phép tính là công thức hiển thị trong file. Không dán giá trị, không ẩn sheet, hàng hay cột, không dùng IFERROR để che lỗi.
- Màu chữ: **xanh dương** cho input nhập tay, **đen** cho công thức, **xanh lá** cho liên kết sang sheet khác (nếu file mẫu có quy ước riêng thì theo mẫu), có chú thích màu trong file.
- Trước khi giao file, skill tính lại toàn bộ và kiểm tra lỗi công thức (#NUM!, #DIV/0!, #REF!, #VALUE!, #NAME?, #N/A, #NULL!) và tham chiếu vòng. Lỗi do input thì báo lại và quay về F1, không sửa bằng cách đổi input.

**3. Khung kết luận cố định**

Kết luận luôn là **Go**, **No-go** hoặc **Go-with-conditions**, lập luận từ NPV, IRR, độ nhạy và ngưỡng gãy, không dùng ngưỡng số cứng để tự phân loại. Go-with-conditions bắt buộc nêu điều kiện cụ thể mà khi vượt qua thì Go không còn giữ được.

Ngoài ra, skill hỏi trước khi bù dữ liệu thiếu. Skill chỉ tạo giả định khi người dùng cho phép, và ưu tiên nói rõ "không có dữ liệu" hơn là đưa thông tin không chắc chắn. Skill cũng dừng lại khi gặp một danh sách câu cố định báo hiệu yêu cầu vi phạm kỷ luật giả định (ví dụ "Chỉnh cho đẹp IRR hơn").

## Ranh giới

- Chỉ dùng cho **quyết định nội bộ sơ bộ**. Không dùng cho báo cáo tài chính doanh nghiệp, kiểm toán, hồ sơ vay vốn ngân hàng hoặc quỹ đầu tư, hay định giá chính thức. Gặp các trường hợp này, skill nói rõ không áp dụng thay vì cố điều chỉnh.
- Skill không tự tìm dữ liệu trừ khi được yêu cầu trực tiếp.
- Skill không phải tư vấn tài chính, đầu tư hay pháp lý chuyên nghiệp.
- Skill không phụ thuộc vào skill nào khác.

## Cấu trúc thư mục

```
project-feasibility/
  SKILL.md
README.md
README.vi.md
LICENSE.md
```

## Cài đặt

### Ứng dụng Claude (claude.ai, Claude desktop)

1. Tải file `project-feasibility.zip` ở trang [Releases](https://github.com/sefxvn16/project-feasibility/releases/latest). Hoặc tải repo về rồi tự nén riêng thư mục `project-feasibility` (file zip phải chứa thư mục `project-feasibility` ở cấp ngoài cùng).
2. Mở Claude, vào **Customize → Skills**, bấm **+** → **Create skill** → **Upload a skill** và chọn `project-feasibility.zip`. Tên và vị trí menu có thể khác tùy phiên bản ứng dụng. Skill cần bật tính năng chạy mã (code execution).
3. Kiểm tra skill `project-feasibility` đã hiện trong danh sách và đang bật.

### Claude Code

Chép thư mục `project-feasibility` vào `~/.claude/skills/` (dùng cho mọi dự án) hoặc `.claude/skills/` của một dự án, rồi khởi động lại Claude Code.

## Cách dùng

Skill kích hoạt khi yêu cầu liên quan đến hiệu quả tài chính của một dự án. Trong Claude Code bạn cũng có thể gọi trực tiếp bằng `/project-feasibility`. Ví dụ:

- "Đây là số liệu vốn đầu tư, giá phòng và công suất của một khách sạn 50 phòng. Dựng mô hình hiệu quả tài chính giúp tôi."
- "Đã có kết quả F2. Phân tích độ nhạy theo giá và công suất, rồi cho biết có đáng đầu tư không."

Skill sẽ dừng ở cuối F1 và F2 để hỏi xác nhận, kể cả khi bạn yêu cầu "dựng mô hình luôn".

## Giới hạn

- Quy trình chưa được kiểm chứng thực nghiệm. Các lý do thiết kế trong SKILL.md là giả thuyết.
- Các câu bị cấm ở mục 9 được liệt kê nguyên văn bằng tiếng Việt. Skill chưa nói cách diễn đạt khác cùng ý, hoặc ngôn ngữ khác, có bị chặn như vậy không.
- Skill chưa nói cách tính khi môi trường không chạy được mã hay bảng tính.
- Mục 3.3 yêu cầu phân tích độ nhạy ở F3, trong khi mục 8 cấm "tính toán mới" ở F3. Chạy lại mô hình F2 với input thay đổi có tính là tính toán mới hay không thì chưa được nói rõ.
- Khi thiếu một input quan trọng (như discount rate) và người dùng không cho phép giả định, skill ghi nhận khoảng trống nhưng chưa nói F2 có tính tiếp các chỉ số không cần input đó hay không.

## Góp ý

Mọi góp ý xin gửi qua mục **Issues** của repo. Để dễ xử lý, nên ghi:

- yêu cầu bạn đưa ra và loại dự án (đã bỏ thông tin cá nhân hoặc thông tin mật);
- pha xảy ra vấn đề (F1, F2 hay F3);
- kết quả bạn mong đợi và kết quả thực tế.

Đặc biệt mong góp ý về: skill kích hoạt nhầm hoặc không kích hoạt, điểm dừng quá chặt hoặc quá lỏng, trường hợp khó gắn nhãn Fact / Estimate / Assumption, các giới hạn nêu trên, và chỗ hướng dẫn khó hiểu.

## Giấy phép

Skill phát hành theo giấy phép **CC BY-NC 4.0**: dùng miễn phí cho mục đích phi thương mại, cần ghi nguồn. Muốn dùng thương mại, vui lòng liên hệ tác giả qua mục **Issues**. Skill được cung cấp nguyên trạng, không kèm bảo đảm. Xem [LICENSE.md](LICENSE.md).
