# AWSConfigRemediation\-DeleteUnusedVPCNetworkACL<a name="automation-aws-delete-vpc-nacl"></a>

**Description**

The AWSConfigRemediation\-DeleteUnusedVPCNetworkACL runbook deletes a network access control list \(ACL\) that is not associated with a subnet\.

[Run this Automation \(console\)](https://console.aws.amazon.com/systems-manager/automation/execute/AWSConfigRemediation-DeleteUnusedVPCNetworkACL)

**Document type**

Automation

**Owner**

Amazon

**Platforms**

Linux, macOS, Windows

**Parameters**
+ AutomationAssumeRole

  Type: String

  Description: \(Required\) The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that allows Systems Manager Automation to perform the actions on your behalf\.
+ NetworkAclId

  Type: String

  Description: \(Required\) The ID of the network ACL that you want to delete\.

**Required IAM permissions**

The `AutomationAssumeRole` parameter requires the following actions to successfully use the runbook\.
+ `ssm:StartAutomationExecution`
+ `ssm:GetAutomationExecution`
+ `ec2:DeleteNetworkAcl`
+ `ec2:DescribeNetworkAcls`

**Document Steps**
+ aws:executeAwsApi \- Deletes the network ACL specified in the `NetworkAclId` parameter\.
+ aws:executeScript \- Confirms the network ACL specified in the `NetworkAclId` parameter was deleted\.