# 1.Tổng quan về giao thức MQTT
- MQTT (Message Queing Telemery Transport) là giao thức truyền thông điệp theo mô hình Publish/subscribe
- Được sử dụng cho các thiết bị IoT băng thông thấp, độ tin cậy cao và khả năng sử dụng trong mạng lưới không ổn định
- Dựa trên Broker (Máy chủ môi giới), thiết kế có tính mở, đơn giản dễ cài đặt
- Môi trường lý tưởng để sử dụng MQTT: 
  + Băng thông thấp, thiếu tin cậy
  + Khi chạy trên các thiết bị nhúng bị giới hạn về tài nguyên tốc độ và bộ nhớ
# 2. Mô hình IoT
![image](https://user-images.githubusercontent.com/92737759/163155900-38c1022d-5509-42a8-8078-7f1c7c7192d8.png)
- Dạng truyền thông điệp theo mô hình Pub/Sub cung cấp việc truyền tin phân tán một chiều, tách biệt với phần ứng dụng
- Việc truyền thông điệp là ngay lập tức, không quan tâm đến nội dung thông điệp được truyền
- Sử dụng giao thức TCP/IP tin cậy
- Tồn tại 3 mức độ QoS:
  + QoS 0: Broker/client sẽ gửi dữ liệu đúng một lần, quá trình gửi được xác nhận bởi chỉ giao thức TCP/IP.
  + QoS 1: Broker/client sẽ gửi dữ liệu với ít nhất một lần xác nhận từ đầu kia, nghĩa là có thể có nhiều hơn 1 lần xác nhận đã nhận được dữ liệu.
  + QoS 2: Broker/client đảm bảo khi gửi dữ liệu thì phía nhận chỉ nhận được đúng một lần, quá trình này phải trải qua 4 bước bắt tay.
# 3. Mô hình Pub/Sub
- Thành phần 
  - Client
  + Publisher: Nơi gửi thông điệp
  + Subscriber: Nơi nhận thông điệp
  - Broker- Máy chủ
 
