# AWS Systems Manager Patch Manager<a name="systems-manager-patch"></a>

Patch Manager, a capability of AWS Systems Manager, automates the process of patching managed nodes with both security related and other types of updates\. You can use Patch Manager to apply patches for both operating systems and applications\. \(On Windows Server, application support is limited to updates for applications released by Microsoft\.\) You can use Patch Manager to install Service Packs on Windows nodes and perform minor version upgrades on Linux nodes\. You can patch fleets of Amazon Elastic Compute Cloud \(Amazon EC2\) instances, edge devices, or your on\-premises servers and virtual machines \(VMs\) by operating system type\. This includes supported versions of Amazon Linux, Amazon Linux 2, CentOS, Debian Server, macOS, Oracle Linux, Raspberry Pi OS \(formerly Raspbian\), Red Hat Enterprise Linux \(RHEL\), SUSE Linux Enterprise Server \(SLES\), Ubuntu Server, and Windows Server\. You can scan instances to see only a report of missing patches, or you can scan and automatically install all missing patches\. To get started with Patch Manager, open the [Systems Manager console](https://console.aws.amazon.com/systems-manager/patch-manager)\. In the navigation pane, choose **Patch Manager**\.

**Important**  
AWS doesn't test patches before making them available in Patch Manager\. Also, Patch Manager doesn't support upgrading major versions of operating systems, such as Windows Server 2016 to Windows Server 2019, or SUSE Linux Enterprise Server \(SLES\) 12\.0 to SLES 15\.0\.  
For Linux\-based operating system types that report a severity level for patches, Patch Manager uses the severity level reported by the software publisher for the update notice or individual patch\. Patch Manager doesn't derive severity levels from third\-party sources, such as the [Common Vulnerability Scoring System](https://www.first.org/cvss/) \(CVSS\), or from metrics released by the [National Vulnerability Database](https://nvd.nist.gov/vuln) \(NVD\)\.

Patch Manager uses *patch baselines*, which include rules for auto\-approving patches within days of their release, in addition to a list of approved and rejected patches\. You can install patches on a regular basis by scheduling patching to run as a Systems Manager maintenance window task\. You can also install patches individually or to large groups of managed nodes by using tags\. \(Tags are keys that help identify and sort your resources within your organization\.\) You can add tags to your patch baselines themselves when you create or update them\. 

Patch Manager provides options to scan your managed nodes and report compliance on a schedule, install available patches on a schedule, and patch or scan targets on demand whenever you need to\. You can also generate patch compliance reports that are sent to an Amazon Simple Storage Service \(Amazon S3\) bucket of your choice\. You can generate one\-time reports, or generate reports on a regular schedule\. For a single managed node, reports include details of all patches for the node\. For a report on all managed nodes, only a summary of how many patches are missing is provided\.

Patch Manager integrates with AWS Identity and Access Management \(IAM\), AWS CloudTrail, and Amazon EventBridge to provide a secure patching experience that includes event notifications and the ability to audit usage\.

For information about using CloudTrail to monitor Systems Manager actions, see [Logging AWS Systems Manager API calls with AWS CloudTrail](monitoring-cloudtrail-logs.md)\.

For information about using EventBridge to monitor Systems Manager events, see [Monitoring Systems Manager events with Amazon EventBridge](monitoring-eventbridge-events.md)\.

**Topics**
+ [Patch Manager prerequisites](patch-manager-prerequisites.md)
+ [How Patch Manager operations work](patch-manager-how-it-works.md)
+ [About SSM documents for patching managed nodes](patch-manager-ssm-documents.md)
+ [About patch baselines](about-patch-baselines.md)
+ [Using Kernel Live Patching on Amazon Linux 2 managed nodes](kernel-live-patching.md)
+ [Working with Patch Manager \(console\)](sysman-patch-working.md)
+ [Working with Patch Manager \(AWS CLI\)](patch-manager-cli-commands.md)
+ [AWS Systems ManagerPatch Manager walkthroughs](patch-walkthroughs.md)
+ [Troubleshooting Patch Manager](patch-manager-troubleshooting.md)