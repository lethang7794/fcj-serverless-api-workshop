---
title: "Tạo hàm update-user"
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

Lặp lại các bước trong [tạo hàm `create-users`](/4-creating-lambda-functions/4.1-creating-create-user-function/), với các điểm khác biệt sau:

1. Tên hàm: `update-user`
1. Mã nguồn:

   ```python
   import datetime
   import os
   import json
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
       Xử lý Lambda để cập nhật thông tin người dùng theo id.
       Yêu cầu tham số đường dẫn 'id' và thân yêu cầu JSON chứa các thuộc tính cần cập nhật.
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
           if not data:
               raise ValueError("Không có dữ liệu cập nhật được cung cấp.")
       except (json.JSONDecodeError, ValueError) as e:
           return response(400, {"error": str(e)})

       data.pop("id", None)  # Xóa id khỏi dữ liệu để tránh cập nhật
       data["updated_at"] = getCurrentTime()  # Thêm dấu thời gian cập nhật

       # Xây dựng UpdateExpression
       update_expr = "SET " + ", ".join(f"#k{i} = :v{i}" for i, _ in enumerate(data))
       expr_attr_names = {f"#k{i}": k for i, k in enumerate(data)}
       expr_attr_values = {f":v{i}": v for i, v in enumerate(data.values())}

       try:
           result = table.update_item(
               Key={"id": user_id},
               UpdateExpression=update_expr,
               ExpressionAttributeNames=expr_attr_names,
               ExpressionAttributeValues=expr_attr_values,
               ConditionExpression="attribute_exists(id)",
               ReturnValues="ALL_NEW",
           )
           return response(200, result.get("Attributes"))
       except dynamodb.meta.client.exceptions.ConditionalCheckFailedException:
           return response(404, {"error": "Không tìm thấy người dùng."})
       except Exception as e:
           return response(500, {"error": str(e)})
   ```

1. Chính sách quyền: `AmazonDynamoDBFullAccess`
