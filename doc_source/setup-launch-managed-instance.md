# Step 5: Attach an IAM instance profile to an Amazon EC2 instance<a name="setup-launch-managed-instance"></a>

This topic describes how to attach the AWS Identity and Access Management \(IAM\) instance profile for AWS Systems Manager that you created in [Step 4: Create an IAM instance profile for Systems Manager](setup-instance-profile.md) to Amazon EC2 instances\. You can attach the instance profile to new Amazon EC2 instances when you launch them, or to existing Amazon EC2 instances\. 

**SSM Agent requirements for instances**  
AWS Systems Manager Agent \(SSM Agent\) is Amazon software that can be installed and configured on an EC2 instance, an on\-premises server, or a virtual machine \(VM\)\. SSM Agent makes it possible for Systems Manager to update, manage, and configure these resources\.

If the Amazon Machine Image \(AMI\) type you choose in the first procedure doesn't come with SSM Agent preinstalled, manually install the agent on the new instance before it can be used with Systems Manager\. If SSM Agent isn't installed on the existing EC2 instance you choose in the second procedure, manually install the agent on the instance before it can be used with Systems Manager\.

SSM Agent is installed by default on the following AMIs:
+ Amazon Linux Base AMIs dated 2017\.09 and later
+ Amazon Linux 2
+ Amazon Linux 2 ECS\-Optimized Base AMIs
+ macOS 10\.14\.x \(Mojave\), 10\.15\.x \(Catalina\), and 11\.x \(Big Sur\)
+ SUSE Linux Enterprise Server \(SLES\) 12 and 15
+ Ubuntu Server 16\.04, 18\.04, and 20\.04  
+ Windows Server 2008\-2012 R2 AMIs published in November 2016 or later
+ Windows Server 2016, 2019, and 2022

For information about manually installing SSM Agent on other Linux operating systems, see [Working with SSM Agent on EC2 instances for Linux](sysman-install-ssm-agent.md)\.

**TLS certificate requirement for instances**  
A Transport Layer Security \(TLS\) certificate must be installed on each managed instance you use with Systems Manager\. These certificates are used to encrypt calls to other AWS services\. A TLS certificate is already installed on each EC2 instance created from any AMI\. On instances created from AMIs not supplied by Amazon, and on your own on\-premises servers and VMs, install the certificate yourself\. For more information, see [Install a TLS certificate on and VMs on\-premises servers](troubleshooting-managed-instances.md#hybrid-tls-certificate)\.

**Topics**
+ [Launch an instance that uses the Systems Manager instance profile \(console\)](#setup-launch-managed-instance-new)
+ [Attach the Systems Manager instance profile to an existing instance \(console\)](#setup-launch-managed-instance-existing)

## Launch an instance that uses the Systems Manager instance profile \(console\)<a name="setup-launch-managed-instance-new"></a>

**To launch an instance that uses the Systems Manager instance profile \(console\)**

1. Open the Amazon EC2 console at [https://console\.aws\.amazon\.com/ec2/](https://console.aws.amazon.com/ec2/)\.

1. On the navigation bar at the top of the screen, select the AWS Region for the instance\.

1. Choose **Launch instance, Launch instance**\.

1. On the **Choose an Amazon Machine Image \(AMI\)** page, locate the AMI for the instance type you want to create, and then choose **Select**\.

1. Choose the type of instance to launch, such as **t2\.micro**, and then choose **Next: Configure Instance Details**\.

1. On the **Configure Instance Details** page, in the **IAM role** dropdown list, select the instance profile you created using the procedure in [Step 4: Create an IAM instance profile for Systems Manager](setup-instance-profile.md)\.

1. For other options on the page, make selections that meet your requirements for the instance\. For more information, choose one of the following, depending on your selected operating system type:
   + **Linux**: [Launch an instance using the Launch Instance Wizard](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/launching-instance.html) in the *Amazon EC2 User Guide for Linux Instances*
   + **Windows Server**: [Launch an instance using the Launch Instance Wizard](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/launching-instance.html) in the *Amazon EC2 User Guide for Windows Instances*

1. Complete the wizard\.

If you create other instances that you want to configure using Systems Manager, specify the instance profile for each instance\.

## Attach the Systems Manager instance profile to an existing instance \(console\)<a name="setup-launch-managed-instance-existing"></a>

1. Sign in to the AWS Management Console and open the Amazon EC2 console at [https://console\.aws\.amazon\.com/ec2/](https://console.aws.amazon.com/ec2/)\.

1. In the navigation pane, under **Instances**, choose **Instances**\.

1. Navigate to and choose your EC2 instance from the list\.

1. In the **Actions** menu, choose **Security**, **Modify IAM role**\.

1. For **IAM role**, select the instance profile you created using the procedure in [Step 4: Create an IAM instance profile for Systems Manager](setup-instance-profile.md)\.

1. Choose **Save**\.

For more information about attaching IAM roles to instances, choose one of the following, depending on your selected operating system type:
+ [Attach an IAM role to an instance](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/iam-roles-for-amazon-ec2.html#attach-iam-role) in the *Amazon EC2 User Guide for Linux Instances*
+ [Attach an IAM role to an instance](https://docs.aws.amazon.com/AWSEC2/latest/WindowsGuide/iam-roles-for-amazon-ec2.html#attach-iam-role) in the *Amazon EC2 User Guide for Windows Instances*

Continue to [Step 6: \(Optional\) Create a VPC endpoint](setup-create-vpc.md)\.