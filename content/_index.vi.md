---
title: "Xây dựng microservice API CRUD không máy chủ với AWS Lambda và function URLs"
weight: 1
chapter: false
---

# Xây dựng microservice API CRUD không máy chủ với AWS Lambda và function URLs

Workshop này sẽ hướng dẫn bạn tạo một microservice API CRUD chỉ với 2 dịch vụ AWS:

- AWS Lambda
- Amazon DynamoDB

Bạn cũng sẽ tìm hiểu về:

- Cách _trực tiếp_ gọi một hàm Lambda theo 3 cách khác nhau
- Cách gọi _đồng bộ_ một hàm Lambda
- Ai có thể gọi các hàm Lambda của bạn (còn gọi là _quyền truy cập_)
- Cách các hàm Lambda của bạn truy cập các tài nguyên AWS khác (ví dụ: bảng DynamoDB)

Kiến trúc cấp cao có dạng như sau:

![alt text](/images/diagrams/workshop-1-high-level.drawio.svg)

Bạn sẽ được hướng dẫn từng bước để đạt được kiến trúc cấp thấp:

![alt text](/images/diagrams/workshop-1-function-urls.drawio.svg)
