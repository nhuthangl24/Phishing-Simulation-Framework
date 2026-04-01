# Phishing Simulation Framework

## 1. Giới thiệu

Dự án **Phishing Simulation Framework** được xây dựng nhằm mô phỏng một cuộc tấn công phishing hoàn chỉnh trong môi trường lab an toàn. Mục tiêu chính là giúp người học hiểu rõ cách thức hoạt động của các cuộc tấn công phishing hiện đại, từ khâu gửi email giả mạo cho đến thu thập thông tin đăng nhập và session của người dùng.

Khác với việc chỉ học lý thuyết, dự án này triển khai thực tế toàn bộ quy trình tấn công để quan sát trực tiếp hành vi của hệ thống và người dùng.

> (Ảnh - Tổng quan kiến trúc hệ thống)

---

## 2. Mục tiêu của dự án

Dự án hướng đến các mục tiêu cụ thể sau:

* Mô phỏng quy trình tấn công phishing trong thực tế
* Hiểu rõ cách thức email phishing được tạo và gửi đi
* Phân tích cách người dùng tương tác với email giả mạo
* Thu thập và đánh giá dữ liệu từ chiến dịch phishing
* Nghiên cứu kỹ thuật đánh cắp thông tin đăng nhập (credentials)
* Hiểu cơ chế hoạt động của session hijacking và bypass 2FA

---

## 3. Kiến trúc hệ thống

Hệ thống được xây dựng theo mô hình client-server, bao gồm các thành phần chính:

### 3.1 Attacker Server

Đây là thành phần trung tâm của hệ thống, chịu trách nhiệm:

* Chạy **GoPhish** để tạo và quản lý chiến dịch phishing
* Chạy **Evilginx2** để thực hiện tấn công Man-in-the-Middle
* Thu thập thông tin từ nạn nhân (credentials, session)
* Lưu trữ và phân tích dữ liệu

### 3.2 SMTP Server

* Dùng để gửi email phishing đến danh sách người dùng mục tiêu
* Có thể sử dụng các dịch vụ như Mailgun, Gmail SMTP hoặc server riêng

### 3.3 Phishing Domain

* Domain giả mạo được cấu hình để giống với website thật
* Dùng để tăng độ tin cậy và đánh lừa người dùng

### 3.4 Victim (Người dùng mục tiêu)

* Nhận email phishing
* Tương tác với link trong email
* Có thể bị thu thập thông tin nếu không nhận diện được tấn công

### 3.5 Hệ thống logging

* Ghi lại toàn bộ hoạt động của chiến dịch
* Bao gồm:

  * Thời điểm mở email
  * Click vào link
  * Nhập thông tin đăng nhập
  * Session cookie

> (Ảnh - Sơ đồ chi tiết kiến trúc hệ thống)

---

## 4. Công nghệ sử dụng

Các công nghệ và công cụ chính trong dự án:

* **GoPhish**: quản lý chiến dịch phishing, gửi email và theo dõi người dùng
* **Evilginx2**: reverse proxy phục vụ tấn công MITM và session hijacking
* **Ubuntu Server**: môi trường triển khai hệ thống
* **SMTP Server**: gửi email (Mailgun / Gmail / custom SMTP)
* **HTML/CSS/JavaScript**: xây dựng landing page giả mạo

---

## 5. Quy trình hoạt động của hệ thống

Quy trình tấn công phishing được mô phỏng theo các bước sau:

### Bước 1: Chuẩn bị chiến dịch

* Tạo email template (nội dung giả mạo)
* Tạo landing page giống website thật
* Cấu hình domain phishing
* Thiết lập campaign trong GoPhish

> (Ảnh - Giao diện tạo campaign trong GoPhish)

### Bước 2: Gửi email phishing

* Sử dụng SMTP server để gửi email đến danh sách mục tiêu
* Email chứa link dẫn đến website giả mạo

> (Ảnh - Ví dụ email phishing)

### Bước 3: Người dùng truy cập link

* Người dùng click vào link trong email
* Request được chuyển qua Evilginx (reverse proxy)
* Evilginx chuyển tiếp đến website thật

> (Ảnh - Luồng request qua Evilginx)

### Bước 4: Thu thập thông tin

Khi người dùng nhập thông tin đăng nhập:

* Username và password được ghi lại
* Session cookie được capture

> (Ảnh - Log thông tin thu thập được)

### Bước 5: Phân tích kết quả

Sau khi chiến dịch kết thúc, hệ thống cung cấp các thống kê:

* Tỷ lệ mở email
* Tỷ lệ click link
* Tỷ lệ nhập thông tin
* Dữ liệu credentials thu thập được

> (Ảnh - Dashboard thống kê GoPhish)

---

## 6. Các kỹ thuật chính được sử dụng

### 6.1 Phishing Email

* Tạo email có nội dung giống thông báo chính thức
* Sử dụng ngôn từ gây áp lực (khẩn cấp, cảnh báo, xác minh)

### 6.2 Landing Page giả mạo

* Sao chép giao diện từ website thật
* Giữ nguyên trải nghiệm người dùng để tránh bị nghi ngờ

### 6.3 Man-in-the-Middle (MITM)

* Evilginx hoạt động như một reverse proxy
* Chuyển tiếp dữ liệu giữa người dùng và server thật

### 6.4 Credential Harvesting

* Ghi lại thông tin đăng nhập khi người dùng nhập vào form

### 6.5 Session Hijacking

* Thu thập session cookie sau khi đăng nhập
* Cho phép truy cập tài khoản mà không cần mật khẩu hoặc 2FA

> (Ảnh - Minh họa cơ chế MITM và đánh cắp session)

---

## 7. Kết quả đạt được

Sau khi triển khai, hệ thống đạt được các kết quả:

* Xây dựng thành công mô hình phishing simulation hoàn chỉnh
* Triển khai và vận hành chiến dịch email phishing
* Thu thập được dữ liệu thực nghiệm từ người dùng
* Hiểu rõ cơ chế hoạt động của:

  * Email phishing
  * Credential harvesting
  * Session hijacking

---

## 8. Hạn chế của hệ thống

* Chỉ hoạt động trong môi trường lab
* Phụ thuộc vào cấu hình domain và SMTP
* Một số hệ thống bảo mật có thể phát hiện và chặn phishing
* Không phản ánh hoàn toàn môi trường tấn công thực tế

---

## 9. Kết luận

Dự án giúp mô phỏng một cách trực quan và đầy đủ quy trình của một cuộc tấn công phishing hiện đại. Thông qua việc triển khai thực tế, người học có thể hiểu rõ hơn về cách thức hoạt động của các kỹ thuật tấn công, từ đó nâng cao khả năng phòng chống trong môi trường thực tế.

> (Ảnh - Demo tổng thể hệ thống)


