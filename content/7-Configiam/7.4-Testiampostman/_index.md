---
title : "Test IAM with Postman"
weight : 4
chapter : false
pre : " <b> 7.4 </b> "
---

#### Test API with Postman
1. Open **Postman**
2. Select method **GET** created
 + Replace **{id}** with `abcd1234`
![API Gateway](/API-Gateway-Security-and-Rate-Limiting/images/7.configiam/018-configiam.png)
3. Select tab **Authorization** 
 + In the **auth type**, choose **AWS Signature**
 + Enter **Accesskey** and **Secretkey**
 + Enter **AWS Region**, such as: `ap-southeast-1`
 + Enter **Service name**: `execute-api`
 + Click **Send**
![API Gateway](/API-Gateway-Security-and-Rate-Limiting/images/7.configiam/019-configiam.png)

4. Successful results
![API Gateway](/API-Gateway-Security-and-Rate-Limiting/images/7.configiam/020-configiam.png)
{{% notice info %}}
Similarly, do the same with POST and DELETE method.
{{% /notice %}}

5. If **Authorization** are not configured, the result will be displayed information.
```
{
  "message": "Missing Authentication Token"
}
```
![API Gateway](/API-Gateway-Security-and-Rate-Limiting/images/7.configiam/021-configiam.png)
