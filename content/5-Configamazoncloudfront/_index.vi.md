---
title : "Cấu hình Amazon CloudFront"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

Sử dụng Bảng điều khiển quản lý AWS, để tạo CloudFront distribution và cấu hình nó để phục vụ s3 Bucket mà chúng ta đã tạo trước đó.

1. Mở bảng điều khiển [Amazon CloudFront](https://console.aws.amazon.com/cloudfront/) 
2. Từ bảng điều khiển, nhấn vào**Create distribution**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/001-configamazoncloudfront.png)

3. Chỉ định các cài đặt sau đây cho bản distribution:
 + Trong trường **Origin domain**, chọn S3 bucket mà bạn đã tạo trước đó.
 + Trong trường **Origin access**, chọn **Legacy access identities**
 + Trong trường **Bucket policy**, chọn **Yes, update the bucket policy**
 + Chọn **Create new OAI**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/002-configamazoncloudfront.png)
 + Chọn **Create**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/003-configamazoncloudfront.png)
 + Các phần còn lại, để mặc định.
4. Trong phần **Settings**
 + Chọn **Use North America, Europe, Asia, Middle East, and Africa** vì Việt Nam trong khu vực **Asia**
 + Trọng mục **Default root object - optional**, điền tên file đã upload lên S3 - vào ô trống (VD: index.html)
 + Cuộn xuống cuối trang, chọn **Create distribution**

![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/004-configamazoncloudfront.png)
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/005-configamazoncloudfront.png)

 + Để quay lại trang CloudFront chọn **Distributions** từ menu điều hướng bên trái.

5. Sau khi CloudFront tạo bản phân phối của bạn, có thể mất khoảng vài phút.
 + Cột Status & cột Last modified sẽ có thông tin như bên dưới hình.
 + Nhấp vào **ID** để lấy **Distribution domain name**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/006-configamazoncloudfront.png)

6. Khi bản phân phối của bạn được triển khai, hãy kiểm tra nội dung tĩnh (index.html) của mình bằng CloudFront **Distribution domain name** mà bạn có thể thấy trong console. Sao chép **domain name** vào browser để kiểm tra.
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/007-configamazoncloudfront.png)

Kết quả được như hình bên dưới
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/008-configamazoncloudfront.png)

7. Kiểm tra thời gian browser tải index.html bằng **Distribution domain name** của CloudFront
 + Nhấp chuột phải, chọn **Inspect**
 + Bên phải trang, chọn **Network**
 + Nhấn ký hiệu tải lại trang

![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/009-configamazoncloudfront.png)

 + Hãy thử tưởng tưởng: web tĩnh của bạn được host tại các Region US & có end user tại khu vực Asian, thì thời gian trả về kết quả sau 1 cú lích chuột có thể lên tới vài giây hoặc chục giây, điều đó - sẽ làm ảnh hưởng đến trãi nghiệm người dùng! Nhưng với CloudFront tốc độ sẽ luôn được tối ưu.
8. Kiểm tra địa điểm của CloudFront Pop 
 + Nhấp 1 lần vào **domain name** ở giữa trang
 + Kiểm tra POP của Cloudfront, vì mình đang truy cập ở Hồ Chi Minh - nên POP là: SGN50-P1 (với SGN là Saigon)
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/010-configamazoncloudfront.png)

9. Giờ đây, bạn có nội dung trong S3 bucket private mà chỉ CloudFront mới có quyền truy cập an toàn. Sau đó, CloudFront phục vụ các yêu cầu, trở thành một dịch vụ lưu trữ tĩnh an toàn, đáng tin cậy một cách hiệu quả với các tính năng như custom certificates và alternate domain names .


