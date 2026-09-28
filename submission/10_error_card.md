# Error analysis card

## Zone × block

| zone    | block | what | count |
| ------- | ----- | ---- | ----: |
| unknown |       |      |     9 |

## Top defects

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: Lỗi nổi bật nhất là **WRONG_CLASS Car→Truck** tại `adasind_167700.jpg` (object_ref L11/R4). Confusion matrix trong `local_quality.md` xác nhận: 1 Car của reference bị gán nhãn thành Truck trong export đã khóa. Nguyên nhân khả dĩ là ranh giới phân loại Car/Truck chưa rõ khi vật ở tư thế nghiêng trên ảnh fisheye — kích thước box (127.7×135.3, gần vuông) không cho thấy rõ đặc trưng dài của Truck, dễ nhầm với Car cỡ lớn.
- Cách sửa và ai nhận việc (`owner`): Mở lại frame `adasind_167700.jpg` trong CVAT, xem object tại vị trí (571.9,869.8), so sánh tỷ lệ khung gầm/kích thước với các Car/Truck khác đã label đúng trong slice để xác định lại class chính xác. Owner: thaoha (annotator chính, tự sửa trong bước rework).
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `findings.csv` dòng "adasind_167700.jpg,Car→Truck,WRONG_CLASS,Confusion matrix xác nhận 1 Car bị gán nhầm thành Truck"; `local_quality.md` bảng confusion matrix hàng Car cột Truck = 1; rule liên quan: Class sáu nhãn (checklist mục 3 trong `selfqc.md`).
