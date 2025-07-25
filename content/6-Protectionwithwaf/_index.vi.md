---
title : "Bảo vệ với WAF"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

Trong phần này, chúng ta sẽ cấu hình WAF để bảo vệ trang web của mình, chống lại các cuộc tấn công SQL Injection, DDoS,...

1. Mở bảng điều khiển [AWS WAF Console](https://console.aws.amazon.com/wafv2/) 
 + Ấn **Create web ACL**
![Protection wtih WAF](/images/6.protectionwithwaf/001-protectionwithwaf.png)
2. Tại mục **Web ACL details**.
 + Tại **Resource type** , click **Global resources**.
 + Tại **Name** `Protection-fcjdmswebstore-5801`.
 + Tại **Description** `Web ACL for the fcjdmswebstore-5801`.
 + Tại **Associated AWS resources** ấn **Add AWS resources**.
![Protection wtih WAF](/images/6.protectionwithwaf/002-protectionwithwaf.png)

3. Tại **AWS resources**.
 + Ấn **CloudFront Distributions**
 + Ấn **E373NUKDTTVAF8 - d3nkar1nu5y1m0.cloudfront.net** (CloudFront Distributions chúng ta đã tạo)
 + Ấn nút **Add**
![Protection wtih WAF](/images/6.protectionwithwaf/003-protectionwithwaf.png)

4. Ấn nút **Next**
![Protection wtih WAF](/images/6.protectionwithwaf/004-protectionwithwaf.png)

5. Tại mục **Rules**.
 + Ấn **Add rules**.
 + Ấn **Add managed rule groups**
![Protection wtih WAF](/images/6.protectionwithwaf/005-protectionwithwaf.png)

6. Tại trang **Add managed rule groups**, ấn **AWS managed rule groups**.
![Protection wtih WAF](/images/6.protectionwithwaf/006-protectionwithwaf.png)

7. Chọn **Core Rule Set**, **SQL Database** và **Known bad inputs**
![Protection wtih WAF](/images/6.protectionwithwaf/007-protectionwithwaf.png)

8. Cuộn xuống cuối trang, ấn **Add rules**
![Protection wtih WAF](/images/6.protectionwithwaf/008-protectionwithwaf.png)

9. Tại trang **Add managed rule groups**, ấn **Next**.
![Protection wtih WAF](/images/6.protectionwithwaf/009-protectionwithwaf.png)

10. Tại trang **Set rule priority**, ấn **Next**
![Protection wtih WAF](/images/6.protectionwithwaf/010-protectionwithwaf.png)

11. Tại trang **Configure metrics**, ấn **Next**
![Protection wtih WAF](/images/6.protectionwithwaf/011-protectionwithwaf.png)

12. Tại trang **Review and create web ACL**, cuộn xuống cuối trang sau đó ấn **Create web ACL**.
![Protection wtih WAF](/images/6.protectionwithwaf/012-protectionwithwaf.png)

13. Ấn vào **Web ACL created**
![Protection wtih WAF](/images/6.protectionwithwaf/013-protectionwithwaf.png)
 + Ấn tab **Rule**  
 + Ấn **Add rules**, sau đó ấn **Add my own rules and rule groups**
![Protection wtih WAF](/images/6.protectionwithwaf/014-protectionwithwaf.png)

14. Tại **Rule type**, ấn **Rule builder**
 + Nhập tên rule: `BlockSQLiLoginPath`
![Protection wtih WAF](/images/6.protectionwithwaf/015-protectionwithwaf.png)

15. Tại **Statement**
 + Tại **Inspect**, chọn `URI path` 
 + Tại **Match type**, chọn `Exactly matches string`
 + Tại **String to match**, nhập `/signin` (URL ở trang đăng nhập trong website của bạn)
![Protection wtih WAF](/images/6.protectionwithwaf/016-protectionwithwaf.png)

16. Tại **Text transformation**
 + Chọn `URI decode`
 + Ấn **Add text transformation**, sau đó chọn `Lowercase`
 + Ấn **Add text transformation**, sau đó chọn `Compress whitespace`
 + Chọn **Block** tại **Action**
![Protection wtih WAF](/images/6.protectionwithwaf/017-protectionwithwaf.png)

17. Ấn **Add rule**
![Protection wtih WAF](/images/6.protectionwithwaf/018-protectionwithwaf.png)

18. Ấn **Save**
![Protection wtih WAF](/images/6.protectionwithwaf/019-protectionwithwaf.png)

19. Mở trang đăng nhập tại website của bạn
 + Nhập username: `' OR '1'='1`
 + Nhập password: `123`
 + Ấn **Sign in**
![Protection wtih WAF](/images/6.protectionwithwaf/020-protectionwithwaf.png)

 + Nhấp chuột phải, chọn **Inspect**
 + Chọn tab **Network**
 + Kiểm tra **status code** sẽ thấy xuất hiện lỗi `403 Forbidden`
![Protection wtih WAF](/images/6.protectionwithwaf/021-protectionwithwaf.png)

20. Mở bảng điều kiển [AWS WAF Console](https://console.aws.amazon.com/wafv2/) 
 + Ấn tab **Sampled requests**
 + Bạn sẽ nhìn thấy **Metric name** `BlockSQLiLoginPath` đã bị chặn
![Protection wtih WAF](/images/6.protectionwithwaf/023-protectionwithwaf.png)
![Protection wtih WAF](/images/6.protectionwithwaf/022-protectionwithwaf.png)

Finally we have successfully configured WAF for the website, next we will continue to configure CloudWatch