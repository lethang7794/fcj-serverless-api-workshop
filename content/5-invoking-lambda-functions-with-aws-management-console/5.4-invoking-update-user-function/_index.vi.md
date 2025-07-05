---
title: "Gọi hàm update-user"
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

1. Mở bảng điều khiển [AWS Lambda functions](https://console.aws.amazon.com/lambda/home?#/functions)
2. Nhấp vào hàm `update-user`.
3. Mở tab `Test`.
4. Trong phần `Test event`,

   - Event name: Điền `update-user-event`
   - Event JSON: Thay thế sự kiện mẫu bằng id của người dùng có tên `Nguyen Van An` nhưng với email và tên mới.

     ```json
     {
       "id": "18d35ef6-a7ae-415b-a97d-34dc069a840d",
       "email": "nguyenvananh@gmail.com",
       "name": "Nguyen Van Anh"
     }
     ```

> [!NOTE]
> Thay thế id người dùng bằng id của bạn, bạn có thể lấy được id này trong phần `Explorer items` của DynamoDB hoặc trong phản hồi sau khi gọi hàm `list-users`.

5. Nhấp `Save`
6. Nhấp vào nút `Test`.

   ![alt text](/images/workshop-1/lambda-invoke-with-console--update-user-event.jpg)

7. Xác minh rằng người dùng đã được cập nhật.

   - Mở trang [`Explore items`](https://console.aws.amazon.com/dynamodbv2/home#item-explorer) trong bảng điều khiển DynamoDB.
   - Nhấp vào nút làm mới.
   - Xác minh rằng:

     - `Nguyen Van An` đã được đổi thành `Nguyen Van Anh`
     - `nguyenvanan@gmail.com` đã được đổi thành `nguyenvananh@gmail.com`

     ![alt text](/images/workshop-1/lambda-invoke-with-console--update-user-verify.jpg)
