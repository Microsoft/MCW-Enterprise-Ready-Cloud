![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Enterprise-ready cloud
</div>

<div class="MCWHeader2">
Before the hands-on lab setup guide
</div>

<div class="MCWHeader3">
November 2018
</div>

Information in this document, including URL and other Internet Web site references, is subject to change without notice. Unless otherwise noted, the example companies, organizations, products, domain names, e-mail addresses, logos, people, places, and events depicted herein are fictitious, and no association with any real company, organization, product, domain name, e-mail address, logo, person, place or event is intended or should be inferred. Complying with all applicable copyright laws is the responsibility of the user. Without limiting the rights under copyright, no part of this document may be reproduced, stored in or introduced into a retrieval system, or transmitted in any form or by any means (electronic, mechanical, photocopying, recording, or otherwise), or for any purpose, without the express written permission of Microsoft Corporation.

Microsoft may have patents, patent applications, trademarks, copyrights, or other intellectual property rights covering subject matter in this document. Except as expressly provided in any written license agreement from Microsoft, the furnishing of this document does not give you any license to these patents, trademarks, copyrights, or other intellectual property.

The names of manufacturers, products, or URLs are provided for informational purposes only and Microsoft makes no representations and warranties, either expressed, implied, or statutory, regarding these manufacturers or the use of the products with any Microsoft technologies. The inclusion of a manufacturer or product does not imply endorsement of Microsoft of the manufacturer or product. Links may be provided to third party sites. Such sites are not under the control of Microsoft and Microsoft is not responsible for the contents of any linked site or any link contained in a linked site, or any changes or updates to such sites. Microsoft is not responsible for webcasting or any other form of transmission received from any linked site. Microsoft is providing these links to you only as a convenience, and the inclusion of any link does not imply endorsement of Microsoft of the site or the products contained therein.

© 2018 Microsoft Corporation. All rights reserved.

Microsoft and the trademarks listed at <https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/Usage/General.aspx> are trademarks of the Microsoft group of companies. All other trademarks are property of their respective owners.

**Contents**

<!-- TOC -->

- [Enterprise-ready cloud before the hands-on lab setup guide](#enterprise-ready-cloud-before-the-hands-on-lab-setup-guide)
    - [Requirements](#requirements)
    - [Before the hands-on lab](#before-the-hands-on-lab)
        - [Task 1: Validate global admin access to Azure AD tenant](#task-1-validate-global-admin-access-to-azure-ad-tenant)
        - [Task 2: Setup a development environment](#task-2-setup-a-development-environment)

<!-- /TOC -->

# Enterprise-ready cloud before the hands-on lab setup guide 

## Requirements

-   Local machine or a virtual machine configured with:
    -   Visual Studio 2015 or 2017 Community Edition or VS Code.
-   Full global admin access to the Azure AD tenant associated with your Azure subscription.

## Before the hands-on lab

Duration: 15 minutes

To complete this lab, you must have full global admin access to the Azure AD tenant associated with your Azure subscription.

### Task 1: Validate global admin access to Azure AD tenant

1.  Login to <http://portal.azure.com>, click on **All Services**, and type in **Azure Active Directory**.

2.  Open the Azure Active Directory tenant. Click Users -\> New User.

3.  Create a new user called testuser/test1. Use the tenant name on the header for the domain name of the email.

    ![Create user Azure portal blade with user name and email domain name highlighted.](images/Setup/image3.png "Create User blade")

>**Note:** If you can create the user, you will enough permissions in Azure AD to complete the lab. If you cannot, you will need more permissions before proceeding.

### Task 2: Setup a development environment

If you do not have a machine set up with Visual Studio, complete this task and use this VM to complete the remainder of the Lab.

1.  Create a DS2\_V2 Azure Virtual Machine using the Visual Studio Community 2017 image from the Azure Marketplace.

You should follow all steps provided *before* performing the Hands-on lab.
