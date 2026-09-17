# Problem backlog

Những chỗ gặp trong lúc gán nhãn mà **guideline chưa trả lời được**, cộng các pain point về công cụ.

Ghi ngay khi gặp, kể cả lúc chưa biết xử lý thế nào. Một edge case không được ghi lại thì
mỗi người sẽ tự xử lý theo một kiểu — và đó là nguồn lớn nhất của nhãn không nhất quán.

## Danh sách

| Mã | Tóm tắt | Loại | Mục guideline | Trạng thái | Kết quả |
|---|---|---|---|---|---|
| [P-001](#p-001) | Cách vẽ polyline cho lane/crosswalk chưa rõ | Guideline mơ hồ | §2, §4.2 | 🔴 Mở | — |
| [P-002](#p-002) | Frame ban đêm bị mờ và lóa mạnh, khó xác định annotation | Guideline chưa nói tới | §5 | 🔴 Mở | — |
|[P-003](#p-003) |Cách xử lý segmentation trường hợp 1 cột có nhiều biển báo, nhiều đèn|Guideline chưa nói tới ||🔴 Mở| —|
|[P-004](#p-004) |Cách xử lý segmentation trường hợp vùng trời/tòa nhà bị object khác phía trước cắt ngang|Guideline chưa nói tới ||🔴 Mở| —|

**Loại**

| Loại | Nghĩa là |
|---|---|
| Guideline chưa nói tới | Tình huống không có trong guideline |
| Guideline mơ hồ | Đọc guideline ra được hai cách hiểu trở lên |
| Guideline mâu thuẫn | Hai mục trong guideline nói ngược nhau |
| Pain point công cụ | Guideline rõ, nhưng làm trên CVAT chậm hoặc dễ sai |

**Trạng thái:** 🔴 Mở · 🗣️ Đang bàn · ↗️ Hỏi BTC · ✅ Đã chốt (trỏ sang QĐ) · 🛠️ Làm tool (trỏ sang `source-tool/`) · ⚪ Bỏ (ghi lý do)

---

## P-001

**Cách vẽ polyline cho lane/crosswalk chưa rõ**

- **Loại:** Guideline mơ hồ
- **Mục guideline:** §2, §4.2
- **Người phát hiện:** @laihoangduy2424-Lại Hoàng Duy-2A202602271 · 16/09/2026
- **Link CVAT:**
  - https://cvat.note.transformerlabs.ai/tasks/146/jobs/1439?frame=77
  - https://cvat.note.transformerlabs.ai/tasks/146/jobs/1439?frame=79
- **Mô tả:** Guideline quy định `lane/crosswalk` sử dụng Polyline nhưng chưa mô tả cụ thể
  hướng và hình học của polyline đối với zebra crossing. Vấn đề xuất hiện ở nhiều frame
  có crosswalk trong dataset.
- **Các cách hiểu:**
  1. Vẽ một polyline theo hướng người đi bộ qua đường, cắt ngang các vạch sơn của crosswalk.
  2. Vẽ polyline dọc theo các vạch sơn crosswalk, theo hướng các vạch kéo ngang mặt đường.
  3. Vẽ nhiều polyline, mỗi vạch sơn của crosswalk là một polyline riêng.
- **Xử lý tạm trong lúc chờ:** ghi nhận các frame có crosswalk và chờ mentor/lead chốt
  một quy tắc thống nhất trước khi sửa toàn bộ các frame tương tự.
- **Kết quả:** 🔴 Mở
- 
## P-002

**Frame ban đêm bị mờ và lóa mạnh, khó xác định annotation**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** §5 — Quy tắc khi class hoặc boundary không rõ
- **Người phát hiện:** @laihoangduy2424-Lại Hoàng Duy-2A202602271 · 16/09/2026
- **Link CVAT:**
  - https://cvat.note.transformerlabs.ai/tasks/146/jobs/1439?frame=76
- **Mô tả:** Toàn frame có chất lượng thị giác thấp do cảnh ban đêm, kính/camera bị mờ
  và ánh sáng từ đèn xe/đèn đường gây flare. Một số object gần vẫn nhận diện được,
  nhưng lane marking, boundary và nhiều object ở xa rất khó xác định chính xác.
  Guideline chưa nêu tiêu chí để quyết định với một frame suy giảm chất lượng toàn cục
  như vậy thì cần annotate phần còn nhìn rõ hay bỏ/escalate toàn bộ frame.
- **Các cách hiểu:**
  1. Vẫn annotate tất cả object/lane có đủ bằng chứng thị giác; phần không chắc thì bỏ và đưa review.
  2. Chỉ annotate các object rõ ràng, không annotate lane/boundary bị mất dấu do blur và glare.
  3. Đưa toàn bộ frame vào review nếu chất lượng ảnh không đủ để annotation nhất quán.
- **Xử lý tạm trong lúc chờ:** chỉ gán các đối tượng có class và boundary đủ rõ;
  không suy đoán các lane/object bị che bởi blur hoặc glare, đồng thời đánh dấu frame để reviewer kiểm tra.
- **Kết quả:** 🔴 Mở

## P-003
**Cách xử lý trường hợp 1 cột có nhiều biển báo, nhiều đèn**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** Bài SEMANTIC SEGMENTATION, không có guideline về việc tách object
- **Người phát hiện:** @linhhl2002-Hoàng Gia Linh-2A202602192 · 16/09/2026
- **Link CVAT:** https://cvat.note.transformerlabs.ai/tasks/200/jobs/1650
- **Mô tả:** Cột biển báo ở khoảng giữa, lệch phải của bức ảnh có 2 biển báo
- **Các cách hiểu:**
  1. Semantic segmentation chỉ cần gán đúng class cho pixel
- **Xử lý tạm trong lúc chờ:**
- **Kết quả:** 🔴 Mở

## P-004
**Cách xử lý trường hợp vùng trời/tòa nhà bị object khác phía trước cắt ngang**

- **Loại:** Guideline chưa nói tới
- **Mục guideline:** Bài SEMANTIC SEGMENTATION, không có guideline về việc tách object
- **Người phát hiện:** @linhhl2002-Hoàng Gia Linh-2A202602192 · 16/09/2026
- **Link CVAT:** https://cvat.note.transformerlabs.ai/tasks/200/jobs/1650
- **Mô tả:** Vùng trời và tòa nhà bị cột điện phía trước cắt thành các vùng nhỏ, có thể tách các vùng nhỏ đó thành các object riêng theo đúng class hay cần xác định cùng 1 object
- **Các cách hiểu:**
- **Xử lý tạm trong lúc chờ:**
- **Kết quả:** 🔴 Mở


## P-005
**Quy tắc gán nhãn cho nhiều xe ô tô đỗ/di chuyển san sát và bị che khuất một phần (occlusion/cluster)**
- **Loại:** Guideline mơ hồ / Thiếu case thực tế
- **Mục guideline:** §1 — Quy tắc bounding box cho Phương tiện (Car/Vehicle)
- **Người phát hiện:** @orc123-PHẠM NGỌC ĐÔNG-2A202602075 · 17/09/2026
- **Link CVAT:** https://cvat.note.transformerlabs.ai/tasks/146/jobs/1436
- **Mô tả:** Trong các khung cảnh có mật độ phương tiện cao (như hàng xe đỗ phía xa dưới bóng râm hoặc các xe di chuyển nối đuôi nhau gần nhau), các xe thường xuyên bị che khuất bởi thân xe khác, cây cối hoặc bị giảm kích thước điểm ảnh (low resolution). Guideline chưa nêu rõ ngưỡng kích thước tối thiểu (min pixel/size) để bỏ qua hay bắt buộc gán nhãn, cũng như quy tắc xử lý khi các xe đỗ san sát tạo thành một cụm (cluster).
- **Các cách hiểu:** Gán nhãn từng xe riêng lẻ bất kể khoảng cách và mức độ che khuất, ước lượng toàn bộ phần thân bị ẩn (bounding box bao trọn cả phần bị che). Chỉ gán bounding box cho phần nhìn thấy được (visible boundary), bỏ qua phần xe bị che khuất hoàn toàn. Bỏ qua các xe ở xa có kích thước nhỏ hơn ngưỡng quy định (ví dụ < 10–15 px) hoặc nằm trong cụm đỗ khuất dưới bóng râm không phân biệt rõ biên dạng từng xe; chỉ tập trung gán các xe độc lập ở cự ly gần đến trung bình.
- **Xử lý tạm trong lúc chờ:** Chỉ gán nhãn cho các xe nhìn rõ ranh giới thân xe và có kích thước nhận diện được; bật thuộc tính occluded: true cho các xe bị che khuất một phần và tránh gom nhiều xe vào một bounding box chung.
- **Kết quả:** 🔴 Mở