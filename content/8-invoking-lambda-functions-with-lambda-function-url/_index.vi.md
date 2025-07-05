---
title: "Gọi hàm Lambda thông qua Function URL"
weight: 8
chapter: false
pre: " <b> 8. </b> "
---

Trước đây, để gọi một hàm Lambda, bạn có thể:

- Mở trang hàm Lambda (trong bảng điều khiển quản lý AWS) và gọi hàm Lambda bằng cách nhấp vào nút `Test`.

  (Trường hợp này IAM sẽ sử dụng thông tin xác thực AWS của tài khoản AWS mà bạn đã đăng nhập).

  ![alt text](/images/diagrams/workshop-1-invoke-with-management-console-low-level.drawio.svg)

- Hoặc sử dụng AWS CLI và ARN của hàm để gọi hàm Lambda.

  (Trường hợp này IAM sẽ sử dụng thông tin xác thực AWS mà bạn đã cấu hình với AWS CLI).

  ![alt text](/images/diagrams/workshop-1-invoke-with-with-cli-low-level.drawio.svg)

---

Trong bước trước, chúng ta đã tạo 5 function URL, bây giờ chúng ta sẽ gọi hàm bằng trình duyệt hoặc bất kỳ HTTP client nào (ví dụ: `curl`)

Kiến trúc lúc này sẽ trông như thế này

![alt text](/images/diagrams/workshop-1-function-urls.drawio.svg)
