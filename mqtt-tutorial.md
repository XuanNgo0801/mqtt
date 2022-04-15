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
  - Client: publish các message lên một/nhiều topic cụ thể hoặc subscribe một/nhiều topic nào đó để nhận message từ topic này.
    + Publisher: Nơi gửi thông điệp
    + Subscriber: Nơi nhận thông điệp
  - Broker- Máy chủ: nhận thông điệp từ Publisher, xếp vào hàng đợi rồi chuyển đến một địa điểm cụ thể.  
![image](https://user-images.githubusercontent.com/92737759/163503498-9ed8bbf2-577d-47f7-b38d-d43f66c1896d.png)  
# 3. Cơ chế tổng quan
![image](https://user-images.githubusercontent.com/92737759/163503693-701f67a4-b9a7-41d8-afc2-5f209fd4a1a4.png)  
- MQTT hoạt động theo cơ chế client/server, nơi mà mỗi cảm biến là 1 client kết nối tới 1 server (MQTT broker), thông qua giao thức TCP
- MQTT là giao thức định hướng bản tin. Mỗi bản tin được publish 1 địa chỉ cụ thể (Topic). Client subscribe vào một hoặc nhiều topic để nhận/gửi dữ liệu. Mỗi client sẽ nhận được dữ liệu khi bất kỳ 1 client nào khác gửi dữ liệu vào Topic đã đăng ký. Khi một client gửi một bản tin đến một kênh nào đó gọi là publish.
# 4. Kiến trúc thành phần
![image](https://user-images.githubusercontent.com/92737759/163504076-e24c4c40-456c-4a82-af71-89d585edb626.png)  
- Thành phần chính của MQTT là Client (Publisher/Subscriber), Server (Broker), Sessions, Subscriptions và Topics.
  + MQTT Client (Publisher/Subscriber): Clients sẽ subscribe một hoặc nhiều topics để gửi và nhận thông điệp từ những topic tương ứng.
  + MQTT Server (Broker): Broker nhận những thông tin subscribe (Subscriptions) từ client, nhận thông điệp, chuyển những thông điệp đến các Subscriber tương ứng dựa trên Subscriptions từ client.
  + Topic: Có thể coi Topic là một hàng đợi các thông điệp, và có sẵn khuôn mẫu dành cho Subscriber hoặc Publisher. Một cách logic thì các topic cho phép Client trao đổi thông tin với những ngữ nghĩa đã được định nghĩa sẵn. Ví dụ: Dữ liệu cảm biến nhiệt độ của một tòa nhà.
  + Session: Một session được định nghĩa là kết nối từ client đến server. Tất cả các giao tiếp giữa client và server đều thông qua 1 session.
  + Subscription: Không giống như session, subscription là kết nối từ client đến topic. Khi đã subscribe một topic, Client có thể nhận/gửi thông điệp với topic đó.

 
