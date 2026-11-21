# Tự đánh giá — Phạm Văn Dương · G06

## Thông tin kiểm tra được

Theo `check_final.txt`, `export_final.zip` có 22 ảnh và cả 22 ảnh có `frame_meta`; checker báo 0 lỗi và 1 cảnh báo. Đây là kết quả kiểm tra tự động, không thay thế việc tự mở lại và rà soát ảnh.

Đã xác nhận cảnh báo D02: người nằm ngang ảnh, nên trái/phải được xác định theo người, không theo trục trái/phải của ảnh.

Đối chiếu hai export mới, cả hai có đủ 22 ảnh; checker báo 0 lỗi và 1 cảnh báo ở D02. Diff hiện không còn khác biệt. Các quyết định review và giá trị cuối được ghi trong `disagreement_log.csv`.

## 1. Tự rà soát 4 cảnh

Chọn 2 ảnh S## và 2 ảnh D## có lỗi cần nhìn lại. Các sửa đổi đã được đưa vào export hiện tại.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01_rgb.png, S01_ir.png | infant_seat.facing | Sai hướng ghế | Đã gán `rear`; hướng đúng là `front`. Đã sửa. | Có |
| S05_rgb.png, S05_ir.png | infant_seat.seat | Sai vị trí ghế | Đã gán `rear_left`; vị trí đúng theo xe là `rear_right`. Đã sửa. | Có |
| D03.png | face13: mouth_right | Lệch điểm | Điểm skeleton `mouth_right` bị đặt lệch; đã sửa và export lại. | Có |
| D06.png | face.eye_left; face.gaze_zone; face13.mouth_right | Sai thuộc tính/cờ | Đã sửa theo review: `eye_left=open`, `gaze_zone=other`, `mouth_right.occluded=0`. | Có |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Nhầm hướng/vị trí ghế em bé ở hai khung: S01 `facing` gán `rear` thay vì `front`; S05 `seat` gán `rear_left` thay vì `rear_right`. Ngoài ra, điểm `mouth_right` ở D03 bị đặt lệch.

Vì sao mình mắc: Chưa tách bạch hướng quay của ghế (`facing`) với vị trí ghế theo xe (`seat`); ở S05 còn nhầm trái/phải của ảnh với phía của xe. Nguyên nhân đặt lệch điểm D03 chưa xác định.

Lần sau tránh bằng cách: Xác định riêng hướng quay và vị trí theo xe trước khi gán; rà tên/vị trí từng điểm face13 trước khi export.

Các sửa đổi khác theo review chéo: D06 (eye_left, gaze_zone, mouth_right), các cờ face13 ở D05 và gaze_zone ở S08; đã ghi chi tiết trong `disagreement_log.csv`.

## 3. Ghi chú về disagreement_log

S01 `infant_seat.facing`: peer chọn `front`, nhãn `rear` của mình sai. Bài học: xác định hướng ghế theo chiều ghế thực tế, không nhầm với vị trí ghế trong xe. Các quyết định review chéo khác được ghi trong `disagreement_log.csv`.
