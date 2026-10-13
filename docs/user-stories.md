# PHÂN TÍCH YÊU CẦU - EDUHUB USER STORIES

## 1. Sinh viên (Student)

### US-01 · Sinh viên: hủy phiếu đăng ký tham gia sự kiện
① Phiếu đăng ký đang ở trạng thái Pending hoặc Confirmed ➔ hủy đăng ký gọi phương thức Cancel() ➔ trạng thái đổi thành Cancelled và hoàn lại chỗ trống
② Phiếu đăng ký đã Cancelled ➔ bấm hủy đăng ký lần nữa ➔ bị từ chối (giữ nguyên trạng thái)

### US-02 · Sinh viên: đăng ký sự kiện trực tuyến (Online)
① Sự kiện Online còn chỗ ➔ đăng ký ➔ tạo phiếu Registration (Pending = chờ xác nhận)
② Sự kiện Online hết chỗ (đủ Capacity) ➔ đăng ký ➔ báo lỗi sự kiện đã hết chỗ

---

## 2. Ban CLB (Club Board)

### US-03 · Ban CLB: duyệt phiếu đăng ký của sinh viên
① Phiếu Pending ➔ bấm duyệt gọi phương thức Confirm() ➔ trạng thái chuyển thành Confirmed
② Phiếu đã bị sinh viên Cancelled ➔ bấm duyệt ➔ bị từ chối (báo lỗi InvalidOperationException)

### US-04 · Ban CLB: cập nhật lại sức chứa của sự kiện
① Capacity mới >= số người đã Confirmed ➔ lưu ➔ cập nhật Capacity thành công
② Capacity mới < số người đã Confirmed ➔ lưu ➔ báo lỗi (không được nhỏ hơn số người đã duyệt)

---

## 3. Admin (Quản trị hệ thống)

### US-05 · Admin: kích hoạt lại tài khoản thành viên
① Tài khoản đang bị ngừng (IsActive = false) ➔ kích hoạt lại ➔ trạng thái chuyển thành IsActive() = true
② Tài khoản đang hoạt động sẵn (IsActive = true) ➔ cố bấm kích hoạt lại ➔ hệ thống thông báo "Tài khoản này đã ở trạng thái hoạt động"

### US-06 · Admin: kiểm tra tính hợp lệ khi tạo thành viên
① Tên, MSSV hợp lệ và email có chứa '@' ➔ tạo thành viên ➔ thành công (Status = Active)
② Email thiếu ký tự '@' hoặc để trống ➔ tạo thành viên ➔ báo lỗi ArgumentException (không tạo thành viên)