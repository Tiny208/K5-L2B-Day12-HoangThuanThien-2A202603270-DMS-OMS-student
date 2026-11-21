# TEAM — Ngày 12

Mã bộ ảnh: **G07** · Hình thức: nhóm

| Họ tên | MSSV | Đã gán đủ 22 ảnh? | Review chéo với (peer diff) | Số dòng disagreement đã xử lý |
|---|---|---|---|---|
| Hoàng Thuận Thiên | 2A202603270 | có | Hoàng Sỹ Khiêm (2A202603244) | 37 dòng |
| Hoàng Sỹ Khiêm | 2A202603244 | có | Hoàng Thuận Thiên (2A202603270) | 37 dòng |

Ca hai bạn vẫn không thống nhất và đã hỏi coach (ghi tên ảnh + đối tượng):

- `S02_rgb.png` & `S02_ir.png` (hàng ghế sau bên phải xe): Phân định hình thái giữa nôi em bé xách tay (`infant_seat`) và ghế ngồi trẻ em cỡ nhỏ (`child_seat`). Hai bạn ghi nhận trạng thái ambiguous để đối chiếu với đáp án ground-truth của coach.

## Cá nhân

Mỗi người một mục, 1–2 dòng mỗi ý.

### HoangThuanThien-2A202603270
- Phần mình làm: Gán hoàn thiện 22 khung hình cốt lõi (16 OMS + 6 DMS); trích xuất số liệu đối chiếu `diff` với bạn Khiêm và cập nhật biên bản xử lý 37 dòng bất đồng.
- Điều mình học được hôm nay: Hiểu sâu sắc sự khác biệt giữa ảnh hồng ngoại thật (NIR active illumination trên Drive&Act) và ảnh hồng ngoại mô phỏng (IR-sim trên SVIRO); nắm vững quy tắc đảo chiều ghế theo xe (trái ảnh là phải xe) và cách xử lý điểm skeleton mặt trên ảnh xoay 90 độ.
