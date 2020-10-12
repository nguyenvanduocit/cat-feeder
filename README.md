# cat-feeder

Project hỗ trợ cho mèo ăn tự động.

## Thành phần

Dự án bao gồm phần cứng, firmware và phần mềm điều khiển.

## Phần cứng

1. ESP32
1. Button xác định start point cho hành trình của động cơ bước
1. Button để kích hoạt cho ăn tự động
1. Mạch điều khiển động cơ bước ULN2003
1. Động cơ bước 28BYJ-48

### Kết nối phần cứng

[Ảnh minh hoạ]

## Firmware

Project sử dụng platformIO để hỗ trợ build và quản lý project firmware.

1. Platform Espressif 32
1. Framwork Arduino
1. AccelStepper để điều khiển động cơ bước
1. WifiManager để quản lý wifi
1. Thư viện nanopb để encode/decode rpc message

## PHầm mềm điều khiển

1. Flutter

Khi ứng dụng được mở, sẽ kết nối tới mqtt broker và gửi trạng thái vào cat-feeder/connection. Thông tin này sẽ được hiển thị dạng đèn nhấp nháy trên thiết bị.

App gửi yêu cầu lấy schedule và devide sẽ hồi đáp.

## Kết nối

Sử dụng MQTT để kết nối.

1. cat-feeder/connection: Trạng thái kết nối của device và app, có thể có các giá trị, device-connected, device-disconnected, app-connected, app-disconnected
1. cat-feeder/feed: Bắt đầu cho ăn, chứa thông tin về số muỗn cần cho ăn.
1. cat-feeder/feed-response: Trang thái cho ăn, có thể có các giá trị: feeding, feed-success, feed-failed
1. cat-feeder/set-schedule: đặt schedule để cho ăn, dữ liệu sẽ bao gồm thời gian và số muỗn cần cho ăn.
1. cat-feeder/set-schedule-response: Trạng thái set schedule.
1. cat-feeder/list-schedule Yêu cầu lấy danh schedule lưu trong device.
1. cat-feeder/list-schedule-response: trả lời về danh sách schedule