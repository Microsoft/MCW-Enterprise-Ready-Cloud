![](https://github.com/Microsoft/MCW-Template-Cloud-Workshop/raw/master/Media/ms-cloud-workshop.png "Microsoft Cloud Workshops")

<div class="MCWHeader1">
Enterprise-ready cloud
</div>

<div class="MCWHeader2">
Whiteboard design session student guide
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

- [Enterprise-ready cloud whiteboard design session student guide](#enterprise-ready-cloud-whiteboard-design-session-student-guide)
    - [Abstract and learning objectives](#abstract-and-learning-objectives)
    - [Step 1: Review the customer case study](#step-1-review-the-customer-case-study)
        - [Customer situation](#customer-situation)
        - [Customer needs](#customer-needs)
        - [Customer objections](#customer-objections)
        - [Infographic for common scenarios](#infographic-for-common-scenarios)
    - [Step 2: Design a proof of concept solution](#step-2-design-a-proof-of-concept-solution)
    - [Step 3: Present the solution](#step-3-present-the-solution)
    - [Wrap-up](#wrap-up)
    - [Additional references](#additional-references)

<!-- /TOC -->
#  Enterprise-ready cloud whiteboard design session student guide

## Abstract and learning objectives 

In this whiteboard design session, you will work in a group to design a comprehensive solution to address concerns about security, charge back, tagging and other areas to help apply an enterprise governance model for Trey Research.

At the end of this whiteboard design session, you will be better able to design a governance plan to showcase the security and governance features of Azure and control costs. In addition, you'll learn how to provide for cost tracking by business unit, environment, and project, provide for a distributed administration model, put a service catalog in place to prevent deployment of unsupported Azure services, and put controls in place to allow deployment of services only in specific regions.

## Step 1: Review the customer case study 

**Outcome**

Analyze your customer's needs.

Timeframe: 15 minutes

Directions: With all participants in the session, the facilitator/SME presents an overview of the customer case study along with technical tips.

1.  Meet your table participants and trainer.

2.  Read all of the directions for steps 1-3 in the student guide.

3.  As a table team, review the following customer case study.

### Customer situation

Trey Research is a manufacturing company that builds consumer products with 29.6 billion USD in annual revenue. Trey's headquarters are in New Jersey, but they have data centers and branch offices scattered across the United States with several major offices in the United Kingdom, France, and Japan.

Even as large as it is, Trey seeks to maximize the cost-effectiveness and flexibility of its IT, especially in new projects and business units. With a dizzying number of existing business units, each with its own unique requirements from IT and ballooning costs from internal hardware and data center investment, Trey is looking to the cloud.

Trey is interested in a large-scale solution that will help mitigate creeping costs and start the transition to a modern cloud-based enterprise architecture.

Trey's technical leadership has decided to move forward with a Microsoft enterprise agreement (EA) with a heavy commitment in Microsoft Azure. Ken Greenwald, Trey Research's CTO, is aware of the potential for the cloud, but also has a keen understanding that without strong architectural guidance, Trey may end up with a sub-optimal deployment that is difficult to support. These incorrect practices can then be disbursed across the enterprise. Ken wants to start on the right foot by focusing on best practices from the start.

To kick off planning for integrating Azure into their environment, Ken introduced you to several directors within Trey's Enterprise IT group that have been part of the initial Azure planning process.

Enterprise IT is responsible for managing corporate network connectivity, datacenter distribution, capacity planning, identity, and enterprise wide SaaS services for Trey Research employees. Enterprise IT is also responsible for supporting the services, datacenters, and setting auditing policy on hardware and services.

*Subscription organization and chargeback*

This table is a partial view of Trey Research's organization. Each rectangle represents a business unit and subunits within the business unit. Each of which has IT resources with an assigned budget/quota that will be able to consume Azure for related IT services.

![Trey Research has three business units: Industrial and Consumer, Electronics, and Life Sciences. Each of the Business Units has the same subunits: Product development, Marketing, and Sales and Support. Sales and Suppoort also has its own sub-unit, Regional (US/EU/Asia). ](images/Whiteboarddesignsessiontrainerguide-Enterprise-readycloudimages/media/image2.png "Trey Research organizational flowchart")

Enterprise IT will be responsible for providing access to Azure for users in each individual business unit and tracking their Azure usage costs at the department and subscription level by the business unit's cost center.

Within a business unit, each new project should track its consumption using a specific tag for its IO code within the business unit.

Each business unit has a requirement to break down their costs into multiple categories so business managers in finance can analyze spending patterns:

-   Development and Test

-   Production

-   Support Services

-   Infrastructure

Business units and the finance department need a cost management dashboard to more easily identify current cost and anomalous spending to better manage their Azure spend.

*Supported services and delegated access control*

With a company the size of Trey Research, providing the ability to delegate permissions to different administrators at the business unit level is critical. At this point, Trey Research has deployed Office 365 and it is configured with federated access to their ADFS servers. Trey's EA has been created within the same organization.

Each business unit and sub-business unit has their own unique IT needs. IT has identified a list of services within Azure that they are willing to support and are interested in options for controlling access to unsupported services throughout the organization:

-   Virtual machines

-   ExpressRoute

    -   The ExpressRoute circuit(s) will be created and managed by IT. IT wants to ensure that sub-business units are able to use the circuits, but not create new ones or change the existing circuits:

-   VPN gateways

-   Storage

-   Virtual networks

-   Backup

-   Site recovery

-   DevTest labs

-   Web Apps

-   SQL Database

For each new project, a user in the business unit should be allowed to have rights for managing his or her team by having the ability to add or remove users and allow them to create resources in the subscription.

*Connectivity*

At a high level, Trey Research is connected globally using an existing MPLS wide area network. There are several smaller offices that are connected via site-to-site VPN.

![An MPLS WAN cloud is in the center, and five bi-directional arrows point to the following location icons: New Jersey (HQ), Branch Office, Japan, UK, and France. ](images/Whiteboarddesignsessiontrainerguide-Enterprise-readycloudimages/media/image3.png "Trey Research Connectivity diagram")

Enterprise IT understands that ExpressRoute is likely going to be the correct connectivity solution. However, they are unsure what they need to consider from a security perspective or for availability. Typically, they protect their perimeter network with firewalls. Is that needed with ExpressRoute and if so, what would they need to do to implement it? How does ExpressRoute implement redundancy? What should they be looking for when they talk to an ExpressRoute partner? Finally, for the sites that are not part of the WAN, how would they connect to resources in Azure?

*Availability*

There are several Internet and intranet-facing web-based workloads that are considered critical to the business. These workloads typically use SQL Server and several use MySQL. With that in mind, Trey Research is recommending to business units to design those applications by deploying across multiple regions, or if that type of architecture is not feasible, to fail-back to on-premises in the event of a failure.

This is a list of primary and secondary regions IT will support for these scenarios:

-   Primary: East United States, Fail over: South Central United States

-   Primary: West Europe, Fail over: North Europe

-   Primary: Japan West, Fail over Japan East

Trey Research would like to know if this list makes sense, if there is any guidance from Microsoft on building geo-redundant solutions across multiple data centers, and what other factors they should consider.

*Security and accident protection*

If a service has an outage, it is important to know the chain of events that led up to the outage and who (if anyone) caused it. Additionally, Trey wants to ensure that production workloads cannot be accidently deleted by administrators getting confused over a test workload versus production. Trey Research are also concerned about how to ensure their VMs meet Azure security best practices and would like to ensure Production workloads are protected even in the event their security perimeter is compromised.

*E-commerce developer team*

The e-commerce team is owned by the Enterprise IT team and is responsible for building and maintaining the corporate website where consumers and channel partners can order products directly from Trey Research. The e-commerce site and order fulfillment system are currently hosted on Apache and Red Hat Enterprise Linux.

This team has a significant percentage of developers that are contingent staff. Often these contingent staff members will come onboard for a short term to implement a new feature that the core team does not have the skills or resources to tackle. Currently, the e-commerce team is bringing resources onsite for this work, due to not having a secure remote access solution. Providing hardware resources and access to the development environment is a challenge due to the constant turnover of contingent staff. The time needed to provide an environment is disproportionally long relative to the amount of time the developer is there. This is because each developer must provision a set of services.

### Customer needs 

1.  Provide access to create and manage new workloads in Azure for various business units.

2.  Identify connectivity requirements with ExpressRoute access control and availability.

3.  Implement a charge back for the business units for resources they consume, while allowing each business unit to monitor their own usage.

4.  Apply governance to business units to control what can be created.

5.  Implement delegated access control for new projects within business unit subscriptions.

6.  Implement a common resource naming standard across the organization.

7.  The above governance controls must be implemented with minimum per-subscription configuration overhead, and compliance with these controls must be auditable to detect any out-of-compliance usage.

8.  Identify a top-level strategy for building geo-redundant solutions.

9.  Identify how Trey Research can track changes to the Azure-based deployments and prevent accidental deletion of resources.

10. Identify a solution of providing remote access to e-commerce team contingent staff.

11. Increase agility to speed up the on-boarding of resources to make the e-commerce team contingent staff productive more quickly.

12. Ensure full-time and contingent staff for e-commerce have access to what they need, but no more.

### Customer objections 

1.  We need the ability to split our Azure bill by business unit and even workload classification. Can Azure support this requirement? How can we analyze our bill for cost optimization and charge back?

2.  As well as implementing our governance rules on how Azure is used, we need a way to audit that no deployments have been made that bypass those roles

3.  Security is important to us. We have evaluated Network Security Groups and our security team does not feel they offer the same level of security that we enjoy with our on-premises firewall-based solutions (examples: intrusion and malware detection).

4.  Delegating control to business units is incredibly important to Trey Research. At our scale, a single team cannot possibly manage all the needs of the business. Corporate IT requires the ability to set policy at the enterprise level and still needs a detailed level of control. How can Azure address these needs?

5.  Trey Research currently monitors their on-premises workloads using SCOM. A small business unit experimented with running virtual machines in AWS and the monitoring team was not thrilled with a completely different system for monitoring for availability. Does Azure have the same problem?

6.  How can we ensure our deployments meet Azure security best practices, and how can we protect our Production workloads even if the security perimeter is compromised?

7.  How can Azure help control the costs associated with non-Production VMs left running out-of-hours?

### Infographic for common scenarios

![This is a screenshot of a slide. Azure EA Portal has the following bulleted list items: Manage access to Azure EA enrollments; Organize and delegate access to subscriptions; View usage; and http://ea.azure.com. A subscription flowchart on the right starts at the top with Enterprise Enrollment, then flows down to Department, Account, and Subscriptions.](images/Whiteboarddesignsessiontrainerguide-Enterprise-readycloudimages/media/image4.png "Azure EA Portal")

![This is a screenshot of a slide. Azure Cost Management has the following bulleted list items: Understand where costs originate; Delegated access to reports and usage. There are two screenshots on the right - one of a daily spend chart and another that displays a full view pivot chart grouped by resource group.](images/Whiteboarddesignsessionstudentguide-Enterprise-readycloudimages/media/image8.png "Azure Cost Management")

![This is a screenshot of a slide. Role-based access control (RBAC) and ARM Policies has two bullets: Governance of Azure Resources, and Granular Access Control. This slide also has an illustration of access control, which is separated into two sides by an arrow labeled Access Inheritance. On the left side are subscription, resource groups, and resources. On the right are three sets each of Contributors, Owner, and Readers.](images/Whiteboarddesignsessiontrainerguide-Enterprise-readycloudimages/media/image5.png "Role-based access control (RBAC) and RM Policies")

![This is a screenshot of a slide, titled Common scenarios - infrastructure as a service. This slide has: a Virtual Machines overview; Virtual Networks Overview; Site-to-Site Connections information; Point-to-Site Connections Information; Virtual Network Example VNET; and a Virtual Network diagram. At this time, we are unable to capture all of the information in the slide. Future versions of this course should address this.](images/Whiteboarddesignsessiontrainerguide-Enterprise-readycloudimages/media/image6.png "Common scenarios - infrastructure as a service")

![ExpressRoute Deployment Options include Cloud Exchange Co-location, Point-to-point Ethernet Connection, and Any-to-any (IPVPN) Connection.](images/Whiteboarddesignsessiontrainerguide-Enterprise-readycloudimages/media/image7.png "ExpressRoute Deployment Options")

## Step 2: Design a proof of concept solution

**Outcome**

Design a solution and prepare to present the solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 60 minutes

**Business needs**

Directions:  With all participants at your table, answer the following questions and list the answers on a flip chart:

1.  Who should you present this solution to? Who is your target customer audience? Who are the decision makers?

2.  What customer business needs do you need to address with your solution?

**Design**

Directions: With all participants at your table, respond to the following questions on a flip chart:

*Subscription organization and charge back*

1.  Diagram how you would suggest organizing the Azure EA portal for Trey Research to allow access to Azure.

2.  How can Enterprise IT assign a spending quota to each business unit and monitor spending for each business unit's cost center? What happens if the business unit exceeds their assigned quota?

3.  How can individual business units monitor their Azure spending?

4.  Within a business unit, costs for each project should be tracked independently based on the IO code for that specific project. How can per project tracking be implemented? How would you implement cost management reporting and alerting?

5.  How can Enterprise IT enforce a company-wide resource naming convention?

6.  How can Enterprise IT minimize per-subscription configuration and centrally audit compliance with their governance rules?

7.  How can Azure help Business Units minimize wasted spend on non-Production VMs left running out-of-hours?

*Supported services and delegated access control*

1.  Identify a solution to restrict which services can be created and used in each business unit subscription. Diagram specifically how your solution would be put into place and perform a requirements analysis to determine if there are services needed that Trey Research has not added to their initial list. This solution should allow access to the following services by default, but not others:

    -   Virtual machines

    -   ExpressRoute

        -   The ExpressRoute circuit(s) will be created and managed by IT, however IT wants to ensure that business units are able to use the circuits, but not create new ones or change the existing circuits.

    -   VPN gateways

    -   Storage

    -   Virtual networks

    -   Backup

    -   Site recovery

    -   DevTest labs

    -   Log analytics

    -   Web Apps

    -   SQL Database

2.  One or more users from the business unit must have the permissions to create resources in the subscription and view all resources. The user should not have the ability to change policies set by Enterprise IT.

3.  How would you assign permission to users and groups?

4.  Could we allow users from partner organizations to access corporate applications?

5.  Is there another way to limit access to services in Azure using templates?

6.  For each project in Azure, the business unit administrator must have permissions to add or remove users, allow them to create resources, or even apply additional policies for resources in that project. Diagram at a high level how this would be achieved and provide some pseudo code that would be needed to accomplish the task.

*Connectivity*

1.  Diagram at a high level how an ExpressRoute deployment for Trey Research should be configured for high availability.

2.  Walk through the steps that Trey Research would have to perform to enable other subscriptions to use ExpressRoute.

3.  From the security perspective, how could Trey Research deploy firewalls to protect their network after ExpressRoute is deployed? What network features are required and where would the firewalls be deployed? Diagram your solution.

4.  For branch office sites that do not connect back to the WAN, how could they connect to Azure? Could Azure also be used to route traffic to different on-premises sites instead of their current site-to-site connections?

*Availability*

1.  Evaluate the list of proposed regions and provide guidance on what policies are in place by Microsoft to help customers design a geo-redundant solution.

2.  Explain how Trey Research could restrict services to just the supported regions.

3.  Diagram at a high level what a geo-redundant solution would look like for a public facing web application with a backend that uses SQL Server. What about a private facing web application?

4.  For workloads within the same region, how could they ensure their virtual machines are available in the event of a physical server failure or a host update?

*Security and accident protection*

1.  What would you recommend to Trey Research on how to mitigate accidently deleting production workloads? If that were to happen, what would the proper procedure be to identify who deleted the resource?

2.  How can we ensure our deployments meet Azure security best practices, and how can we protect our Production workloads even in the event that the security perimeter is compromised?

*E-commerce developer team*

1.  Identify a solution to provide access to a development environment that would be suitable for contingent staff for the e-commerce team:

   -   What steps are needed to allow access to the environment?

   -   What would be needed to automate the environment to speed up on-boarding?

   -   What options could you propose to allow access for remote employees? Specifically, how could they access resources on the ECommerceDev network but nothing else on the Azure network?
   
2.  What cost control options would you propose to put in place to optimize this environment?

**Prepare**

Directions: With all participants at your table:

1.  Identify any customer needs that are not addressed with the proposed solution.

2.  Identify the benefits of your solution.

3.  Determine how you will respond to the customer's objections.

Prepare a 15-minute chalk-talk style presentation to the customer.

## Step 3: Present the solution

**Outcome**

Present a solution to the target customer audience in a 15-minute chalk-talk format.

Timeframe: 30 minutes

**Presentation**

Directions:

1.  Pair with another table.

2.  One table is the Microsoft team and the other table is the customer.

3.  The Microsoft team presents their proposed solution to the customer.

4.  The customer makes one of the objections from the list of objections.

5.  The Microsoft team responds to the objection.

6.  The customer team gives feedback to the Microsoft team.

7.  Tables switch roles and repeat Steps 2-6.

##  Wrap-up 

Timeframe: 15 minutes

Directions: Tables reconvene with the larger group to hear the facilitator/SME share the preferred solution for the case study.

##  Additional references

|    |            |
|----------|:-------------:|
|Videos on the Azure EA Portal | <https://channel9.msdn.com/blogs/EA.Azure.com>|
|EA Portal Roles  |  <http://www.redbaronofazure.com/?cat=111>|
|Azure Policy| <https://docs.microsoft.com/azure/azure-policy/azure-policy-introduction>|
|Azure Policy Initiatives | https://docs.microsoft.com/azure/azure-policy/azure-policy-introduction\#initiative-definition|
|Role Based Access Control Configuration|<https://docs.microsoft.com/azure/active-directory/role-based-access-control-configure>|
|Built in Roles for RBAC  | <https://docs.microsoft.com/azure/active-directory/role-based-access-built-in-roles>|
|Custom Roles for RBAC| <https://docs.microsoft.com/en-us/azure/role-based-access-control/custom-roles>|
|Management Groups   |<https://docs.microsoft.com/azure/azure-resource-manager/management-groups-overview>|
|Virtual Networks User Defined Routes  | <https://docs.microsoft.com/azure/virtual-network/virtual-networks-udr-overview>|
|Azure Traffic Manager  | <https://docs.microsoft.com/azure/traffic-manager/>|
|ExpressRoute FAQ   | <https://azure.microsoft.com/en-us/documentation/articles/expressroute-faqshttps://docs.microsoft.com/azure/expressroute/expressroute-faqs>](https://docs.microsoft.com/azure/expressroute/expressroute-faqs)|
|SQL Server in Azure Virtual Machines with High Availability  | https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sql-high-availability-dr?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json|
|Azure Active Directory B2B collaboration | <https://docs.microsoft.com/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b>|
|Azure Cost Management by Cloudyn | <https://docs.microsoft.com/en-us/azure/cost-management/overview>|
|Azure Security Center | <https://docs.microsoft.com/azure/security-center/security-center-intro>|
|Auto-shutdown of VMs   |<https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.StartStopVMSolution?tab=Overview>|
