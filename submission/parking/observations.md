# Quan sát vạch ô đỗ

- Quan sát vạch ô đỗ
- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): Đã vẽ các vạch sơn phân chia ô đỗ xe nằm ở khu vực tiền cảnh và trung cảnh của bãi đỗ.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: Không vẽ các đường viền mép biên ngoài cùng không rõ ràng hoặc các vết loang trên mặt đường vì chúng không phải là vạch chia ô đỗ xe riêng biệt.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: Vùng `free_space` bao phủ phần mặt đường trống của lối xe chạy giữa các hàng ô đỗ, dừng lại trước các xe ô tô hoặc khu vực bị che khuất, không đè lên xe hay vật cản.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): Không có.
