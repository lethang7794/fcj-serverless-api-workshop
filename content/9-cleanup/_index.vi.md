+++
title = "Dọn dẹp tài nguyên"
weight = 9
chapter = false
pre = "<b>9. </b>"
+++

{{% toc %}}

> [!NOTE]
> Nếu bạn muốn thực hiện workshop tiếp theo trong loạt bài, hãy giữ lại các tài nguyên này.

<!-- TODO: liên kết đến workshop tiếp theo -->

Bạn cần dọn dẹp các tài nguyên sau:

### **Bảng DynamoDB**

- Mở phần [_Tables_](https://console.aws.amazon.com/dynamodbv2/home?#tables) của bảng điều khiển DynamoDB
- Chọn bảng `UsersTable`
- Nhấp vào `Delete`

  ![alt text](/images/workshop-1/cleanup-dynamodb--resources.jpg)

- Nhập `confirm`
- Nhấp vào `Delete`

  ![alt text](/images/workshop-1/cleanup-dynamodb--confirm.jpg)

### Các **Hàm Lambda**

- Mở phần [_Functions_](https://console.aws.amazon.com/lambda/home#/functions) của bảng điều khiển Lambda.
- Chọn 5 hàm: `create-user`, `list-user`, `get-user`, `update-user`, `delete-user`.
- Nhấp vào `Actions`, chọn `Delete`.

  ![alt text](/images/workshop-1/cleanup-lambda--resources.jpg)

- Nhập `confirm`, nhấp vào `Delete`.

  ![alt text](/images/workshop-1/cleanup-lambda--confirm.jpg)

### Các **IAM Role** được sử dụng làm role thực thi (execution role) cho hàm Lambda

- Mở phần [_Roles_](https://console.aws.amazon.com/iam/home#/roles) của bảng điều khiển IAM
- Chọn 5 roles: `create-user-role-XXXXXXX`, `delete-user-role-XXXXXXX`, `get-user-role-XXXXXXX`, `list-users-role-XXXXXXX`, `update-user-role-XXXXXXX`
- Nhấp vào `Delete`.

  ![alt text](/images/workshop-1/cleanup-iam-role--resources.jpg)

- Nhập `Delete`, nhấp vào `Delete`

  ![alt text](/images/workshop-1/cleanup-iam-role--confirm.jpg)
