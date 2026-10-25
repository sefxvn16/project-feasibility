---
name: project-feasibility
description: Dùng để lập hoặc phân tích hiệu quả tài chính dự án phục vụ việc ra quyết định nội bộ ở giai đoạn sơ bộ, như dòng tiền, NPV, IRR, thời gian hoàn vốn, phân tích độ nhạy và kết luận đầu tư. Dự án có thể là đầu tư mới, thương vụ M&A hoặc hợp tác kinh doanh. Kích hoạt khi yêu cầu liên quan đến hiệu quả tài chính của một dự án, kể cả khi người dùng không gọi tên skill. Không dùng cho báo cáo tài chính doanh nghiệp, kiểm toán, hồ sơ vay vốn ngân hàng hoặc quỹ đầu tư, hay định giá chính thức.
---

# Project Feasibility: Phân tích hiệu quả tài chính dự án

## 1. Phạm vi & mục tiêu

Skill này dùng để lập và phân tích hiệu quả tài chính dự án, phục vụ đánh giá sơ bộ và ra quyết định nội bộ. Phân tích dựa trên dữ liệu thị trường, các giả định được nêu rõ và mô hình dòng tiền, đồng thời chỉ ra mức độ chắc chắn của kết quả và những điều kiện có thể làm thay đổi hoặc khiến phương án không còn hiệu quả.

Dự án được phân tích có thể là đầu tư mới, thương vụ M&A hoặc hợp tác kinh doanh. Với M&A, skill đánh giá hiệu quả đầu tư của thương vụ cho quyết định nội bộ, không thay thế định giá chính thức.

Không dùng cho báo cáo tài chính doanh nghiệp, kiểm toán, hồ sơ vay vốn ngân hàng hoặc quỹ đầu tư, hay định giá chính thức. Nếu yêu cầu thuộc các trường hợp này, cần nói rõ skill không áp dụng thay vì cố điều chỉnh để sử dụng.

Kết quả chỉ phục vụ phân tích và thảo luận nội bộ ở mức sơ bộ, không thay thế tư vấn tài chính, đầu tư hoặc pháp lý chuyên nghiệp. Người dùng cần tự kiểm chứng số liệu và chịu trách nhiệm về quyết định của mình.

Skill này áp dụng cùng một mức độ chặt chẽ trong mọi trường hợp, kể cả khi dùng cho mục đích học thuật hoặc minh họa. Nếu cần cách xử lý khác, người dùng phải nêu rõ yêu cầu.

## 2. Nguyên tắc nền tảng: kỷ luật giả định

Mọi nhận định trong phân tích phải được gắn một trong ba nhãn:

- **Fact** - có nguồn, số liệu quan sát được hoặc thông tin đã được công bố.
- **Estimate** - ước tính, phải thể hiện dưới dạng khoảng thay vì chốt một con số duy nhất.
- **Assumption** - giả định nội bộ, dùng khi chưa có Fact hoặc Estimate đủ tin cậy.

Không trộn các nhãn trong cùng một nhận định. Mỗi con số hoặc kết luận chỉ được mang một nhãn.

Ba điều tuyệt đối không được làm, không có ngoại lệ:

- Không điều chỉnh giả định để kết quả đẹp hơn.
- Không suy ngược giả định từ kết quả mong muốn, nghĩa là không được biết trước NPV cần đạt rồi mới chỉnh các input cho khớp.
- Không hợp thức hóa rủi ro bằng cách bỏ qua hoặc làm nhẹ một giả định bất lợi.

## 3. Pipeline ba pha

Toàn bộ quá trình gồm ba pha, thực hiện theo thứ tự **F1 → F2 → F3**. Mỗi lượt chỉ làm một pha. Sau khi hoàn thành, phải trình bày đầy đủ kết quả của pha đó và chờ người dùng xác nhận mới được chuyển sang pha tiếp theo. Không tự động chuyển pha.

Cơ chế này nhằm tránh hai vấn đề. Thứ nhất, nếu giả định ở F1 sai, sai lệch đó sẽ đi vào toàn bộ tính toán ở F2 và kết luận ở F3, nhưng có thể vẫn tạo ra một kết quả cuối nhìn có vẻ hợp lý. Thứ hai, nếu biết trước kết quả F3, người phân tích có thể âm thầm điều chỉnh giả định ở F1 để đạt kết quả mong muốn.

Việc dừng lại sau mỗi pha buộc các giả định và mô hình phải được kiểm tra trước khi biết kết quả cuối, qua đó hạn chế việc điều chỉnh ngược từ kết quả về đầu vào.

### 3.1 F1: Data & Assumptions

Nhiệm vụ bắt buộc:

