# AWSConfigRemediation\-EnableEnhancedMonitoringOnRDSInstance<a name="automation-aws-enable-rds-monitoring"></a>

**Description**

The AWSConfigRemediation\-EnableEnhancedMonitoringOnRDSInstance runbook enables Enhanced Monitoring on the Amazon RDS database instance you specify\. For information on Enhanced Monitoring, see [Enhanced Monitoring](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/USER_Monitoring.OS.html) in the *Amazon RDS User Guide*\.

[Run this Automation \(console\)](https://console.aws.amazon.com/systems-manager/automation/execute/AWSConfigRemediation-EnableEnhancedMonitoringOnRDSInstance)

**Document type**

Automation

**Owner**

Amazon

**Platforms**

Databases

**Parameters**
+ AutomationAssumeRole

  Type: String

  Description: \(Required\) The Amazon Resource Name \(ARN\) of the AWS Identity and Access Management \(IAM\) role that allows Systems Manager Automation to perform the actions on your behalf\.
+ MonitoringInterval

  Type: Integer

  Valid values: 1 \| 5 \| 10 \| 15 \| 30 \| 60

  Description: \(Required\) The interval in seconds when Enhanced Monitoring metrics are collected from the DB instance\.
+ MonitoringRoleArn

  Type: String

  Description: \(Required\) The Amazon Resource Name \(ARN\) of the IAM role that allows Amazon RDS to send Enhanced Monitoring metrics to Amazon CloudWatch Logs\.
+ ResourceId

  Type: String

  Description: \(Required\) The resource identifier for the DB instance you want to enable Enhanced Monitoring on\.

**Required IAM permissions**

The `AutomationAssumeRole` parameter requires the following actions to successfully use the runbook\.
+ `ssm:StartAutomationExecution`
+ `ssm:GetAutomationExecution`
+ `rds:DescribeDBInstances`
+ `rds:ModifyDBInstance`

**Document Steps**
+ aws:executeAwsApi \- Gathers the DB instance identifier from the DB instance resource identifier\.
+ aws:assertAwsResourceProperty \- Confirms the DB Instance is in an `AVAILABLE` state\.
+ aws:executeAwsApi \- Enables Enhanced Monitoring on your DB instance\.
+ aws:executeScript \- Confirms that Enhanced Monitoring is enabled on your DB instance\.