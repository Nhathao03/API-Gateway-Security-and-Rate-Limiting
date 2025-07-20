---
title : "Test lambda function"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

In this section we will create tests to see if the functions are working properly.

To test the functions, download the following file to your computer and run the command: `aws dynamodb batch-write-item --request-items file://documentData.json`

📎 Document Data

- [documentData.json](https://000133.awsstudygroup.com/3-test-lambda-functions/_index.files/documentData.json) (3 KB)

![Documents](/images/2.deloydatabase/030-testlambdafunction.png)

#### Test listing function
1. Open the **list_documents** function console
2. Click **Test** tab
 + Enter `tc_1` for event name
 + Enter the below json for **Event JSON**

```
{ 
  "pathParameters": {
    "id": "abcd1234"
  }
}

```
3. Click **Save**, then click **Test**
![Documents](/images/2.deloydatabase/031-testlambdafunction.png)

4. You will get all the information of the user's files with the id **abcd1234**
![Documents](/images/2.deloydatabase/032-testlambdafunction.png)

#### Test creating function
1. Open the **upload_document** function console
2. Click **Test** tab
 + Enter `tc_1` for event name
 + Enter the below json for **Event JSON**

```
{
  "body":{
      "user_id": "abcd1234",
      "file": "aws_serverless.doc",
      "folder": "",
      "identityId": "123456cvbn",
      "modified": "13-03-2023",
      "size": "2MB",
      "type": "doc",
      "tag": "aws, serverless"
  }
}


```
3. Click **Save**, then click **Test**
![Documents](/images/2.deloydatabase/033-testlambdafunction.png)

4. You will get a return result of **succeeded**
![Documents](/images/2.deloydatabase/034-testlambdafunction.png)

5. Open **Documents** table to check if added successfully
![Documents](/images/2.deloydatabase/035-testlambdafunction.png)

#### Test deleting function
1. Open the **delete_documents** function console
2. Click **Test** tab
 + Enter `tc_1` for event name
 + Enter the below json for **Event JSON**

```
{
  "pathParameters": {
    "id": "abcd1234"
  },
  "queryStringParameters": {
    "file": "aws-exports.js"
  }
}

```
3. Click **Save**, then click **Test**
![Documents](/images/2.deloydatabase/036-testlambdafunction.png)

4. You will get a return result of **succeeded**
![Documents](/images/2.deloydatabase/037-testlambdafunction.png)

5. Open **Documents** table to check if added successfully
![Documents](/images/2.deloydatabase/038-testlambdafunction.png)

You are done creating Lambda functions that interact with DynamoDB. In the next post we will authenticate to the archive with the Amplify library.