- Phân loại toàn bộ dữ liệu đầu vào theo ba nhãn **Fact / Estimate / Assumption**.
- Đánh giá độ tin cậy của từng dữ liệu (**mạnh, trung bình, yếu**), mức độ nhất quán và tính cập nhật.
- Chuẩn hóa dữ liệu thành bảng hoặc cấu trúc rõ ràng. Nếu dữ liệu chỉ có dạng khoảng thì giữ nguyên dạng khoảng, không tự chốt thành một con số.
- Ghi nhận các rủi ro ngoài phạm vi mô hình như pháp lý, kỹ thuật, thị trường thành giả định hoặc flag riêng để đưa vào điều kiện gãy ở F3.

Chế độ mặc định: chỉ xử lý dữ liệu người dùng cung cấp, không tự tìm kiếm hoặc mở rộng dữ liệu nếu chưa được yêu cầu. Chỉ tìm nguồn dữ liệu công khai khi người dùng yêu cầu trực tiếp, chẳng hạn tìm giá thị trường hoặc comp set theo routing tại mục 7. Nếu thiếu dữ liệu quan trọng cho mô hình, xử lý theo mục 4. Không tự bỏ qua và cũng không tự đặt giả định thay thế.

Việc không được làm ở F1: tính hiệu quả tài chính, phân tích chiến lược, kết luận đầu tư, tạo giả định vượt ngoài những gì đã xác lập (giả định thay thế chỉ được tạo khi người dùng cho phép theo mục 4) hoặc đưa ra các đánh giá như “tốt”, “khả quan”, “ổn”. F1 chỉ xác định dữ liệu, điều kiện, biến nhạy và những khoảng trống cần xử lý.

### 3.2 F2: Modeling & Calculation

Trước khi dựng file:

- Nếu người dùng cung cấp file mẫu, dựng mô hình theo đúng mẫu đó (cấu trúc sheet, bố cục, định dạng). Nếu mẫu mâu thuẫn với các yêu cầu của skill, ví dụ có công thức ẩn hoặc giả định hard-code, nêu rõ chỗ mâu thuẫn và hỏi người dùng trước khi dựng.
- Nếu không có file mẫu, đề xuất cơ cấu file để người dùng xem trước: danh sách sheet, nội dung từng sheet, các dòng và cột chính, các mốc thời gian. Chỉ dựng file sau khi người dùng đồng ý với cơ cấu này.

Nhiệm vụ bắt buộc:

- Thiết kế cấu trúc mô hình theo logic của dự án, gồm sheet, dòng, cột và các mốc thời gian.
- Tách rõ ba lớp: **input** lấy từ F1, công thức tính toán và kết quả đầu ra.
- Dựng dòng tiền theo thời gian, bao gồm đầy đủ doanh thu, chi phí, vốn đầu tư và các khoản thu hồi vốn.
- Tính **NPV, IRR, Payback** phù hợp với mục đích đánh giá nội bộ.
- Kiểm tra đơn vị đo lường, timeline, dấu dương/âm và bảo đảm không hard-code giả định trực tiếp trong công thức.

Mô hình phải dễ theo dõi và truy vết. Công thức cần rõ ràng, nhất quán, và bắt buộc không có công thức ẩn:

- Mọi phép tính phải nằm trong công thức hiển thị được ngay trong file. Không tính ở ngoài rồi dán giá trị vào, không dán giá trị tĩnh thay cho công thức.
- Không ẩn sheet, hàng hoặc cột có chứa tính toán; không khóa hay che công thức.
- Không dùng IFERROR hoặc hàm tương tự để che lỗi công thức.

Quy ước màu chữ trong file (nếu file mẫu của người dùng có quy ước riêng thì theo mẫu):

- **Xanh dương**: giá trị nhập tay, tức input lấy từ F1.
- **Đen**: công thức tính toán trong cùng sheet.
- **Xanh lá**: công thức lấy dữ liệu từ sheet khác.

File phải có phần chú thích quy ước màu để người xem đọc được.

Việc không được làm ở F2: tạo hoặc điều chỉnh giả định đầu vào. Mọi thay đổi giả định phải quay lại F1 theo quy tắc tại mục 8. F2 cũng không phân tích độ nhạy, diễn giải ý nghĩa kết quả, đưa ra kết luận đầu tư hoặc trình bày mô hình theo dạng báo cáo tài chính hay tài liệu kiểm toán.

### 3.3 F3: Analysis & Decision

Nhiệm vụ bắt buộc:

