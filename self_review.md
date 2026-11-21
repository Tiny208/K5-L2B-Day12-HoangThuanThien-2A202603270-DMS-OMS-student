# Tự đánh giá — Hoàng Thuận Thiên · G07

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb.png | child_seat | ok | Thuộc tính `occupied = yes` chuẩn xác cho trường hợp ghế trẻ em có đồ vật chiếm dụng theo cập nhật bài học | Đã chuẩn hóa |
| S02_rgb.png | frame_meta | flag | Gán nhầm `light = day` theo cảm quan thị giác thay vì tuân thủ quy tắc ảnh mô phỏng SVIRO phải là `unknown` | Đã sửa (đổi thành `unknown` ở v2) |
| D04.png | face13 | flag | Mắt tài xế bị bóng lóa kính râm nhưng chưa bật cờ `occluded = 1` cho các điểm landmark mắt | Đã sửa (bật cờ `occluded = 1` ở v2) |
| D06.png | face | guess | Các điểm mắt trái bị che khuất nhưng vẫn phỏng đoán `eye_left = open` | Đã sửa (đổi thành `unknown` ở v2) |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Gán thuộc tính `light = day` trên các ảnh SVIRO do thói quen nhìn ảnh ban ngày sáng rõ thì chọn `day`.

Vì sao mình mắc: Do phản xạ tự nhiên khi quan sát ảnh thực tế mà chưa chú ý đến quy định kỹ thuật: ảnh SVIRO là ảnh mô phỏng 3D tổng hợp không có mốc thời gian thực, nên bắt buộc phải gán `light = unknown`.

Lần sau tránh bằng cách: Đọc kỹ tài liệu mô tả bộ dữ liệu và quy định guideline trước khi gán; chạy script kiểm tra `cabin_check` ngay ở Checkpoint A (sau 2 cảnh đầu) để bắt lỗi sớm, không để lặp lại sang các cảnh tiếp theo.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó:
Dòng kiểm tra thuộc tính `light` trên các ảnh SVIRO (`S02_rgb.png` &rarr; `S08_rgb.png`), bạn Khiêm đúng khi chọn `unknown` cho toàn bộ ảnh SVIRO. Mình học được rằng với dữ liệu thị giác máy tính, bản chất quang học và nguồn gốc dữ liệu (ảnh mô phỏng 3D không có thời gian thực) quan trọng hơn nhiều so với việc chỉ nhìn cảm tính bề ngoài.
