---
title : "Create creating function"
weight : 2 
chapter : false
pre : " <b> 2.2.2 </b> "
---

This section will create a function to add document information stored in the DynamoDB table.

## Create function creating
1. Open [AWS Lambda console](https://console.aws.amazon.com/lambda/)
2. Click **Create function**

![Creating function](/images/2.deloydatabase/005-createlistingfunction.png)

3. Enter function name: `upload_document`
 + Select **Python 3.9** for Runtime
 + Click **Create function**

![Creating function](/images/2.deloydatabase/014-createcreatingfunction.png)

4. Enter the following code for the **lambda_function.py** file:

```python
import json
import boto3
import os
from datetime import datetime, timezone

dynamodb = boto3.resource('dynamodb')

def lambda_handler(event, context):
    table_name = os.environ['TABLE_NAME']
    now = datetime.now(tz=timezone.utc)
    dt_string = now.strftime("%d/%m/%Y %H:%M:%S")
    #doc_data = json.loads(event["body"])
    doc_data = event["body"]

    path = "protected/{}/{}".format(doc_data['identityId'], doc_data['file'])
    doc_data.update({"path": path, "modified": dt_string})
    table = dynamodb.Table(table_name)
    table.put_item(Item = doc_data)
        
    # TODO implement
    return {
        'statusCode': 200,
        'body': 'successfully upload!',
        'headers': {
            'Content-Type': 'application/json',
            "Access-Control-Allow-Headers": "Access-Control-Allow-Headers, Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method,X-Access-Token, XKey, Authorization",
            "Access-Control-Allow-Origin": "*",
            "Access-Control-Allow-Methods": "GET,PUT,POST,DELETE,OPTIONS"
        }
    }

```

 + Then click **Deloy**

![Creating function](/images/2.deloydatabase/015-createcreatingfunction.png)

 The above code executes to get the user’s **TABLE_NAME** and **id** environment variables from the event. Then **query** to the DynamoDB table provided that the value of **Partition key** is equal to the user’s id. Then reformat the data returned after the query.

5. We need to add an environment variable to the function. Click the **Configuration** tab, then select **Environment variables** in the left menu. Press **Edit**

![Creating function](/images/2.deloydatabase/016-createcreatingfunction.png)

6. Click **Add environment variable**
 + Enter `TABLE_NAME` as key
 + Enter the DynamoDB table name that you just created
 + Click **Save**

![Creating function](/images/2.deloydatabase/017-createcreatingfunction.png)

 7. Next, add permissions for function to access DynamoDB table
 + Click **Permission** on the left menu
 + Click on the execution role of the function

![Creating function](/images/2.deloydatabase/018-createcreatingfunction.png)

8. Expand the **AWSLambdaBasicExecutionRole…** policy, then click **Edit**

![Creating function](/images/2.deloydatabase/019-createcreatingfunction.png)

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

![Creating function](/images/2.deloydatabase/020-createcreatingfunction.png)

10. Click **Save changes**

![Creating function](/images/2.deloydatabase/021-createcreatingfunction.png)