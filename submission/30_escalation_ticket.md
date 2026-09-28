# Escalation ticket

## Ticket 1

- **Frame:** adasind_199770.jpg và toàn slice B3-dense (Bike recall = 0.500, 3/6 bị bỏ sót)
- **Ảnh chụp:** `submission/screenshots/bike_missing_199770.png` (chụp vùng nửa phải ảnh, x>800, nơi không có box Bike nào dù reference có)
- **Expected impact:** Bike/xe hai bánh là đối tượng nguy hiểm cao trong SVM (dễ va chạm ở tốc độ thấp, blind spot). Recall 0.500 nghĩa là mô hình huấn luyện trên dữ liệu này sẽ bỏ sót một nửa số xe đạp/xe máy thực tế — rủi ro an toàn nghiêm trọng nếu đưa vào hệ thống cảnh báo va chạm.
- **Owner:** `annotator`
- **Recommendation:** Bổ sung bước bắt buộc trong self-QC checklist: quét lại toàn khung hình theo lưới trước khi khóa (Ctrl+S), ưu tiên kiểm tra vùng rìa phải/trái nơi Bike dễ bị bỏ sót do kích thước nhỏ và nằm gần mép ảnh. Đề xuất thêm rule R_bike_scan vào `docs/02-rules-vi.md` (liên kết với `20_guideline_patch.md`).
