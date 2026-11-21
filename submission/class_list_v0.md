# Danh sách lớp v0 — Phạm Văn Dương · G06

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `face.eye_left`, `face.eye_right` | open / closed / unknown | Nhận biết trạng thái từng mắt; hỗ trợ phát hiện mắt nhắm kéo dài. | Thường thấy nếu mắt không bị che hoặc phản xạ; không rõ thì `unknown`. |
| 2 | `face.gaze_zone` | road / mirror_l / mirror_r / mirror_c / cluster / center / lap / other | Nhận biết hướng nhìn và vùng tài xế đang quan sát. | Có thể ước lượng từ mắt và hướng đầu; ảnh tối, kính hoặc mặt quay đi có thể làm không rõ. |
| 3 | `face.glasses` | unknown / none / clear / sun | Nhận biết kính làm thay đổi khả năng quan sát mắt. | Có thể thấy gọng/kính; NIR có thể làm kính râm trông trong suốt, nên dùng `unknown` khi không chắc. |
| 4 | `face13` | 13 điểm; cờ occluded / outside | Định vị đặc điểm mặt để phân tích tư thế và trạng thái tài xế; không đặt điểm không nhìn thấy. | Thường thấy một phần; phản xạ, kính, tay và góc mặt có thể che điểm. |
| 5 | `hand.on_wheel` | yes / no / unknown | Nhận biết tay tài xế có chạm vô lăng hay không. | Có thể thấy hình dạng tay; vùng tối hoặc bị che thì `unknown`. |
| 6 | `phone` | held / mounted / lap | Phát hiện việc sử dụng điện thoại khi lái xe. | Có thể nhận ra theo hình dạng và vị trí; chỉ gán khi thấy ít nhất một phần hình dạng điện thoại. |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` + `seat` | driver / front_passenger / rear_left / rear_middle / rear_right | Đếm người và xác định vị trí ngồi trong xe. | Thường nhận ra theo hình dáng người và vị trí; gọi ghế theo xe, không theo trái/phải ảnh. |
| 2 | `person.seatbelt` | worn_correct / worn_incorrect / not_worn / unknown | Theo dõi tình trạng dây an toàn của người ngồi. | Chỉ thấy khi dải dây đủ rõ; không suy ra từ ảnh khác. Trên SVIRO chỉ dùng `not_worn` hoặc `unknown`. |
| 3 | `child_seat` | occupied: no / unknown; seat | Phát hiện ghế trẻ em và tình trạng có nhìn rõ bên trong hay không. | Có thể nhận ra hình dáng ghế; vùng bên trong tối hoặc bị che thì `unknown`. |
| 4 | `infant_seat` | facing: rear / front; seat | Phát hiện nôi/ghế em bé và hướng quay của ghế. | Thường dựa vào hình dạng và hướng đặt; IR không cung cấp màu đáng tin cậy. |
| 5 | `object` | type: bag / box / cup / other; seat | Nhận biết đồ vật trong cabin, hỗ trợ kiểm kê và phát hiện vật bị bỏ quên. | Dựa vào hình dáng, vị trí và ngữ cảnh; không đoán theo màu ảnh IR. |
| 6 | `face` (box trong OMS) | box mặt người lớn | Gắn vùng mặt với người trong xe để biểu diễn người lớn nhất quán. | Có thể thấy đường viền mặt; OMS chỉ yêu cầu box, không gán thuộc tính DMS cho mặt trong SVIRO. |

## 2 câu hỏi leo thang

1. D02 từng có bất đồng `gaze_zone` (`road` / `cluster`) và đã thống nhất `road`. Khi mắt và hướng đầu không cho cùng một tín hiệu rõ ràng, tiêu chí nào được ưu tiên để phân biệt nhìn đường với nhìn cụm đồng hồ?
   Khung ví dụ: D02.png.
   Tạm gán `road` theo hướng nhìn đã thống nhất sau khi xem lại ảnh.

2. Với `camera_blocked`, guideline chưa nêu ngưỡng cho trường hợp chỉ một phần vùng nhìn của camera bị che. Khi nào trường hợp đó phải gán `yes` thay vì `no`?
   Khung ví dụ: D05.png.
   Tạm gán `no` cho D05 theo xác nhận sau khi kiểm tra ảnh; nếu mức che một phần vẫn không rõ, hỏi coach.
