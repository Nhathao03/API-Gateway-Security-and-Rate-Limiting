---
title : "Tạo IAM User"
weight : 2
chapter : false
pre : " <b> 7.2 </b> "
---

#### Tạo IAM User
1. Ấn **Users**, sau đó ấn **Create user**
![Create IAM User]({{< relref "/" >}}images/7.configiam/004-configiam.png)
2. Tại mục **User details**:
 + Nhập username: `Admin_fcjdmswebstore_5801`
 + Ấn **I want to create an IAM user**
 + Ấn **Custom password**, sau đó nhập password 
 + Ấn **Next**
![Create IAM User]({{< relref "/" >}}images/7.configiam/005-configiam.png)

3. Tại mục **Set permisstions**:
 + Ấn **Attach policies directly**
 + Tìm kiếm `fcj`, sau đó chọn **fcjdmswebstore_5801_policy**
 + Ấn **Next**
![Create IAM User]({{< relref "/" >}}images/7.configiam/006-configiam.png)
4. Ấn **Create user**
![Create IAM User]({{< relref "/" >}}images/7.configiam/007-configiam.png)
5. Chọn **User** mà bạn đã tạo
![Create IAM User]({{< relref "/" >}}images/7.configiam/008-configiam.png)
6. Ấn **Create access key**
![Create IAM User]({{< relref "/" >}}images/7.configiam/009-configiam.png)

7. Tại mục **Access key best practices & alternatives**:
 + Ấn **Command Line Interface(CLI)**
 + Ấn **I understand above recommendation and want to proceed to create an access key**
![Create IAM User]({{< relref "/" >}}images/7.configiam/010-configiam.png)

8. Ấn **Create access key**
![Create IAM User]({{< relref "/" >}}images/7.configiam/011-configiam.png)

9. Tại mục **Retrieve access keys** 
 + Ấn **Download .csv file**, sau đó ấn **Done**
![Create IAM User]({{< relref "/" >}}images/7.configiam/012-configiam.png)



 