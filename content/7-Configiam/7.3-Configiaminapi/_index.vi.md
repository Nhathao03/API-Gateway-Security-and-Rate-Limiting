---
title : "Cấu hình IAM trong API"
weight : 3
chapter : false
pre : " <b> 7.3 </b> "
---

#### Cấu hình IAM trong API
1. Mở bảng điều khiển [API Gateway](https://console.aws.amazon.com/apigateway) 
 + Chọn **API** đã tạo
![API Gateway](/images/7.configiam/013-configiam.png)

2. Ấn **Resources**
 + Chọn method **GET**, sau đó ấn **Edit**
![API Gateway](/images/7.configiam/014-configiam.png)

3. Tại mục **Edit method request**:
 + Tại **Authorization**, chọn `AWS_IAM`
 + Ấn **Save**
![API Gateway](/images/7.configiam/015-configiam.png)

{{% notice info %}}
Tương tự, thực hiện với phương thức POST và DELETE.
{{% /notice %}}

4. Ấn **/docs**, sau đó ấn **Deloy API**
![API Gateway](/images/7.configiam/016-configiam.png)

5. Tại **Deloy API**
 + Chọn **New stage**
 + Nhập tên stage: `dev`
 + Ấn **Deloy**
![API Gateway](/images/7.configiam/017-configiam.png)