---
title : "Create deleting function"
weight : 3
chapter : false
pre : " <b> 2.2.3 </b> "
---

In this section, we will create a function to delete document information stored in the DynamoDB table by user id and filename.

1. Open [AWS Lambda console](https://console.aws.amazon.com/lambda/)
2. Click **Create function**

![Deleting function](/images/2.deloydatabase/005-createlistingfunction.png)

3. Enter function name: `delete_documents`
 + Select **Python 3.9** for Runtime
 + Click **Create function**

![Deleting function](/images/2.deloydatabase/014-createcreatingfunction.png)

4. Enter the following code for the **lambda_function.py** file:

```python
import json
import boto3
import os

client = boto3.resource('dynamodb')

def lambda_handler(event, context):
    # TODO implement
    table_name = os.environ['TABLE_NAME']
    error = None
    doc_pk = event['pathParameters']['id']
    print("doc_pk ", doc_pk)
    doc_sk = event['queryStringParameters']['file']
    print("doc_sk ", doc_sk)
    table = client.Table(table_name)
    key = {
        'user_id':doc_pk,
        'file':  doc_sk
    }
    
    try:
        table.delete_item(Key = key)
    except Exception as e:
        error = e
        
        
    except Exception as e:
        error = e
        
    if error is None:
        message = 'delete document successful!'
    else:
        print(error)
        message = 'delete document fail'
    
    return {
            'statusCode': 200,
            'body': message,
            'headers': {
                'Content-Type': 'application/json',
                'Access-Control-Allow-Origin': '*'
            },
        }

```

 + Then click **Deloy**

![Deleting function](/images/2.deloydatabase/015-createcreatingfunction.png)

 The above code executes to get the user’s **TABLE_NAME** and **id** environment variables from the event. Then **query** to the DynamoDB table provided that the value of **Partition key** is equal to the user’s id. Then reformat the data returned after the query.

5. We need to add an environment variable to the function. Click the **Configuration** tab, then select **Environment variables** in the left menu. Press **Edit**

![Deleting function](/images/2.deloydatabase/016-createcreatingfunction.png)

6. Click **Add environment variable**
 + Enter `TABLE_NAME` as key
 + Enter the DynamoDB table name that you just created
 + Click **Save**

![Deleting function](/images/2.deloydatabase/017-createcreatingfunction.png)

 7. Next, add permissions for function to access DynamoDB table
 + Click **Permission** on the left menu
 + Click on the execution role of the function

![Deleting function](/images/2.deloydatabase/018-createcreatingfunction.png)

8. Expand the **AWSLambdaBasicExecutionRole…** policy, then click **Edit**

![Deleting function](/images/2.deloydatabase/019-createcreatingfunction.png)

9. Click **JSON**. Copy the JSON below into the editor

```
,
        {
            "Effect": "Allow",
            "Action": "dynamoDB:PutItem",
            "Resource": "arn:aws:dynamodb:REGION:ACCOUNT_ID:table/Documents"
        }

```

Replace `REGION` and `ACCOUNT_ID` with the region you create the table and your account id.
+ Click **Review policy**

![Deleting function](/images/2.deloydatabase/020-createcreatingfunction.png)

10. Click **Save changes**

![Deleting function](/images/2.deloydatabase/021-createcreatingfunction.png)