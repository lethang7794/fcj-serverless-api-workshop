---
title: "Gọi hàm delete-user"
weight: 5
chapter: false
pre: " <b> 8.5. </b> "
---

> [!NOTE]
> Thay thế URL bằng function URL của hàm Lambda `delete-user` của bạn.

1. Thực thi lệnh sau:

   ```shell
   curl 'https://5ywq2njgsehqpl3xl2nrs334ue0inscy.lambda-url.ap-southeast-1.on.aws/' \
     -H 'content-type: application/json' \
     -d '{ "id": "bcfe3cf9-1607-489e-8501-f99c194e6cc9" }'
   ```

   ![alt text](/images/workshop-1/lambda-invoke-with-curl--delete-user.jpg)

> [!NOTE]
> Khi gọi `delete-user` bằng `curl`, bạn sẽ không nhận được thông báo nào (Phản hồi không có nội dung).

2. Xác minh rằng người dùng đã bị xóa bằng bảng điều khiển DynamoDB.

   ![alt text](/images/workshop-1/lambda-invoke-with-curl--delete-user-verify.jpg)
