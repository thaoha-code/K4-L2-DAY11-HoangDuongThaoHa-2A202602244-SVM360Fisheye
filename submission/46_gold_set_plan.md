# Gold Set Plan — SVM 4 Camera

## Mục tiêu

Chọn 200 frame đại diện cho 4 camera × 2 điều kiện từ 50.000 frame giả lập,
đảm bảo coverage đủ các ca khó đặc thù từng camera.

## Phân bổ frame (xem 45_sampling_plan.csv)

| Camera          | Normal       | Hard          | Tổng         |
| --------------- | ------------ | ------------- | ------------- |
| Front           | 20           | 25            | 45            |
| Rear            | 20           | 35            | 55            |
| Left            | 20           | 30            | 50            |
| Right           | 20           | 30            | 50            |
| **Tổng** | **80** | **120** | **200** |

## Lý do phân bổ hard nhiều hơn normal

- Rear/hard nhiều nhất (35): vật thấp bị ego_body che là lỗi nguy hiểm nhất
- Left/hard và Right/hard (30): vòng kính fisheye cắt vật, người đi bộ sát xe
- Front/hard ít hơn (25): trường nhìn rộng hơn, lỗi ít nghiêm trọng hơn rear

## Tiêu chí loại frame

- Frame quá tối hoặc quá sáng không phân biệt được vật
- Frame liên tiếp giống nhau >80% (chọn 1 trong chuỗi đó)
- Frame không có vật nào trong vùng hợp lệ

## Cập nhật sau P4

*(Bổ sung sau khi hoàn thành diagnosis — ghi lỗi thực tế ảnh hưởng tiêu chí chọn frame)*
