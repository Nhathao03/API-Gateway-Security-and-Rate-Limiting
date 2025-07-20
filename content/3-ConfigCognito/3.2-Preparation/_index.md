---
title : "Preparation"
weight : 2
chapter : false
pre : " <b> 3.2 </b> "
---

We perform the following steps to prepare for authentication and save files with the Amplify library in the following section:

1. To install Amplify CLI, run the command below:

```
npm install -g @aws-amplify/cli
```

{{% notice info %}}
You must install NodeJs before installing Amplify CLI
You should create a user and configure an AWS profile with credentials on your machine.
{{% /notice %}}

2. Run the below commands to clone the application to your device:

```
git clone https://github.com/AWS-First-Cloud-Journey/FCJ-Serverless-DMS
cd FCJ-Serverless-DMS
npm install

```

3. Open the project and open **src/component/Home/Upload.js** file. Comment the block codes that call API to interact with DynamoDB
![Config cognito](/images/3.configcognito/001-configcognito.png)

4. To initialize Amplify for your application, run the following command from the application’s root directory:

```
amplify init

```
 + Enter the following information:

   ? Enter a name for the project `fcjdms``
   The following configuration will be applied:

   Project information
   - | Name: fcjdms
   - | Environment: dev
   - | Default editor: Visual Studio Code
   - | App type: javascript
   - | Javascript framework: react
   - | Source Directory Path: src
   - | Distribution Directory Path: build
   - | Build Command: npm run-script build
   - | Start Command: npm run-script start

   - ? Initialize the project with the above configuration? `Yes`
   - Using default provider awscloudformation
   - ? Select the authentication method you want to use: AWS profile

   - For more information on AWS Profiles, see:
   - https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.html

   - ? Please choose the profile you want to use default
   - ? Help improve Amplify CLI by sharing non sensitive configurations on failures (y/N) › `No`

![Config cognito](/images/3.configcognito/002-configcognito.png)

5. Open [CloudFormation console](https://console.aws.amazon.com/cloudformation)

6. Select **Stacks** on the left menu, you will see the newly created stack. Click the **Resources** tab and you will see the resources that Amplify 
creates 
![Config cognito](/images/3.configcognito/003-configcognito.png)