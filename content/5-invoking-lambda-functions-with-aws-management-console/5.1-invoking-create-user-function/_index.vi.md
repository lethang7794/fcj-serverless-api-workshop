---
title: "Gọi hàm create-user"
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

1. Mở [mục Functions trong bảng điều khiển Lambda](https://console.aws.amazon.com/lambda/home?#/functions)

1. Nhấp vào hàm `create-user`.
1. Mở tab `Test`
1. Trong phần `Test event`,

   - Event name: Điền `create-user-event`
   - Event JSON: Thay thế sự kiện mẫu bằng

     ```json
     {
       "email": "nguyenvanan@gmail.com",
       "name": "Nguyen Van An"
     }
     ```

1. Nhấp `Save`

   ![alt text](/images/workshop-1/lambda-invoke-with-console--test-event.png)

1. Nhấp `Test`
1. Trong bảng thông báo `Execution functions`, nhấp `Details`.

   ![alt text](/images/workshop-1/lambda-invoke-with-console--invoke.png)

1. Bạn có thể kiểm tra phản hồi của hàm Lambda và thông tin về quá trình thực thi

   ![alt text](/images/workshop-1/lambda-invoke-with-console--exection-detail.jpg)

1. Xác minh rằng một người dùng mới đã được tạo trong bảng DynamoDB `UsersTable`

   - Mở trang [`Explore items`](https://console.aws.amazon.com/dynamodbv2/home#item-explorer) trong bảng điều khiển DynamoDB.
   - Chọn bảng `UsersTable`
   - Thao tác Scan sẽ tự động chạy.
   - Xác minh rằng một người dùng mới đã được tạo (nghĩa là một mục DynamoDB mới đã được tạo).

   ![alt text](/images/workshop-1/lambda-invoke-with-console--verify-user-created.jpg)

1. Gọi hàm Lambda `create-user` trong bước này với các `Event JSON` khác nhau để tạo thêm người dùng:

   ```json
   {
     "email": "nguyenvanbinh@gmail.com",
     "name": "Nguyen Van Binh"
   }
   ```

   ```json
   {
     "email": "nguyenvancanh@gmail.com",
     "name": "Nguyen Van Canh"
   }
   ```

   ```json
   {
     "email": "nguyenvandong@gmail.com",
     "name": "Nguyen Van Dong"
   }
   ```

   ```json
   {
     "email": "nguyenvanem@gmail.com",
     "name": "Nguyen Van Em"
   }
   ```

1. Sau khi gọi hàm Lambda `create-user` với 4 sự kiện này, bạn sẽ có tổng cộng 5 người dùng.

   - Mở trang [`Explore items`](https://console.aws.amazon.com/dynamodbv2/home#item-explorer) trong bảng điều khiển DynamoDB.
   - Chọn bảng `UsersTable`
   - Nhấp nút Refresh
   - Xác minh rằng có 5 mục trong bảng DynamoDB.

     ![alt text](/images/workshop-1/lambda-invoke-with-console--verify-dynamodb-items.jpg)
