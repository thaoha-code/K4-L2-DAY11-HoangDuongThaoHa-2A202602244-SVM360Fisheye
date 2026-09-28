# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone   | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
| ------ | ----: | --------: | ---------: | ----------------------------------: | --------------------------------: | ------------------------ |
| center |     9 |         1 |          2 |                                   2 |                                 3 | WRONG_CLASS (1)          |
| mid    |     7 |         3 |          1 |                                   3 |                                 4 | MISSING (3)              |
| edge   |     4 |         2 |          1 |                                   4 |                                 3 | MISSING (2)              |

## Nhận xét

- Zone nào người (L) và model (M) gãy nhiều nhất, dẫn số ở bảng trên: Zone **edge** gãy nhiều nhất — L missing 2/4 (50%), M missing 4/4 (100%). Kế đến là **mid** — L missing 3/7 (~43%), M missing 3/7 (~43%). Zone **center** ít missing nhất (1/9 ≈ 11%) nhưng có tỷ lệ spurious cao nhất (2/9) và là zone duy nhất xuất hiện WRONG_CLASS.
- Giả thuyết vì sao (méo fisheye, box lỏng, thiếu `ego_body`, ...) và giới hạn của slice ba frame: Ở edge, méo fisheye kéo dài/biến dạng vật và vật thường nằm sát `lens_border`, khiến cả người và model khó đạt đủ H=40px hoặc dễ lẫn với ignore_region, nên missing cao ở cả hai phía. Ở mid, vật đứng gần nhau gây che khuất một phần, dễ bỏ sót hoặc box lỏng không tách được từng vật. Ở center, box rõ nhất nên missing thấp nhưng ranh giới phân loại (Truck/Car) chưa nhất quán gây WRONG_CLASS. Giới hạn: slice chỉ 3 frame nên n_ref từng zone rất nhỏ (4–9), số liệu dễ nhiễu, chưa đủ để khẳng định pattern hệ thống.
