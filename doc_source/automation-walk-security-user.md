# Running an automation as the current authenticated user<a name="automation-walk-security-user"></a>

The following procedures describe how to run an automation that runs in the context of the current AWS Identity and Access Management \(IAM\) user using the AWS Systems Manager console and AWS Command Line Interface \(AWS CLI\)\. Running the automation in the context of the current IAM user means that you don't need to configure additional IAM permissions as long as IAM user has permission to use the runbook, and any actions called by the runbook\. If the IAM user has have administrator permissions in IAM, then you have permission to use this runbook\.

## Running an automation as the current authenticated user \(console\)<a name="automation-walk-security-user-console"></a>

The following procedure describes how to use the Systems Manager console to run an automation as the current authenticated user\.

**To use the runbook as the current authenticated user**

1. Open the AWS Systems Manager console at [https://console\.aws\.amazon\.com/systems\-manager/](https://console.aws.amazon.com/systems-manager/)\.

1. In the navigation pane, choose **Automation**, and then choose **Execute automation**\.

1. In the **Automation document** list, choose a runbook\. Choose one or more options in the **Document categories** pane to filter SSM documents according to their purpose\. To view a runbook that you own, choose the **Owned by me** tab\. To view a runbook that is shared with your account, choose the **Shared with me** tab\. To view all runbooks, choose the **All documents** tab\.
**Note**  
You can view information about a runbook by choosing the runbook name\.

1. In the **Document details** section, verify that **Document version** is set to the version that you want to run\. The system includes the following version options: 
   + **Default version at runtime**: Choose this option if the Automation runbook is updated periodically and a new default version is assigned\.
   + **Latest version at runtime**: Choose this option if the Automation runbook is updated periodically, and you want to run the version that was most recently updated\.
   + **1 \(Default\)**: Choose this option to run the first version of the document, which is the default\.

1. Choose **Next**\.

1. In the **Execution Mode** section, choose **Simple execution**\.
**Note**  
This procedure uses the **Simple execution** mode\. However, you can alternatively choose **Rate control** or **Manual execution** and run the automation as the current authenticated user\.

1. In the **Input parameters** section, specify the required inputs\. To run the automation as the current authenticated user, don't specify an IAM service role for the value AutomationAssumeRole\.

1. Choose **Execute**\. The console displays the status of the automation\.

## Running an automation as the current authenticated user \(command line\)<a name="automation-walk-security-user-commandline"></a>

The following procedure describes how to use the AWS CLI \(on Linux or Windows\) or AWS Tools for PowerShell to run an automation as the current authenticated user\.

**To run the automation as the current authenticated user**

1. Install and configure the AWS CLI or the AWS Tools for PowerShell, if you haven't already\.

   For information, see [Install or upgrade AWS command line tools](getting-started-cli.md)\.

1. Run the following command to start an automation as the current authenticated user\. Replace each *example resource placeholder* with your own information\.

------
#### [ Linux & macOS ]

   ```
   aws ssm start-automation-execution \
       --document-name runbook name \
       --parameters runbook parameters
   ```

------
#### [ Windows ]

   ```
   aws ssm start-automation-execution ^
       --document-name runbook name ^
       --parameters runbook parameters
   ```

------
#### [ PowerShell ]

   ```
   Start-SSMAutomationExecution `
       -DocumentName runbook name `
       -Parameter runbook parameters
   ```

------

   Here is an example using the runbook `AWS-RestartEC2Instance` to restart the specified Amazon Elastic Compute Cloud \(Amazon EC2\) instance\.

------
#### [ Linux & macOS ]

   ```
   aws ssm start-automation-execution \
       --document-name "AWS-RestartEC2Instance" \
       --parameters "InstanceId=i-02573cafcfEXAMPLE"
   ```

------
#### [ Windows ]

   ```
   aws ssm start-automation-execution ^
       --document-name "AWS-RestartEC2Instance" ^
       --parameters "InstanceId=i-02573cafcfEXAMPLE"
   ```

------
#### [ PowerShell ]

   ```
   Start-SSMAutomationExecution `
       -DocumentName AWS-RestartEC2Instance `
       -Parameter @{"InstanceId"="i-02573cafcfEXAMPLE"}
   ```

------

   The system returns information like the following\.

------
#### [ Linux & macOS ]

   ```
   {
       "AutomationExecutionId": "4105a4fc-f944-11e6-9d32-0123456789ab"
   }
   ```

------
#### [ Windows ]

   ```
   {
       "AutomationExecutionId": "4105a4fc-f944-11e6-9d32-0123456789ab"
   }
   ```

------
#### [ PowerShell ]

   ```
   4105a4fc-f944-11e6-9d32-0123456789ab
   ```

------

1. Run the following command to retrieve the status of the automation\. Replace the *automation execution ID* with your own information\.

------
#### [ Linux & macOS ]

   ```
   aws ssm describe-automation-executions \
       --filter "Key=ExecutionId,Values=automation execution ID"
   ```

------
#### [ Windows ]

   ```
   aws ssm describe-automation-executions ^
       --filter "Key=ExecutionId,Values=automation execution ID"
   ```

------
#### [ PowerShell ]

   ```
   Get-SSMAutomationExecutionList | `
       Where {$_.AutomationExecutionId -eq "automation execution ID"}
   ```

------

   The system returns information like the following\.

------
#### [ Linux & macOS ]

   ```
   {
       "AutomationExecutionMetadataList": [
           {
               "AutomationExecutionStatus": "InProgress",
               "CurrentStepName": "stopInstances",
               "Outputs": {},
               "DocumentName": "AWS-RestartEC2Instance",
               "AutomationExecutionId": "4105a4fc-f944-11e6-9d32-0123456789ab",
               "DocumentVersion": "1",
               "ResolvedTargets": {
                   "ParameterValues": [],
                   "Truncated": false
               },
               "AutomationType": "Local",
               "Mode": "Auto",
               "ExecutionStartTime": 1564600648.159,
               "CurrentAction": "aws:changeInstanceState",
               "ExecutedBy": "arn:aws:sts::123456789012:assumed-role/Administrator/Admin",
               "LogFile": "",
               "Targets": []
           }
       ]
   }
   ```

------
#### [ Windows ]

   ```
   {
       "AutomationExecutionMetadataList": [
           {
               "AutomationExecutionStatus": "InProgress",
               "CurrentStepName": "stopInstances",
               "Outputs": {},
               "DocumentName": "AWS-RestartEC2Instance",
               "AutomationExecutionId": "4105a4fc-f944-11e6-9d32-0123456789ab",
               "DocumentVersion": "1",
               "ResolvedTargets": {
                   "ParameterValues": [],
                   "Truncated": false
               },
               "AutomationType": "Local",
               "Mode": "Auto",
               "ExecutionStartTime": 1564600648.159,
               "CurrentAction": "aws:changeInstanceState",
               "ExecutedBy": "arn:aws:sts::123456789012:assumed-role/Administrator/Admin",
               "LogFile": "",
               "Targets": []
           }
       ]
   }
   ```

------
#### [ PowerShell ]

   ```
   AutomationExecutionId       : 4105a4fc-f944-11e6-9d32-0123456789ab
   AutomationExecutionStatus   : InProgress
   AutomationType              : Local
   CurrentAction               : aws:changeInstanceState
   CurrentStepName             : startInstances
   DocumentName                : AWS-RestartEC2Instance
   DocumentVersion             : 1
   ExecutedBy                  : arn:aws:sts::123456789012:assumed-role/Administrator/Admin
   ExecutionEndTime            : 1/1/0001 12:00:00 AM
   ExecutionStartTime          : 7/31/2019 7:17:28 PM
   FailureMessage              : 
   LogFile                     : 
   MaxConcurrency              : 
   MaxErrors                   : 
   Mode                        : Auto
   Outputs                     : {}
   ParentAutomationExecutionId : 
   ResolvedTargets             : Amazon.SimpleSystemsManagement.Model.ResolvedTargets
   Target                      : 
   TargetMaps                  : {}
   TargetParameterName         : 
   Targets                     : {}
   ```

------