---
title: "Gọi hàm get-user"
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

1. Mở bảng điều khiển [AWS Lambda functions](https://console.aws.amazon.com/lambda/home?#/functions)
2. Nhấp vào hàm `get-user`.
3. Mở tab `Test`.
4. Trong phần `Test event`,

   - Event name: Điền `get-user-event`
   - Event JSON: Thay thế sự kiện mẫu bằng id của người dùng có tên `Nguyen Van An`.

     ```json
     {
       "id": "18d35ef6-a7ae-415b-a97d-34dc069a840d"
     }
     ```

> [!NOTE]
> Thay thế id người dùng bằng id của bạn, bạn có thể lấy được id này trong phần `Explorer items` của DynamoDB hoặc trong phản hồi sau khi gọi hàm `list-users`.

5. Nhấp `Save`
6. Nhấp vào nút `Test`.

   ![alt text](/images/workshop-1/lambda-invoke-with-console--get-user-event.jpg)

7. Xác minh rằng thông tin người dùng đã được trả về.

   ![alt text](/images/workshop-1/lambda-invoke-with-console--get-user-detail.jpg)
