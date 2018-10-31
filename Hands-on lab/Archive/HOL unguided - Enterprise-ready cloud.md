![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Enterprise-ready cloud
</div>

<div class="MCWHeader2">
Hands-on lab unguided
</div>

<div class="MCWHeader3">
September 2018
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Enterprise-ready cloud hands-on lab unguided](#enterprise-ready-cloud-hands-on-lab-unguided)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Overview](#overview)
    - [Solution architecture](#solution-architecture)
    - [Requirements](#requirements)
    - [Exercise 1: Create the policy for Enterprise IT](#exercise-1-create-the-policy-for-enterprise-it)
        - [Help references](#help-references)
        - [Task 1: Create a Management Group](#task-1-create-a-management-group)
            - [Tasks to complete](#tasks-to-complete)
            - [Exit criteria](#exit-criteria)
        - [Task 1: Create the service catalog policy](#task-1-create-the-service-catalog-policy)
            - [Tasks to complete](#tasks-to-complete-1)
            - [Exit criteria](#exit-criteria-1)
        - [Task 2: Restrict the creation of ExpressRoute circuits](#task-2-restrict-the-creation-of-expressroute-circuits)
            - [Tasks to complete](#tasks-to-complete-2)
            - [Exit criteria](#exit-criteria-2)
        - [Task 3: Restrict the creation of resources in regions](#task-3-restrict-the-creation-of-resources-in-regions)
            - [Tasks to complete](#tasks-to-complete-3)
            - [Exit criteria](#exit-criteria-3)
        - [Task 5: Create and apply a naming convention](#task-5-create-and-apply-a-naming-convention)
            - [Tasks to complete](#tasks-to-complete-4)
            - [Exit criteria](#exit-criteria-4)
        - [Task 6: Test the policies](#task-6-test-the-policies)
            - [Tasks to complete](#tasks-to-complete-5)
            - [Exit criteria](#exit-criteria-5)
    - [Exercise 2: Configure delegated permissions](#exercise-2-configure-delegated-permissions)
        - [Help references](#help-references-1)
        - [Task 1: Create user accounts in Azure AD](#task-1-create-user-accounts-in-azure-ad)
            - [Tasks to complete](#tasks-to-complete-6)
            - [Exit criteria](#exit-criteria-6)
        - [Task 2: Create groups in Azure AD for delegation](#task-2-create-groups-in-azure-ad-for-delegation)
            - [Tasks to complete](#tasks-to-complete-7)
            - [Exit criteria](#exit-criteria-7)
        - [Task 3: Configure delegated permissions](#task-3-configure-delegated-permissions)
            - [Tasks to complete](#tasks-to-complete-8)
            - [Exit criteria](#exit-criteria-8)
        - [Task 4: Enable project-based delegation and chargeback](#task-4-enable-project-based-delegation-and-chargeback)
            - [Tasks to complete](#tasks-to-complete-9)
            - [Exit criteria](#exit-criteria-9)
    - [Exercise 3: Create the environment for the e-commerce team](#exercise-3-create-the-environment-for-the-e-commerce-team)
        - [Help references](#help-references-2)
        - [Task 1: Create a new virtual network](#task-1-create-a-new-virtual-network)
            - [Tasks to complete](#tasks-to-complete-10)
            - [Exit criteria](#exit-criteria-10)
        - [Task 2: Configure secure VPN for connectivity](#task-2-configure-secure-vpn-for-connectivity)
            - [Tasks to complete](#tasks-to-complete-11)
            - [Exit criteria](#exit-criteria-11)
        - [Task 3: Create an Azure DevTest labs environment](#task-3-create-an-azure-devtest-labs-environment)
            - [Tasks to complete](#tasks-to-complete-12)
            - [Exit criteria](#exit-criteria-12)
        - [Task 4: Test access to the DevTest labs environment](#task-4-test-access-to-the-devtest-labs-environment)
            - [Tasks to complete](#tasks-to-complete-13)
            - [Exit criteria](#exit-criteria-13)
        - [Task 5: Finish configure secure connectivity](#task-5-finish-configure-secure-connectivity)
            - [Tasks to complete](#tasks-to-complete-14)
            - [Exit criteria](#exit-criteria-14)
    - [After the hands-on lab](#after-the-hands-on-lab)
        - [Task 1: Remove resources and configuration created during this lab](#task-1-remove-resources-and-configuration-created-during-this-lab)

<!-- /TOC -->

# Enterprise-ready cloud hands-on lab unguided

## Abstract and learning objectives 

In this hands-on lab, you are working with Trey Research to setup some best practices regarding policies, permissions, and remote access to their network.  Tasks include creating scripts that Enterprise IT will use to automatically set policy and delegate permissions when a new subscription is created. You will help them solve a critical problem for on-boarding new developers and controlling access to what they can access on the network.

At the end of this hands-on lab, you will know how to provide cost tracking by business unit, environment and project, provide for a distributed administration model, put a service catalog in place to prevent deployment of unsupported Azure services, and put controls in place to allow deployment of services only in specific regions.

## Overview

Trey Research is a manufacturing company that builds consumer products with 29.6 billion USD in annual revenue. Trey's headquarters are in New Jersey, but they have datacenters and branch offices scattered across the United States; with several major offices in the United Kingdom, France, and Japan.

Even as large as it is, Trey seeks to maximize the cost-effectiveness and flexibility of its IT, especially in new projects and business units. With a dizzying number of existing business units; each with their own unique requirements from IT and ballooning costs from internal hardware and datacenter investment, Trey is looking to the cloud.

Trey is interested in a large-scale solution that will help mitigate creeping costs and start the transition to a modern cloud-based enterprise architecture using a solid set of controls for governance.

## Solution architecture

![Hierarching showing Azure AD at the root, then a Management Group, then an Azure Subscription, then resource groups, then resources. It is tagged \'Policies and RBAC\'.](images/Hands-onlabunguided-Enterprise-readycloudimages/media/image2.png "Azure AD - Management Group - Subscription - Resource Group hierarchy")

## Requirements

-   Local machine or a virtual machine configured with:

    -   Visual Studio 2015 or 2017 Community Edition or VS Code

-   Full global admin access to the Azure AD tenant associated with your Azure subscription


## Exercise 1: Create the policy for Enterprise IT

Duration: 60 minutes

In this exercise, you will first create a Management Group for your Azure subscription(s). You will apply several of the built-in Azure Policy definitions to that Management Group to ensure that users stay within the scope of supported services for Enterprise IT. Finally, you will create a new policy initiative defining a multi-resource naming convention and apply that initiative to the Management Group.

### Help references

|    |            |
|----------|:-------------:|
| **Description** | **Links** |
| WAzure Policy  | <https://docs.microsoft.com/azure/azure-policy/azure-policy-introduction>|
| Azure Management Groups | <https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview>|

### Task 1: Create a Management Group

In this Task, you will create a new Management Group so that policies can be applied automatically to all subscriptions under that scope.

#### Tasks to complete

-   Create a new Management Group, and move a subscription into this Management Group.

>**Note**: We'll use our own Management Group, if you have permissions you could also use the Tenant Root Management Group.

#### Exit criteria

-   Management group created with at least one subscription within it.

### Task 1: Create the service catalog policy

In this exercise, you will use Azure Policy to restrict the type of resources that can be used within Trey Research.

#### Tasks to complete

-   Assign one of the built-in Azure policies to restrict resource types available in Trey Research to the following list. The policy should be applied at the Management Group scope.

  Resource Name
  --------------------------
  - Resource Group
  - Virtual Machines
  - Disk
  - Network Interface
  - Public IP Address
  - Network Security Group
  - Virtual Networks
  - Virtual Network Gateways
  - ExpressRoute Circuits
  - VPN Gateways
  - Storage Accounts
  - Backup Vault
  - Site Recovery Vault
  - DevTest Labs
  - Key Vault
  - Web Apps
  - SQL Database

#### Exit criteria 

-   Policy applied as described.

### Task 2: Restrict the creation of ExpressRoute circuits

In this exercise, use Azure policy to restrict the creation of an ExpressRoute circuit, except as required by Enterprise IT

#### Tasks to complete

-   Apply an existing Azure Policy to prevent the creation of ExpressRoute circuits. The policy should be applied at the Management Group scope. Use an Exception Path to define a resource group that Enterprise IT can use for their permitted ExpressRoute circuits.

#### Exit criteria 

-   Policy applied as described.

### Task 3: Restrict the creation of resources in regions

In this exercise, use Azure Policy to restrict which regions resources can be created in.

#### Tasks to complete

-   Assign one of the built-in Azure Policies to restrict resource creation to the following regions:

    -   Primary: East United States, Failover: West United States

    -   Primary: West Europe, Failover: North Europe

    -   Primary: Japan West, Failover: Japan East

-   The policy should be applied at Management Group scope.

#### Exit criteria 

-   Policy applied as described.

### Task 5: Create and apply a naming convention

In this task, we will define a simple naming convention for Azure resources. We shall simply require that virtual machine names end with '-vm', virtual networks end with '-vnet' and so on across the various resource types. We shall implement this naming convention using the custom policy definition and policy initiative assigned at the management group scope.

#### Tasks to complete

-   Create a generic policy definition that restricts resources of a given type to have a given name suffix. The resource type and name suffix shall be specified using parameters.

-   Create a policy initiative that defines the naming convention. The policy initiative should use multiple instances of the above policy definition, each with different values for the resource type and name suffix.

-   Apply the policy initiative at Management Group scope.

#### Exit criteria

-   Policy initiative deployed, restricting all permitted resources to have a type-specific resource name suffix.

### Task 6: Test the policies

In this task, you will use the Azure management portal to validate the policies work and understand how to identify policy events.

#### Tasks to complete

-   Attempt to create ARM resources in violation of each policy you have created. Observe the error messages.

-   Create ARM resources that are compliant with each policy you have created.

#### Exit criteria 

-   You should not be able to create resources of a type not permitted by the Service Catalog policy.

-   You should not be able to create ExpressRoute circuits, except in the exception path scope defined for Enterprise IT.

-   You should not be able to create resources in any regions other than those permitted.

-   You should not be able to create resources that do not conform to the naming convention.

-   You **can** create resources as long as the type, location, and resource name do not infringe the respective policies.

## Exercise 2: Configure delegated permissions

Duration: 60 minutes

In this exercise, you will configure delegated permissions for users in the Trey Research business unit. You will extend a PowerShell script to automatically provision a limited access user with the configuration of the subscription.

### Help references

|    |            |
|----------|:-------------:|
| Add new users to Active Directory | <https://docs.microsoft.com/azure/active-directory/add-users-azure-active-directory> |
| How Subscriptions are associated with Azure AD | <https://docs.microsoft.com/azure/active-directory/active-directory-how-subscriptions-associated-directory> |
| Managing Azure AD Security Groups | <https://docs.microsoft.com/azure/active-directory/active-directory-groups-create-azure-portal> |
| Role Based Access Control  | <https://docs.microsoft.com/azure/active-directory/role-based-access-control-configure> |
| Manage RBAC with PowerShell | <https://docs.microsoft.com/azure/active-directory/role-based-access-control-manage-access-powershell> |


### Task 1: Create user accounts in Azure AD 

In this task, you will create two user accounts in Azure AD that you will use for testing delegated access control.

#### Tasks to complete

-   Within Azure AD create two users:

    -   ElectronicsAdmin@\[your tenant name\].onmicrosoft.com

    -   ElectronicsUser@\[your tenant name\].onmicrosoft.com

#### Exit criteria 

-   Two users that will be used to test delegated permissions using role based access control (RBAC).

### Task 2: Create groups in Azure AD for delegation 

In this task, you will create two groups in Azure AD that you will use for testing delegated access control. You will add the users created in the previous task to the groups.

#### Tasks to complete

-   Within Azure AD create two groups:

    -   BU-Electronics-Admin-- add the ElectronicsAdmin user to the group

    -   BU-Electronics-Users -- add the ElectronicsUser user to this group

#### Exit criteria 

-   Two groups with users that will be used to test delegated permissions using role based access control (RBAC).

### Task 3: Configure delegated permissions 

In this task, you will create a PowerShell script to add a user to the contributor role of the subscription automatically.

#### Tasks to complete

-   Create a new script ConfigureSubscription.ps1 that accepts an Azure AD Group and subscription ID and adds to the group to the subscription with the contributor role.

-   Use the modified script (not the portal) to add the BU-Electronics-Admin group to your subscription in the contributor role.

#### Exit criteria 

-   A modified script that will add the BU-Electronics-Admin group to the contributor role automatically.

-   Run the script, and verify the group assignment via the Azure portal.

### Task 4: Enable project-based delegation and chargeback

In this task, you will create a script that will create a new resource group, assign 'Owner' rights over the resource group to a given AD group, and then apply a policy to enforce an 'IOCode' tag with a given value.

#### Tasks to complete

-   Create a new PowerShell script called CreateProjectResourceGroup.ps1 that will create a new resource group with the following settings applied:

    -   Accepts an Azure AD Group Name as a parameter that will be assigned to the owner role of the new resource group.

    -   Accepts a project IO code value (for example 1000150) and uses a built-in Azure policy to add the IOCode tag to all resources created within the resource group.

-   Using the new script, create a new resource group called DelegatedProjectDemo that has the BU-Electronics-Admin group added to the subscription in the owner role, has the policy applied, and has the IOCode policy applied with the ioCode parameter set to 1000150.

-   Create a new storage account within the resource group and validate the new tag is applied.

#### Exit criteria 

-   A reusable script that will accept the subscription ID, an IOCode value, and the group to add as parameters. When the script is executed, it should create the resource group, automatically add the group to the owner role, and apply the Azure Policy to add the IOCode tag to all resources with a specified value.

## Exercise 3: Create the environment for the e-commerce team

Duration: 75 minutes

In this exercise, you will configure a new environment for the developers of the e-commerce team. You will configure access to a subnet where other developer resources are available and provide secure access to the network for the developers.

### Help references

|    |            |
|----------|:-------------:|
| Configuring Point-to-Site Secure VPN  | <https://azure.microsoft.com/en-us/documentation/articles/vpn-gateway-howto-point-to-site-rm-ps/>|
| Network Security Groups | <https://azure.microsoft.com/en-us/documentation/articles/virtual-networks-nsg/> |
| Azure DevTest Labs    | <https://azure.microsoft.com/en-us/documentation/services/devtest-lab/> |
| MakeCert.exe |  <https://cloudworkshop.blob.core.windows.net/enterprise-ready-cloud/makecert.exe> |


### Task 1: Create a new virtual network

In this task, you will create a new virtual network for Trey Research.

#### Tasks to complete

-   Create a new virtual network with the following properties:

    -   Name: TreyResearchVNET

    -   Address Space: 10.10.0.0/16

    -   Subnet Name: Apps

    -   Subnet address Range: 10.10.0.0/24

    -   Resource Group: TreyResearchRG

-   Add an additional subnet to the virtual network:

    -   Name: ECommerce

    -   Address Space: 10.10.1.0/24

-   Add a gateway subnet.

#### Exit criteria 

-   A virtual network named TreyResearchVNET with the correct settings noted above.

### Task 2: Configure secure VPN for connectivity

In this task, you will start provisioning of a VPN gateway that will be used for secure connectivity for Trey Research.

#### Tasks to complete

-   Configure a dynamic VPN gateway on the virtual network that will allow individual developers to connect securely and access virtual machines by their private IP address.

#### Exit criteria 

-   A VPN gateway (dynamic) in the provisioning state.

### Task 3: Create an Azure DevTest labs environment 

In this task, you will create and configure a new development environment for Trey Research developers and contingent staff.

#### Tasks to complete

-   Create an environment that developers can use to provision and access virtual machines.

#### Exit criteria 

-   The environment should only allow virtual machines to deploy to the ECommerceDev subnet.

-   Virtual machines should not be allowed to be deployed on any subnet other than ECommerceDev.

-   The only virtual machines that can be provisioned are Standard\_DS2.

-   Each user of the environment should only be able to deploy one VM.

-   The BU-Electronics-Admin group should be allowed to grant access to the environment to other users.

### Task 4: Test access to the DevTest labs environment 

In this task, you will use the ElectronicsAdmin user account to grant access to the developer environment, and then validate as a user whether access was successfully granted.

#### Tasks to complete

-   Login as the ElectronicsAdmin user and grant access to the environment to the ElectronicsUser user.

-   Login as the ElectronicsUser user and provision a virtual machine that has Azure PowerShell and Fiddler 4 installed at provision time.

#### Exit criteria 

-   The ElectronicsUser account should only be allowed to use the environment you assigned permissions to (nothing further).

-   The exit criteria put in place in Task 4 should apply to this user.

### Task 5: Finish configure secure connectivity

In this task, you will configure certificates for the VPN gateway and the end users, and complete configuration of the VPN gateway. You will then configure and test access to the development environment.

#### Tasks to complete

-   Complete the configuration of the secure VPN solution.

-   Provision a certificate that can be used to authenticate a client to the VPN solution.

-   Connect to the virtual network using the VPN solution.

-   Sign in to the Azure Management Portal using the ElectronicsUser user and connect to the previously created virtual machine using its private IP address.

#### Exit criteria 

-   The ElectronicsUser user should be able to login to the portal, find his or her virtual machine, select **Connect** and successfully connect to its private IP address (no public IPs allowed).

## After the hands-on lab 

Duration: 10 minutes

After the hands-on lab, you will remove the policies on your subscription.

### Task 1: Remove resources and configuration created during this lab

1.  Log in to the Azure portal.

2.  Navigate to the **Policy** blade.

3.  Select **Assignments** and delete all policy assignments created during this lab.

4.  Select **Definitions** and delete any policy definitions or initiative definitions created during this lab.

5.  Navigate to the **Management Groups** blade.

6.  Remove any Management Groups crated during this lab.

7.  Navigate to the **Resource Groups** blade.

8.  Remove any resource groups created during this lab. This will also delete any resources in those resource groups.

9.  Navigate to the **Azure Active Directory** blade.

10. Remove any users and groups created during this lab.

You should follow all steps provided *after* attending the hands-on lab.
