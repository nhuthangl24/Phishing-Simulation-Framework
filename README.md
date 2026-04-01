# Phishing Simulation Framework (GoPhish + Evilginx)


## Giới thiệu

Đây là trang tổng quan của dự án, giúp người đọc nhanh chóng nắm bắt mục tiêu, kiến trúc và cách tiếp cận của hệ thống.

Dự án tập trung vào việc **mô phỏng một chiến dịch tấn công phishing qua email trong môi trường an toàn**, sử dụng các công cụ phổ biến như **GoPhish** và **Evilginx2**.

## Tài liệu chi tiết

Vui lòng xem các tài liệu bên dưới để đọc chi tiết theo ngôn ngữ mong muốn:

* [**README_VI.md**](https://github.com/nhuthangl24/Phishing-Simulation-Framework/blob/main/README_VI.md) : Tài liệu chi tiết tiếng Việt
* [**README_EN.md**](https://github.com/nhuthangl24/Phishing-Simulation-Framework/blob/main/README_EN.md) : Detailed documentation in English

## Nội dung chính của dự án

* Mô phỏng chiến dịch phishing qua email
* GoPhish (Email Campaign & Tracking System)
* Evilginx2 (Reverse Proxy & Session Hijacking)
* Landing Page giả mạo
* SMTP Server gửi email
* Thu thập credentials và session

## Mô hình hệ thống

Các thành phần chính:

* Attacker Server (GoPhish + Evilginx)
* SMTP Server
* Phishing Domain
* Victim User
* Logging System

Luồng hoạt động:

1. Gửi email phishing
2. Nạn nhân click link
3. Proxy tới trang đăng nhập thật
4. Thu thập thông tin đăng nhập
5. Ghi log và phân tích

## Mục tiêu

README này đóng vai trò trang điều hướng chính của repository.

* Mô phỏng tấn công phishing trong môi trường an toàn
* Hiểu cơ chế hoạt động phishing hiện đại
* Phân tích hành vi người dùng
* Nâng cao nhận thức an ninh mạng

## Phạm vi

* Chỉ sử dụng trong môi trường lab
* Không áp dụng vào mục đích tấn công thực tế
* Dữ liệu chỉ phục vụ nghiên cứu

## Công nghệ sử dụng

* GoPhish
* Evilginx2
* Ubuntu Server
* SMTP Server
* HTML/CSS/JS

## Đóng góp

Mọi đóng góp đều được hoan nghênh.

1. Fork repository
2. Tạo branch mới
3. Commit thay đổi
4. Tạo Pull Request

---

> Nếu bạn thấy dự án hữu ích, hãy ⭐ repository để ủng hộ!
