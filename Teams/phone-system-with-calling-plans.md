---
title: Phone System with Calling Plans in Microsoft Teams
author: LolaJacobsen

ms.author: arachman
manager: lolaj
ms.date: 12/07/2017
ms.topic: article

ms.prod: teams
description: Practical guidance for deploying Phone System with Calling Plans in Microsoft Teams.
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Phone System with Calling Plans in Microsoft Teams
===================================================

> [!IMPORTANT]

> Office 365 Phone System with Calling Plans in Teams is in public preview. It is available to all customers who have an Office 365 subscription that includes Teams. Phone System with Calling Plans features and capabilities in Teams could change as additional features and capabilities are released.

Phone System is an Office 365 feature that provides the ability to manage call routing, policies, and user provisioning. This includes phone calling management system, call routing, and call control.

Office 365 Calling Plans is an add-on service for the Phone System feature, delivered through Teams and Skype for Business Online. Calling Plans provides the people in your business with a primary phone number and lets them make and receive phone calls outside of your organization over the public switched telephone network (PSTN).

To learn more, read [Here's what you get with Phone System in Office 365](https://support.office.com/article/Here-s-what-you-get-with-Phone-System-in-Office-365-bc9756d1-8a2f-42c4-98f6-afb17c29231c) and [What are Calling Plans in Office 365?](https://support.office.com/article/What-are-Calling-Plans-in-Office-365-3dc773b9-95e0-4448-b2f1-887c54022429)

> [!NOTE]
> Calling Plans supports both Teams and Skype for Business Online. To manage Calling Plans, use the Skype for Business Admin center and remote PowerShell commands.


Envision <a name="Envision_PhoneSystemWithCallingPlans"> </a>
========

The Envision phase provides the foundation for the Office 365 customer journey and is applicable to all workloads such as Phone System with Calling Plans.

In this phase, business goals are captured, with relevant project stakeholders assembled, to ultimately deliver:


-   A high-level success plan that contains business use cases, key stakeholders, objectives and key results (OKRs), key success indicators (KSIs), risks, environmental assessment, adoption readiness, and operational plan.

-   A detailed Phone System with Calling Plans technical implementation plan to achieve the desired end state.



Define business use cases for Phone System with Calling Plans
-------------------------------------------------------------



Phone System with Calling Plans allows organizations to modernize their workplace by enabling users to make business-related phone calls from their computers and mobile devices.


Workplace modernization can be part of activity-based working implementation, office moves, office fit-out refresh, retirement of legacy private branch exchange (PBX) solutions, conclusion of a PSTN service provider contract, etc.

In this step, core project stakeholders will define business use cases that support the implementation of Phone System with Calling Plans.

Business use cases are meant to document expected, measurable business outcomes, and include the following:



-   Description of current business process

-   Challenges with existing business process defined

-   How technology can help overcome these challenges

-   The expected, measurable business outcomes if these challenges are overcome


<table>
<tbody>
<tr class="header">
<th align="left"><p><img src="media/audio_conferencing_image2.png" /></p></th>
<td align="left"><p><strong>Description of current business process</strong></p>


<p>Standard configuration of Contoso’s office workspaces includes a desktop phone for every desk. Each employee will be provided with a direct inward dialing (DID) phone number. The desktop phones are connected to a PBX system and connected to PSTN via session initiation protocol (SIP) trunk. Employees can only make and receive phone calls at their assigned desktop phones. </p></td>

</tr>
<tr class="odd">
<td align="left"><p><img src="media/audio_conferencing_image3.png" /></p></td>
<td align="left"><p><strong>Challenges with existing business process</strong></p>
<p>Usage analysis of the desktop phones shows that only 10% of the desktop phones are actively used, with the rest either configured to forward calls to mobile phones, or configured to simultaneously ring to mobile phones. Maintenance of existing PBX system and the associated desktop phones contributes to 20% of monthly telephony service cost.</p></td>
</tr>
<tr class="even">
<td align="left"><p><img src="media/audio_conferencing_image4.png" /></p></td>
<td align="left"><p><strong>How technology can overcome these challenges</strong></p>


<p>Phone System with Calling Plans will allow end user’s personal computer to receive and place phone calls over data network by leveraging the native Microsoft Teams app, removing the necessity to roll out and maintain desktop phones, and opens the opportunity to decommission the existing PBX system, as the phone service can be delivered via the cloud over the network with no dependency on traditional phone system.</p></td>

</tr>
<tr class="odd">
<td align="left"><p><img src="media/audio_conferencing_image5.png" /></p></td>
<td align="left"><p><strong>Expected, measurable, business outcomes</strong></p>
<p>Removing requirements to maintain and decommissioning existing legacy PBX and desktop phones, will deliver a 20% reduction of monthly telephony service expense. Phone System with Calling Plans will simplify office workspaces, allowing Contoso to expand its operations by establishing new offices with minimal upfront telephony costs. </p></td>
</tr>
</tbody>
</table>

_Table 1 Business use case example_



In addition to defining your business use cases, you should also get clarity around organizational scope and project timelines as you move into the next step of the Envision phase.


Identify key stakeholders
-------------------------

The business use cases defined in the previous step will include organizational scope of Phone System with Calling Plans implementation, and based on that, the comprehensive stakeholder matrix can be completed to include the right people to be involved in the project.

<table>
<thead>
<tr class="header">
<th align="left">Role</th>
<th align="left">Description</th>
<th align="left">Name, contact information, location</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>Project Executive Sponsor</strong></td>
<td align="left"><ul><li>Ultimate authority and accountability for the project and delivery on project objectives</li>
<li>Help resolve issues escalated by Project Lead</li>
<li>Sponsors communication within the company about project goals</li>
<li>Responsible for making key strategic decisions</li>
<li>Responsible for availability of required resources and budget</p>
<li>Leading Quarterly Business Reviews (QBR)</li>
<li>Buy-In and support of awareness campaign effort</li>
<li>Serving as the Project Sponsor to the program rollout</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>Project Lead</strong></td>
<td align="left"><ul><li>Managing and leading project team</li>
<li>Coordinates partners and working teams engaged in the project</li>
<li>Accountable for creating and managing project plans to meet quarterly key results</li>
<li>Resolving cross-functional issues</li>
<li>Providing regular updates to the project sponsors</li>
<li>Incorporating Adoption aspects into the all-up project plan</li>
<li>Leading Monthly Business and Operational Reviews (MBR), contributing to Quarterly Business Reviews</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left"><strong>Collaboration Lead/Architect</strong></td>
<td align="left"><ul><li>Responsible for execution on collaboration strategy defined by company executives</li>
<li>Analyzing and choosing collaboration products for the company that meets business goals</li>
<li>Responsible for the design of the operations for collaboration products</li>
<li>Defines operation and support model</li>
<li>Contributing to Monthly and Quarterly Business Reviews</li><ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>Consultant</strong></td>
<td align="left"><ul><li>Responsible for configuration services</li>
<li>Contributes in overall solution architecture</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left"><strong>Project Manager</strong></td>
<td align="left"><ul><li>Developing and maintaining project plan</li>
<li>Managing project deliverables in line with project plan and budget</li>
<li>Recording and managing project issues, including escalations</li>
<li>Conducting weekly stand up calls</li>
<li>Liaises with, and provides updates to project executive sponsors</li>
<li>Working with the Architect to define the Change Management approach and Communication Plans</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>Change Management/Adoption Specialist</strong></td>
<td align="left"><ul><li>Provide input on Discovery phase into adoption and training processes</li>
<li>Participate in adoption strategy workshop</li>
<li>Developing and responsible for adoption strategy</li>
<li>Developing and executing communication plan</li>
<li>Responsible for delivering trainings to end users</li>
<li>Collect feedback and conduct surveys</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left"><strong>Network Lead</strong></td>
<td align="left"><ul><li>Providing input on Discovery phase into network design</li>
<li>Participating in planning during Envisioning workshop</li>
<li>Coordinates work of networking team during the project execution</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>Security Lead</strong></td>
<td align="left"><ul><li>Providing input on Discovery phase into security design and processes</li>
<li>Participating in planning during Envisioning workshop</li>
<li>Coordinates work of security team during the project execution</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left"><strong>Telephony Lead</strong></td>
<td align="left"><ul><li>Providing input on Discovery phase into telephony design</li>
<li>Participating in planning during envisioning workshop</li>
<li>Coordinates work of telephony team during the project execution</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>Desktop Lead</strong></td>
<td align="left"><ul><li>Providing input on Discovery phase into clients and update process</li>
<li>Participating in planning during envisioning workshop</li>
<li>Coordinates work of desktop team during the project execution</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left"><strong>Support/Help Desk Lead</strong></td>
<td align="left"><ul><li>Providing input on Discovery phase into operational and support model</li>
<li>Participating in planning during envisioning workshop</li>
<li>Participating into support model planning</li>
<li>Coordinates work of support teams/resources during the project execution</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>Business Unit Representatives</strong></td>
<td align="left"><ul><li>Contribute in End User based adoption guides and materials</li>
<li>Contribute to and review Business Use Cases</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left"><strong>Deployment Lead</strong></td>
<td align="left"><ul><li>Ensure that deployment prerequisites are met</li>
<li>Engage customer resources to engage on prepare and deploy stage activities</li>
<li>Participate in meetings to review prepare and deploy status</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>IT Admins</strong></td>
<td align="left"><ul><li>IT Pros responsible for assistance with test planning and execution</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left"><strong>Service Owner</strong></td>
<td align="left"><ul><li>Is responsible for the operation of the Phone System with Calling Plans service all up</li>
<li>Owner of Phone System with Calling Plans service</li></ul></td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left"><strong>Quality Champion</strong></td>
<td align="left"><ul><li>Drives quality, reliability and user feedback</li>
<li>Identifies the quality trends and drive remediation with the respective teams</li>
<li>Reports through the steering committee back to leadership</li>
<li>Reports on quality, reliability, and user sentiment through Rate My Call and Net Promoter Score</li></ul></td>
<td align="left">TBA</td>
</tr>
</tbody>
</table>

_Table 2 Stakeholder matrix template example_


> [!NOTE]
> The example table above and subsequent tables throughout this document serve as a template. You'll see "TBA" (to be added) for information that you need to complete as part of your planning process.

Define objectives and key results, key success indicators, and risks
--------------------------------------------------------------------

With the project stakeholders assembled, business use cases, organizational scope and project timelines can be translated into your objectives and key results (OKRs) and the measures of project success can be defined into a list of key success indicators (KSIs).

Full participation from project stakeholders when defining the OKRs and KSIs will ensure sense of ownership and they are aligned to organizational business requirements.

OKRs will contain the list of objectives set in the beginning of the project, with measurable key results defined in a quarterly basis. The key results are reviewed monthly to track status of the overall project, and based on progress, adjustment to the quarterly plans can be made as needed.

<table>
<thead>
<tr class="header">
<th align="left"><p><strong>Vision</strong>: Increase productivity by maximizing Office 365 investments</p>
</th>
<th align="left"></th>
<th align="left"></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>Objectives</strong></td>
<td align="left"><strong>Key Results</strong></td>
<td align="left"><strong>To Do</strong></td>
</tr>
<tr class="even">
<td align="left">Deploy Phone System with Calling Plans in European branch offices by end of fiscal year 2018</td>
<td align="left">FY18Q3: Deploy Phone System with Calling Plans in London office</td>
<td align="left"><p>Envision</p>
<ul><li>Create success plan</li>
<li>Create detailed technical implementation plan</li></ul>
<p>Onboard</p>
<ul><li>Execute success plan</li>
<li>Execute technical implementation plan</li></ul></td>
</tr>
<tr class="odd">
<td align="left">Decommission legacy PBX in London office by end of fiscal year 2018</td>
<td align="left">FY18Q4: Decommission legacy PBX in London office</td>
<td align="left"><p>Drive Value</p>
<ul><li>Boost user engagement and drive adoption</li>
<li>Manage and prepare change</li>
<li>Measure, share success, and iterate</li></ul></td>
</tr>
</tbody>
</table>

_Table 3 Example of OKRs_

KSIs measure quality and success of the key results and complement the binary nature of OKRs (achieved or not achieved), by detailing the good and/or bad results. When defining KSIs, we recommend leveraging the “specific, measurable, assignable, realistic, time-related” or SMART criteria.

<table>
<thead>
<tr class="header">
<th align="left">Type</th>
<th align="left"><p>KSI questions &amp;</p>
<p>criteria</p></th>
<th align="left">How measured</th>
<th align="left">Success criteria</th>
<th align="left">Measured</th>
<th align="left">Responsible</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>Usage/adoption</strong></td>
<td align="left">Call quality is equal to or better than the previous solution</td>
<td align="left">Survey</td>
<td align="left">80% of users agree or strongly agree</td>
<td align="left">After enablement and quarterly</td>
<td align="left">Information Technology team</td>
</tr>
<tr class="even">
<td align="left"><strong>Usage/adoption</strong></td>
<td align="left">Microsoft Teams and Skype for Business made the communication process easier</td>
<td align="left">Survey</td>
<td align="left">80% of users agree or strongly agree</td>
<td align="left">After enablement and quarterly</td>
<td align="left">Change Management team</td>
</tr>
<tr class="odd">
<td align="left"><strong>Usage/adoption</strong></td>
<td align="left">Users actively use the solution</td>
<td align="left">Office 365 reports, Call Quality Dashboard</td>
<td align="left">80% of users are active daily users</td>
<td align="left">Daily</td>
<td align="left">Change Management team</td>
</tr>
<tr class="even">
<td align="left"><strong>Usage/quality</strong></td>
<td align="left">Percentage of poor calls/conferences should be minimal</td>
<td align="left">Call Quality Dashboard</td>
<td align="left">&lt; 5% of poor calls per month</td>
<td align="left">Daily</td>
<td align="left">Information Technology team</td>
</tr>
<tr class="odd">
<td align="left"><strong>Usage/support</strong></td>
<td align="left">I know how to get technical support</td>
<td align="left">Survey</td>
<td align="left">90% of users agree or strongly agree</td>
<td align="left">After enablement and quarterly</td>
<td align="left">Change Management team</td>
</tr>
<tr class="even">
<td align="left"><strong>Usage/support</strong></td>
<td align="left">I am satisfied with the quality of technical support</td>
<td align="left">Survey</td>
<td align="left">80% of users agree or strongly agree</td>
<td align="left">After each incident</td>
<td align="left">Information Technology team</td>
</tr>
<tr class="odd">
<td align="left"><strong>Financial</strong></td>
<td align="left">Reduction of monthly telephony service expense</td>
<td align="left">Financial system</td>
<td align="left">Meet defined ROI</td>
<td align="left">Based on ROI</td>
<td align="left">Change Management team</td>
</tr>
</tbody>
</table>

_Table 4 Example of KSIs_


You need to identify business risks as part of this exercise and define a mitigation plan for each identified risk. This information can be captured into a risk plan.

<table>
<thead>
<tr class="header">
<th align="left">Risk</th>
<th align="left">Likelihood</th>
<th align="left">Impact</th>
<th align="left">Overall</th>
<th align="left">Mitigation plan</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Upcoming merger will add up to 1,000 people</td>
<td align="left">High</td>
<td align="left">High</td>
<td align="left">High</td>
<td align="left"><p>For merged companies, separate OKR with own process (Envision, Onboard, Drive Value)</p>
<p>Do not include them in existing OKRs</p></td>
</tr>
<tr class="even">
<td align="left">Telephone number porting will delay project completion</td>
<td align="left">High</td>
<td align="left">High</td>
<td align="left">High</td>
<td align="left"><p>Prepare all the required information to support telephone number porting ahead of time (i.e.: customer service record, billing details, Letter of Authorization)</p>
<p>Adjust project timeline to accommodate turnaround time of telephone number porting execution</p>
<p>Use temporary telephone numbers with Caller ID manipulation</p></td>
</tr>
<tr class="odd">
<td align="left">Planned network redesign</td>
<td align="left">High</td>
<td align="left">Medium</td>
<td align="left">Medium</td>
<td align="left">Before implementing Teams as modern communications and collaboration platform, run network readiness assessment for sites in scope of the project</td>
</tr>
</tbody>
</table>

_Table 5 Risk plan example_

Assess environment and evaluate adoption readiness
--------------------------------------------------

To achieve the intended OKRs, you may have to define the high-level architecture of the solution. It takes environmental discovery to evaluate all aspects relating to IT and telephony infrastructure, networking, and operations.

All matters related to end-user computing, such as readiness assessment of the personal computers and mobile devices to support Phone System with Calling Plans business use cases, from hardware requirements to software requirements, will be included as part of the environmental discovery.



Environmental discovery can also uncover if there are requirements to [transfer phone numbers to Microsoft](https://support.office.com/article/Transfer-phone-numbers-to-Office-365-47b3af8e-4171-4dec-8333-c956f108664e). This will help your organization to adjust the project plan accordingly and prepare the necessary information required for number porting. You can perform environmental discovery by leveraging the following [questionnaire](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_1_0_3).

Environmental discovery must include network readiness assessment to ensure the network is ready to support the implementation of Phone System with Calling Plans.

Network readiness to support Phone System with Calling Plans can be determined by leveraging the information captured through the environmental discovery (such as details of internet connectivity and WAN topology, site links and available bandwidth) and persona analysis data (that can be translated into an expected usage of each workload) into the [My Advisor Network Planning](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner) tool. To further confirm network readiness, real-time media traffic simulation can be performed using the solutions provided by [Microsoft](https://www.microsoft.com/download/details.aspx?id=53885) or by [Network Readiness Assessment tools partners](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Partners?ToolPartners).


The results of network readiness assessment will paint a clearer picture of the required network optimization or remediation required for the success of Phone System with Calling Plans implementation.

Adoption readiness can be evaluated by executing persona analysis to come up with a list of personas in the organization who can be targeted for the implementation of the Phone System with Calling Plans. The persona analysis includes the identification of additional peripherals or devices required to realize the intended business outcomes.

To perform persona analysis, you can conduct a workshop by involving relevant project stakeholders, leveraging the [Persona Alignment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_2_0_7) workshop deck and [Persona Feature Matrix](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_2_0_8). The result of persona analysis workshop can be summarized into a report using the [Persona Analysis Report](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_2_0_9) template.

> [!NOTE]
> While the Discovery Questionnaire and Persona Analysis examples were initially written for Skype for Business Online, a majority of the content is relevant to Teams. Feel free to modify and remove items that are not relevant to the project goals.

You can identify technical risks as part of an environmental assessment and adoption readiness evaluation and develop a mitigation plan for each identified risk. This information should be incorporated as part of the risk plan.

Map operational roles
---------------------

Planning for operations and identifying the teams that will operate the Phone System with Calling Plans service is an important step, as operations must start when the first pilot users are enabled. Each identified team must review and agree on the tasks and responsibilities identified and start the preparation to operate Phone System with Calling Plans service. The preparation might include training and readiness, additional staffing, or ensuring external providers are set up to deliver the service.

<table>
<thead>
<tr class="header">
<th align="left">Operational Role</th>
<th align="left">Description</th>
<th align="left">Team</th>
<th align="left">Contact Details</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Service Owner</td>
<td align="left">Service owner, interface to business divisions, strategy</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left">Phone System with Calling Plans Operations</td>
<td align="left">Daily operations, user and device account move/add/change, monitoring</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left">Tenant Admin</td>
<td align="left">Change tenant-wide settings, enable new features</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left">Help Desk</td>
<td align="left">Interface for end-users to get support</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left">Network Operations</td>
<td align="left">Runs LAN, WAN, Wi-Fi, and Internet Access</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left">Client &amp; Endpoints Team</td>
<td align="left">Manage desktop deployments</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left">Identity Operations</td>
<td align="left">Manage identity infrastructure (AD, ADFS, Azure AD)</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left">Adoption/change management</td>
<td align="left">Manage awareness, training and adoption for the solution</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
<tr class="odd">
<td align="left">Exchange Operations</td>
<td align="left">Manages the Exchange environment</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
</tr>
</tbody>
</table>

_Table 6 Example of operational roles mapping_

To facilitate a more detailed operational roles mapping, including the tasks associated with each operational role, you can use the [Operational Role Mapping Workbook](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_4_0_16) to capture the details that will provide the clarity around roles and responsibilities to support Phone System with Calling Plans service.

 Document success plan
---------------------

A success plan is the documentation created in the Envision phase that consists of business case, service readiness, adoption plan, and operational plan.

The success plan will provide the project team, which can include FastTrack or deployment partner, with sufficient information to realize the organization’s goals with Phone System with Calling Plans.

In general, a success plan will contain the following main sections:

-   Business case

-   Service readiness

-   Adoption plan

-   Operational plan

### Business case

Business use cases, stakeholders, OKRs and KSIs, risks, and project timelines typically make up the bulk of information required for a business case. You need to document them as part of the success plan.

### Service readiness

Environmental assessment provides the initial information required to determine technical readiness for the organization to implement Phone System with Calling Plans.

Included here is the plan to address areas needing remediation discovered through environmental assessment. You need to include the service readiness assessment and remediation plan as part of the success plan.

### Adoption plan

Following an adoption readiness assessment, further detailed planning must be completed for the project team to come up with a comprehensive set of communication plans, training plan, and pre-launch, at-launch, and post-launch adoption activities.

Resources to support adoption activities such as flyers, welcome emails, and training materials are identified at this step, along with any customizations needed to meet organizational requirements.

The templates for adoption activities are available [here](https://www.microsoft.com/download/details.aspx?id=54244).

### Operational plan

Operational roles mapping exercise will establish the roles and responsibilities, and the teams assigned to each operational role to support the implementation of Phone System with Calling Plans.

You need to complete this and include the operational plan as part of the success plan to ensure operational readiness of the solution.

Planning for Phone System with Calling Plans in Teams  <a name="Planning_PhoneSystemWithCallingPlans"> </a>
=====================================================

To plan for the implementation of Phone System with Calling plans, a series of decisions must be made ahead of time to better prepare your organization to implement a solution that meets business requirements. These decisions will be documented into a technical implementation plan.

## Availability of Calling Plans



Calling Plans service is available in these [countries and regions](https://support.office.com/article/Countries-regions-that-are-supported-for-Audio-Conferencing-and-Calling-Plans-6ba72f37-d303-4795-aa8f-7e1845078ed7).


> [!IMPORTANT]
> Due to legal constraints, for Calling Plans to be available to multinational organizations, the contract for Office 365 subscriptions must be sourced from countries and regions covered by Calling Plans service, or where Calling Plans service is commercially available from.

After confirming your organization’s eligibility for obtaining the Calling Plans add-on, compile the list of user locations or offices where Calling Plans service will be implemented based on the list of available countries and regions.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><p>Decide which user locations or offices where Calling Plans service will be implemented .</p></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><p>Document the user locations or offices to be enabled for Calling Plans service.</p></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">Office</th>
<th align="left">Location</th>
<th align="left">Phone System Service</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">One Epping Road</td>
<td align="left">Australia</td>
<td align="left">Legacy PSTN service</td>
</tr>
<tr class="even">
<td align="left">100 Cyberport Road</td>
<td align="left">Hong Kong SAR</td>
<td align="left">Legacy PSTN service</td>
</tr>
<tr class="odd">
<td align="left">One Marina Boulevard</td>
<td align="left">Singapore</td>
<td align="left">Legacy PSTN service</td>
</tr>
<tr class="even">
<td align="left">32 London Bridge Street</td>
<td align="left">United Kingdom</td>
<td align="left">Phone System with Calling Plan</td>
</tr>
<tr class="odd">
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">France</td>
<td align="left">Phone System with Calling Plan</td>
</tr>
</tbody>
</table>

_Table 7 Example of Phone System with Calling Plans site enablement list_

## Licensing for Calling Plans

Calling Plan is an add-on to Phone System feature in Office 365, therefore Phone System license is the prerequisite for users to be enabled for Calling Plans.



[Phone System license](https://support.office.com/article/Skype-for-Business-and-Microsoft-Teams-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7) is available as part of Office 365 E5 subscription plans, or as an add-on to Office 365 E1 or Office 365 E3 subscription plans.
There are two types of [Calling Plan licenses](https://support.office.com/article/Calling-Plans-for-Office-365-f47c6a97-bc8b-42e6-b5d4-ce6b41ed1918):

-	Domestic Calling Plan
-	International and Domestic Calling Plan

> [!NOTE]
> What is considered “domestic” for a specific user is determined by the user’s assigned Office 365 usage location.



Each Calling Plan type provides [calling minutes allocation](https://support.office.com/article/Countries-regions-that-are-supported-for-Audio-Conferencing-and-Calling-Plans-6ba72f37-d303-4795-aa8f-7e1845078ed7) that users can use per month, either to make domestic calls or international calls. Domestic Calling Plan costs less compares to International and Domestic Calling Plan.


Typically, not everybody in an organization requires the ability to make international calls. The flexibility of subscribing and assigning the most appropriate Calling Plan type for individual user’s business requirements allows your organization to control the costs of Calling Plans implementation.

For each Office 365 tenant, the combined number of calling minutes are pooled by country or region, and per Calling Plan type. When the monthly calling minutes cap for the tenant is reached, Calling Plans service (except for emergency calling) will be suspended for the remainder of the month. Calling Plans services will resume automatically on the first day of the next calendar month.



To enable users to make outbound calls after the calling minutes are exhausted without having to wait until the next month billing cycle, you can setup Communications Credits for your organization. [Communications Credits](https://support.office.com/article/What-are-Communications-Credits-524dbea7-117f-493d-8005-6461f7f10059) also gives the ability for users assigned with Domestic Calling Plan to make International calls charged by a “pay-per-minute” model.

The first consideration to make when implementing Communications Credits is to decide the initial amount of funds to be purchased. Recommended funding amounts can be referenced from [Communications Credits](https://support.office.com/article/What-are-Communications-Credits-524dbea7-117f-493d-8005-6461f7f10059) article.

If your organization choose to use auto-recharge, a recommendation on the trigger (lowest amount of funds) is also included in the [Communications Credits](https://support.office.com/article/What-are-Communications-Credits-524dbea7-117f-493d-8005-6461f7f10059) article. Auto-recharge amount needs to be determined by the actual usage. Communications Credits usage should be monitored over time and recharge amount needs to be adjusted as required.


The use of Communications Credits can be controlled at per user basis, allowing you to ensure the capability is assigned to individuals in the organization that have proper business needs.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>If your organization does not have the required Phone System license, decide whether Phone System license will be acquired by stepping up existing Office 365 subscriptions or by acquiring Phone System add-ons.</li>
<li>Decide which users require Domestic Calling Plan license and which users require Domestic and International Calling Plan license.</li>
<li>Decide if Communications Credits is required for Calling Plans implementation. If so, decide the initial amount of funds to be purchased. Where applicable, decide the trigger amount and auto-recharge amount.</li>
<li>Decide which users require the use of Communications Credits license.</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the users to be assigned with Phone System license along with Domestic Calling Plan license, and users to be assigned with Phone System license with Domestic and International Calling Plan license.</li>
<li>Document the Communications Credits plan (initial amount, trigger amount, auto-recharge amount).</li>
<li>Document the users to be enabled for Communications Credits license.</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">User</th>
<th align="left">Office</th>
<th align="left">Office 365 License</th>
<th align="left">Communications Credtis</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Emily Braun</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Office 365 E5, International and Domestic Calling Plan</td>
<td align="left">Enabled</td>
</tr>
<tr class="even">
<td align="left">Lidia Holloway</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Office 365 E5, Domestic Calling Plan</td>
<td align="left">Disabled</td>
</tr>
<tr class="odd">
<td align="left">Pradeep Gupta</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Office 365 E5, Domestic Calling Plan</td>
<td align="left">Enabled</td>
</tr>
<tr class="even">
<td align="left">Marcel Beauchamp</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Office 365 E3, Phone System add-on, Domestic Calling Plan</td>
<td align="left">Disabled</td>
</tr>
<tr class="odd">
<td align="left">Rachelle Cormier</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Office 365 E5, International and Domestic Calling Plan</td>
<td align="left">Enabled</td>
</tr>
<tr class="even">
<td align="left">Isabell Potvin</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Office 365 E3, Phone System add-on, Domestic Calling Plan</td>
<td align="left">Disabled</td>
</tr>
</tbody>
</table>

_Table 8 Example of license assignment list for Phone System with Calling Plans users_

<table>
<thead>
<tr class="header">
<th align="left">Initial amount</th>
<td align="left">$ 1,000</td>
</tr>
</thead>
<thead>
<tr class="header">
<th align="left">Trigger amount</th>
<td align="left">$ 400</td>
</tr>
<tr class="header">
<th align="left">Auto-recharge amount</th>
<td align="left">TBA</td>
</tr>
</tbody>
</table>

_Table 9 Example of Communications Credits planning numbers_

## Phone Numbers and Emergency Locations



With Calling Plans in Office 365, every user in your organization needs to have a unique Direct Inward Dialing (DID) phone number and a corresponding [validated emergency address](https://support.office.com/article/What-are-emergency-locations-addresses-and-call-routing-589bf5f5-490a-4215-8588-99bab7d33e31).

Phone numbers can be [obtained directly from Microsoft](https://support.office.com/article/Manage-phone-numbers-for-your-organization-6b61cb3c-361c-48a8-a9ef-d81bddde27bb), or existing phone numbers can be [transferred (ported) to Microsoft](https://support.office.com/article/Transfer-phone-numbers-to-Office-365-47b3af8e-4171-4dec-8333-c956f108664e).


> [!NOTE]
> Complexity of transferring phone numbers to Microsoft varies greatly based on the countries or regions, carriers, the number of circuits involved, and many other contributing factors. To plan for phone number porting, check out the [Number Porting Guide](https://go.microsoft.com/fwlink/?linkid=859011) for the details.



When obtaining phone numbers from Microsoft directly, you can choose to use [Skype for Business admin center](https://support.office.com/article/Getting-Skype-for-Business-phone-numbers-for-your-users-aa2ec464-3481-4bbb-8c14-e13e18093df5) or [remote PowerShell](https://technet.microsoft.com/library/mt228132.aspx), or to [submit a completed New Telephone Number Request form](https://support.office.com/article/Manage-phone-numbers-for-your-organization-6b61cb3c-361c-48a8-a9ef-d81bddde27bb).


The manual form submission is preferred for a planned phone number acquisition since contiguous block of phone numbers can be requested. Obtaining phone numbers using Skype for Business admin center or remote PowerShell are not available in every countries or regions, and therefore the manual form submission method is the widely available method to obtain phone numbers.

The other method, using Skype for Business admin center or remote PowerShell, will work for one-off, instantaneous, phone number acquisition, and when contiguous block of phone numbers is not required.

> [!NOTE]


> There is a limit on the [number of the phone numbers](https://support.office.com/article/How-many-phone-numbers-can-you-get-61dfb27c-5bfa-4481-a930-9c026e73ff3a) that can be acquired from Microsoft based on the number of Calling Plan licenses subscribed by your organization. For user (subscriber) phone numbers, the formula is (Number of Domestic Calling Plan + Domestic and International Calling Plan licenses) x 1.1 +10. For example, if you have 50 users with Calling Plan licenses, you can acquire 65 phone numbers ((50 x 1.1) + 10).


When you are configuring phone numbers for Calling Plans, it is required that an emergency address be assigned to each telephone number prior to assignment to a user. This is required to support emergency calling. The emergency address must be validated to ensure the emergency address is recognized that it is in a correct format that can be used by emergency response services.

> [!IMPORTANT]


> Emergency Services Calling operates differently with Calling Plans service than on traditional telephone services. It is important that you understand these differences and communicate them to all users. Check [Emergency calling terms and conditions](https://support.office.com/article/Emergency-calling-terms-and-conditions-ca2c751b-53ab-42c7-aed9-cfe27e662940) for further details.


In addition to validated emergency address, emergency locations can be defined and associated with validated emergency address to give a more exact location within an address. An emergency location is typically building number, floor, building wing, or office number where the user is located.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>Decide how phone numbers will be obtained for user locations or offices in-scope for the Calling Plans implementation (obtain from Microsoft or transfer existing phone numbers)</li>
<li>If you choose to obtain from Microsoft, decide the method to obtain phone numbers (form submission or automated) for user locations or offices in-scope for the Calling Plans implementation.</li>
<li>Decide the granularity of emergency locations information to be collected for user locations or offices in-scope for the Calling Plans implementation.</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the master plan for phone numbers acquisition, detailing how phone numbers will be obtained for each user location or office in-scope for the Calling Plans implementation.</li>


<li>If applicable, complete <a href="https://support.office.com/article/Manage-phone-numbers-for-your-organization-6b61cb3c-361c-48a8-a9ef-d81bddde27bb">the New Telephone Number Request form</a>, one form for each location or office</li>

<li>If you choose to transfer existing phone numbers, check out the <a href="https://go.microsoft.com/fwlink/?linkid=859011">Number Porting Guide</a> to plan it and adjust Calling Plans implementation timeline accordingly.</li>
<li>Document the detailed emergency address and emergency locations for each user location or office in-scope for the Calling Plans implementation.</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">User</th>
<th align="left">Emergency Location and Address</th>
<th align="left">Phone Number Acquisition</th>
<th align="left">Phone Number</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Emily Braun</td>
<td align="left">1034/32 London Bridge Street, London, SE1, United Kingdom</td>
<td align="left">Port existing</td>
<td align="left">+44 20 7946 0034</td>
</tr>
<tr class="even">
<td align="left">Lidia Holloway</td>
<td align="left">1023/32 London Bridge Street, London, SE1, United Kingdom</td>
<td align="left">Port existing</td>
<td align="left">+44 20 7946 0065</td>
</tr>
<tr class="odd">
<td align="left">Pradeep Gupta</td>
<td align="left">1023/32 London Bridge Street, London, SE1, United Kingdom</td>
<td align="left">Port existing</td>
<td align="left">+44 20 7946 0023</td>
</tr>
<tr class="even">
<td align="left">Marcel Beauchamp</td>
<td align="left">07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France</td>
<td align="left">Acquire new</td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left">Rachelle Cormier</td>
<td align="left">07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France</td>
<td align="left">Acquire new</td>
<td align="left">TBA</td>
</tr>
<tr class="even">
<td align="left">Isabell Potvin</td>
<td align="left">07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France</td>
<td align="left">Acquire new</td>
<td align="left">TBA</td>
</tr>
</tbody>
</table>

_Table 10 Example of phone number acquisition, phone numbers and emegency location details_


> [!NOTE]
> The example table above and subsequent tables throughout this document serve as a template and will denote TBA (to be added) for information that you need to complete as part of your planning process.


## Calling Identity


By default, all outbound calls use the assigned phone number as calling identity (Caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call. In some cases, there are legitimate business requirements to mask the Caller ID to protect the identity of callers by using the office main line number—this is typically a service number serviced by [Auto Attendant](https://support.office.com/article/What-are-Phone-System-auto-attendants-ab9f05a2-22cb-4692-a585-27f82d1b37c7) configuration—as Caller ID, or to block Caller ID presentation altogether.


<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>Decide whether Caller ID manipulation is required for Calling Plans implementation.</li>
<li>If applicable, decide the types of Caller ID manipulation (mask with service number or anonymize) to be implemented.</li>
<li>•If applicable, decide which user require Caller ID manipulation, and the type of Caller ID manipulation to be assigned to each user.</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the users to be assigned with Caller ID manipulation and Caller ID manipulation type applicable for each user.</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">User</th>
<th align="left">Enable Caller ID masking</th>
<th align="left">Caller ID masking type</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Emily Braun</td>
<td align="left">No</td>
<td align="left">N/A</td>
</tr>
<tr class="even">
<td align="left">Lidia Holloway</td>
<td align="left">Yes</td>
<td align="left">Service number (OrgAA, +44 20 7946 0000)</td>
</tr>
<tr class="odd">
<td align="left">Pradeep Gupta</td>
<td align="left">No</td>
<td align="left">N/A</td>
</tr>
<tr class="even">
<td align="left">Marcel Beauchamp</td>
<td align="left">Yes</td>
<td align="left">Service number (OrgAA, TBA)</td>
</tr>
<tr class="even">
<td align="left">Rachelle Cormier</td>
<td align="left">Yes</td>
<td align="left">Anonymize</td>
</tr>
<tr class="even">
<td align="left">Isabell Potvin</td>
<td align="left">Yes</td>
<td align="left">Service number (OrgAA, TBA)</td>
</tr>
</tbody>
</table>

_Table 11 Example of Caller ID masking configuration details_

## Dial plans

A [Dial Plan](https://support.office.com/article/What-are-PSTN-Calling-dial-plans-2f0cfb59-1ca1-4e31-84ce-09d0b1a7ce1b), in the Phone System feature of Office 365, is a set of normalization rules that translates dialed phone numbers into an alternate format (typically [E.164](https://go.microsoft.com/fwlink/?linkid=859014) format) for call authorization and call routing. 

A dial plan allows users to dial phone numbers the way they are accustomed to, such as omitting area code for local calls, omitting country code for domestic calls, or even using short digit dialing when performing conference dial out.

Within the Phone System feature of Office 365, there are two types of dial plans:

-   **Service dial plan**. This is the default dial plan and applied to users based on Office 365 usage location, and it cannot be modified.

<!-- -->

-   **Tenant dial plan**. This is a customizable dial plan within a tenant, and further divided into two types:

    -   **Tenant-global dial plan**—the dial plan applies to all users within the tenant.

    -   **Tenant-user dial plan**—the dial plan applies only to specific users.


> [!NOTE]
> Check out the [Office 365 Calling Plan dial plans](https://support.office.com/article/What-are-PSTN-Calling-dial-plans-2f0cfb59-1ca1-4e31-84ce-09d0b1a7ce1b) documentation for further details and examples.

The effective dial plan assigned to users is the combination of service dial plan (based on user’s Office 365 usage location) and tenant dial plan (can be either tenant-global dial plan or tenant-user dial plan).

![Table shows three combinations of service and tenant dial plans.](media/audio_conferencing_image8.png)

There is a maximum of 25 normalization rules in each tenant dial plan, and thus duplication with normalization rules already available as part of service dial plan needs to be avoided.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>Decide if your organization requires customized dial plans (business requirements, adoption requirements, etc.).</li>
<li>If applicable, decide the scope of tenant dial plan (tenant-global or tenant-user) to support the requirements for customized dial plans.</li>
<li>If applicable, decide the tenant dial plans that will be created to support user locations or offices in-scope for the Calling Plans implementation.</li>
<li>If applicable, decide which user require customized dial plan and the tenant dial plan to be assigned for each user.</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the customized dial plans and the associated normalization rules to be configured as part of Calling Plans implementation.</li>
<li>Document the users to be assigned with customized dial plan and the tenant dial plan to be assigned for each user.</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left"><p>Tenant Dial Plan Name</p><p>Description</p></th>
<th align="left"><p>Normalization Rules Name</p><p>Description</p></th>
<th align="left"><p>Pattern</p><p>Translation</p><p>IsInternalExtension</p></th>
</tr>
</thead>
<tbody>
<tr class="even">
<td align="left"><p><strong>FR-Paris-Issy-39qdPR</strong></p>
<p><em>39 quai du Président Roosevelt Issy-les-Moulineaux, France Dial Plan</em></p></td>
<td align="left"><p><strong>FR-39qdPR-Internal</strong></p>
<p><em>Internal number (x7000 – x7999) for 39 quai du Président Roosevelt office, Issy-les-Moulineaux, France</em></p></td>
<td align="left"><p>^(7\d{3})$</p><p>+3319999$1</p><p>True</p></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><p><strong>FR-TollFree</strong></p>
<p><em>Toll Free number normalization for France</em></p></td>
<td align="left"><p>^0?(80\d{7})\d*$</p><p>+33$1</p><p>False</p></td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"><p><strong>FR-Service</strong></p>
<p><em>Service number normalization for France</em></p></td>
<td align="left"><p>^(1\d{1,2}|11[68]\d{3}|10\d{2}|3\d{3})$</p><p>$1</p><p>False</p></td>
</tr>
</tbody>
</table>

_Table 12 Example of tenant dial plans_

<table>
<thead>
<tr class="header">
<th align="left">User</th>
<th align="left">Office</th>
<th align="left">Dial Plan Type</th>
<th align="left">Dial Plan Name</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Emily Braun</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Service dial plan</td>
<td align="left">N/A</td>
</tr>
<tr class="even">
<td align="left">Lidia Holloway</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Service dial plan</td>
<td align="left">N/A</td>
</tr>
<tr class="odd">
<td align="left">Pradeep Gupta</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Service dial plan</td>
<td align="left">N/A</td>
</tr>
<tr class="even">
<td align="left">Marcel Beauchamp</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Tenant dial plan</td>
<td align="left">FR-Paris-Issy-39qdPR</td>
</tr>
<tr class="odd">
<td align="left">Rachelle Cormier</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Tenant dial plan</td>
<td align="left">FR-Paris-Issy-39qdPR</td>
</tr>
<tr class="even">
<td align="left">Isabell Potvin</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Tenant dial plan</td>
<td align="left">FR-Paris-Issy-39qdPR</td>
</tr>
</tbody>
</table>

_Table 13 Example of dial plan assignments_

## Document technical implementation plan

Use the decision points above to document your technical implementation plan.
This technical implementation plan will provide the project team, which can include FastTrack or deployment partner, with the information required to execute the technical onboarding for the implementation of Phone System with Calling Plans.

In general, a technical implementation plan will contain the following main sections:

-	Phone System with Calling Plans site enablement list

-	License assignment for Phone System with Calling Plans users

-	Communications Credits planning numbers

-	Phone number acquisition, phone numbers, and emergency location details

-	Caller ID masking configuration details

-	Tenant dial plans

-	Dial plan assignments

With the completion of success plan and technical implementation plan, you are now ready to take your organization to the next steps along the Office 365 customer journey.

Onboard
=======

*Coming soon.*

Drive Value
===========

*Coming soon.*



