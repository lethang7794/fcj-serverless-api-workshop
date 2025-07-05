---
title: "Gọi hàm get-user"
weight: 3
chapter: false
pre: " <b> 6.3. </b> "
---


> [!NOTE]
> Nhớ cập nhật **tên hàm** và **id** của người dùng có tên `Nguyen Van Dong`.

1. Thực thi lệnh sau

   ```shell
   aws lambda invoke \
       --function-name arn:aws:lambda:ap-southeast-1:971422684006:function:get-user \
       --cli-binary-format raw-in-base64-out \
       --payload '{ "id": "6c539686-de1c-4bef-85ef-f68a4b5aabe0" }' \
       response.json
   ```

2. Kiểm tra phản hồi

   ```
   cat response.json
   ```

   ```json
   {"statusCode": 200, "headers": {"Content-Type": "application/json", "Access-Control-Allow-Origin": "*"}, "body": "{\"updated_at\": \"2025-05-14T10:07:42\", \"created_at\": \"2025-05-14T10:07:42\", \"id\": \"6c539686-de1c-4bef-85ef-f68a4b5aabe0\", \"email\": \"nguyenvandong@gmail.com\", \"name\": \"Nguyen Van Dong\"}"}%
   ```

   ![alt text](/images/workshop-1/lambda-invoke-with-aws-cli--get-user.jpg)