- Phân tích các chỉ số hiệu quả dựa trên kết quả F2.
- Phân tích độ nhạy đối với các biến số then chốt: giá, công suất, chi phí và tiến độ.
- Xác định ngưỡng hòa vốn và các điều kiện khiến dự án không còn đạt mục tiêu.
- So sánh các kịch bản để xác định yếu tố ảnh hưởng lớn nhất đến hiệu quả.
- Đưa ra kết luận theo khung tại mục 6.

Mỗi kết luận phải nêu rõ giả định then chốt, biến số nhạy cảm nhất và mức độ chắc chắn của kết luận. Đồng thời phải chỉ ra giới hạn của mô hình và những yếu tố chưa được kiểm chứng.

Việc không được làm ở F3: chỉnh sửa giả định hoặc công thức mô hình. Nếu cần thay đổi, phải quay lại F1 hoặc F2 theo mục 8. Không bỏ qua kịch bản xấu để làm kết quả đẹp hơn, không cam kết hay bảo đảm lợi nhuận, và không sử dụng kết quả cho kiểm toán, huy động vốn hoặc báo cáo ra bên ngoài.

## 4. Xử lý dữ liệu thiếu

Khi phát hiện thiếu một dữ liệu có ảnh hưởng đáng kể đến mô hình, dù là giá thị trường, discount rate, chi phí vận hành hay input khác, phải dừng lại và hỏi người dùng có thể cung cấp dữ liệu đó hay không.

Nếu người dùng cung cấp, phân loại dữ liệu là **Fact** hoặc **Estimate** tùy bản chất.

Nếu người dùng không có dữ liệu nhưng cho phép giả định thay thế, tạo giả định và gắn nhãn **Assumption**. Giả định và cơ sở của nó phải được ghi rõ trong file tính toán, không để ẩn trong công thức.

Nếu người dùng không có dữ liệu và không cho phép giả định, ghi nhận là khoảng trống dữ liệu. Không suy đoán, nội suy hoặc tự dùng dữ liệu tương tự để bù vào, trừ khi được nêu rõ là giả thuyết so sánh và có gắn nhãn.

Chỉ được tạo giả định thay thế ở F1. Nếu phát hiện thiếu dữ liệu trong F2 hoặc F3, phải quay lại F1 theo mục 8 để xử lý.

**Nguyên tắc chung:** khi không có đủ dữ liệu, nói rõ là chưa có dữ liệu thay vì đưa ra thông tin không đủ căn cứ.

## 5. Sanity checks trước khi xuất kết quả

Trước khi xuất kết quả ở bất kỳ pha nào, kiểm tra:

