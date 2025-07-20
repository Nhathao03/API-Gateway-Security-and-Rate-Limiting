---
title : "Application với Amplify"
weight : 1
chapter : false
pre : " <b> 3.3.1 </b> "
---

1. Chạy câu lệnh dưới đây tại thư mục gốc của ứng dụng mà bạn clone về để thêm authentication cho ứng dụng:

```
amplify add auth

```

+ Chọn theo các thông tin dưới đây:

    - Do you want to use the default authentication and security configuration? ***Default configuration***
    - Warning: you will not be able to edit these selections.
    - How do you want users to be able to sign in? ***Username***
    - Do you want to configure advanced settings? ***No, I am done.***

![Authentication with Amplify](/images/3.configcognito/004-configcognito.png)

2. Chạy câu lệnh sau để cập nhật tài nguyên trên cloud:
```
amplify push

```
![Authentication with Amplify](/images/3.configcognito/005-configcognito.png)

3. Mở lại bảng điều khiển của CloudFormation để kiểm tra xem stack đã được tạo hay chưa.
 + Ấn **id** của UserPool để mở bảng điều khiển của **Cognito User Pool**

![Authentication with Amplify](/images/3.configcognito/006-configcognito.png)

4. Chạy câu lệnh sau để bắt đầu với ứng dụng: `npm start`
 + Ấn **Sign up** để đăng ký tài khoản mới.
![Authentication with Amplify](/images/3.configcognito/007-configcognito.png)

5. Nhập thông tin người dùng:
 + Tên người dùng, ví dụ: `admin`
 + Nhập email của bạn.
 + Mật khẩu, ví dụ: `Admin123`
 + Ấn **Sign up**

![Authentication with Amplify](/images/3.configcognito/008-configcognito.png)

6. Mở lại bảng điều khiển của Cognito User Pool, chọn tab **User** bạn sẽ thấy một người dùng đã được đăng ký nhưng chưa xác nhận
![Authentication with Amplify](/images/3.configcognito/009-configcognito.png)

7. Mở mail của bạn để lấy mã xác thực đã được gửi tự động.
![Authentication with Amplify](/images/3.configcognito/010-configcognito.png)

8. Nhập mã xác nhập vào ứng dụng rồi ấn **Submit**
![Authentication with Amplify](/images/3.configcognito/011-configcognito.png)

9. Mở lại bảng điều khiển của Cognito User Pool, ấn biểu tượng **Refresh** bạn sẽ thấy ngừoi dùng đã được xác thực
![Authentication with Amplify](/images/3.configcognito/012-configcognito.png)

10. Đăng nhập vào ứng dụng với tài khoản bạn vừa đăng ký.
![Authentication with Amplify](/images/3.configcognito/013-configcognito.png)

11. Bạn đã đăng nhập thành công.
![Authentication with Amplify](/images/3.configcognito/014-configcognito.png)