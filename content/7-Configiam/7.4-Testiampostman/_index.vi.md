---
title : "Kiểm tra IAM với Postman"
weight : 4
chapter : false
pre : " <b> 7.4 </b> "
---

#### Kiểm tra API với Postman
1. Mở **Postman**
2. Chọn method **GET** đã tạo
 + Thay thế **{id}** với `abcd1234`
![API Gateway]({{< relref "/" >}}images/7.configiam/018-configiam.png)
3. Chọn tab **Authorization** 
 + Tại **auth type**, chọn **AWS Signature**
 + Nhập **Accesskey** và **Secretkey**
 + Nhập **AWS Region**, ví dụ như: `ap-southeast-1`
 + Nhập **Service name**: `execute-api`
 + Ấn **Send**
![API Gateway]({{< relref "/" >}}images/7.configiam/019-configiam.png)

4. Kết quả thành công
![API Gateway]({{< relref "/" >}}images/7.configiam/020-configiam.png)
{{% notice info %}}
Tương tự, thực hiện với phương thức POST và DELETE.
{{% /notice %}}

5. Nếu **Authorization** chưa được cấu hình thì kết quả sẽ được hiển thị thông báo.
```
{
  "message": "Missing Authentication Token"
}
```

![API Gateway]({{< relref "/" >}}images/7.configiam/021-configiam.png)
