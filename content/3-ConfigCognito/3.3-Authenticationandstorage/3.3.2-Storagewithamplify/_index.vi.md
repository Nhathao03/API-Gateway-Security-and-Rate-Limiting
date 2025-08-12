---
title : "Storage với Amplify"
weight : 2
chapter : false
pre : " <b> 3.3.2 </b> "
---

Sau khi bạn đã tạo tài khoản với Cognito User Pool thành công, chúng ta sẽ dùng tài khoản đó để upload file lên S3 bucket với Amplify trong phần này.

1. Ấn tổ hợp **Ctrl+C** trong terminal hoặc command line

2. Chạy câu lệnh dưới đây tại thư mục gốc của ứng dụng mà bạn clone về để thêm storage cho ứng dụng:
```
amplify add storage

```

 + Chọn và nhập theo các thông tin dưới đây:

    - ? Please select from one of the below mentioned services: Content (Images, audio, video, etc.)
    - Provide a friendly name for your resource that will be used to label this cateogry in the project: `fcjdmsstore`
    - Provide bucket name: `fcjdmsstore`
    - Who should have access: Auth users only
    - What kind of access do you want for Authenticated user? ***Ấn tổ hợp Ctrl + A***
    - Do you want to add a Lambda Trigger for your S3 Bucket? `no`

![Storage with Amplify](images/3.configcognito/015-configcognito.png)

3. Chạy câu lệnh sau để cập nhật tài nguyên trên cloud:
```
amplify push

```
![Storage with Amplify](images/3.configcognito/016-configcognito.png)

4. Mở lại bảng điều khiển của CloudFormation để kiểm tra xem stack đã được tạo hay chưa.
 + Ấn vào tên của bucket để mở bảng điều khiển của bucket đó
![Storage with Amplify](images/3.configcognito/017-configcognito.png)

5. Chạy câu lệnh sau để bắt đầu với ứng dụng: `npm start`
 + Ấn  **Upload**
![Storage with Amplify](images/3.configcognito/018-configcognito.png)

6. Ấn  **Add files** và chọn những tệp bạn muốn tải lên
![Storage with Amplify](images/3.configcognito/019-configcognito.png)

7. Thêm tag cho các tệp hoặc có thể bỏ qua. Sau đó ấn **Upload**
![Storage with Amplify](images/3.configcognito/020-configcognito.png)

8. Bạn đã tải lên thành công các tệp của mình
![Storage with Amplify](images/3.configcognito/021-configcognito.png)

9. Quay lại với bảng điều khiển của S3 bucket, kiểm tra xem các file đã được tải lên hay chưa.
![Storage with Amplify](images/3.configcognito/022-configcognito.png)

Vậy là bạn đã hoàn thành việc xác thực người dùng và tải tệp lên S3 với Amplify. Trong S3 bucket đã được tạo thư mục **protected** bởi vì ứng dụng của chúng ta chọn **Access Level** là **protected**. Để tìm hiểu thêm về **Access Level**, bạn hãy chuyển sang phần tiếp theo.