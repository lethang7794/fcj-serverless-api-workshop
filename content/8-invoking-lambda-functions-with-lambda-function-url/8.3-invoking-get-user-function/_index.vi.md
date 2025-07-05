---
title: "Gọi hàm get-user"
weight: 3
chapter: false
pre: " <b> 8.3. </b> "
---

> [!NOTE]
> Thay thế URL bằng function URL của hàm Lambda `get-user` của bạn.

- Hàm `get-user` yêu cầu id của người dùng trong phần thân yêu cầu HTTP, hãy chọn id của một người dùng từ phản hồi của `list-users`.

  ```shell
  curl 'https://qzpsv22gd3s4qbnfwz2v5yefoy0dmipa.lambda-url.ap-southeast-1.on.aws/' \
    -H 'content-type: application/json' \
    -d '{ "id": "a3127179-6ba4-4c3b-855a-4f65d4ee6345" }'
  ```

  ```json
  {
    "updated_at": "2025-05-14T10:07:29",
    "created_at": "2025-05-14T10:07:29",
    "id": "a3127179-6ba4-4c3b-855a-4f65d4ee6345",
    "email": "nguyenvancanh@gmail.com",
    "name": "Nguyen Van Canh"
  }
  ```

  ![alt text](/images/workshop-1/lambda-invoke-with-curl--get-user.jpg)
