---
title: "Tóm tắt"
weight: 10
chapter: false
pre: "<b>10. </b>"
---

## Tóm tắt

Trong workshop này, bạn đã có kinh nghiệm thực hành về:

{{<figure src="/images/workshop-1/Amazon-DynamoDB.svg" title="Amazon DynamoDB" width=100pc >}}

- Dịch vụ DynamoDB
  - Tạo một **bảng DynamoDB**.
  - Tương tác với một bảng DynamoDB từ một hàm Lambda.
  - Khám phá các phần tử của một bảng DynamoDB sử dụng AWS Management Console.

{{<figure src="/images/workshop-1/AWS-Lambda.svg" title="AWS Lambda" width=100pc >}}

- Dịch vụ Lambda:
  - Tạo **hàm Lambda**.
  - _Trực tiếp_ gọi hàm Lambda:
    - Sử dụng AWS Management Console
    - Sử dụng AWS CLI
    - Sử dụng bất kỳ trình khách HTTP nào, ví dụ: trình duyệt, `curl`, và _URL hàm (function URL)_.
  - _Đồng bộ_ gọi một hàm Lambda (và chờ phản hồi)
  - Sử dụng _URL hàm (function URL)_ để expose hàm Lambda cho người dùng công khai, không xác thực (không có thông tin xác thực AWS).

{{<figure src="/images/workshop-1/AWS-Identity-and-Access-Management.svg" title="AWS Identity and Access Management" width=100pc >}}

Bạn cũng hiểu về cách IAM hoạt động với Lambda và DynamoDB:

- _quyền truy cập_ - quyền cho các thực thể khác truy cập các hàm của bạn - nói cách khác, đó là cách IAM xác thực và ủy quyền gọi hàm Lambda của bạn.
  - Khi gọi hàm Lambda sử dụng AWS Management Console, bạn đang sử dụng quyền của thông tin xác thực IAM mà bạn đã đăng nhập.
  - Khi gọi hàm Lambda sử dụng AWS CLI, bạn đang sử dụng quyền của thông tin xác thực IAM mà bạn đã cấu hình cho AWS CLI.
  - Khi gọi hàm Lambda sử dụng địa chỉ hàm công khai, IAM vẫn cần xác thực/ủy quyền gọi hàm đó (mặc dù IAM cho phép bất kỳ nguyên tắc nào bao gồm cả người dùng không xác thực).

- _role thực thi (execution role)_ - cung cấp quyền cho các hàm truy cập các tài nguyên khác, ví dụ: bảng DynamoDB.

## Tổng kết

Hãy tổng kết nhanh kiến trúc của workshop:

![alt text](/images/diagrams/workshop-1-function-urls.drawio.svg)

- Microservice CRUD API serverless của chúng tôi được phục vụ qua _URL hàm (function URL)_.
- URL hàm (function URL) là một URL công khai có thể được truy cập bởi bất kỳ ai.
- Định tuyến đến từng hoạt động CRUD được thực hiện bởi ứng dụng người dùng cuối thông qua _URL hàm (function URL)_ duy nhất của từng hàm Lambda.

Bạn có thể thấy rằng expose các microservice CRUD API serverless của chúng ta cho người dùng cuối qua _URL hàm (function URL)_ không phải là một ý tưởng hay.

> [!NOTE]
> Mặc dù ỦL hàm không phải là một lựa chọn phù hợp cho trường hợp của chúng tôi, nó vẫn là một cách nhanh chóng, đơn giản để expose một hàm Lambda như một webhook (tất nhiên với xác thực cơ bản hoặc xác thực IAM).

## Tiếp theo?

Nếu bạn muốn tìm hiểu thêm về function URL của Lambda, bạn có thể tham khảo các tài nguyên sau:

- [Chọn phương thức để gọi hàm Lambda bằng yêu cầu HTTP - AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/furls-http-invoke-decision.html)
- [Function URL của AWS Lambda - Hướng dẫn chi tiết AWS](https://docs.aws.amazon.com/prescriptive-guidance/latest/choosing-the-right-aws-service-for-your-microservice-endpoints/function-urls.html)

Nếu không, bạn có thể theo dõi workshop tiếp theo để tìm hiểu về:

<!-- TODO: Thêm liên kết đến workshop tiếp theo -->

- Quản lý các hàm Lambda thành một REST API với API Gateway.
