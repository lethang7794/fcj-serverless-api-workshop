---
title: "Gọi hàm delete-user"
weight: 5
chapter: false
pre: " <b> 6.5. </b> "
---

> [!NOTE]
> Nhớ cập nhật **tên hàm** và **id** của người dùng có tên `Nguyen Van Dong`.

1. Thực thi lệnh sau

   ```shell
   aws lambda invoke \
       --function-name arn:aws:lambda:ap-southeast-1:971422684006:function:delete-user \
       --cli-binary-format raw-in-base64-out \
       --payload '{ "id": "6c539686-de1c-4bef-85ef-f68a4b5aabe0" }' \
       response.json
   ```

2. Kiểm tra phản hồi

   ```
   cat response.json
   ```

   ```json
   {"statusCode": 204, "headers": {"Content-Type": "application/json", "Access-Control-Allow-Origin": "*"}}%
   ```

   ![alt text](/images/workshop-1/lambda-invoke-with-aws-cli--delete-user.jpg)

3. Để xác minh rằng người dùng đã bị xóa, bạn có thể:
   - Gọi lại hàm `list-users`
   - Hoặc sử dụng bảng điều khiển DynamoDB
