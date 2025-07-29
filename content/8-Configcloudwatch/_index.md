---
title : "Config CloudWatch to monitor user actions using API"
weight : 8
chapter : false
pre : " <b> 8. </b> "
---

In this section, we will configure cloudwatch to monitor user actions using API.
1. Open [API Gateway](https:console.aws.amazon.com/apigateway)
2. Select **API** created
![API Gateway](/images/8.configcloudwatch/001-configcloudwatch.png)

3. Select **Stage**
 + In the **Logs and tracing**, click **Edit**
![API Gateway](/images/8.configcloudwatch/002-configcloudwatch.png)

4. In the **Edit logs and tracing**
 + Choose **Errors and info logs**
 + Click **Save**
![API Gateway](/images/8.configcloudwatch/003-configcloudwatch.png)

5. Open **Postman** and send any request
![Postman](/images/8.configcloudwatch/004-configcloudwatch.png)

6. Open [CloudWatch](https:console.aws.amazon.com/cloudwatch)
 + Click **Log groups**
 + Select ***API-Gateway-Execution-Logs_66r5ayu9s7/dev***
![API Gateway](/images/8.configcloudwatch/005-configcloudwatch.png)
 + Select **Log streams**
 + Copy the **ARN**, we will use it in the next part.
![API Gateway](/images/8.configcloudwatch/006-configcloudwatch.png)

7. Successful results
![API Gateway](/images/8.configcloudwatch/007-configcloudwatch.png)

{{% notice info %}}
Here you will see all the actions we have done with the API, we have done the GET method. But we will edit a part in the Log and follow to see more information.
{{% /notice %}}

8. Reopen the **Stages**
 + In the **Logs and tracing**, click **Edit**
 ![API Gateway](/images/8.configcloudwatch/008-configcloudwatch.png)
 + Paste the **ARN** we recorded here
 + Copy the below code block to **Log format**
```
{ "requestId":"$context.requestId", "ip":"$context.identity.sourceIp", "userAgent":"$context.identity.userAgent", "requestTime":"$context.requestTime", "method":"$context.httpMethod", "path":"$context.resourcePath", "status":"$context.status", "error":"$context.error.message" }
```
 + Click **Save**
![API Gateway](/images/8.configcloudwatch/009-configcloudwatch.png)

9. Open **Postman** and send request again
10. Open **CloudWatch** and go to ***API-Gateway-Execution-Logs_66r5ayu9s7/dev***
 + Select newest **Log streams**
![API Gateway](/images/8.configcloudwatch/010-configcloudwatch.png)
 + You can see more details after we have configured
![API Gateway](/images/8.configcloudwatch/011-configcloudwatch.png)
