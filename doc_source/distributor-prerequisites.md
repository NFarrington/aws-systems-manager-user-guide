# Step 1: Complete Distributor prerequisites<a name="distributor-prerequisites"></a>

Before you use Distributor, a capability of AWS Systems Manager, be sure your environment meets the following requirements\.


**Distributor prerequisites**  

| Requirement | Description | 
| --- | --- | 
|  SSM Agent  |  AWS Systems Manager SSM Agent version 2\.3\.274\.0 or later must be installed on the managed nodes on which you want to deploy or from which you want to remove packages\. To install or update SSM Agent, see [Working with SSM Agent](ssm-agent.md)\.  | 
|  AWS CLI  |  \(Optional\) To use the AWS Command Line Interface \(AWS CLI\) instead of the Systems Manager console to create and manage packages, install the newest release of the AWS CLI on your local computer\. For more information about how to install or upgrade the CLI, see [Installing the AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/installing.html) in the *AWS Command Line Interface User Guide*\.  | 
|  AWS Tools for PowerShell  |  \(Optional\) To use the Tools for PowerShell instead of the Systems Manager console to create and manage packages, install the newest release of Tools for PowerShell on your local computer\. For more information about how to install or upgrade the Tools for PowerShell, see [Setting Up the AWS Tools for Windows PowerShell or AWS Tools for PowerShell Core](https://docs.aws.amazon.com/powershell/latest/userguide/pstools-getting-set-up.html) in the *AWS Tools for PowerShell User Guide*\.  | 

**Note**  
Systems Manager doesn't support distributing packages to Oracle Linux managed nodes by using Distributor\.