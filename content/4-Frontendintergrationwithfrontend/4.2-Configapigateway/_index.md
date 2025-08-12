---
title : "Config API Gateway"
weight : 2
chapter : false
pre : " <b> 4.2 </b> "
---

#### Update Lambda function

1. Open [AWS Lambda Console](https://console.aws.amazon.com/lambda)
2. Select **upload_documents** function
3. Comment on line 13 and uncomment line 12
4. Click **Deloy**
![Lambda](images/4.frontendintergrationwithapigateway/016-frontendintergrationwithapigateway.png)


#### Config API Gateway
1. Open [Amazon API Gateway Console]()
2. Click **Create API**
![Lambda](images/4.frontendintergrationwithapigateway/017-frontendintergrationwithapigateway.png)

3. Scroll down to **REST API** section, click **Build**
![Lambda](images/4.frontendintergrationwithapigateway/018-frontendintergrationwithapigateway.png)

4. Leave the default REST for the protocol.
 + Select **New API**
 + Enter API name: `fcj-dms-api-5801`
 + Select Endpoint type as **Regional**
 + Click **Create API**
![Lambda](images/4.frontendintergrationwithapigateway/019-frontendintergrationwithapigateway.png)

5. Select **API Gateway** created
![Lambda](images/4.frontendintergrationwithapigateway/019-frontendintergrationwithapigateway.png)

6. Click **Create Resource** to create resource for API.
![Lambda](images/4.frontendintergrationwithapigateway/021-frontendintergrationwithapigateway.png)

7. Enter resource name: `docs`, then click **Create Resource**
![Lambda](images/4.frontendintergrationwithapigateway/022-frontendintergrationwithapigateway.png)

8. Select **docs** resource, then click **Create Method**
![Lambda](images/4.frontendintergrationwithapigateway/023-frontendintergrationwithapigateway.png)

9. Set up the method as follows:
 + Keep default Integration type as **Lambda Function**
 + Check to **Lambda Proxy integration**
 + Select the region of the **Lambda function** you created
 + Select **upload_document** function
 + Finally press **Save**
![Lambda](images/4.frontendintergrationwithapigateway/024-frontendintergrationwithapigateway.png)
![Lambda](images/4.frontendintergrationwithapigateway/025-frontendintergrationwithapigateway.png)

10. After created **POST** method, click **Create Resource** to create next resource.
![Lambda](images/4.frontendintergrationwithapigateway/026-frontendintergrationwithapigateway.png)

11. Enter resource name: `id` and resource path as `{id}`, then click **Create Resource**
![Lambda](images/4.frontendintergrationwithapigateway/027-frontendintergrationwithapigateway.png)

12. Select **{id}** resource, then click **Create Method**
![Lambda](images/4.frontendintergrationwithapigateway/028-frontendintergrationwithapigateway.png)

13. Set up the method as follows:
 + Keep default Integration type as **Lambda Function**
 + Check to **Lambda Proxy integration**
 + Select the region of the **Lambda function** you created
 + Select **list_documents** function
 + Finally press **Save**
![Lambda](images/4.frontendintergrationwithapigateway/029-frontendintergrationwithapigateway.png)
![Lambda](images/4.frontendintergrationwithapigateway/030-frontendintergrationwithapigateway.png)

14. Click **Create Method** to create a new method
![Lambda](images/4.frontendintergrationwithapigateway/031-frontendintergrationwithapigateway.png)

15. Set up the method as follows:
 + Keep default Integration type as **Lambda Function**
 + Check to **Lambda Proxy integration**
 + Select the region of the **Lambda function** you created
 + Select **delete_document** function
 + Finally press **Save**
![Lambda](images/4.frontendintergrationwithapigateway/032-frontendintergrationwithapigateway.png)
![Lambda](images/4.frontendintergrationwithapigateway/033-frontendintergrationwithapigateway.png)

16. Select **DELETE** method, then click **Edit** in **Method request settings**
![Lambda](images/4.frontendintergrationwithapigateway/034-frontendintergrationwithapigateway.png)

17. Expand **URL Query String Parameters** section, click **Add query string** to add a new parameter
 + Enter parameter name: `file`. This parameter is value of of the name of the file you want to delete.
 + Click **Save**
![Lambda](images/4.frontendintergrationwithapigateway/035-frontendintergrationwithapigateway.png)

18. Select **docs** resource, then click **Enable CORS**
![Lambda](images/4.frontendintergrationwithapigateway/036-frontendintergrationwithapigateway.png)

19. Check to **POST**, then click **Save**
![Lambda](images/4.frontendintergrationwithapigateway/037-frontendintergrationwithapigateway.png)

20. Select **{id}** resource, then click **Enable CORS**
![Lambda](images/4.frontendintergrationwithapigateway/038-frontendintergrationwithapigateway.png)

21. Check to **GET** and **DELETE**, then click **Save**
![Lambda](images/4.frontendintergrationwithapigateway/039-frontendintergrationwithapigateway.png)

22. After completing the setup, we deploy the API. Select **/docs**, then click **Deploy API**
![Lambda](images/4.frontendintergrationwithapigateway/040-frontendintergrationwithapigateway.png)

23. Select **[New Stage]**
 + Enter stage name: `dev`
 + Click **Deploy**
![Lambda](images/4.frontendintergrationwithapigateway/041-frontendintergrationwithapigateway.png)

24. Note down the URL of the **API** used for the next section.
![Lambda](images/4.frontendintergrationwithapigateway/042-frontendintergrationwithapigateway.png)

25. Expand the stage, select the **POST** method and write down the URL.
![Lambda](images/4.frontendintergrationwithapigateway/043-frontendintergrationwithapigateway.png)

26. Expand the stage, select the **DELETE** method and write down the URL.
![Lambda](images/4.frontendintergrationwithapigateway/044-frontendintergrationwithapigateway.png)

27. Expand the stage, select the **GET** method and write down the URL.
![Lambda](images/4.frontendintergrationwithapigateway/045-frontendintergrationwithapigateway.png)

You have finished setting up the API. Next, we will test the API working and integrate it into our application.


