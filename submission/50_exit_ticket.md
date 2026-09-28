# Exit ticket

Đọc `docs/10-svm360-reading-vi.md` trước khi trả lời câu 1–2. Các câu về zone, `why`, rework, parking và sampling
đã nằm trong file tương ứng nên không hỏi lại ở đây.

1. Một vật ở vùng seam giữa hai camera thật xuất hiện với hai box khác nhau: đó là lỗi `DUPLICATE` hay cần một quy
   tắc riêng? Vì sao? **Không phải `DUPLICATE`.** `DUPLICATE` là hai box cho cùng vật trên **cùng một camera**. Ở seam, vật nằm trong vùng chồng của **hai camera khác nhau**, mỗi camera có box hợp lệ riêng — đây là hiện tượng hình học tự nhiên, không phải lỗi. Cần quy tắc riêng để **liên kết** hai box thành một vật vật lý, chỉ áp dụng được khi có timestamp đồng bộ, calibration và chính sách output rõ ràng.
2. Một vật đi qua nhiều frame trên cùng camera: khi nào giữ cùng track ID, khi nào thêm keyframe hoặc trạng thái
   Outside? Nêu bằng chứng sẽ cần trước khi nối track qua hai camera. Giữ cùng track ID khi vật còn nhìn thấy liên tục và danh tính không mơ hồ. Thêm **keyframe** khi vị trí/kích thước box đổi đáng kể để nội suy bám đúng vật. Đặt **Outside** khi vật rời khung hình hoặc bị che hoàn toàn. Trước khi nối track qua hai camera, cần: **timestamp** đồng bộ, **calibration** ánh xạ tọa độ giữa hai camera, và **chính sách output** xác định ID hợp nhất — thiếu một trong ba thì chưa đủ căn cứ.
3. Nhìn lại cả buổi: một chỗ bạn tin nhãn mình đúng nhưng reference hoặc người soát nghĩ khác (dẫn frame/`object_ref`),
   bạn đã xử lý thế nào, và nếu làm lại slice này bạn sẽ đổi gì trong cách làm? Ở `adasind_167700.jpg`, object L11 (571.9,869.8 – 127.7×135.3), tôi gán `Truck` nhưng reference gán `Car` (xác nhận qua confusion matrix). Tôi ghi thành finding `WRONG_CLASS`, `why=E2_guideline_gap` vì rule chưa có tiêu chí hình học rõ, rồi đề xuất rule mới ở `20_guideline_patch.md` thay vì tự sửa theo reference. Nếu làm lại, tôi sẽ kiểm tỷ lệ box và tìm đặc trưng thùng xe **trước khi** chọn class, thay vì chọn theo cảm giác rồi sửa sau.
