# AWS\-DeleteDynamoDbBackup<a name="automation-aws-deletedynamodbbackup"></a>

**Description**

Delete the backup of an Amazon DynamoDB table\.

[Run this Automation \(console\)](https://console.aws.amazon.com/systems-manager/automation/execute/AWS-DeleteDynamoDbBackup)

**Document type**

Automation

**Owner**

Amazon

**Platforms**

Databases

**Parameters**
+ AutomationAssumeRole

  Type: String

  Description: \(Optional\) The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that allows Systems Manager Automation to perform the actions on your behalf\. If no role is specified, Systems Manager Automation uses the permissions of the user that runs this runbook\.
+ BackupArn

  Type: String

  Description: \(Required\) ARN of the DynamoDB table backup to delete\.