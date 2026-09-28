# Đối chiếu chất lượng cục bộ — rectangle

Teaching reference, không phải gold set đã phê duyệt; không có điểm đạt tự động.
Nguồn: export r1_craft đã khóa SHA256 `6f2fd5d7b4777b35b80719538f45b28b2de86f7b22f051f812f8e38c4b6a310b`; slice `B3-dense`.
Ghép hình học greedy một-một theo IoU ≥ 0.50, rồi so class; H ≥ 40 px.
Box trái nằm chủ yếu trong ignore_region reference không tính. Polygon, polyline, track không được chấm.
Đây là phép tính offline của lab, không phải báo cáo hay kết quả tương đương CVAT Premium.

Frame được tính: adasind_145860.jpg, adasind_167700.jpg, adasind_199770.jpg. Frame thiếu trong export: không.
TP=14; FP=4; FN=6; số lần đối chiếu=23; mean IoU của TP=0.754.

| Chỉ số | Micro | Macro | Nhãn thấp nhất |
|---|---:|---:|---:|
| accuracy | 0.609 | 0.928 | 0.870 |
| precision | 0.778 | 0.733 | 0.000 |
| recall | 0.700 | 0.583 | 0.000 |
| jaccard | 0.583 | 0.508 | 0.000 |
| dice | 0.737 | 0.624 | 0.000 |

| Nhãn | TP | FP | FN | Accuracy | Precision | Recall | Jaccard | Dice |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Bike | 3 | 0 | 3 | 0.870 | 1.000 | 0.500 | 0.500 | 0.667 |
| Car | 1 | 0 | 1 | 0.957 | 1.000 | 0.500 | 0.500 | 0.667 |
| Pedestrian | 3 | 0 | 1 | 0.957 | 1.000 | 0.750 | 0.750 | 0.857 |
| ThreeWheeler | 3 | 2 | 1 | 0.870 | 0.600 | 0.750 | 0.500 | 0.667 |
| Truck | 4 | 1 | 0 | 0.957 | 0.800 | 1.000 | 0.800 | 0.889 |
| ignore_region | 0 | 1 | 0 | 0.957 | 0.000 | 0.000 | 0.000 | 0.000 |

| Frame | TP | FP | FN | Accuracy | Precision | Recall |
|---|---:|---:|---:|---:|---:|---:|
| adasind_145860.jpg | 2 | 0 | 0 | 1.000 | 1.000 | 1.000 |
| adasind_167700.jpg | 7 | 2 | 2 | 0.700 | 0.778 | 0.778 |
| adasind_199770.jpg | 5 | 2 | 4 | 0.455 | 0.714 | 0.556 |

Confusion matrix: hàng = teaching reference; cột = export đã khóa.
`<missing>` là thiếu box; `<extra>` là box thừa. Xem `local_quality_confusion.csv`.

| Reference \ Export | Bike | Car | Pedestrian | ThreeWheeler | Truck | ignore_region | <missing> |
|---|---:|---:|---:|---:|---:|---:|---:|
| Bike | 3 | 0 | 0 | 0 | 0 | 0 | 3 |
| Car | 0 | 1 | 0 | 0 | 1 | 0 | 0 |
| Pedestrian | 0 | 0 | 3 | 0 | 0 | 0 | 1 |
| ThreeWheeler | 0 | 0 | 0 | 3 | 0 | 0 | 1 |
| Truck | 0 | 0 | 0 | 0 | 4 | 0 | 0 |
| ignore_region | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| <extra> | 0 | 0 | 0 | 2 | 0 | 1 | 0 |

Chi tiết xung đột trong `local_quality_conflicts.csv`; dữ liệu máy đọc trong `local_quality.json`.
Mismatching label đóng góp một FP cho class vẽ và một FN cho class reference; attribute khác được báo riêng.
Micro accuracy đếm mỗi cặp ghép sai class là một lần đối chiếu; Jaccard đếm cả FP và FN.
Macro/worst bỏ nhãn không xuất hiện ở cả hai phía; chỉ số không có mẫu là N/A.
