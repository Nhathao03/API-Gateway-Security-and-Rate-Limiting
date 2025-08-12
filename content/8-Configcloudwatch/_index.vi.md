---
title : "Config CloudWatch to monitor user actions using API"
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

Ở phần này, chúng ta sẽ cấu hình CloudWatch để giám sát người dùng sử dụng API.

1. Mở bảng điều khiển [API Gateway](https:console.aws.amazon.com/apigateway)
2. Chọn **API** đã tạo
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/001-configcloudwatch.png)

3. Chọn **Stage**
 + Tại **Logs and tracing**, ấn **Edit**
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/002-configcloudwatch.png)

4. Tại **Edit logs and tracing**
 + Chọn **Errors and info logs**
 + Ấn **Save**
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/003-configcloudwatch.png)

5. Mở **Postman** và gửi bất kỳ yêu cầu nào
![Postman]({{< relref "/" >}}images/8.configcloudwatch/004-configcloudwatch.png)

6. Mở [CloudWatch](https:console.aws.amazon.com/cloudwatch)
 + Ấn **Log groups**
 + Chọn ***API-Gateway-Execution-Logs_66r5ayu9s7/dev***
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/005-configcloudwatch.png)
 + Chọn **Log streams**
 + Sao chép **ARN**, chúng ta sẽ sử dụng ở phần tiếp theo.
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/006-configcloudwatch.png)

7. Kết quả thành công
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/007-configcloudwatch.png)

{{% notice info %}}
Ở đây chúng ta sẽ nhìn thấy tất cả các hành động chúng ta đã hoàn thành với API, chúng ta đã thành công với phương thức **GET**. Chúng ta sẽ chỉnh sửa ở phần Log để xem nhiều thông tin hơn.
{{% /notice %}}

8. Mở lại **Stages**
 + Tại **Logs and tracing**, ấn **Edit**
 ![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/008-configcloudwatch.png)
 + Dán **ARN** chúng ta đã ghi lại vào đây
 + Sao chép đoạn code bên dưới dán vào **Log format**
```
{ "requestId":"$context.requestId", "ip":"$context.identity.sourceIp", "userAgent":"$context.identity.userAgent", "requestTime":"$context.requestTime", "method":"$context.httpMethod", "path":"$context.resourcePath", "status":"$context.status", "error":"$context.error.message" }
```
 + Ấn **Save**
![API Gateway](/images/8.configcloudwatch/009-configcloudwatch.png)

9. Mở **Postman** và gửi yêu cầu một lần nữa
10. Mở **CloudWatch** và chọn ***API-Gateway-Execution-Logs_66r5ayu9s7/dev***
 + Chọn **Log streams** mới nhất
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/010-configcloudwatch.png)
 + Bạn có thể nhìn thấy thông tin chi tiết sau khi chúng ta đã cấu hình.
![API Gateway]({{< relref "/" >}}images/8.configcloudwatch/011-configcloudwatch.png)
