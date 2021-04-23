# AWSConfigRemediation\-EnableKeyRotation<a name="automation-aws-enable-key-rotation"></a>

**Description**

The AWSConfigRemediation\-EnableKeyRotation runbook enables automatic key rotation for the symmetric AWS Key Management Service \(AWS KMS\) customer managed key\.

[Run this Automation \(console\)](https://console.aws.amazon.com/systems-manager/automation/execute/AWSConfigRemediation-EnableKeyRotation)

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
+ KeyId

  Type: String

  Description: \(Required\) The ID of the customer managed key you want to enable automatic key rotation on\.

**Required IAM permissions**

The `AutomationAssumeRole` parameter requires the following actions to successfully use the runbook\.
+ `ssm:StartAutomationExecution`
+ `ssm:GetAutomationExecution`
+ `kms:EnableKeyRotation`
+ `kms:GetKeyRotationStatus`

**Document Steps**
+ aws:executeAwsApi \- Enables automatic key rotation on the customer managed key you specify in the `KeyId` parameter\.
+ aws:assertAwsResourceProperty \- Confirms that automatic key rotation is enabled on your customer managed key\.