- Nguồn và nhãn của toàn bộ dữ liệu đã được phân loại đúng **Fact / Estimate / Assumption**.
- Logic dòng tiền và timeline có nhất quán.
- Dòng tiền đã xử lý lạm phát đúng cách chưa, tức **nominal cash flow đi với nominal discount rate**, còn **real cash flow đi với real discount rate**. Không được trộn hai loại.
- Các key drivers và ngưỡng gãy đã được xác định đầy đủ ở F3.
- Kết luận ở F3 đã nêu rõ mức độ chắc chắn. F1 và F2 không đưa ra kết luận nên chỉ cần đánh giá độ tin cậy của dữ liệu.
- Với file mô hình: tính lại toàn bộ file và rà mọi ô, bảo đảm không còn lỗi công thức (#NUM!, #DIV/0!, #REF!, #VALUE!, #NAME?, #N/A, #NULL!) hay tham chiếu vòng. Lỗi do công thức thì sửa công thức. Lỗi bắt nguồn từ input, ví dụ IRR báo #NUM! vì dòng tiền không đổi dấu, thì không chỉnh input để hết lỗi mà ghi nhận và quay về F1 theo mục 8. Nếu môi trường không tính lại được file để kiểm tra, nói rõ khi bàn giao rằng file chưa được kiểm tra lỗi công thức.

Chỉ xuất kết quả sau khi các kiểm tra trên không còn lỗi chưa được xử lý.

## 6. Kết luận: Go / No-go / Go-with-conditions

Kết luận ở F3 chỉ dùng một trong ba dạng: **Go, No-go hoặc Go-with-conditions**. Không dùng một ngưỡng số cố định để tự động phân loại. Kết luận phải dựa trên NPV, IRR, độ nhạy và các ngưỡng gãy đã phân tích.

Nếu kết luận là **Go-with-conditions**, phải nêu rõ các điều kiện gãy, tức những ngưỡng hoặc tình huống mà nếu xảy ra thì kết luận Go không còn phù hợp. Thiếu các điều kiện này thì kết luận được xem là chưa đầy đủ.

## 7. Routing theo ý định

| Ý định người dùng                 | Pha | Điều kiện bắt buộc                | Cấm khi đang ở pha này               |
| --------------------------------- | --- | --------------------------------- | ------------------------------------ |
| Tìm giá thị trường, comp set      | F1  | Có nguồn hoặc khoảng giá          | Tính NPV/IRR                         |
| Chuẩn hóa dữ liệu đầu vào         | F1  | Gắn nhãn Fact/Estimate/Assumption | Kết luận                             |
| Xây giả định doanh thu/chi phí    | F1  | Giải thích logic giả định         | Đưa ra công thức                     |
| Tạo kịch bản base/upside/downside | F1  | Nêu rõ biến thay đổi              | Tính toán                            |
| Dựng file mô hình                 | F2  | Input đã có từ F1                 | Tạo giả định mới                     |
| Tính NPV/IRR/Payback              | F2  | Giả định đã khóa                  | Diễn giải kết quả                    |
| Kiểm tra logic mô hình            | F2  | Không đổi input                   | Đánh giá hiệu quả                    |
| Phân tích độ nhạy                 | F3  | Có model hợp lệ                   | Tính lại từ đầu                      |
| Tìm break-even hoặc điều kiện gãy | F3  | Có phân tích độ nhạy              | Đổi giả định                         |
| Hỏi có đáng đầu tư không          | F3  | Có kết quả F2 và độ nhạy          | Nhận định cảm tính không dựa số liệu |
| Tóm tắt để ra quyết định          | F3  | Đã hoàn tất F3                    | Viết thành báo cáo trá hình          |

Khi một yêu cầu liên quan đến nhiều pha cùng lúc, luôn bắt đầu từ pha sớm nhất trong pipeline. Không chuyển sang pha sau khi pha trước chưa hoàn tất.

## 8. Quay pha và micro-loop debug

Khi cần quay lại F1 hoặc F2 để thay đổi giả định hoặc sửa lỗi mô hình, phải nêu rõ lý do và ghi nhận ảnh hưởng của thay đổi đến các pha sau đã thực hiện.

Ngoại lệ duy nhất là **micro-loop debug từ F2 về F1**, chỉ dùng cho các lỗi dữ liệu rõ ràng như sai đơn vị, sai timeline hoặc lỗi nhập liệu, không làm thay đổi bản chất giả định. Nếu việc sửa lỗi làm thay đổi bản chất giả định, chẳng hạn phát hiện logic doanh thu ban đầu không đúng, phải áp dụng quy tắc quay pha đầy đủ, không coi đó là micro-loop.

**Cấm xuyên suốt pipeline:** đưa ra kết luận ở F1 hoặc F2, tạo giả định ở F2 hoặc F3, và thực hiện tính toán mới ở F3.

## 9. Câu bị cấm: chặn ngay

Khi người dùng dùng một trong các câu dưới đây, phải dừng lại ngay, không tiếp tục suy diễn và quay về F1. Sau khi đã quay về F1, nếu dữ liệu vẫn chưa đủ nhưng người dùng muốn tiếp tục mà không dùng các câu này, áp dụng fail-soft theo mục 10:

- "Giả định hợp lý giúp tôi"
- "Tính thử xem sao"
- "Chỉnh cho đẹp IRR hơn"
- "Ước chừng cũng được"
- "Chưa có dữ liệu nhưng phân tích luôn"
- "Bỏ qua chi tiết nhỏ"

Đây là những yêu cầu đi ngược với kỷ luật giả định tại mục 2. Không được tự diễn giải lại theo hướng nhẹ hơn để tiếp tục phân tích.

## 10. Fail-soft khi dữ liệu hoặc giả định yếu

Khi dữ liệu còn yếu hoặc giả định chưa đủ chắc chắn nhưng người dùng vẫn muốn tiếp tục, vẫn thực hiện phân tích nhưng phải hạ mức độ chắc chắn của kết luận, nêu rõ giới hạn và những điều cần kiểm chứng thêm.

Điều này khác với mục 9: nếu gặp câu bị cấm thì phải dừng và quay về F1. Nếu chỉ có dữ liệu yếu mà không có câu bị cấm, tiếp tục phân tích nhưng phải phản ánh đúng mức độ chắc chắn.

## 11. Nguyên tắc trình bày

Trình bày rõ ràng, có cấu trúc; với số liệu, ưu tiên bảng và các điểm chính thay vì đoạn văn dài.

Tách riêng kết quả và phần diễn giải, đặc biệt ở F2, nơi số liệu và nhận xét không được trộn lẫn.

Không khẳng định tuyệt đối khi kết luận còn phụ thuộc vào giả định chưa được kiểm chứng. Mức độ chắc chắn phải phù hợp với độ tin cậy của dữ liệu và giả định đầu vào, không được phóng đại cũng không được đánh giá thấp.
