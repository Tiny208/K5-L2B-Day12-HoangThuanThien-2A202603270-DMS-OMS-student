# Danh sách lớp v0 — Hoàng Thuận Thiên · G07

Viết tiếp từ slide 54 bài giảng. Mỗi lớp trả lời: **model cần nhận ra cái này để làm gì?**

## DMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `eye_state` | open / closed / unknown | Đo chỉ số PERCLOS và EAR (Eye Aspect Ratio) để phát hiện tài xế buồn ngủ hoặc ngủ gật thời gian thực | Có (NIR phân biệt rõ con ngươi đen và mống mắt sáng, trừ khi bị chói lóa kính) |
| 2 | `head_pose` | yaw, pitch, roll (hoặc vùng nhìn định tính) | Ước lượng hướng đầu 3D để phát hiện mất tập trung (Distraction) khi quay đầu nói chuyện hoặc cúi gập quá 2 giây | Có (nhận diện rõ hình thái học khuôn mặt và các góc quay 3D trên ảnh NIR) |
| 3 | `gaze_zone` | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Giám sát vector ánh nhìn, phát hiện hành vi liếc nhìn màn hình giải trí hoặc nhìn điện thoại trên đùi khi xe đang chạy | Có (xác định vị trí con ngươi tương quan với khóe mắt trên ảnh cận hồng ngoại) |
| 4 | `hands_on_wheel` | yes / no / unknown | Phục vụ tính năng lái bán tự động L2/L2+ (Hands-on Detection), phát cảnh báo nếu tài xế buông cả hai tay khỏi vô lăng quá 15 giây | Có (thấy rõ viền bàn tay và vành vô lăng, kể cả ban đêm) |
| 5 | `phone_usage` | held / mounted / lap / none | Phát hiện hành vi sử dụng điện thoại cầm tay bất hợp pháp khi điều khiển phương tiện (áp tai nghe gọi hoặc bấm phím) | Có (nhận diện phản xạ góc cạnh thân máy và màn hình điện thoại) |
| 6 | `driver_activity` | normal / smoking / drinking / eating / calling | Nhận diện các hành vi xao nhãng sinh hoạt làm giảm khả năng phản xạ và xử lý tình huống giao thông khẩn cấp | Có (thấy hình khối chai nước, tẩu thuốc hoặc động tác tay đưa lên miệng) |

## OMS (ít nhất 6 lớp)

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `child_presence` | child_seat / infant_seat / child_alone / empty | Tính năng phát hiện trẻ em bị bỏ quên trong xe (Child Presence Detection - CPD theo Euro NCAP) để kích hoạt còi báo và hạ kính | Có (nhận diện hình khối nôi xách em bé hoặc ghế trẻ em) |
| 2 | `occupant_classification` | adult / child / object / empty | Phân loại tải trọng và kích thước người ngồi để điều khiển túi khí thông minh (Smart Airbag - tắt túi khí nếu là ghế trẻ em hoặc đồ vật) | Có (dựa trên tỷ lệ khung xương và độ choán chỗ của cơ thể) |
| 3 | `seatbelt_status` | worn_correct / worn_incorrect / not_worn / unknown | Hệ thống nhắc nhở thắt dây an toàn (Seatbelt Reminder - SBR) và phát hiện các hành vi cài chốt đối phó (luồn sau lưng) | Có (nhận diện dải dây đai chéo qua vai nếu có độ tương phản đủ với áo) |
| 4 | `occupant_posture` | normal / out_of_position / lying / sleeping | Phát hiện hành khách ngồi sai vị trí an toàn (gác chân lên táp-lô, ngả ghế nằm) để điều chỉnh lực bung túi khí tránh gãy xương | Có (theo dõi khung xương cơ thể trên camera góc rộng cabin) |
| 5 | `forgotten_objects` | bag / box / phone / laptop / other | So sánh ảnh trước và sau hành trình để phát hiện hành lý, đồ vật có giá trị bỏ quên trên xe và gửi tin nhắn nhắc nhở chủ xe | Có (phát hiện vùng dị vật mới xuất hiện trên bề mặt ghế) |
| 6 | `pet_detection` | dog / cat / pet_cage / none | Phát hiện thú cưng bị bỏ lại trong khoang xe khi trời nắng gắt để kích hoạt chế độ Pet Mode duy trì nhiệt độ điều hòa an toàn | Có (nhận diện hình thái động vật hoặc lồng vận chuyển thú cưng) |

## 2 câu hỏi leo thang

Câu hỏi bạn muốn hỏi người viết guideline (hoặc khách hàng) vì guideline v1.0 chưa trả lời. Mỗi câu kèm **tên khung** làm ví dụ.

1. **Câu hỏi:** Khi chương trình cập nhật bổ sung giá trị `occupied = yes` cho ghế trẻ em (`child_seat`) có chứa đồ vật/chiếm dụng, trong trường hợp ghế trẻ em chỉ bị chăn phủ một góc nhỏ hoặc chỉ có 1 chai nước/đồ vật rất nhỏ đặt trên đệm ghế thì ngưỡng diện tích chiếm dụng tối thiểu bao nhiêu % sẽ được đánh dấu là `occupied = yes` thay vì `occupied = no`?
   - **Khung ví dụ:** `S01_rgb.png` và `S08_rgb.png` (ghế trẻ em có túi đồ bên trong).
   - **Bạn tạm gán thế nào và vì sao:** Nhóm gán `child_seat` có `occupied = yes` kèm thêm box `object` theo đúng hướng dẫn cập nhật mới nhất của chương trình học, đảm bảo phản ánh đúng thực tế ghế đang có vật chiếm chỗ.

2. **Câu hỏi:** Trên ảnh chụp camera hồng ngoại bị xoay 90° (như bộ ảnh Drive&Act), khi tài xế cúi đầu sử dụng điện thoại và một bàn tay chỉ chạm 1–2 đầu ngón tay vào vô lăng trong khi lòng bàn tay đã rời hẳn vô lăng, tiêu chuẩn tính `on_wheel = yes` được xác định theo diện tích tiếp xúc hay chỉ cần có bất kỳ điểm chạm nào?
   - **Khung ví dụ:** `D04.png`.
   - **Bạn tạm gán thế nào và vì sao:** Nhóm tạm gán `on_wheel = yes` vì mắt người quan sát thấy đầu ngón tay vẫn tiếp xúc vật lý với vành vô lăng. Cần người viết guideline xác định ngưỡng tiếp xúc cụ thể (ví dụ: nắm chặt vô lăng hay chỉ cần chạm tiếp xúc) để đồng bộ dữ liệu cho bài toán an toàn lái rảnh tay (Hands-free Driving).
