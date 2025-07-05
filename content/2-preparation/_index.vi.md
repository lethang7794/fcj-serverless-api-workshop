---
title: "Chuẩn bị"
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

Trước khi bắt đầu workshop này, bạn cần:

1. Một người dùng IAM với quyền `AdministratorAccess` để đăng nhập vào AWS Management Console.

   ![alt text](/images/workshop-1/IAM-user-login-and-permissions.png)

   Nếu bạn chưa tạo người dùng IAM, hãy làm theo hướng dẫn [Tạo Nhóm IAM và Người dùng IAM :: QUẢN LÝ KIỂM SOÁT TRUY CẬP VỚI AWS IAM (ĐỊNH DANH VÀ QUẢN LÝ TRUY CẬP)](https://000002.awsstudygroup.com/2-create-admin-user-and-group/) để tạo.

1. Cài đặt và cấu hình AWS CLI với thông tin xác thực cho người dùng IAM đó.

   - Chạy lệnh `aws sts get-caller-identity` để xác minh:

     ![alt text](/images/workshop-1/AWS-CLI--verify-credential.png)

   - Kết quả của bạn có thể hơi khác.

   - Nếu không thể chạy `aws sts get-caller-identity`, hãy làm theo hướng dẫn [Cài đặt AWS CLI :: BẮT ĐẦU VỚI AWS CLI](https://000011.awsstudygroup.com/3-installcli/).
