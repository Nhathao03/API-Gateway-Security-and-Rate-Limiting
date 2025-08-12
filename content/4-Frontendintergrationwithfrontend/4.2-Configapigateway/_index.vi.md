---
title : "Cấu hình API Gateway"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### Cập nhật Lambda function

1. Mở bảng điều khiển [AWS Lambda Console](https://console.aws.amazon.com/lambda)
2. Chọn hàm **upload_documents**
3. Comment dòng 13 và mở comment dòng 12
4. Ấn **Deloy**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/016-frontendintergrationwithapigateway.png)


#### Cấu hình API Gateway
1. Mở bảng điều khiển [Amazon API Gateway Console]()
2. Ấn **Create API**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/017-frontendintergrationwithapigateway.png)

3. Kéo xuống mục **REST API**, ấn **Build**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/018-frontendintergrationwithapigateway.png)

4. Để mặc định **REST** protocol.
 + Chọn **New API**
 + Nhập tên API, ví dụ: `fcj-dms-api-5801`
 + Chọn kiểu Endpoint là **Regional**
 + Ấn **Create API**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/019-frontendintergrationwithapigateway.png)

5. Chọn **API Gateway** đã tạo
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/019-frontendintergrationwithapigateway.png)

6. Chọn **Create Resource** để tạo resource cho API.
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/021-frontendintergrationwithapigateway.png)

7. Nhập tên cho resource: `docs`, sau đó ấn **Create Resource**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/022-frontendintergrationwithapigateway.png)

8. Chọn resource **docs**, sau đó ấn **Create Method**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/023-frontendintergrationwithapigateway.png)

9. Thiết lập method như sau:
 + Giữ mặc định kiểu tích hợp là **Lambda Function**
 + Tích vào **Lambda Proxy integration**
 + Chọn cùng của **Lambda function** mà bạn đã tạo
 + Chọn hàm **upload_document** 
 + Cuối cùng ấn **Save**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/024-frontendintergrationwithapigateway.png)
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/025-frontendintergrationwithapigateway.png)

10. Sau đó tạo method **POST**, ấn **Create Resource** để tạo resource.
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/026-frontendintergrationwithapigateway.png)

11. Nhập tên resource **{id}**, sau đó ấn **Create Resource**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/027-frontendintergrationwithapigateway.png)

12. Chọn resource **{id}**, sau đó ấn **Create Method**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/028-frontendintergrationwithapigateway.png)

13. Thiết lập method như sau:
 + Giữ mặc định kiểu tích hợp là **Lambda Function**
 + Tích vào **Lambda Proxy integration**
 + Chọn cùng của **Lambda function** mà bạn đã tạo
 + Chọn hàm **list_documents** 
 + Cuối cùng ấn **Save**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/029-frontendintergrationwithapigateway.png)
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/030-frontendintergrationwithapigateway.png)

14. Click **Create Method** to create a new method
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/031-frontendintergrationwithapigateway.png)

15. Thiết lập method như sau:
 + Giữ mặc định kiểu tích hợp là **Lambda Function**
 + Tích vào **Lambda Proxy integration**
 + Chọn cùng của **Lambda function** mà bạn đã tạo
 + Chọn hàm **delete_document** 
 + Cuối cùng ấn **Save**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/032-frontendintergrationwithapigateway.png)
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/033-frontendintergrationwithapigateway.png)

16. Chọn method **DELETE**, sau đó ấn **Edit** tại mục **Method request settings**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/034-frontendintergrationwithapigateway.png)

17. Mở rộng mục **URL Query String Parameters**, ấn **Add query string** để thêm một parameter mới
 + Nhập tên parameter: `file`. Parameter này lưu giá trị tên của file mà bạn muốn xoá.
 + Ấn **Save**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/035-frontendintergrationwithapigateway.png)

18. Chọn resource **docs**, sau đó ấn **Enable CORS**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/036-frontendintergrationwithapigateway.png)

19. Tích vào **POST**, sau đó ấn **Save**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/037-frontendintergrationwithapigateway.png)

20. Chọn resource **{id}**, sau đó ấn **Enable CORS**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/038-frontendintergrationwithapigateway.png)

21.Tích vào **GET** và **DELETE**, sau đó ấn **Save**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/039-frontendintergrationwithapigateway.png)

22. Sau khi hoàn thành thiết lập, chúng ta deploy API. Chọn **/docs**, sau đó ấn **Deploy API**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/040-frontendintergrationwithapigateway.png)

23. Chọn **[New Stage]**
 + Nhập tên stage: `dev`
 + Ấn **Deploy**
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/041-frontendintergrationwithapigateway.png)

24. Ghi lại URL của **API** dùng cho phần tiếp theo.
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/042-frontendintergrationwithapigateway.png)

25. Mở rộng stage, chọn method **POST** và ghi lại URL.
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/043-frontendintergrationwithapigateway.png)

26. Chọn method **DELETE** và ghi lại URL.
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/044-frontendintergrationwithapigateway.png)

27. Chọn method **GET** và ghi lại URL.
![Lambda]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/045-frontendintergrationwithapigateway.png)

Bạn đã hoàn thành việc thiết lập API. Tiếp theo chúng ta sẽ kiểm tra hoạt động của API và tích hợp nó vào ứng dụng của mình.



