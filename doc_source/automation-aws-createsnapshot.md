# AWS\-CreateSnapshot<a name="automation-aws-createsnapshot"></a>

**Description**

Create a snapshot of an Amazon EBS volume\.

[Run this Automation \(console\)](https://console.aws.amazon.com/systems-manager/automation/execute/AWS-CreateSnapshot)

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
+ Description

  Type: String

  Description: \(Optional\) A description for the snapshot
+ VolumeId

  Type: String

  Description: \(Required\) The ID of the volume\.