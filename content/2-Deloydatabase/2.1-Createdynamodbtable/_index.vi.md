---
title : "Tạo bảng với DynamoDB"
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

### CREATE DYNAMODB TABLE

1. Open [DynamoDB console](https://console.aws.amazon.com/dynamodbv2)
2. Click **Create table**

![DynamoDB](images/2.deloydatabase/001-createdynamodbtable.png)

3. Enter table name: `Documents`
 + Enter **Parition key** is `user_id`
 + Enter **Sort key** is `file`

![DynamoDB](images/2.deloydatabase/002-createdynamodbtable.png)

4. In **Table setting** section, select **Customsize setting**
 + Keep **DynamoDB Standard** for **Table class**
 + Select **On-demand** for **Capacity mode**

![DynamoDB](images/2.deloydatabase/003-createdynamodbtable.png)

5. Scroll to the bottom of the page, click **Create table**

![DynamoDB](images/2.deloydatabase/004-createdynamodbtable.png)