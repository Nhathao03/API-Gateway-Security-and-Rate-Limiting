---
title : "Create Policy"
weight : 1
chapter : false
pre : " <b> 7.1 </b> "
---


#### Create new policy
1. Open [AWS IAM](https://console.aws.amazon.com/iam) 
 + Click **Policy**, then click **Create policy**
![Create new policy](/images/7.configiam/001-configiam.png)

2. In the **Specify permissions** section:
 + Click **JSON**
 + Copy the below code block to **Policy**
 + Click **Next**
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "execute-api:Invoke",
      "Resource": "arn:aws:execute-api:<REGION>:<ACCOUNT_ID>:<API_ID>/*"
    }
  ]
}

```
![Create new policy](/images/7.configiam/002-configiam.png)

3. In the **Policy details** section:
 + Enter policy name: `fcjdmswebstore_5801_policy`
 + Click **Next**
![Create new policy](/images/7.configiam/003-configiam.png)

