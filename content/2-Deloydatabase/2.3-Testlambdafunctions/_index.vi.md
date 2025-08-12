---
title : "Kiểm tra các funcrion"
weight : 3
chapter : false
pre : " <b> 2.3 </b> "
---

Trong phần này chúng ta sẽ tạo kiểm tra xem các function có hoạt động đúng hay không.

Để kiểm tra các function, bạn hãy tải tệp dưới đây về máy và chạy câu lệnh: `aws dynamodb batch-write-item --request-items file://documentData.json`

📎 Document Data

- [documentData.json](https://000133.awsstudygroup.com/3-test-lambda-functions/_index.files/documentData.json) (3 KB)

![Documents]({{< relref "/" >}}images/2.deloydatabase/030-testlambdafunction.png)

#### Kiểm tra function liệt kê
1. Mở bảng điều kiển của function **list_documents**
2. Ấn tab **Test**
 + Nhập `tc_1` cho tên event
 + Nhập đoạn json dưới đây cho **Event JSON**

```
{ 
  "pathParameters": {
    "id": "abcd1234"
  }
}

```
3. Ấn **Save**, sau đó ấn **Test**
![Documents]({{< relref "/" >}}images/2.deloydatabase/031-testlambdafunction.png)

4. Bạn sẽ nhận kết quả trả về là toàn bộ thông tin của các tệp của người dùng với id là **abcd1234**
![Documents]({{< relref "/" >}}images/2.deloydatabase/032-testlambdafunction.png)

#### Kiểm tra function tạo dữ liệu
1. Mở bảng điều khiển của function **upload_document** 
2. Ấn tab **Test** 
 + Nhập `tc_1` cho tên event
 + Nhập đoạn json dưới đây cho **Event JSON**

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
3. Ấn **Save**, sau đó ấn **Test**
![Documents]({{< relref "/" >}}images/2.deloydatabase/033-testlambdafunction.png)

4. Bạn sẽ nhận kết quả trả về là **succeeded**
![Documents]({{< relref "/" >}}images/2.deloydatabase/034-testlambdafunction.png)

5. Mở bảng **Documents** để kiểm tra xem đã thêm thành công hay chưa
![Documents]({{< relref "/" >}}images/2.deloydatabase/035-testlambdafunction.png)

#### Kiểm tra function xóa dữ liệu  
1. Mở bảng điều kiển của function **delete_documents**
2. Ấn tab **Test** 
 + Nhập `tc_1` cho tên event
 + Nhập đoạn json dưới đây cho **Event JSON**

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
3. Ấn **Save**, sau đó ấn **Test**
![Documents]({{< relref "/" >}}images/2.deloydatabase/036-testlambdafunction.png)

4. Bạn sẽ nhận kết quả trả về là **succeeded**
![Documents]({{< relref "/" >}}images/2.deloydatabase/037-testlambdafunction.png)

5. Mở bảng **Documents** để xem là đã xóa thành công hay chưa
![Documents]({{< relref "/" >}}images/2.deloydatabase/038-testlambdafunction.png)

Vậy là bạn đã hoàn thành tạo các Lambda function tương tác với DynamoDB. Trong bài tiếp theo chúng ta xác thực vào lưu trữ với thư viện Amplify.