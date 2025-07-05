---
title: "Summary"
weight: 10
chapter: false
pre: "<b>10. </b>"
---

## Summary

In this workshop, you have hands-on experience about:

{{<figure src="/images/workshop-1/Amazon-DynamoDB.svg" title="Amazon DynamoDB" width=100pc >}}

- DynamoDB service
  - Creating a **DynamoDB table**.
  - Interact with a DynamoDB table from a Lambda functions.
  - Explore the items of a DynamoDB table using AWS Management Console.

{{<figure src="/images/workshop-1/AWS-Lambda.svg" title="AWS Lambda" width=100pc >}}

- Lambda service:
  - Creating **Lambda functions**.
  - _Directly_ invoking Lambda functions:
    - Using AWS Management Console
    - Using AWS CLI
    - Using any HTTP client, e.g. a browser, `curl`, and _function URL_.
  - _Synchronously_ invoking a Lambda (and wait for the response)
  - Using _function URL_ to expose Lambda functions to public, unauthenticated users (that doesn't have AWS credential).

{{<figure src="/images/workshop-1/AWS-Identity-and-Access-Management.svg" title="AWS Identity and Access Management" width=100pc >}}

You also understand about IAM works with Lambda and DynamoDB:

- _access permissions_ - permissions for other entities to access your functions - in other words, it's how the IAM authenticate and authorize the invocation of your Lambda functions.
  - When invoking a Lambda function using AWS Management Console, you're using the permission of the IAM credential you've logged in.
  - When invoking a Lambda function using AWS CLI, you're using the permission of the IAM credential you've configured for AWS CLI.
  - When invoking a Lambda function using its public function, IAM still needs to authenticate/authorize that invocation (although IAM allow any principle which including unauthenticated users).

- _execution role_ - which provide permissions for functions to access other resources, e.g. DynamoDB table.

## Recap

Let's have a quick recap of the architecture of the workshop:

![alt text](/images/diagrams/workshop-1-function-urls.drawio.svg)

- Our serverless CRUD API microservice is exposed via function URL.
- The function URL is a public URL that can be accessed by anyone.
- The routing to each CRUD operation is done by the consumer app via the unique function URL of each Lambda function.

You can see that exposing our serverless CRUD API microservice to public via function URL is not a good idea.

> [!NOTE]
> Although function URL is not a good fit for our use case, it's still a quick, simple way to expose a Lambda function as a webhook (of course with basic authentication or IAM authentication).

## What's next?

If you're interested in learning more about Lambda function URL, you can refer to the following resources:

- [Select a method to invoke your Lambda function using an HTTP request - AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/furls-http-invoke-decision.html)
- [AWS Lambda function URLs - AWS Prescriptive Guidance](https://docs.aws.amazon.com/prescriptive-guidance/latest/choosing-the-right-aws-service-for-your-microservice-endpoints/function-urls.html)

Otherwise, you can follow the next workshop to learn about:

<!-- TODO: Add the link to the next workshop -->

- Managing the Lambda functions into a REST API with API Gateway.
