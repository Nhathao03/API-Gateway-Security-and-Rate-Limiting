---
title : "Cấp độ truy cập"
weight : 4
chapter : false
pre : " <b> 3.4 </b> "
---

Khi tải tệp lên S3 bucket, chúng ta có 3 cấp độ truy cập là public, protected và private:

 + **Public**: Tất cả người dùng ứng dụng của bạn có thể truy cập. Các tệp được lưu trữ dưới đường dẫn chung/trong bộ chứa S3 của bạn.
 + **Protected**: Tất cả người dùng có thể đọc nhưng chỉ người dùng tạo mới có thể ghi. Các tệp được lưu trữ trong protected/{user_identity_id}/ trong đó user_identity_id tương ứng với ID nhận dạng Amazon Cognito duy nhất cho người dùng đó.
 + **Private**: Chỉ có thể truy cập cho người dùng cá nhân. Các tệp được lưu trữ trong private/{user_identity_id}/ trong đó user_identity_id tương ứng với ID nhận dạng Amazon Cognito duy nhất cho người dùng đó.

Trong phần này chúng ta sẽ thay đổi quyền của người dùng để tải tệp lên S3.

1. Truy cập vào bảng điều khiển của [Cognito console](https://console.aws.amazon.com/cognito/)

2. Ấm **Identity pools** ở menu bên trái
![Config cognito](images/3.configcognito/023-configcognito.png)

3. Chọn **fcjdms...identitypool...**
![Config cognito](images/3.configcognito/024-configcognito.png)

4. Ấn tab **User access**  và ghi lại tên của **Authenticated role**
![Config cognito](images/3.configcognito/025-configcognito.png)

5. Mở bảng điều khiển của [IAM Role]()
 + Chọn **Roles** ở menu bên trái
 + Nhập tên của **Authenticated role** và ấn vào role tìm thấy
![Config cognito](images/3.configcognito/026-configcognito.png)

6. Mở rộng chính sách để xem quyền của user
![Config cognito](images/3.configcognito/027-configcognito.png)

7. Chọn chính sách **Protected_policy_...**
 - Ấn **Remove**
![Config cognito](images/3.configcognito/028-configcognito.png)

Chúng ta sẽ xóa quyền ở mức độ truy cập là **protected** bởi vì ứng dụng đang sử dụng cấp độ đó.

8. Nhập tên chính sách và ấn **Delete**
![Config cognito](images/3.configcognito/029-configcognito.png)

9. Bạn đã xóa thành công
![Config cognito](images/3.configcognito/030-configcognito.png)

10. Trở về ứng dụng và chọn **Add files**, tiếp tục chọn tệp mà bạn muốn tải lên. Sau đó ấn **Upload**
![Config cognito](images/3.configcognito/031-configcognito.png)

11. Truy cập vào bảng điều khiển **Inspect | Console**. Chúng ta đã nhận được một lỗi.
![Config cognito](images/3.configcognito/032-configcognito.png)

12. Thêm lại quyền cho người dùng.
 + Ấm **Add permissions**
 + Chọn **Create inline policy**
![Config cognito](images/3.configcognito/033-configcognito.png)

13. Chọn service là **S3**
![Config cognito](images/3.configcognito/034-configcognito.png)

14. Tại mục **Actions | Read**, chọn **GetObject**
![Config cognito](images/3.configcognito/035-configcognito.png)

15. Tại mục **Actions | Write**, chọn **PutObject** và **DeleteObject**
![Config cognito](images/3.configcognito/036-configcognito.png)

16. Tại mục **Resources**, chọn **Add ARN**
![Config cognito](images/3.configcognito/037-configcognito.png)

17. Nhập ARN: `arn:aws:s3:::YOUR_BUCKET-dev/protected/${cognito-identity.amazonaws.com:sub}/*`
 {{% notice info %}}
Thay thế `YOUR_BUCKET` bằng tên bucket mà bạn đã tạo trước đó.
{{% /notice %}}
 + Ấn **Add**
![Config cognito](images/3.configcognito/038-configcognito.png)

18. Ấn **Review policy**
![Config cognito](images/3.configcognito/039-configcognito.png)

19. Nhập tên chính sách: `Protected_policy`. Sau đó ấn **Create policy**
![Config cognito](images/3.configcognito/040-configcognito.png)

20. Trở về ứng dụng, tải lại tệp mà bạn vừa thất bại
 + Ấn **Add files**, chọn tệp mà bạn muốn tải lên
 + Ấn **Upload** 
![Config cognito](images/3.configcognito/042-configcognito.png)

21. Mở bảng điều khiển của S3 bucket xem tệp đã tải thành công hay chưa.
![Config cognito](images/3.configcognito/041-configcognito.png)