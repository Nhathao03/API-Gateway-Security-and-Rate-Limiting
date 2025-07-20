---
title : "Access level"
weight : 4 
chapter : false
pre : " <b> 3.4 </b> "
---

When uploading files to S3 bucket, we have 3 levels of access: public, protected and private:

 + **Public**: Accessible by all users of your app. Files are stored under the public/ path in your S3 bucket.
 + **Protected**: Readable by all users, but writable only by the creating user. Files are stored under protected/{user_identity_id}/ where the user_identity_id corresponds to the unique Amazon Cognito Identity ID for that user.
 + **Private**: Only accessible for the individual user. Files are stored under private/{user_identity_id}/ where the user_identity_id corresponds to the unique Amazon Cognito Identity ID for that user.

In this section we will change the user permission to upload files to S3.

1. Open [Cognito console](https://console.aws.amazon.com/cognito/)

2. Click **Identity pools** on the left menu
![Config cognito](/images/3.configcognito/023-configcognito.png)

3. Select **fcjdms...identitypool...**
![Config cognito](/images/3.configcognito/024-configcognito.png)

4. Click **User access** tab and note down the name of the **Authenticated role**
![Config cognito](/images/3.configcognito/025-configcognito.png)

5. Open [IAM Role]()
 + Select **Roles** on the left menu
 + Enter name of **Authenticated role** and click to searched role
![Config cognito](/images/3.configcognito/026-configcognito.png)

6. Expand policies to view user permissions
![Config cognito](/images/3.configcognito/027-configcognito.png)

7. Select **Protected_policy_...** policy
 - Click **Remove**
![Config cognito](/images/3.configcognito/028-configcognito.png)

We will remove the access level permission **protected** because the application is using that level.

8. Enter policy name and click **Delete**
![Config cognito](/images/3.configcognito/029-configcognito.png)

9. You have successfully removed.
![Config cognito](/images/3.configcognito/030-configcognito.png)

10. Back in the application, click **Add files** and select the file you want to upload. Then click **Upload**
![Config cognito](/images/3.configcognito/031-configcognito.png)

11. Access to **Inspect | Console** mode. We received an error.
![Config cognito](/images/3.configcognito/032-configcognito.png)

12. Re-add permissions for the user.
 + Click **Add permissions**
 + Select **Create inline policy**
![Config cognito](/images/3.configcognito/033-configcognito.png)

13. Select S3 for service
![Config cognito](/images/3.configcognito/034-configcognito.png)

14. In **Actions | Read** section, select **GetObject**
![Config cognito](/images/3.configcognito/035-configcognito.png)

15. In **Actions | Write** section, select **PutObject** and **DeleteObject**
![Config cognito](/images/3.configcognito/036-configcognito.png)

16. In **Resources** secttion, click **Add ARN**
![Config cognito](/images/3.configcognito/037-configcognito.png)

17. Enter ARN: `arn:aws:s3:::YOUR_BUCKET-dev/protected/${cognito-identity.amazonaws.com:sub}/*`
{{% notice info %}}
Replace `YOUR_BUCKET` with the bucket name you created earlier.
{{% /notice %}}
 + Click **Add**
![Config cognito](/images/3.configcognito/038-configcognito.png)

18. Click **Review policy**
![Config cognito](/images/3.configcognito/039-configcognito.png)

19. Enter policy name: `Protected_policy`. Then click **Create policy**
![Config cognito](/images/3.configcognito/040-configcognito.png)

20. Go back to the web app, reload the file you just failed
 + Click **Add files**, select the file you want to download
 + Click **Upload** 
![Config cognito](/images/3.configcognito/042-configcognito.png)

21. Open the console of the S3 bucket to see if the file has loaded successfully.
![Config cognito](/images/3.configcognito/041-configcognito.png)