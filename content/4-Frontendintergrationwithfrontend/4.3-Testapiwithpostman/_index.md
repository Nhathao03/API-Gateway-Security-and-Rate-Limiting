---
title : "Test API with Postman"
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

In this step, we will test operation of the APIs using [Postman](https://www.postman.com/downloads/) tool.

#### Test the listing API
1. Create new collection, then click **Bank collection**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/046-frontendintergrationwithapigateway.png)

2. Enter collection name, such as: `fcjdmswebstore-5801`
 + Click **Add request**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/047-frontendintergrationwithapigateway.png)
 + Select **GET** method 
 + Replace **{id}** with `abcd1234`
 + Click **Send**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/048-frontendintergrationwithapigateway.png) 

3. Successful results
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/049-frontendintergrationwithapigateway.png)

#### Test the creating API
1. Similarly add new request
 + Select **POST** method
 + Enter URL of the writing API that recorded from the previous step
 + In **Body** pattern, select **raw**
 + Copy the below text block:

```
{
      "user_id": "abcd1234",
      "file": "flowers.png",
      "folder": "",
      "identityId": "123456cvbn",
      "modified": "21-03-2023",
      "size": "32KB",
      "type": "png",
      "tag": "image"
}
```

 + Click **Send**
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/051-frontendintergrationwithapigateway.png)

2. Open the console of **DynamoDB**, select **Documents** and select the **Explore items** table to check the results:
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/052-frontendintergrationwithapigateway.png)

#### Test the deleting API
1. Similarly add new request
 + Select **DELETE** method
 + Enter URL of the writing API that recorded from the previous step, replace **{id}** with `abcd1234`
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/053-frontendintergrationwithapigateway.png)
 + In the **Params** section, enter `file` for the key and `flowers.png` for the value
 + Click Send
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/054-frontendintergrationwithapigateway.png)

2. Successful results
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/055-frontendintergrationwithapigateway.png)

3. Back to the **Documents** table, click the **Refresh** button to see the results
![Test API]({{< relref "/" >}}images/4.frontendintergrationwithapigateway/056-frontendintergrationwithapigateway.png)

