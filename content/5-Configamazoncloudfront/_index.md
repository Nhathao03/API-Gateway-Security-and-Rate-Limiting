---
title : "Config Amazon CloudFront"
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

Using the AWS Management Console, we will create a CloudFront distribution, and configure it to serve the S3 bucket we previously created.
1. Open the Amazon CloudFront console at [Amazon CloudFront](https://console.aws.amazon.com/cloudfront/) 
2. From the console dashboard, click **Create distribution**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/001-configamazoncloudfront.png)

3. Specify the following settings for the distribution:
 + In the **Origin domain** field Select the S3 bucket you created previously.
 + In the **Origin access**, choose **Legacy access identities**
 + In the **Bucket policy**, choose **Yes, update the bucket policy**
 + Choose **Create new OAI**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/002-configamazoncloudfront.png)
 + Choose **Create**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/003-configamazoncloudfront.png)
 + Another field, let it default
4. In the **Settings**
 + Choose **Use North America, Europe, Asia, Middle East, and Africa** because, Vietnam in **Asia**
 + In the **Default root object - optional**, input file already upload on S3 (Fx: index.html)
 + Scroll down last page, choose **Create distribution**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/004-configamazoncloudfront.png)
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/005-configamazoncloudfront.png)

 + To return to the main CloudFront page click Distributions from the left navigation menu.

5. After CloudFront creates your distribution which may take approximately a few minutes
 + Column Status & Column Last modified has infomation like below.
 + Lick on **ID** to get **Distribution domain name**
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/006-configamazoncloudfront.png)

6. When your distribution is deployed, confirm that you can access your content using your new CloudFront **Distribution domain name** which you can see in the console. Copy the Domain Name into a web browser to test.
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/007-configamazoncloudfront.png)

Result like below
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/008-configamazoncloudfront.png)

7. Check the period of time for brower loading index.html by **Distribution domain name** of CloudFront
 + Lick rightmost button , choose **Inspect**
 + On the right, choose » and choose **Network**
 + Lick the icon reload page

![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/009-configamazoncloudfront.png)

 + Imagine: your static web is hosted in Region US & has end user in Asian, the time to return results after 1 mouse click can be up to a few seconds or tens of seconds, that - will affect the user experience! But with CloudFront speed will always be optimal.
8. Check the location of CloudFront Pop
 + lick one time in **domain name** central page
 + Check POP - Cloudfront, i request from Ho Chi Minh - so POP is: SGN50-P1 (with SGN is Saigon)
example
![CloudFront]({{< relref "/" >}}images/5.configamazoncloudfront/010-configamazoncloudfront.png)

9. You now have content in a private S3 bucket, that only CloudFront has secure access to. CloudFront then serves the requests, effectively becoming a secure, reliable static hosting service with additional features available such as custom certificates and alternate domain names .
