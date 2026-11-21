# Tự đánh giá — <Phạm Văn Dương> · <Gxx>

## 1. Tự rà soát 4 cảnh

Nghỉ tay 1 phút, mở lại bài của mình, chọn 4 ảnh (2 S##, 2 D##), đọc như người lạ.

Loại lỗi: `seat_flip`, `wrong_class`, `guess`, `box`, `missing`, `extra`, `lr_flip` (trái/phải mặt), `flag` (thiếu cờ điểm), `ok`.

Đã mở lại 4 ảnh và kiểm tra annotation thủ công. Không phát hiện lỗi về bounding box, phân loại đối tượng, đối tượng bị bỏ sót hoặc keypoints.

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S01 | OMS annotations | `ok` | Đã kiểm tra bounding box và nhãn đối tượng, không phát hiện sai sót. | Không cần |
| S05 | OMS annotations | `ok` | Đã kiểm tra bounding box và phân loại đối tượng, không phát hiện sai sót. | Không cần |
| D02 | face, face13 | `ok` | Đã kiểm tra vị trí keypoints và quy ước trái/phải theo người tài xế. | Không cần |
| D04 | person, face, hand, phone | `ok` | Đã kiểm tra bounding box và các thuộc tính liên quan, không phát hiện sai sót. | Không cần |

## 2. Lỗi mình lặp lại nhiều nhất hôm nay

Lỗi: Không phát hiện lỗi.

Vì sao mình mắc: Không phát hiện lỗi.

Lần sau tránh bằng cách: Tiếp tục kiểm tra kỹ bounding box, phân loại đối tượng, các đối tượng bị bỏ sót và quy ước trái/phải của keypoints trước khi hoàn thành annotation.

## 3. Ghi chú về disagreement_log

Một dòng bạn của mình đúng và mình sai. Mình học được gì từ dòng đó: …
