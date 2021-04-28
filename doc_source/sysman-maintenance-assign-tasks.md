# Assign tasks to a maintenance window \(console\)<a name="sysman-maintenance-assign-tasks"></a>

In this procedure, you add a task to a maintenance window\. Tasks are the actions performed on a resource when a maintenance window\. 

The following four types of tasks can be added to a maintenance window:
+ AWS Systems Manager Run Command commands
+ Systems Manager Automation workflows
+ AWS Step Functions tasks
+ AWS Lambda functions
**Important**  
The IAM policy for Maintenance Windows requires that you add the prefix `SSM` to Lambda function \(or alias\) names\. Before you proceed to register this type of task, you must update its name in AWS Lambda to include `SSM`\. For example, if your Lambda function name is `MyLambdaFunction`, change it to `SSMMyLambdaFunction`\.

**To assign tasks to a maintenance window**

1. Open the AWS Systems Manager console at [https://console\.aws\.amazon\.com/systems\-manager/](https://console.aws.amazon.com/systems-manager/)\.

1. In the navigation pane, choose **Maintenance Windows**\. 

1. In the list of maintenance windows, choose a maintenance window\.

1. Choose **Actions**, and then choose the option for the type of task you want to register with the maintenance window\.
   + **Register Run command task**
   + **Register Automation task**
   + **Register Step Functions task**
   + **Register Lambda task**

1. For **Name**, enter a name for the task\.

1. For **Description**, enter a description\.

1. For **Document**, choose the Systems Manager command document \(SSM\) document or Automation runbook that defines the tasks to run\.

1. For **Document version** \(for Automation tasks\), choose the document version to use\.

1. For **Task priority**, specify a priority for this task\. Zero \(`0`\) is the highest priority\. Tasks in a maintenance window are scheduled in priority order with tasks that have the same priority scheduled in parallel\.

1. In the **Targets** section, identify the instances on which you want to run this operation by specifying tags, selecting instances manually, or specifying a resource group\.
**Note**  
If an Amazon EC2 instance you expect to see is not listed, see [Troubleshooting Amazon EC2 managed instance availability](troubleshooting-managed-instances.md) for troubleshooting tips\.
**Note**  
You must specify one or more targets for maintenance window Run Command\-type tasks\. Depending on the task, targets are optional for other maintenance window task types \(Automation, AWS Lambda, and AWS Step Functions\)\. For more information about running tasks that do not specify targets, see [Registering maintenance window tasks without targets](maintenance-windows-targetless-tasks.md)\.

1. For **Rate control**:
   + For **Concurrency**, specify either a number or a percentage of instances on which to run the command at the same time\.
**Note**  
If you selected targets by specifying tags applied to managed instances or by specifying AWS resource groups, and you are not certain how many instances are targeted, then restrict the number of instances that can run the document at the same time by specifying a percentage\.
   + For **Error threshold**, specify when to stop running the command on other instances after it fails on either a number or a percentage of instances\. For example, if you specify three errors, then Systems Manager stops sending the command when the fourth error is received\. Instances still processing the command might also send errors\.

1. In the ** IAM service role** area, choose one of the following options to provide permissions for Systems Manager to run tasks on your target instances:
   +  ** Create and use a service\-linked role for Systems Manager **

     Service\-linked roles provide a secure way to delegate permissions to AWS services because only the linked service can assume a service\-linked role\. Additionally, AWS automatically defines and sets the permissions of service\-linked roles, depending on the actions that the linked service performs on your behalf\.
**Note**  
If a service\-linked role has already been created for your account, choose **Use the service\-linked role for Systems Manager**\.
   + **Use a custom service role**

     You can create a custom service role for maintenance window tasks if you want to use stricter permissions than those provided by the service\-linked role\. 

     If you need to create a custom service role, see one of the following topics:
     + [Control access to maintenance windows \(console\)](sysman-maintenance-perm-console.md)
     + [Control access to maintenance windows \(AWS CLI\)](sysman-maintenance-perm-cli.md)
     + [Control access to maintenance windows \(Tools for Windows PowerShell\)](sysman-maintenance-perm-ps.md)

   To help you decide whether to use a custom service role or the Systems Manager service\-linked role with a maintenance window task, see [Should I use a service\-linked role or a custom service role to run maintenance window tasks?](sysman-maintenance-permissions.md#maintenance-window-tasks-service-role)\.

1. In the **Input Parameters** section, specify parameters for the document\. For Automation runbooks, the system auto\-populates some of the values\. You can keep or replace these values\.

1. Complete the wizard\.