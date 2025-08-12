---
title : "Deloy Front-end"
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

In the first step in this serious, we will host the web application with S3 Static website hosting

1. Open [Amazon S3 Console](https://console.aws.amazon.com/s3)
2. Click **Create Bucket**
![S3](images/4.frontendintergrationwithapigateway/001-frontendintergrationwithapigateway.png)

3. Enter bucket name, such as `fcjdmswebstore-5801`
![S3](images/4.frontendintergrationwithapigateway/002-frontendintergrationwithapigateway.png)

4. Uncheck block from allowing public access
 + Check to **I acknowledge that the current settings might result in this bucket and the objects within becoming public**
 ![S3](images/4.frontendintergrationwithapigateway/003-frontendintergrationwithapigateway.png)

5. Click **Create bucket** button
![S3](images/4.frontendintergrationwithapigateway/004-frontendintergrationwithapigateway.png)

6. Click on created bucket
![S3](images/4.frontendintergrationwithapigateway/005-frontendintergrationwithapigateway.png)

7. Click **Properties** tab
![S3](images/4.frontendintergrationwithapigateway/006-frontendintergrationwithapigateway.png)

8. Scroll down to the bottom, click **edit** in **Static web hosting** pattern
![S3](images/4.frontendintergrationwithapigateway/007-frontendintergrationwithapigateway.png)

9. Select **Enable** to enable host web static on S3
 + Select **Host a static website** for **Hosting type**
 + Enter `index.html` for **Index document** pattern

![S3](images/4.frontendintergrationwithapigateway/008-frontendintergrationwithapigateway.png)

10. Click **Save changes**
![S3](images/4.frontendintergrationwithapigateway/009-frontendintergrationwithapigateway.png)
 + After successfully enabling, please write down the path of the web
![S3](images/4.frontendintergrationwithapigateway/010-frontendintergrationwithapigateway.png)

11. After successful enable, please take note of the path of the web:
 + Select **Permissions** tab
 + Click **Edit** of **Bucket policy** pattern
![S3](images/4.frontendintergrationwithapigateway/011-frontendintergrationwithapigateway.png)

12. Copy the below code block to **Policy**

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::BUCKET_NAME/*"
        }
    ]
}

```

 + Replace `BUCKET_NAME` with the bucket name you created, then click **Save changes**
![S3](images/4.frontendintergrationwithapigateway/012-frontendintergrationwithapigateway.png)

13. Open the **src/component/Home/Upload.js** file in the application’s source code directory and uncomment the code that calls the API to write data to DynamoDB.
![S3](images/4.frontendintergrationwithapigateway/013-frontendintergrationwithapigateway.png)

14. Next run the following command at the root of the project you downloaded. (FCJ-Serverless-DMS)
```
yarn build
aws s3 cp build s3://BUCKET_NAME --recursive

```
 + Replace `BUCKET_NAME` with the bucket name you created

Result after uploading:
![S3](images/4.frontendintergrationwithapigateway/014-frontendintergrationwithapigateway.png)

15. Paste the web link you take notes into your web browser
![S3](images/4.frontendintergrationwithapigateway/015-frontendintergrationwithapigateway.png)

You have finished hosting your website on S3. In the next section, we update the lambda functions