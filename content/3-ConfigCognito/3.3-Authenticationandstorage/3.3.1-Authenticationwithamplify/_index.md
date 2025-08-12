---
title : "Authentication with Anplify"
weight : 1
chapter : false
pre : " <b> 3.3.1 </b> "
---

1. Run the following command at the root of the application you cloned to add authentication to the application:

```
amplify add auth

```

+ Select follow the informations below:

    - Do you want to use the default authentication and security configuration? ***Default configuration***
    - Warning: you will not be able to edit these selections.
    - How do you want users to be able to sign in? ***Username***
    - Do you want to configure advanced settings? ***No, I am done.***

![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/004-configcognito.png)

2. Run the following command to update cloud resources:

```
amplify push

```
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/005-configcognito.png)

3. Navigate to the CloudFormation console to check if the stack has been created.
 + Click **id** of UserPool to open dashboard of **Cognito User Pool**

![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/006-configcognito.png)

4. Run the following command to start the application: `npm start`
 + Click **Sign up** to register a new account.
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/007-configcognito.png)

5. Enter user information:
 + Username, for example: `admin`
 + Enter your email.
 + Password, for example: `Admin123`
 + Click ****Sign up**

![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/008-configcognito.png)

6. Navigate to Cognito User Pool console, select **User** tab you will see a registered but unconfirmed user
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/009-configcognito.png)

7. Open your email to get the verification code that was sent automatically.
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/010-configcognito.png)

8. Enter the verification code into the app and click **Submit**
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/011-configcognito.png)

9. Navigate to Cognito User Pool console, click the **Refresh** icon and you will see that the user is confirmed
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/012-configcognito.png)

10. Log in to the app with the account you just registered with.
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/013-configcognito.png)

11. Successful login.
![Authentication with Amplify]({{< relref "/" >}}images/3.configcognito/014-configcognito.png)