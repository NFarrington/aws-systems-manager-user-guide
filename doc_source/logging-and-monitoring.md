# Logging and monitoring in AWS Systems Manager<a name="logging-and-monitoring"></a>

Monitoring is an important part of maintaining the reliability, availability, and performance of AWS Systems Manager and your AWS solutions\. You should collect monitoring data from all of the parts of your AWS solution so that you can more debug a multi\-point failure if one occurs\. AWS provides several tools for monitoring your Systems Manager and other resources and responding to potential incidents\.

**AWS CloudTrail logs**  
CloudTrail provides a record of actions taken by a user, role, or an AWS service in Systems Manager\. Using the information collected by CloudTrail, you can determine the request that was made to Systems Manager, the IP address from which the request was made, who made the request, when it was made, and additional details\. For more information, see [Logging AWS Systems Manager API calls with AWS CloudTrail](monitoring-cloudtrail-logs.md)\.

**Amazon CloudWatch alarms**  
Using Amazon CloudWatch alarms, you watch a single metric over a time period that you specify for your Amazon Elastic Compute Cloud \(Amazon EC2\) instances and other resources\. If the metric exceeds a given threshold, a notification is sent to an Amazon Simple Notification Service \(Amazon SNS\) topic or AWS Auto Scaling policy\. CloudWatch alarms don't invoke actions because they're in a particular state\. Rather the state must have changed and been maintained for a specified number of periods\. For more information, see [Using Amazon CloudWatch alarms](https://docs.aws.amazon.com/AmazonCloudWatch/latest/monitoring/AlarmThatSendsEmail.html) in the *Amazon CloudWatch User Guide*\.

**Amazon CloudWatch dashboards**  
CloudWatch dashboards are customizable home pages in the CloudWatch console that you can use to monitor your resources in a single view, even those resources that are spread across different AWS Regions\. You can use CloudWatch dashboards to create customized views of the metrics and alarms for your AWS resources\. For more information, see [Amazon CloudWatch dashboards hosted by Systems Manager](systems-manager-cloudwatch-dashboards.md)\.

**Amazon EventBridge**  
Using Amazon EventBridge, you can configure rules to alert you to changes in Systems Manager resources, and to direct EventBridge to take actions based on the content of those events\. EventBridge provides support for a number of events that are emitted by various Systems Manager capabilities\. For more information, see [Monitoring Systems Manager events with Amazon EventBridge](monitoring-eventbridge-events.md)\.

**Amazon CloudWatch Logs and SSM Agent logs**  
SSM Agent writes information about executions, scheduled actions, errors, and health statuses to log files on each node\. You can view log files by manually connecting to a node\. We recommend automatically sending agent log data to a log group in CloudWatch Logs for analysis\. For more information, see [Sending node logs to CloudWatch Logs \(CloudWatch agent\)](monitoring-cloudwatch-agent.md) and [Viewing SSM Agent logs](sysman-agent-logs.md)\.

**AWS Systems Manager Compliance**  
You can use Compliance, a capability of AWS Systems Manager, to scan your fleet of managed nodes for patch compliance and configuration inconsistencies\. You can collect and aggregate data from multiple AWS accounts and AWS Regions, and then drill down into specific resources that aren’t compliant\. By default, Compliance displays current compliance data about patching in Patch Manager, a capability of AWS Systems Manager, and associations in State Manager, a capability of AWS Systems Manager\. For more information, see [AWS Systems Manager Compliance](systems-manager-compliance.md)\.

**AWS Systems Manager Explorer**  
Explorer, a capability of AWS Systems Manager, is a customizable operations dashboard that reports information about your AWS resources\. Explorer displays an aggregated view of operations data \(OpsData\) for your AWS accounts and across AWS Regions\. In Explorer, OpsData includes metadata about your EC2 instances, patch compliance details, and operational work items \(OpsItems\)\. Explorer provides context about how OpsItems are distributed across your business units or applications, how they trend over time, and how they vary by category\. You can group and filter information in Explorer to focus on items that are relevant to you and that require action\. For more information, see [AWS Systems Manager Explorer](Explorer.md)\.

**AWS Systems Manager OpsCenter**  
OpsCenter, a capability of AWS Systems Manager, provides a central location where operations engineers and IT professionals can view, investigate, and resolve operational work items \(OpsItems\) related to AWS resources\. OpsCenter aggregates and standardizes OpsItems across services while providing contextual investigation data about each OpsItem, related OpsItems, and related resources\. OpsCenter also provides runbooks in Automation, a capability of AWS Systems Manager, that you can use to quickly resolve issues\. OpsCenter is integrated with Amazon EventBridge\. This means you can create EventBridge rules that automatically create OpsItems for any AWS service that publishes events to EventBridge\. For more information, see [AWS Systems Manager OpsCenter](OpsCenter.md)\.

**Amazon Simple Notification Service**  
You can configure Amazon Simple Notification Service \(Amazon SNS\) to send notifications about the status of commands that you send using Run Command or Maintenance Windows, capabilities of AWS Systems Manager\. Amazon SNS coordinates and manages sending and delivering notifications to clients or endpoints that are subscribed to Amazon SNS topics\. You can receive a notification whenever a command changes to a new state or to a specific state, such as `Failed` or `Timed Out`\. In cases where you send a command to multiple nodes, you can receive a notification for each copy of the command sent to a specific node\. For more information, see [Monitoring Systems Manager status changes using Amazon SNS notifications](monitoring-sns-notifications.md)\.

**AWS Trusted Advisor and AWS Health Dashboard**  
Trusted Advisor draws upon best practices learned from serving hundreds of thousands of AWS customers\. Trusted Advisor inspects your AWS environment and then makes recommendations when opportunities exist to save money, improve system availability and performance, or help close security gaps\. All AWS customers have access to five Trusted Advisor checks\. Customers with either an AWS Support Business or Enterprise plan can view all Trusted Advisor checks\. For more information, see [AWS Trusted Advisor](https://docs.aws.amazon.com/awssupport/latest/user/trusted-advisor.html) in the *AWS Support User Guide* and the *[AWS Health User Guide](https://docs.aws.amazon.com/health/latest/ug/)*\.  

**Related content**
+ [Monitoring AWS Systems Manager](monitoring.md)