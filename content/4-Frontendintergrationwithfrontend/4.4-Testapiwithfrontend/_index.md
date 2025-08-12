---
title : "Test APIs with Front-end"
weight : 4
chapter : false
pre : " <b> 4.4 </b> "
---

After testing that the APIs work properly with Postman, we will test the APIs that are called with the front-end built from part 2.

1. Open **constant.js** in the root folder of project
 + Change value of **APP_API_URL** with your URL:
 + Save file

![Test API](images/4.frontendintergrationwithapigateway/057-frontendintergrationwithapigateway.png)

2. Run the command lines under here:

```
yarn build
aws s3 cp build s3://BUCKET_NAME --recursive
```
Replace `BUCKET_NAME` with the bucket name you created in part 1.

3. Go back to the web application in part 1. Log in with the account you registered in workshop 2.
 + Click **Upload**
![Test API](images/4.frontendintergrationwithapigateway/058-frontendintergrationwithapigateway.png)

4. Click Add files
 + Select the files you want to upload
 + Can enter tag or ignore
 + Click Upload
![Test API](images/4.frontendintergrationwithapigateway/059-frontendintergrationwithapigateway.png)

5. Return to the DynamoDB dashboard and click the Refresh icon to see the results.
![Test API](images/4.frontendintergrationwithapigateway/060-frontendintergrationwithapigateway.png)

 + Open the console of the S3 bucket, check if the file has been uploaded.
![Test API](images/4.frontendintergrationwithapigateway/061-frontendintergrationwithapigateway.png)

6. Return to the application, and select the My Document tab on the left menu. You will see a list of files that have just been uploaded.
 + Click Choose to switch to delete mode
![Test API](images/4.frontendintergrationwithapigateway/062-frontendintergrationwithapigateway.png)
 + Select the file you want to delete
 + Click **Delete**
![Test API](images/4.frontendintergrationwithapigateway/063-frontendintergrationwithapigateway.png)
 + Click **OK** to confirm deleting
![Test API](images/4.frontendintergrationwithapigateway/064-frontendintergrationwithapigateway.png)
 + File has been deleted
![Test API](images/4.frontendintergrationwithapigateway/065-frontendintergrationwithapigateway.png)
 + Check Documents table
![Test API](images/4.frontendintergrationwithapigateway/066-frontendintergrationwithapigateway.png)
