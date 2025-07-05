---
title: "Gọi hàm create-user"
weight: 1
chapter: false
pre: " <b> 6.1. </b> "
---

> [!NOTE]
> Thay thế `ap-southeast-1` bằng AWS region của bạn, `971422684006` bằng số tài khoản AWS của bạn, hoặc thay thế toàn bộ `arn:aws:lambda:ap-southeast-1:971422684006:function:create-user` bằng ARN của hàm từ bảng điều khiển quản lý.

1. Thực thi lệnh sau

   ```shell
   aws lambda invoke \
       --function-name arn:aws:lambda:ap-southeast-1:971422684006:function:create-user \
       --cli-binary-format raw-in-base64-out \
       --payload '{ "email": "nguyenvandong@gmail.com", "name": "Nguyen Van Dong" }' \
       response.json
   ```

2. Kiểm tra phản hồi

   ```
   cat response.json
   ```

   ```json
   {"statusCode": 200, "headers": {"Content-Type": "application/json", "Access-Control-Allow-Origin": "*"}, "body": "{\"updated_at\": \"2025-05-14T10:07:42\", \"created_at\": \"2025-05-14T10:07:42\", \"id\": \"6c539686-de1c-4bef-85ef-f68a4b5aabe0\", \"email\": \"nguyenvandong@gmail.com\", \"name\": \"Nguyen Van Dong\"}"}%
   ```

3. Để xác minh rằng người dùng đã được cập nhật, bạn có thể:
   - Gọi lại hàm `list-users`
   - Hoặc sử dụng bảng điều khiển DynamoDB
