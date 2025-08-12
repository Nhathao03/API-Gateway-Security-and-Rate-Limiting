---
title : "Tạo function tạo dữ liệu"
weight : 2 
chapter : false
pre : " <b> 2.2.2 </b> "
---

Trong phần này chúng ta sẽ tạo function để thêm thông tin tài liệu được lưu trong DynamoDB table.

## Tạo hàm thêm mới
1. Mở bảng điều kiển [AWS Lambda console](https://console.aws.amazon.com/lambda/)
2. Nhấn nút **Create function**

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/005-createlistingfunction.png)

3. Nhập tên function: `upload_document`
 + Chọn **Python 3.9** cho mục Runtime
 + Nhấn nút **Create function**

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/014-createcreatingfunction.png)

4. Nhập vào đoạn code sau cho tệp **lambda_function.py**:

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

 + Sau đó nhấn nút **Deloy**

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/015-createcreatingfunction.png)

 Đoạn code trên thực hiện lấy biến môi trường **TABLE_NAME** và dữ liệu của event. Sau đó thêm từng item vào DynamoDB table.

5. Chúng ta cần thêm biến môi trường cho function. Ấn tab **Configuration**, sau đó chọn **Environment variables** ở menu phía bên trái. Ấn **Edit**

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/016-createcreatingfunction.png)

6. Nhấn nút **Add environment variable**
 + Nhập `TABLE_NAME` vào key
 + Nhập tên DynamoDB table bạn vừa tạo làm giá trị
 + Nhấn nút **Save**

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/017-createcreatingfunction.png)

 7. Tiếp theo, thêm quyền cho function để truy cập vào DynamoDB table
 + Nhấn nút **Permission** ở menu bên trái
 + Ấn vào tên role mà lambda function đang thực hiện

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/018-createcreatingfunction.png)

8. Mở rộng chính sách **AWSLambdaBasicExecutionRole…** sau đó ấn **Edit**

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/019-createcreatingfunction.png)

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

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/020-createcreatingfunction.png)

10. Nhấn nút **Save changes**

![Listing function](/API-Gateway-Security-and-Rate-Limiting/images/2.deloydatabase/021-createcreatingfunction.png)