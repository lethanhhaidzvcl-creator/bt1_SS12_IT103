# bt1_SS12_IT103

# README.md

## 1. Phân tích lỗi

Lỗi nằm ở điều kiện `sub.daysOverdue >= 3`.

Điều kiện này khiến thuê bao bị hạ cấp ngay khi nợ cước đúng 3 ngày. Theo yêu cầu, thuê bao được giữ gói cũ trong 3 ngày đầu và chỉ bị hạ cấp khi nợ cước trên 3 ngày.

Cách sửa: đổi điều kiện `sub.daysOverdue >= 3` thành `sub.daysOverdue > 3`.

Khi nợ cước trên 3 ngày, hệ thống hạ cấp gói về `FREE`, giới hạn thiết bị còn 1 và chuyển trạng thái thành `EXPIRED`. Nếu nợ cước từ 1 đến 3 ngày, trạng thái là `GRACE_PERIOD` và giữ nguyên gói thuê bao.

## 2. Bảng Test Cases

| Trường hợp kiểm thử | Dữ liệu đầu vào | Kết quả sai thực tế | Kết quả đúng mong đợi |
|---|---|---|---|
| Nợ cước đúng 3 ngày | `daysOverdue = 3`, `planTier = 'FAMILY'`, `deviceLimit = 5` | Hạ cấp về `FREE`, giới hạn 1 thiết bị, trạng thái `EXPIRED` | Giữ gói `FAMILY`, giới hạn 5 thiết bị, trạng thái `GRACE_PERIOD` |
| Nợ cước 4 ngày | `daysOverdue = 4`, `planTier = 'FAMILY'`, `deviceLimit = 5` | Hạ cấp về `FREE`, giới hạn 1 thiết bị, trạng thái `EXPIRED` | Hạ cấp về `FREE`, giới hạn 1 thiết bị, trạng thái `EXPIRED` |

## 3. Kết luận

Đã sửa điều kiện từ `>= 3` thành `> 3`, giúp chương trình xử lý đúng thời gian ân hạn thanh toán và cập nhật đồng bộ thông tin thuê bao.
