## BillRoute
- Admin xem chi tiết của một hóa đơn
- Admin xem toàn bộ hóa đơn
- Admin lọc hóa đơn 
	- Từ ngày đến ngày
	- Theo mã hóa đơn
	- Theo tên khách hàng
- Khách xem chi tiết giỏ hàng
- Khách thêm món ăn vào hóa đơn
	- Tìm hóa đơn chưa thanh toán:
		- Nếu có thì thêm món ăn vào hóa đơn đó, nếu không thì thêm món ăn vào hóa đơn đã tồn tại
		- Nếu không thì thêm món ăn vào hóa đơn mới
	- Nếu món ăn đã có trong hóa đơn, tăng số lượng món ăn lên 1
- Khách xóa món ăn ra khỏi hóa đơn
- Khách thanh toán hóa đơn (có mã giảm giá, phương thức thanh toán, đợi figma xong để xác nhận lại)
- Khách xem lịch sử hóa đơn của mình (giống admin lọc hóa đơn theo mã khách hàng)

## TableRoute
- Admin thêm bàn
- Admin xóa bàn
- admin sửa bàn
- Admin xem thông tin đặt bàn (thường)
- Admin lọc bàn
	- Theo tình trạng
	- Theo vị trí
	- Theo ngày đặt
- Khách xem thông tin đặt bàn (khách, web socket)
- Khách đặt bàn
- Khách hủy đặt bàn
- Khách kiểm tra tình trạng đặt bàn (xem bàn đang được đặt của một khách)

## RevenueRoute
- Tính tổng doanh thu 
	- Tổng
	- Từ ngày đến ngày
	- Theo khách hàng
	- Theo mã hóa đơn