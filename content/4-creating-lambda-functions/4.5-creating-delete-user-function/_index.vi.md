---
title: "Tạo hàm delete-user"
weight: 5
chapter: false
pre: " <b> 4.5. </b> "
---

Lặp lại các bước trong [tạo hàm `create-users`](/4-creating-lambda-functions/4.1-creating-create-user-function/), với các điểm khác biệt sau:

1. Tên hàm: `delete-user`
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
       Helper to build HTTP responses
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
       Lambda handler to delete a user by id.
       Expects path parameter 'id'.
       """
       try:
           data = json.loads(event["body"]) if "body" in event else event
       except json.JSONDecodeError:
           return response(400, {"error": "Invalid JSON body: " + event["body"]})

       try:
           user_id = data["id"]
       except (KeyError, json.JSONDecodeError):
           return response(400, {"error": "Invalid request body; id is required."})

       try:
           table.delete_item(
               Key={"id": user_id}, ConditionExpression="attribute_exists(id)"
           )
           return response(204)
       except dynamodb.meta.client.exceptions.ConditionalCheckFailedException:
           return response(404, {"error": "User not found."})
       except Exception as e:
           return response(500, {"error": str(e)})
   ```

1. Chính sách quyền: `AmazonDynamoDBFullAccess`

---

Lúc này, hãy kiểm tra [mục Functions trong bảng điều khiển Lambda](https://console.aws.amazon.com/lambda/home?#/functions) và xác nhận rằng bạn đã có đủ 5 hàm Lambda.

![alt text](/images/workshop-1/lambda--list-functions.png)
