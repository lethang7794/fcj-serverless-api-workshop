---
title: "Gọi hàm list-users"
weight: 2
chapter: false
pre: " <b> 6.2. </b> "
---

> [!NOTE]
> Thay thế `ap-southeast-1` bằng AWS region của bạn, `971422684006` bằng số tài khoản AWS của bạn, hoặc thay thế toàn bộ `arn:aws:lambda:ap-southeast-1:971422684006:function:list-users` bằng ARN của hàm từ bảng điều khiển quản lý.

1. Thực thi lệnh sau

   ```shell
   aws lambda invoke \
       --function-name arn:aws:lambda:ap-southeast-1:971422684006:function:list-users \
       response.json
   ```

2. Nếu terminal hiển thị:

   ```shell
   {
       "StatusCode": 200,
       "ExecutedVersion": "$LATEST"
   }
   ```

   Bạn đã gọi hàm Lambda thành công bằng AWS CLI.

3. Kiểm tra nội dung phản hồi từ hàm Lambda

   ```
   cat response.json
   ```

   ```json
   {"statusCode": 200, "headers": {"Content-Type": "application/json", "Access-Control-Allow-Origin": "*"}, "body": "{\"users\": [{\"updated_at\": \"2025-05-14T10:07:42\", \"created_at\": \"2025-05-14T10:07:42\", \"id\": \"6c539686-de1c-4bef-85ef-f68a4b5aabe0\", \"email\": \"nguyenvandong@gmail.com\", \"name\": \"Nguyen Van Dong\"}, {\"updated_at\": \"2025-05-14T10:07:29\", \"created_at\": \"2025-05-14T10:07:29\", \"id\": \"a3127179-6ba4-4c3b-855a-4f65d4ee6345\", \"email\": \"nguyenvancanh@gmail.com\", \"name\": \"Nguyen Van Canh\"}, {\"updated_at\": \"2025-05-14T10:07:51\", \"created_at\": \"2025-05-14T10:07:51\", \"id\": \"e1f0cca8-cd19-4d8b-9124-70a63c351e3a\", \"email\": \"nguyenvanem@gmail.com\", \"name\": \"Nguyen Van Em\"}, {\"updated_at\": \"2025-05-14T10:07:15\", \"created_at\": \"2025-05-14T10:07:15\", \"id\": \"bb15f9cb-1379-4783-9f6f-23616d633d2a\", \"email\": \"nguyenvanbinh@gmail.com\", \"name\": \"Nguyen Van Binh\"}]}"}%
   ```

   Bạn sẽ thấy danh sách người dùng đã tạo ở bước trước.

4. [Tùy chọn] Dữ liệu phản hồi ở định dạng JSON, bạn có thể sử dụng `jq` để hiển thị đẹp mắt hơn

   ```shell
   cat response.json | jq
   ```

   ```json
   {
     "statusCode": 200,
     "headers": {
       "Content-Type": "application/json",
       "Access-Control-Allow-Origin": "*"
     },
     "body": "{\"users\": [{\"updated_at\": \"2025-05-14T10:07:42\", \"created_at\": \"2025-05-14T10:07:42\", \"id\": \"6c539686-de1c-4bef-85ef-f68a4b5aabe0\", \"email\": \"nguyenvandong@gmail.com\", \"name\": \"Nguyen Van Dong\"}, {\"updated_at\": \"2025-05-14T10:07:29\", \"created_at\": \"2025-05-14T10:07:29\", \"id\": \"a3127179-6ba4-4c3b-855a-4f65d4ee6345\", \"email\": \"nguyenvancanh@gmail.com\", \"name\": \"Nguyen Van Canh\"}, {\"updated_at\": \"2025-05-14T10:07:51\", \"created_at\": \"2025-05-14T10:07:51\", \"id\": \"e1f0cca8-cd19-4d8b-9124-70a63c351e3a\", \"email\": \"nguyenvanem@gmail.com\", \"name\": \"Nguyen Van Em\"}, {\"updated_at\": \"2025-05-14T10:07:15\", \"created_at\": \"2025-05-14T10:07:15\", \"id\": \"bb15f9cb-1379-4783-9f6f-23616d633d2a\", \"email\": \"nguyenvanbinh@gmail.com\", \"name\": \"Nguyen Van Binh\"}]}"
   }
   ```

   ![alt text](/images/workshop-1/lambda-invoke-with-aws-cli--list-users.jpg)
