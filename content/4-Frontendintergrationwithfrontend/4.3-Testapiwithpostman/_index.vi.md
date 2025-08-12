---
title : "Kiểm tra API bằng Postman"
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

Trong bước này, chúng ta sẽ kiểm tra hoạt động của các API bằng công cụ [Postman](https://www.postman.com/downloads/)

#### Kiểm tra API liệt kê
1. Tạo collection mới, sau đó ấn **Bank collection**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/046-frontendintergrationwithapigateway.png)

2. Nhập tên cho collection, ví dụ như: `fcjdmswebstore-5801`
 + Ấn **Add request**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/047-frontendintergrationwithapigateway.png)
 + Chọn method **GET** với `abcd1234`
 + Ấn **Send**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/048-frontendintergrationwithapigateway.png) 

3. Kết quả thành công
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/049-frontendintergrationwithapigateway.png)

#### Kiểm tra API thêm mới
1. Tương tự thêm request mới
 + Chọn method **POST**
 + Nhập URL của API ghi đã ghi lại từ bước trước
 + Trong mục **Body**, chọn **raw**
 + Sao chép đoạn dưới đây:

```
{
      "user_id": "abcd1234",
      "file": "flowers.png",
      "folder": "",
      "identityId": "123456cvbn",
      "modified": "21-03-2023",
      "size": "32KB",
      "type": "png",
      "tag": "image"
}
```

 + Ấn **Send**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/051-frontendintergrationwithapigateway.png)

2. Mở bảng điều khiển **DynamoDB**, chọn **Documents** và chọn **Explore items** để kiểm tra kết quả:
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/052-frontendintergrationwithapigateway.png)

#### Kiểm tra API xóa
1. Tương tự thêm request mới
 + Chọn method **DELETE** 
 + Nhập URL của API ghi đã ghi lại từ bước trước, thay thế **{id}** với `abcd1234`
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/053-frontendintergrationwithapigateway.png)
 + Tại mục **Params**, nhập `file` cho key và `flowers.png` cho value
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/054-frontendintergrationwithapigateway.png)

2. Kết quả thành công
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/055-frontendintergrationwithapigateway.png)

3. Quay lại bảng **Documents**, ấn nút **Refresh** để xem kết quả
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/056-frontendintergrationwithapigateway.png)

