# Using roles to collect inventory, run maintenance window tasks, and view OpsData: `AWSServiceRoleForAmazonSSM`<a name="using-service-linked-roles-service-action-1"></a>

AWS Systems Manager uses AWS Identity and Access Management \(IAM\) [service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role)\. A service\-linked role is a unique type of IAM role that is linked directly to Systems Manager\. Service\-linked roles are predefined by Systems Manager and include all the permissions that the service requires to call other AWS services on your behalf\. 

A service\-linked role makes setting up Systems Manager easier because you don’t have to manually add the necessary permissions\. Systems Manager defines the permissions of its service\-linked roles, and unless defined otherwise, only Systems Manager can assume its roles\. The defined permissions include the trust policy and the permissions policy, and that permissions policy can't be attached to any other IAM entity\.

You can delete a service\-linked role only after first deleting their related resources\. This protects your Systems Manager resources because you can't inadvertently remove permission to access the resources\.

For information about other services that support service\-linked roles, see [AWS services that work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) and look for the services that have **Yes** in the **Service\-linked roles** column\. Choose a **Yes** with a link to view the service\-linked role documentation for that service\.

## Service\-linked role permissions for Systems Manager<a name="service-linked-role-permissions-service-action-1"></a>

Systems Manager uses the service\-linked role named `AWSServiceRoleForAmazonSSM` – AWS Systems Manager uses this IAM service role to manage AWS resources on your behalf\.

The `AWSServiceRoleForAmazonSSM` service\-linked role trusts only `ssm.amazonaws.com` to assume this role\. 

Three Systems Manager capabilities use the service\-linked role:
+ The Inventory capability requires a service\-linked role\. The role allows the system to collect Inventory metadata from tags and resource groups\.
+ Systems Manager Maintenance Windows can optionally use the service\-linked role\. The role allows the Maintenance Windows service to run maintenance tasks on target nodes\. The service\-linked role for Systems Manager doesn't provide the permissions needed for all scenarios\. For more information, see [Should I use a service\-linked role or a custom service role to run maintenance window tasks?](sysman-maintenance-permissions.md#maintenance-window-tasks-service-role)\.
+ The Explorer capability uses the service\-linked role to allow viewing OpsData and OpsItems from multiple accounts\. This service\-linked role also allows Explorer to create a managed rule when you allow Security Hub as a data source from Explorer or OpsCenter\.

The managed policy that is used to provide permissions for the `AWSServiceRoleForAmazonSSM` role is `AmazonSSMServiceRolePolicy`\. For details about the permissions it grants, see [AWS managed policy: AmazonSSMServiceRolePolicy](security-iam-awsmanpol.md#security-iam-awsmanpol-AmazonSSMServiceRolePolicy)\.

## Creating the `AWSServiceRoleForAmazonSSM` service\-linked role for Systems Manager<a name="create-service-linked-role-service-action-1"></a>

You can use the IAM console to create a service\-linked role with the **EC2** use case\. Using commands for IAM in the AWS Command Line Interface \(AWS CLI\) or using the IAM API, create a service\-linked role with the `ssm.amazonaws.com` service name\. For more information, see [Creating a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#create-service-linked-role) in the *IAM User Guide*\.

For maintenance windows only, you don't need to manually create a service\-linked role\. When you create a maintenance window task in the AWS Management Console, the AWS CLI, or the Systems Manager API, Systems Manager creates the service\-linked role for you if you choose not to provide a custom service role\.

If you delete this service\-linked role, and then need to create it again, you can use the same process to recreate the role in your account\. 

## Editing the `AWSServiceRoleForAmazonSSM` service\-linked role for Systems Manager<a name="edit-service-linked-role-service-action-1"></a>

Systems Manager doesn't allow you to edit the `AWSServiceRoleForAmazonSSM` service\-linked role\. After you create a service\-linked role, you can't change the name of the role because various entities might reference the role\. However, you can edit the description of the role using IAM\. For more information, see [Editing a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#edit-service-linked-role) in the *IAM User Guide*\.

## Deleting the `AWSServiceRoleForAmazonSSM` service\-linked role for Systems Manager<a name="delete-service-linked-role-service-action-1"></a>

If you no longer need to use any feature or service that requires a service\-linked role, then we recommend that you delete that role\. That way you don’t have an unused entity that isn't actively monitored or maintained\. You can use the IAM console, the AWS CLI, or the IAM API to manually delete the service\-linked role\. To do this, you must first manually clean up the resources for your service\-linked role, and then you can manually delete it\.

Because the `AWSServiceRoleForAmazonSSM` service\-linked role can be used by multiple capabilities, ensure that none are using the role before attempting to delete it\.
+ **Inventory:** If you delete the service\-linked role used by the Inventory capability, then the Inventory data for tags and Resource Groups will no longer be synchronized\. You must clean up the resources for your service\-linked role before you can manually delete it\.
+ **Maintenance Windows:** You can't delete the service\-linked role if any maintenance window tasks rely on the role\. You must first remove the service\-linked role from the tasks before you can delete the role\. 
+ **Explorer:** If you delete the service\-linked role used by the Explorer capability, then the cross\-account and cross\-Region OpsData and OpsItems are no longer viewable\. 

**Note**  
If the Systems Manager service is using the role when you try to delete tags, resource groups, or maintenance window tasks, then the deletion might fail\. If that happens, wait for a few minutes and try the operation again\.

**To delete Systems Manager resources used by the `AWSServiceRoleForAmazonSSM`**

1. To delete tags, see [Add and delete tags on an individual resource](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Using_Tags.html#adding-or-deleting-tags)\.

1. To delete resource groups, see [Delete groups from AWS Resource Groups](https://docs.aws.amazon.com/ARG/latest/userguide/deleting-resource-groups.html)\.

1. To delete maintenance window tasks, see [Updating or deregistering maintenance window tasks \(console\)](sysman-maintenance-update.md#sysman-maintenance-update-tasks)\.

**To manually delete the `AWSServiceRoleForAmazonSSM` service\-linked role using IAM**

Use the IAM console, the AWS CLI, or the IAM API to delete the `AWSServiceRoleForAmazonSSM` service\-linked role\. For more information, see [Deleting a service\-linked role](https://docs.aws.amazon.com/IAM/latest/UserGuide/using-service-linked-roles.html#delete-service-linked-role) in the *IAM User Guide*\.

## Supported Regions for the Systems Manager`AWSServiceRoleForAmazonSSM` service\-linked role<a name="slr-regions-service-action-1"></a>

Systems Manager supports using the `AWSServiceRoleForAmazonSSM` service\-linked role in all of the AWS Regions where the service is available\. For more information, see [AWS Systems Manager endpoints and quotas](https://docs.aws.amazon.com/general/latest/gr/ssm.html)\.