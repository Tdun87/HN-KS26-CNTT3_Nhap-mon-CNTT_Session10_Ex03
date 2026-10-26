

# BÀI 3: CHUẨN HÓA QUY TRÌNH GIAO VẬN VÀ TRA CỨU GIÁ CƯỚC

## Phần 1. Phân tích mô hình VLOOKUP
* **lookup_value**: Mã vận đơn in trên gói hàng mà nhân viên kho cần tra cứu.
* **table_array**: Bảng giá cước niêm yết chuẩn dùng để đối chiếu.
* **col_index_num**: Thứ tự cột chứa số tiền cước trong bảng đối chiếu.
* **range_lookup (FALSE)**: Tìm kiếm chính xác 100% mã vận đơn, không lấy mã gần giống.

---

## Phần 2. Triển khai giải pháp cho FastMove
* **Cố định vùng tra cứu**: Sử dụng dấu `$` trong VLOOKUP (ví dụ: `KhoaHoc!$A$2:$C$8`) để bảng giá cước không bị lệch vị trí khi kéo công thức xuống 500 dòng.
* **Đảm bảo dữ liệu sạch**: Tuyệt đối không sử dụng gộp ô (Merge Cell) trong bảng tính Excel để hàm VLOOKUP hoạt động chính xác.

---

## Phần 3. Kiểm thử & Xử lý lỗi
* **Hiện tượng lỗi**: Khi mã vận đơn chứa ký tự lạ hoặc không tồn tại trong bảng giá, hàm VLOOKUP sẽ trả về lỗi `#N/A`.
* **Giải pháp xử lý**: Bọc hàm VLOOKUP bằng hàm `IFERROR` để hiển thị thông báo thân thiện:
  `=IFERROR(VLOOKUP(E2, KhoaHoc!$A$2:$C$8, 3, FALSE), "Không tìm thấy mã")`

