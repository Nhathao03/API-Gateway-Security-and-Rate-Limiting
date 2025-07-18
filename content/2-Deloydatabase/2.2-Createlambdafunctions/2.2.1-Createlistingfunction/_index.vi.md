---
title : "Tạo function liệt kê"
weight : 1
chapter : false
pre : " <b> 2.2.1 </b> "
---

Trong phần này chúng ta sẽ tạo function để liệt kê các tài liệu được lưu trong DynamoDB table theo id của người dùng.

1. Mở bảng điều kiển [AWS Lambda console](https://console.aws.amazon.com/lambda/)
2. Nhấn nút **Create function**

![Listing function](/images/2.deloydatabase/005-createlistingfunction.png)

3. Nhập tên function: `list_documents`
 + Chọn **Python 3.9** cho mục Runtime
 + Nhấn nút **Create function**

![Listing function](/images/2.deloydatabase/006-createlistingfunction.png)

4. Nhập vào đoạn code sau cho tệp **lambda_function.py**:

```python
import json
import boto3
import os
from decimal import *
from boto3.dynamodb.types import TypeDeserializer

dynamodb = boto3.client('dynamodb') 
serializer = TypeDeserializer()

class DecimalEncoder(json.JSONEncoder):
    def default(self, obj):
        if isinstance(obj, Decimal):
            return str(obj)
        return json.JSONEncoder.default(self, obj)

def deserialize(data):
    if isinstance(data, list):
        return [deserialize(v) for v in data]

    if isinstance(data, dict):
        try:
            return serializer.deserialize(data)
        except TypeError:
            return {k: deserialize(v) for k, v in data.items()}
    else:
        return data
        
def lambda_handler(event, context):
    table_name = os.environ['TABLE_NAME']
    user_id = event['pathParameters']['id']
    print(user_id)
    docs = dynamodb.query(
        TableName=table_name,
        KeyConditionExpression="user_id = :id",
        ExpressionAttributeValues={ ":id": { 'S': user_id } }
    )
    
    format_data_docs = deserialize(docs["Items"])
    # TODO implement
    return {
        "statusCode": 200,
        "headers": {
            "Content-Type": "application/json",
            "Access-Control-Allow-Origin": "*",
            "Access-Control-Allow-Methods": "GET,PUT,POST,DELETE, OPTIONS",
            "Access-Control-Allow-Headers": "Access-Control-Allow-Headers, Origin,Accept, X-Requested-With, Content-Type, Access-Control-Request-Method,X-Access-Token,XKey,Authorization"
        },
        "body": json.dumps(format_data_docs, cls=DecimalEncoder)
    }
```

 + Sau đó nhấn nút **Deloy**

![Listing function](/images/2.deloydatabase/007-createlistingfunction.png)

 Đoạn code trên thực hiện lấy biến môi trường **TABLE_NAME** và **id** của người dùng từ event. Sau đó **query** đến DynamoDB table với điều kiện giá trị của **Partition key** bằng id của người dùng. Sau đó định dạng lại dữ liệu được trả về sau khi query.

5. Chúng ta cần thêm biến môi trường cho function. Ấn tab **Configuration**, sau đó chọn **Environment variables** ở menu phía bên trái. Ấn **Edit**

![Listing function](/images/2.deloydatabase/008-createlistingfunction.png)

6. Nhấn nút **Add environment variable**
 + Nhập `TABLE_NAME` vào key
 + Nhập tên DynamoDB table bạn vừa tạo làm giá trị
 + Nhấn nút **Save**

![Listing function](/images/2.deloydatabase/009-createlistingfunction.png)

 7. Tiếp theo, thêm quyền cho function để truy cập vào DynamoDB table
 + Nhấn nút **Permission** ở menu bên trái
 + Ấn vào tên role mà lambda function đang thực hiện

![Listing function](/images/2.deloydatabase/010-createlistingfunction.png)

8. Mở rộng chính sách **AWSLambdaBasicExecutionRole…** sau đó ấn **Edit**

![Listing function](/images/2.deloydatabase/011-createlistingfunction.png)

9. Nhấn nút **JSON**. Sao chép đoạn json dưới đây vào editor

```
,
        {
            "Effect": "Allow",
            "Action": [
                "dynamodb:Query"
            ],
            "Resource": "arn:aws:dynamodb:REGION:ACCOUNT_ID:table/Documents"
        }
```

Thay thế `REGION` và `ACCOUNT_ID` bằng vùng mà bạn tạo bảng và account id của bạn.
+ Nhấn nút **Review policy**

![Listing function](/images/2.deloydatabase/012-createlistingfunction.png)

10. Nhấn nút **Save changes**

![Listing function](/images/2.deloydatabase/013-createlistingfunction.png)