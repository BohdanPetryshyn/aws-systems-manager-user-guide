# AWS\-DeleteCloudFormationStack<a name="automation-aws-deletecloudformationstack"></a>

**Description**

Delete an AWS CloudFormation stack\.

[Run this Automation \(console\)](https://console.aws.amazon.com/systems-manager/automation/execute/AWS-DeleteCloudFormationStack)

**Document type**

Automation

**Owner**

Amazon

**Platforms**

Linux, macOS, Windows

**Parameters**
+ AutomationAssumeRole

  Type: String

  Description: \(Optional\) The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that allows Systems Manager Automation to perform the actions on your behalf\. If no role is specified, Systems Manager Automation uses the permissions of the user that runs this runbook\.
+ StackNameOrId

  Type: String

  Description: \(Required\) Name or Unique ID of the CloudFormation stack to be deleted