---
title : "Protection with WAF"
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

In this section, we will configure WAF to protect our website, protect against SQL Injection attacks, DDoS,...

1. Go [AWS WAF Console](https://console.aws.amazon.com/wafv2/) 
 + Click **Create web ACL**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/001-protectionwithwaf.png)
2. In the **Web ACL details** section.
 + In the **Resource type** section, click **Global resources**.
 + In the **Name** section type `Protection-fcjdmswebstore-5801`.
 + In the **Description** section type `Web ACL for the fcjdmswebstore-5801`.
 + In the **Associated AWS resources** section, Click **Add AWS resources**.
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/002-protectionwithwaf.png)

3. In the **AWS resources**.
 + Click **CloudFront Distributions**
 + Click **E373NUKDTTVAF8 - d3nkar1nu5y1m0.cloudfront.net** (CloudFront Distributions we created)
 + Click **Add**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/003-protectionwithwaf.png)

4. Click **Next**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/004-protectionwithwaf.png)

5. In the **Rules** section.
 + Click **Add rules**.
 + Click **Add managed rule groups**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/005-protectionwithwaf.png)

6. In the **Add managed rule groups** page, Click **AWS managed rule groups**.
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/006-protectionwithwaf.png)

7. Select **Core Rule Set**, **SQL Database** and **Known bad inputs**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/007-protectionwithwaf.png)

8. Drag the screen down, Click **Add rules**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/008-protectionwithwaf.png)

9. In the **Add managed rule groups** page, click **Next**.
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/009-protectionwithwaf.png)

10. In the **Set rule priority** page, click **Next**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/010-protectionwithwaf.png)

11. In the **Configure metrics** page, click **Next**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/011-protectionwithwaf.png)

12. In the **Review and create web ACL** page, Drag the screen down, click **Create web ACL**.
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/012-protectionwithwaf.png)

13. Click **Web ACL created**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/013-protectionwithwaf.png)
 + Click **Rule** tab 
 + Click **Add rules**, then click **Add my own rules and rule groups**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/014-protectionwithwaf.png)

14. In **Rule type** section, click **Rule builder**
 + Enter rule name `BlockSQLiLoginPath`
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/015-protectionwithwaf.png)

15. In the **Statement**
 + In **Inspect**, choose `URI path` 
 + In **Match type**, choose `Exactly matches string`
 + In **String to match**, enter `/signin` (Your URL login in your website)
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/016-protectionwithwaf.png)

16. In **Text transformation**
 + Choose `URI decode`
 + Click **Add text transformation**, then choose `Lowercase`
 + Click **Add text transformation**, then choose `Compress whitespace`
 + Choose **Block** in **Action**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/017-protectionwithwaf.png)

17. Click **Add rule**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/018-protectionwithwaf.png)

18. Click **Save**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/019-protectionwithwaf.png)

19. Open page Login in your website
 + Enter username: `' OR '1'='1`
 + Enter password: `123`
 + Click **Sign in**
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/020-protectionwithwaf.png)

 + Lick rightmost button , choose **Inspect**
 + On the right, choose » and choose **Network**
 + Check **status code** appear error `403 Forbidden`
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/021-protectionwithwaf.png)

20. Open [AWS WAF Console](https://console.aws.amazon.com/wafv2/) 
 + Click **Sampled requests**
 + You will see **Metric name** `BlockSQLiLoginPath` blocked
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/023-protectionwithwaf.png)
![Protection wtih WAF]({{< relref "/" >}}images/6.protectionwithwaf/022-protectionwithwaf.png)

Finally we have successfully configured WAF for the website, next we will continue to configure CloudWatch