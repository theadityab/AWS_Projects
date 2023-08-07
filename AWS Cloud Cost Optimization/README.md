# AWS Cloud Cost Optimization - Identifying Stale Resources

## Description

This document provides detailed information on how to create an AWS Lambda function using the `boto3` Python module to identify and delete stale Amazon Elastic Block Store (EBS) snapshots. Stale snapshots are those snapshots that are no longer associated with any active EC2 instance, and deleting them can lead to cost optimization by reducing unnecessary storage costs.

## Prerequisites

1. **AWS Account**: You should have access to an AWS account with sufficient permissions to create and manage Lambda functions and work with EBS snapshots.

2. **Python and `boto3`**: Ensure that you have Python installed on your local machine, along with the `boto3` module. You can install the module using the following command:

   ```bash
   pip install boto3

3. **IAM Role**: Create an IAM role with the necessary permissions to allow the Lambda function to interact with EC2 and EBS resources. The required permissions include:
*ec2:DescribeSnapshots*: To fetch a list of EBS snapshots.
*ec2:DescribeVolumes*: To get information about EBS volumes.
*ec2:DescribeInstances*: To retrieve a list of active EC2 instances.
*ec2:DeleteSnapshot*: To delete stale EBS snapshots.

## Lambda Code

Create a new Python file, e.g., stale_ebs_snapshots.py and paste the code. 

## 
## Deployment

To deploy this project:

*Create Lambda Function*: Go to the AWS Lambda console and click on "Create function." Provide a name for your Lambda function and select "Author from scratch." For the "Runtime," choose "Python" (the version you prefer). For the "Permissions," select an existing IAM role with the required permissions or create a new role.

*Copy Script*: In the "Function code" section, paste the Python script directly into the code editor.


*Create Function*: Click on "Create function" to create the Lambda function.

*Set up CloudWatch Events Rule*: Set up a CloudWatch Events rule to trigger the Lambda function periodically (e.g., daily or weekly).

*Testing*: Once the Lambda function is triggered, it will fetch all EBS snapshots owned by the account and check if each snapshot's associated volume is not associated with any active EC2 instance. If any stale snapshots are found, they will be deleted, and the function's output will indicate the number of snapshots deleted.

*Test Lambda Function*: Use the "Test" button in the AWS Lambda console to test the function. You can also check the CloudWatch logs for any errors or additional debugging information.





## Conclusion

By following the steps outlined in this document, you have created an AWS Lambda function to identify and delete stale EBS snapshots, helping to optimize storage costs in your AWS environment. The Lambda function can be scheduled to run periodically, ensuring that your EBS snapshot resources stay clean and cost-effective. Always be cautious when deleting resources, and thoroughly test the function before deploying it in a production environment.