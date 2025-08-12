---
title : "Config IAM in API"
weight : 3
chapter : false
pre : " <b> 7.3 </b> "
---

#### Config IAM in API
1. Open [API Gateway](https://console.aws.amazon.com/apigateway) 
 + Select **API** created
![API Gateway]({{< relref "/" >}}images/7.configiam/013-configiam.png)

2. Click **Resources**
 + Click **GET** method, then click **Edit**
![API Gateway]({{< relref "/" >}}images/7.configiam/014-configiam.png)

3. In the **Edit method request** section:
 + In **Authorization**, choose `AWS_IAM`
 + Click **Save**
![API Gateway]({{< relref "/" >}}images/7.configiam/015-configiam.png)

{{% notice info %}}
Similarly, do the same with POST and DELETE method.
{{% /notice %}}

4. Click **/docs**, then click **Deloy API**
![API Gateway]({{< relref "/" >}}images/7.configiam/016-configiam.png)

5. In the **Deloy API**
 + Select **New stage**
 + Enter stage name: `dev`
 + Click **Deloy**
![API Gateway]({{< relref "/" >}}images/7.configiam/017-configiam.png)

