---
title: "Tạo bảng DynamoDB"
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

Trong bước này, chúng ta sẽ tạo một bảng DynamoDB để lưu trữ dữ liệu.

1. Đăng nhập vào AWS Management Console bằng [liên kết đăng nhập console và thông tin đăng nhập IAM](https://000002.awsstudygroup.com/2-create-admin-user-and-group/2.3-login-admin-user/) của bạn.
1. Mở [bảng điều khiển DynamoDB](https://console.aws.amazon.com/dynamodbv2/home).
1. Mở phần `Tables` trong thanh điều hướng.
1. Nhấp vào `Create table`

   ![alt text](/images/workshop-1/dynamodb-create-table.png)

1. Trong phần `Table details`, nhập:

   - Table name: `UsersTable`
   - Partition key: `id`

   ![alt text](/images/workshop-1/dynamodb-create-table--detail.png)

1. Trong phần `Table settings`, chọn `Default settings` với:

   - Table class là `DynamoDB Standard`
   - Capacity mode là `On-demand`

1. Nhấp vào `Create table`

   ![alt text](/images/workshop-1/dynamodb-create-table--default-settings.png)

1. Chờ trạng thái của bảng chuyển từ `Creating` sang `Active`.

   ![alt text](/images/workshop-1/dynamodb-create-table--successful.png)
