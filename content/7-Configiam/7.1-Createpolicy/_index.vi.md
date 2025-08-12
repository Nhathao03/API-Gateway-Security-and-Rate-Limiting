---
title : "Tạo chính sach mới"
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---

In this section, chúng ta sẽ cấu hình IAM để tăng bảo mật cho API.

#### Tạo chính sách mới
1. Mở bảng điều khiển [AWS IAM](https://console.aws.amazon.com/iam) 
 + Ấn **Policy**, sau đó ấn **Create policy**
![Create new policy](images/7.configiam/001-configiam.png)

2. Tại mục **Specify permissions**:
 + Ấn **JSON**
 + Sao chép chính sách dưới đây vào mục **Policy**
 + Ấn **Next**
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "execute-api:Invoke",
      "Resource": "arn:aws:execute-api:<REGION>:<ACCOUNT_ID>:<API_ID>/*"
    }
  ]
}

```
![Create new policy](images/7.configiam/002-configiam.png)

3. Tại mục **Policy details**:
 + Nhập tên chính sách: `fcjdmswebstore_5801_policy`
 + Ấn **Next**
![Create new policy](images/7.configiam/003-configiam.png)
