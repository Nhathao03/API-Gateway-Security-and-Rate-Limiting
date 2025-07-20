---
title : "Storage with Amplify"
weight : 2
chapter : false
pre : " <b> 3.3.2 </b> "
---

After you have successfully created an account with Cognito User Pool, we will use that account to upload files to S3 bucket with Amplify in this section.

1. Press the combination Ctrl+C in terminal or command line

2. Run the below command at the root of the application you cloned to add storage to the application:

```
amplify add storage

```

 + Select and enter follow the below informations:

    - ? Please select from one of the below mentioned services: Content (Images, audio, video, etc.)
    - Provide a friendly name for your resource that will be used to label this cateogry in the project: `fcjdmsstore`
    - Provide bucket name: `fcjdmsstore`
    - Who should have access: Auth users only
    - What kind of access do you want for Authenticated user? ***Ấn tổ hợp Ctrl + A***
    - Do you want to add a Lambda Trigger for your S3 Bucket? `no`

![Storage with Amplify](/images/3.configcognito/015-configcognito.png)

3. Run the following command to update cloud resources:
```
amplify push

```
![Storage with Amplify](/images/3.configcognito/016-configcognito.png)

4. Navigate to the CloudFormation console to check if the stack has been created.
 + Click on a bucket’s name to open the S3 bucket’s dashboard
![Storage with Amplify](/images/3.configcognito/017-configcognito.png)

5. Run the following command to start the application: `npm start`
 + Click **Upload**
![Storage with Amplify](/images/3.configcognito/018-configcognito.png)

6. Click **Add files** and select the files you want to upload
![Storage with Amplify](/images/3.configcognito/019-configcognito.png)

7. Add tags to files or can be omitted. Then press **Upload**
![Storage with Amplify](/images/3.configcognito/020-configcognito.png)

8. You have successfully uploaded your files
![Storage with Amplify](/images/3.configcognito/021-configcognito.png)

9. Back to the S3 bucket dashboard, check if the files have been uploaded.
![Storage with Amplify](/images/3.configcognito/022-configcognito.png)

You are done with user authentication and file upload to S3 with Amplify. The S3 bucket has created a **protected** folder because our application chooses **Access Level** as protected. To learn more about **Access Level**, go to the next section.