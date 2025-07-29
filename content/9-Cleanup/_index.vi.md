---
title : "Dọn dẹp tài nguyên"
weight : 9
chapter : false
pre : " <b> 9. </b> "
---

## Delete WAF Resources

1. **Delete WAF Web ACL**:
   - Mở bảng điều khiển [AWS WAF console](https://console.aws.amazon.com/wafv2/)
   - Select your Web ACL
   - Remove associated CloudFront distribution
   - Click **Delete**

## Delete CloudFront Distribution

2. **Delete CloudFront distribution**:
   - Go to the [CloudFront console](https://console.aws.amazon.com/cloudfront/)
   - Select your distribution
   - Click **Disable** and wait for deployment
   - Once disabled, click **Delete**

## Delete API Gateway Resources

3. **Delete the API Gateway**:
   - Go to the [API Gateway console](https://console.aws.amazon.com/apigateway/)
   - Select your API
   - Click **Actions** → **Delete API**
   - Confirm deletion

## Delete Lambda Functions

4. **Delete Lambda functions**:
   - Go to the [Lambda console](https://console.aws.amazon.com/lambda/)
   - Delete all functions created (listing, creating, deleting)
   - Click **Actions** → **Delete**

## Delete Cognito Resources

5. **Delete Cognito User Pool**:
   - Go to the [Cognito console](https://console.aws.amazon.com/cognito/)
   - Delete User Pool and Identity Pool created by Amplify

## Delete S3 Resources

6. **Delete S3 buckets**:
   - Go to the [S3 console](https://console.aws.amazon.com/s3/)
   - Empty and delete all buckets created
   - Delete Amplify deployment bucket

## Delete DynamoDB Table

7. **Delete DynamoDB table**:
   - Go to the [DynamoDB console](https://console.aws.amazon.com/dynamodbv2/)
   - Select the `Documents` table
   - Click **Delete table**

## Delete IAM Resources

8. **Delete IAM roles and policies**:
   - Go to the [IAM console](https://console.aws.amazon.com/iam/)
   - Delete custom roles and policies created
   - Delete IAM users created for testing

## Delete CloudWatch Resources

9. **Delete CloudWatch log groups** (optional):
   - Go to the [CloudWatch console](https://console.aws.amazon.com/cloudwatch/)
   - Navigate to **Logs** → **Log groups**
   - Delete log groups created by services

{{% notice warning %}}
Delete resources in the order listed above to avoid dependency issues. CloudFront distributions take 15-20 minutes to delete.
{{% /notice %}}
