---
title: "Building serverless CRUD API microservice with AWS Lambda and function URLs"
weight: 1
chapter: false
---

# Building serverless CRUD API microservice with AWS Lambda and function URLs

This workshop will guide you to create a CRUD API microservice with only 2 AWS services:

- AWS Lambda
- Amazon DynamoDB

You will also learn about

- _directly_ invoking a Lambda function in 3 ways
- _synchronously_ invoking a Lambda
- who can invoke your Lambda functions (aka _access permissions_)
- how your Lambda functions access other AWS resources (e.g. DynamoDB table)

The high level architecture looks like this:

![alt text](/images/diagrams/workshop-1-high-level.drawio.svg)

You will guide with a walk-through to achieve the low level architecture:

![alt text](/images/diagrams/workshop-1-function-urls.drawio.svg)
