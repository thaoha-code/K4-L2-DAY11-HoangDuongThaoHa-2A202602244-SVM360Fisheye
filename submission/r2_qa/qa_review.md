# QA review · B3-dense

Mã khóa: 6F2F-D5D7

| frame              | object_ref | rule_id         | nhận xét                                                                           |
| ------------------ | ---------- | --------------- | ------------------------------------------------------------------------------------ |
| adasind_167700.jpg | L3         | R_spurious      | Box hẹp, chồng lấn nhiều với L1/L2, nghi là vật thừa không tồn tại riêng |
| adasind_167700.jpg | L11        | R_class         | Tỷ lệ vuông bất thường cho Truck, nghi sai class (có thể là Car)            |
| adasind_199770.jpg | L6         | R_ignore_region | ignore_region đang vẽ dạng box, sai định dạng — phải là polygon             |
| adasind_199770.jpg | L5         | R_spurious      | Box rất nhỏ, gần trùng vị trí với L3, nghi thừa                              |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
