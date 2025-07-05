---
title: "Gọi hàm delete-user"
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

1. Mở bảng điều khiển [AWS Lambda functions](https://console.aws.amazon.com/lambda/home?#/functions)
2. Nhấp vào hàm `delete-user`.
3. Mở tab `Test`.
4. Trong phần `Test event`,

   - Event name: Điền `delete-user-event`
   - Event JSON: Thay thế sự kiện mẫu bằng

     ```json
     {
       "id": "18d35ef6-a7ae-415b-a97d-34dc069a840d"
     }
     ```

> [!NOTE]
> Thay thế id người dùng bằng id của bạn, bạn có thể lấy được id này trong phần `Explorer items` của DynamoDB hoặc trong phản hồi sau khi gọi hàm `list-users`.

5. Nhấp `Save`
6. Nhấp vào nút `Test`.

   ![alt text](/images/workshop-1/lambda-invoke-with-console--delete-user-event.jpg)

7. Xác minh rằng người dùng đã bị xóa.

   - Mở trang [`Explore items`](https://console.aws.amazon.com/dynamodbv2/home#item-explorer) trong bảng điều khiển DynamoDB.
   - Nhấp vào nút làm mới.
   - Xác minh rằng `Nguyen Van Anh` không còn tồn tại trong bảng nữa.

   ![alt text](/images/workshop-1/lambda-invoke-with-console--delete-user-verify.jpg)
