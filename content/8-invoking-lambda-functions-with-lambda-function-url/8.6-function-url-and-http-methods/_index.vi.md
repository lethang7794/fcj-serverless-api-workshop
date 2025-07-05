---
title: "Function URL và các phương thức HTTP"
weight: 6
chapter: false
pre: " <b> 8.6. </b> "
---

Khi gọi hàm Lambda thông qua function URL, bạn có thể sử dụng bất kỳ phương thức HTTP nào: GET, POST, DELETE, PATCH, PUT..., Lambda sẽ xử lý tất cả chúng như nhau.

- Thử với `GET`

  ```shell
  curl 'https://qzpsv22gd3s4qbnfwz2v5yefoy0dmipa.lambda-url.ap-southeast-1.on.aws/' \
    -X GET \
    -H 'content-type: application/json' \
    -d '{ "id": "a3127179-6ba4-4c3b-855a-4f65d4ee6345" }'
  ```

- Hoặc `POST`

  ```shell
  curl 'https://qzpsv22gd3s4qbnfwz2v5yefoy0dmipa.lambda-url.ap-southeast-1.on.aws/' \
    -X GET \
    -H 'content-type: application/json' \
    -d '{ "id": "a3127179-6ba4-4c3b-855a-4f65d4ee6345" }'
  ```

Tất cả các yêu cầu của bạn sẽ thành công và bạn sẽ nhận được cùng một phản hồi.
