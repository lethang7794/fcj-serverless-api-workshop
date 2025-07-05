---
title: "Tạo Function URLs cho các hàm Lambda"
weight: 7
chapter: false
pre: " <b> 7. </b> "
---

{{% toc %}}

#### Function URL là gì?

Function URL là một điểm cuối HTTP(S) chuyên dụng cho hàm Lambda của bạn.

- Khi bạn tạo function URL, Lambda sẽ tự động tạo một URL endpoint duy nhất cho bạn.

Bạn có thể kiểm soát quyền truy cập vào function URL bằng tham số AuthType:

- Khi cấu hình function URL, bạn phải chỉ định một trong các tùy chọn AuthType sau:
  - `AWS_IAM` – Lambda sử dụng AWS Identity and Access Management (IAM) để xác thực và ủy quyền các yêu cầu dựa trên chính sách danh tính của IAM principal và chính sách dựa trên tài nguyên của hàm. Chọn tùy chọn này nếu bạn chỉ muốn người dùng và vai trò đã xác thực mới có thể gọi hàm của bạn thông qua function URL.
  - `NONE` – Lambda không thực hiện bất kỳ xác thực nào trước khi gọi hàm của bạn. Tuy nhiên, chính sách dựa trên tài nguyên của hàm luôn có hiệu lực và phải cấp quyền truy cập công khai trước khi function URL của bạn có thể nhận yêu cầu. Chọn tùy chọn này để cho phép truy cập công khai, không xác thực vào function URL của bạn.

> [!NOTE]
> Trong workshop này, để đơn giản hóa việc học tập, chúng ta sẽ tạo function URL với `AuthType` là `NONE` mà không triển khai bất kỳ cơ chế xác thực nào trong hàm Lambda.

> [!WARNING]
> Ngoại trừ một số trường hợp hiếm hoi khi bạn muốn function URL của mình công khai dưới dạng webhook, đừng sử dụng `AuthType` là `NONE` cho function URL của bạn. Và trong những trường hợp hiếm hoi đó, bạn vẫn cần triển khai cơ chế xác thực cơ bản trong hàm Lambda của mình. Xem thêm tại [Hướng dẫn: Tạo webhook endpoint sử dụng Lambda function URL - AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/urls-webhook-tutorial.html)

#### Tạo Function URLs

Trong bước này, bạn sẽ tạo 5 function URL, mỗi URL cho một hàm Lambda.

![alt text](/images/diagrams/workshop-1-function-urls-high-level.drawio.svg)

1. Để tạo function URL cho hàm Lambda `list-users`:

   - Mở [trang Functions trong bảng điều khiển Lambda](https://console.aws.amazon.com/lambda/home?#/functions)

   - Nhấp vào hàm `list-users`.

   - Mở tab `Cấu hình` (Configuration)
   - Mở phần `Function URL`
   - Nhấp vào `Tạo function URL` (Create function URL)

     ![alt text](/images/workshop-1/lambda-function-url--create.jpg)

   - Trang `Cấu hình Function URL`, chọn `Loại xác thực` (Auth type) là `NONE`.

   - Nhấp `Lưu` (Save)

     ![alt text](/images/workshop-1/lambda-function-url--configure.jpg)

   - Sau khi tạo xong function URL, bạn có thể xem nó trong phần `Tổng quan về hàm` (Function overview) hoặc trong phần `Cấu hình` / `Function URL`.

     ![alt text](/images/workshop-1/lambda-function-url--location.jpg)

   - Sao chép function URL, bạn sẽ cần nó cho bước tiếp theo.

1. Lặp lại quy trình này để tạo function URL cho các hàm Lambda khác: `create-user`, `get-user`, `update-user`, `delete-user`.
