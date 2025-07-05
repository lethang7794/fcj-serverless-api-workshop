---
title: "Tạo hàm create-user"
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

1. Mở [phần `Functions`](https://console.aws.amazon.com/lambda/home#/functions) trong [bảng điều khiển Lambda](https://console.aws.amazon.com/lambda/home)
1. Nhấp vào `Create function`

   ![alt text](/images/workshop-1/lambda-create-function--functions-page.png)

1. Chọn `Author from scratch`
1. Trong phần `Basic information`, nhập:
   - Function name: `create-user`
   - Runtime: `Python 3.13`
   - Architecture: Giữ nguyên `x86_64`
   - Permissions - `Change default execution role`: Giữ nguyên `Create a new role with basic Lambda permissions` để cho phép Lambda tạo vai trò thực thi mới cho hàm.
1. Nhấp vào `Create function`

   ![alt text](/images/workshop-1/lambda-create-function--options.png)

1. Sau khi hàm được tạo, bạn sẽ được chuyển hướng đến trang chi tiết của hàm.

   ![alt text](/images/workshop-1/lambda-create-function--function-detail.png)

1. Trong tab `Code`, phần `Code source`:

   - Chờ trình chỉnh sửa mã tải xong.
   - Trong tab chỉnh sửa cho `lambda_function.py`, thay thế toàn bộ mã giữ chỗ bằng mã sau:

     ```python
     import datetime
     import os
     import json
     import uuid
     import boto3

     # Initialize DynamoDB resource and table
     dynamodb = boto3.resource("dynamodb")
     TABLE_NAME = os.environ.get("USERS_TABLE", "UsersTable")
     table = dynamodb.Table(TABLE_NAME)


     def getCurrentTime():
         return datetime.datetime.now().replace(microsecond=0).isoformat()


     def response(status_code, body=None):
         """
         Hàm trợ giúp để tạo phản hồi HTTP
         """
         resp = {
             "statusCode": status_code,
             "headers": {
                 "Content-Type": "application/json",
                 "Access-Control-Allow-Origin": "*",
             },
         }
         if body is not None:
             resp["body"] = json.dumps(body)
         return resp


     def lambda_handler(event, context):
         """
         Xử lý Lambda để tạo người dùng và lưu dữ liệu vào DynamoDB.
         Yêu cầu thân yêu cầu JSON chứa 'id', 'name', 'email' và tùy chọn các thuộc tính khác.
         """
         try:
             data = json.loads(event["body"]) if "body" in event else event
         except json.JSONDecodeError:
             return response(400, {"error": "JSON không hợp lệ: " + event["body"]})

         now = getCurrentTime()
         id = uuid.uuid4()

         try:
             # Xác thực các trường bắt buộc
             name = data["name"]
             email = data["email"]
         except (KeyError, json.JSONDecodeError):
             return response(
                 400, {"error": "Thiếu thông tin bắt buộc: name và email là bắt buộc."}
             )

         item = {
             "id": str(id),
             "name": name,
             "email": email,
             "created_at": now,
             "updated_at": now,
             **{k: v for k, v in data.items() if k not in ["name", "email"]},
         }

         try:
             table.put_item(Item=item, ConditionExpression="attribute_not_exists(id)")
             return response(201, item)
         except dynamodb.meta.client.exceptions.ConditionalCheckFailedException:
             return response(409, {"error": "Người dùng với id đã tồn tại."})
         except Exception as e:
             return response(500, {"error": str(e)})
     ```

   - Nhấp vào `Deploy (Ctrl + Shift + U)` để triển khai hàm lambda.

     ![alt text](/images/workshop-1/lambda-create-function--source-code-and-deploy.png)

1. Mở tab `Configuration`
1. Mở phần `Permissions`
1. Trong `Execution Role`, nhấp vào tên vai trò `create-user-role-XXXXXXXX` để mở trang IAM role.

   ![alt text](/images/workshop-1/lambda-create-function--execution-role.png)

1. Trang IAM role, tab `Permissions`, nhấp vào nút `Add permissions`, chọn `Attach Polices`.

   ![alt text](/images/workshop-1/lambda-create-function--attach-permission-policy.png)

1. Tìm kiếm chính sách `AmazonDynamoDBFullAccess`.
1. Chọn chính sách `AmazonDynamoDBFullAccess`.
1. Nhấp `Add permissions` để gắn chính sách IAM vào Vai trò IAM.

   ![alt text](/images/workshop-1/lambda-create-function--permission-policy-for-dynamodb.png)
