---
title: "Tạo hàm get-user"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---

Lặp lại các bước trong [tạo hàm `create-users`](/4-creating-lambda-functions/4.1-creating-create-user-function/), với các điểm khác biệt sau:

1. Tên hàm: `get-user`
1. Mã nguồn:

   ```python
   import os
   import json
   import boto3

   # Initialize DynamoDB resource and table
   dynamodb = boto3.resource("dynamodb")
   TABLE_NAME = os.environ.get("USERS_TABLE", "UsersTable")
   table = dynamodb.Table(TABLE_NAME)


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
       Xử lý Lambda để lấy thông tin người dùng theo id.
       Yêu cầu tham số đường dẫn 'id'.
       """

       try:
           data = json.loads(event["body"]) if "body" in event else event
       except json.JSONDecodeError:
           return response(400, {"error": "JSON không hợp lệ: " + event["body"]})

       try:
           user_id = data["id"]
       except (KeyError, json.JSONDecodeError):
           return response(400, {"error": "Thiếu thông tin bắt buộc: id là bắt buộc."})

       try:
           result = table.get_item(Key={"id": user_id})
           item = result.get("Item")
           if not item:
               return response(404, {"error": "Không tìm thấy người dùng."})
           return response(200, item)
       except Exception as e:
           return response(500, {"error": str(e)})
   ```

1. Chính sách quyền: `AmazonDynamoDBReadOnlyAccess`
