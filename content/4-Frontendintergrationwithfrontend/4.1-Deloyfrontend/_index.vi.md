---
title : "Triển khai giao diện người dùng"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

Bước đầu trong phần này, chúng ta sẽ host ứng dụng web với S3 Static website hosting:

1. Mở bảng điều khiển [Amazon S3 Console](https://console.aws.amazon.com/s3)
2. Nhấn chọn **Create Bucket**
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/001-frontendintergrationwithapigateway.png)

3. Nhập tên cho bucket, ví dụ như `fcjdmswebstore-5801`
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/002-frontendintergrationwithapigateway.png)

4. Bỏ chọn chặn cho phép truy cập public
 + Tích vào mục **I acknowledge that the current settings might result in this bucket and the objects within becoming public**
 ![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/003-frontendintergrationwithapigateway.png)

5. Ấn nút **Create bucket** 
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/004-frontendintergrationwithapigateway.png)

6. Ấn vào bucket đã tạo
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/005-frontendintergrationwithapigateway.png)

7. Ấn tab **Properties** 
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/006-frontendintergrationwithapigateway.png)

8. Kéo xuống cuối trang, ấn **edit** của mục **Static web hosting**
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/007-frontendintergrationwithapigateway.png)

9. Chọn **Enable** để kích hoạt host web tình trên S3
 + Chọn **Host a static website** cho mục **Hosting type**
 + Nhập `index.html` cho mục **Index document** 

![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/008-frontendintergrationwithapigateway.png)

10. Ấn **Save changes**
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/009-frontendintergrationwithapigateway.png)
 + Sau khi kích hoạt thành công, bạn hãy ghi lại đường dẫn của web
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/010-frontendintergrationwithapigateway.png)

11. Sau đó, chúng ta cần thêm policy cho S3 bucket để có thể truy cập được:
 + Chọn tab **Permissions** 
 + Ấn **Edit** của mục **Bucket policy**
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/011-frontendintergrationwithapigateway.png)

12. Sao chép chính sách dưới đây vào mục **Policy**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*"
        }
    ]
}

```

 + Thay thế `BUCKET_NAME` với tên bucket mà bạn đã đặt, sau đó ấn **Save changes**
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/012-frontendintergrationwithapigateway.png)

13. Mở tệp **src/component/Home/Upload.js** trong thư mục source code của ứng dụng và bỏ comment đoạn code gọi API ghi dữ liệu vào DynamoDB.

![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/013-frontendintergrationwithapigateway.png)

14. Tiếp theo chạy câu lệnh sau tại thư mục gốc của project bạn đã tải về. (FCJ-Serverless-DMS)
```
yarn build
aws s3 cp build s3://BUCKET_NAME --recursive

```
 + Thay thế `BUCKET_NAME` với tên bucket mà bạn đã đặt

Kết quả sau khi chạy xong câu lệnh
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/014-frontendintergrationwithapigateway.png)

15. Dán đường dẫn web mà bạn vừa ghi lại vào trình duyệt web của bạn
![S3]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/015-frontendintergrationwithapigateway.png)

Bạn đã hoàn thành việc host website của mình trên S3. Sang phần tiếp theo chúng ta cập nhật lại các lambda function