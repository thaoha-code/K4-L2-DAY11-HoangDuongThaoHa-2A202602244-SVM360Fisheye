# Guideline patch

- **Rule mới đề xuất:** Khi box gần vuông (tỷ lệ width/height trong khoảng 0.8–1.2) và không thấy rõ khoang chở hàng/khung xe dài đặc trưng, ưu tiên gán nhãn `Car` thay vì `Truck`; chỉ gán `Truck` khi thấy rõ thùng xe hoặc kích thước dài rõ rệt theo trục ngang.
- **Áp dụng cho:** class `Car` và `Truck` (bounding box), toàn bộ zone nhưng đặc biệt ở center/mid nơi vật đứng gần camera và dễ thấy tỷ lệ hình học rõ.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** Rule hiện tại chỉ mô tả định nghĩa chung của từng class, không có tiêu chí hình học cụ thể để phân biệt khi vật ở góc nhìn khiến box gần vuông — dẫn tới nhầm lẫn đã xác nhận qua confusion matrix (`local_quality.md`: 1 Car bị gán thành Truck, object L11 trong `adasind_167700.jpg`, box 127.7×135.3, tỷ lệ ~0.94).
- **`rules_version` mới:** v1.0.0 → v1.1.0
- **Hiệu lực từ:** Round `rework` (R2) trở đi — áp dụng ngay khi sửa lại nhãn Car/Truck trong bản rework này.
