---
title : "Tạo function xóa dữ liệu"
weight : 3
chapter : false
pre : " <b> 2.2.3 </b> "
---

Trong phần này chúng ta sẽ tạo function để xoá thông tin tài liệu được lưu trong DynamoDB table theo id của người dùng và tên tệp.

1. Mở bảng điều kiển [AWS Lambda console](https://console.aws.amazon.com/lambda/)
2. Nhấn nút **Create function**

![Deleting function](/images/2.deloydatabase/005-createlistingfunction.png)

3. Nhập tên function: `delete_documents`
 + Chọn **Python 3.9** cho mục Runtime
 + Nhấn nút **Create function**

![Deleting function](/images/2.deloydatabase/022-createdeletingfunction.png)

4. Nhập vào đoạn code sau cho tệp **lambda_function.py**:

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

 + Sau đó nhấn nút **Deloy**

![Deleting function](/images/2.deloydatabase/023-createdeletingfunction.png)

 Đoạn code trên thực hiện lấy biến môi trường **TABLE_NAME** và **partition key** và **sort key** từ event. Sau đó thêm xoá item có **partition key** và **sort key** khớp với input.

5. Chúng ta cần thêm biến môi trường cho function. Ấn tab **Configuration**, sau đó chọn **Environment variables** ở menu phía bên trái. Ấn **Edit**

![Deleting function](/images/2.deloydatabase/024-createdeletingfunction.png)

6. Nhấn nút **Add environment variable**
 + Nhập `TABLE_NAME` vào key
 + Nhập tên DynamoDB table bạn vừa tạo làm giá trị
 + Nhấn nút **Save**

![Deleting function](/images/2.deloydatabase/025-createdeletingfunction.png)

 7. Tiếp theo, thêm quyền cho function để truy cập vào DynamoDB table
 + Nhấn nút **Permission** ở menu bên trái
 + Ấn vào tên role mà lambda function đang thực hiện

![Deleting function](/images/2.deloydatabase/026-createdeletingfunction.png)

8. Mở rộng chính sách **AWSLambdaBasicExecutionRole…** sau đó ấn **Edit**

![Deleting function](/images/2.deloydatabase/027-createdeletingfunction.png)

9. Nhấn nút **JSON**. Sao chép đoạn json dưới đây vào editor

```
,
        {
            "Effect": "Allow",
            "Action": "dynamoDB:PutItem",
            "Resource": "arn:aws:dynamodb:REGION:ACCOUNT_ID:table/Documents"
        }

```

Thay thế `REGION` và `ACCOUNT_ID` bằng vùng mà bạn tạo bảng và account id của bạn.
+ Nhấn nút **Review policy**

![Deleting function](/images/2.deloydatabase/028-createdeletingfunction.png)

10. Nhấn nút **Save changes**

![Deleting function](/images/2.deloydatabase/029-createdeletingfunction.png)