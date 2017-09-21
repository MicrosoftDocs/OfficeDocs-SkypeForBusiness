---
title: Audio Conferencing in Microsoft Teams
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: article
ms.service: msteams
description: Practical guidance for deploying audio conferencing in Microsoft Teams.
Set_Free_Tag: Strat_MT_TeamsAdmin
---

Audio Conferencing in Microsoft Teams
=====================================

*Before you start, please note that Audio Conferencing in Teams is currently available as Public Preview feature, and this guidance is still a work in progress.*

Audio Conferencing in Office 365 (formerly known as PSTN Conferencing) allows participants to join your meetings from any telephone. This feature is now available in Teams, allowing users to join Teams meetings using their phones. The practical guidance in this article steps you through the Office 365 FastTrack customer journey framework for Audio Conferencing - Envision, Onboard, and Drive value.

Here's what you get with [Audio Conferencing](https://go.microsoft.com/fwlink/?linkid=858992) in Office 365.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left" valign="center">Audio Conferencing service supports both Teams and Skype for Business Online. Currently, the existing Skype for Business Admin Center and remote PowerShell provide the administrative interfaces to manage Audio Conferencing.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

> [!NOTE]
> Audio Conferencing supports both Teams and Skype for Business Online. Currently, the existing Skype for Business Admin Center and remote PowerShell provide the administrative interfaces to manage Audio Conferencing.


|  |  |
|---------|---------|
|  <iframe width="350" height="200" src="https://www.youtube.com/embed/cOOLZJCFjKw" frameborder="0" allowfullscreen></iframe>   | |

Envision <a name="Envision_AudioConferencing"> </a>
=========

The Envision phase provides the foundation for the Office 365 customer journey, and is applicable to all workloads such as Audio Conferencing.

In this phase, business goals are captured, with relevant project stakeholders assembled, to ultimately deliver:

-   a high-level success plan that contains business use cases, key stakeholders, objectives and key results (OKRs), key success indicators (KSIs), risks, environmental assessment, adoption readiness, and operational plan.

-   and subsequently, a detailed Audio Conferencing technical implementation plan to achieve the desired end state.

Define business use cases for Audio Conferencing
------------------------------------------------

Audio Conferencing provides organizations with additional entry points to any scheduled meetings by allowing meeting participants to join via PSTN by dialing in using traditional landline, PBX, or mobile phones.

This is useful when the organizer or participants are not in front of a computer, or when data connections are unavailable or unreliable to support voice communications—such as when in a remote area with spotty mobile data coverage, or if connected to a free, public Wi-Fi service with limited bandwidth, or when meeting participants prefer to dial in to the meeting using telephony endpoint readily accessible to them.

In this step, core project stakeholders will define business use cases that support the implementation of Audio Conferencing.

Business use cases are meant to define and document the expected and measurable business outcomes, and include the following:

-   Description of current business process.

-   Challenges with existing business process defined.

-   How technology can help overcome these challenges.

-   The expected and measurable business outcome if these challenges are overcome.

<table>
<tbody>
<tr class="header">
<th align="left"><p><img src="media/audio_conferencing_image2.png" /></p></th>
<td align="left"><p><strong>Description of current business process</strong></p>
<p>Contoso currently relies on PSTN conferencing services provided by the incumbent local telephony provider chargeable by meeting minutes for internal meetings and meetings involving external parties.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><img src="media/audio_conferencing_image3.png" /></p></td>
<td align="left"><p><strong>Challenges with existing business process</strong></p>
<p>Contoso spends roughly USD 1 million per year for the current PSTN conferencing service, with 75% of the cost incurred for internal meetings.</p>
<p>The use of traditional telephony endpoints to join the meetings hosted by the PSTN conferencing service is not aligned with the plan for the organization to adopt Microsoft Teams as modern communications and collaboration platform.</p></td>
</tr>
<tr class="even">
<td align="left"><p><img src="media/audio_conferencing_image4.png" /></p></td>
<td align="left"><p><strong>How technology can overcome these challenges</strong></p>
<p>With the adoption of Microsoft Teams as modern communications and collaboration platform, internal users are expected to primarily join meetings using their PCs equipped with optimized headsets and meeting room devices. Audio Conferencing service will be available to support external participants or to support situations where the use of PC audio is not favorable for the internal participants.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><img src="media/audio_conferencing_image5.png" /></p></td>
<td align="left"><p><strong>Expected, measurable, business outcomes</strong></p>
<p>The move to Microsoft Teams as modern communications and collaboration platform, combined with Audio Conferencing service, will greatly reduce the cost to deliver the PSTN conferencing service to the point that Contoso is expected to only spend approximately 20% of the annual cost of the existing PSTN conferencing service.</p></td>
</tr>
</tbody>
</table>

_Table 1 Business use case example_


In addition to defining the business use cases, having a clarity around the organizational scope and project timelines at this step helps move onto the next step of the Envision phase.

Identify key stakeholders
-------------------------

The business use cases defined in the previous step will include organizational scope of Audio Conferencing implementation, and based on that, the comprehensive stakeholder matrix can be completed to include the right people to be involved in the project.

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
<td align="left"><ul><li>Is responsible for the operation of the Audio Conferencing service all up</li>
<li>Owner of Audio Conferencing service</li></ul></td>
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

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td style="vertical-align:top">The example table above and subsequent tables throughout this document serve as a template and will denote TBA (to be added) for information that you need to complete as part of your planning process.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

Define objectives and key results, key success indicators, and risks
--------------------------------------------------------------------

With the project stakeholders assembled, business use cases, organizational scope and project timelines can be translated into objectives and key results (OKRs) and the measures of project success can be defined into a list of key success indicators (KSIs).

Full participation from project stakeholders when defining the OKRs and KSIs will ensure sense of ownership and they are aligned to organizational business requirements.

OKRs will contain the list of objectives set in the beginning of the project, with measurable key results defined in a quarterly basis. The key results are reviewed monthly to track status of the overall project, and based on progress, adjustment to the quarterly plans can be made as needed.

<table>
<thead>
<tr class="header">
<th align="left"><p>Vision</p>
<p>Increase productivity by maximizing Office 365 investments</p></th>
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
<td align="left">Deploy Audio Conferencing in Microsoft Teams by end of fiscal year 2018</td>
<td align="left">FY18Q1: Deploy Audio Conferencing in Microsoft Teams globally</td>
<td align="left"><p>Envision</p>
<ul><li>Create success plan</li>
<li>Create detailed technical implementation plan</li></ul>
<p>Onboard</p>
<ul><li>Execute success plan</li>
<li>Execute technical implementation plan</li></ul></td>
</tr>
<tr class="odd">
<td align="left">Decommission legacy PSTN Conferencing service globally by mid of fiscal year 2018</td>
<td align="left">FY18Q2: Decommission legacy PSTN Conferencing service globally</td>
<td align="left"><p>Deliver Value</p>
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
<td align="left">Microsoft Teams made the communication process easier</td>
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
<td align="left">Reduction of legacy conferencing minutes</td>
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
<p>Communicate the use of new dial-in conferencing numbers to external participants</p></td>
</tr>
<tr class="odd">
<td align="left">Planned network redesign</td>
<td align="left">High</td>
<td align="left">Medium</td>
<td align="left">Medium</td>
<td align="left">Before implementing Microsoft Teams as modern communications and collaboration platform, run network readiness assessment for sites in scope of the project</td>
</tr>
</tbody>
</table>

_Table 5 Risk plan example_


Assess environment and evaluate adoption readiness
--------------------------------------------------

To achieve the intended OKRs, you may have to define the high-level architecture of the solution. It takes environmental discovery to evaluate all aspects relating to IT and telephony infrastructure, networking, and operations.

All matters related to end-user computing, such as readiness assessment of the personal computers and mobile devices to support Audio Conferencing business use cases, from hardware requirements to software requirements, will be included as part of the environmental discovery.

Environmental discovery can also uncover if there are requirements to [transfer phone numbers to Microsoft](https://support.office.com/en-us/article/Transfer-phone-numbers-to-Skype-for-Business-Online-47b3af8e-4171-4dec-8333-c956f108664e). This will help your organization to adjust the project plan accordingly and prepare the necessary information required for number porting. You can perform environmental discovery by leveraging the following [questionnaire](https://go.microsoft.com/fwlink/?linkid=858995).

Environmental discovery must include network readiness assessment to ensure the network is ready to support the implementation of the Audio Conferencing service.

Network readiness to support the Audio Conferencing service can be determined by leveraging the information captured through the environmental discovery (such as details of internet connectivity and WAN topology, site links and [available bandwidth](https://go.microsoft.com/fwlink/?linkid=858997)) and persona analysis data (that can be translated into an expected usage of each workload) into the [My Advisor Network Planner tool](https://go.microsoft.com/fwlink/?linkid=858999). To further confirm network readiness, real-time media traffic simulation can be performed using the solutions provided by [Microsoft](https://go.microsoft.com/fwlink/?linkid=859002) or by [Network Readiness Assessment tools partners](https://go.microsoft.com/fwlink/?linkid=859003).

The results of the Network Readiness Assessment will paint a clearer picture of the required network optimization or remediation required for the success of Audio Conferencing implementation.

Adoption readiness can be evaluated by executing persona analysis to come up with a list of personas in the organization who can be targeted for the implementation of Audio Conferencing service. The persona analysis includes the identification of additional peripherals or devices required to realize the intended business outcomes.

To perform persona analysis, you can conduct a workshop by involving relevant project stakeholders, leveraging the [Persona Alignment](https://go.microsoft.com/fwlink/?linkid=859005) workshop deck and [Persona Feature Matrix](https://go.microsoft.com/fwlink/?linkid=859006). The result of persona analysis workshop can be summarized into a report using the [Persona Analysis Report](https://go.microsoft.com/fwlink/?linkid=859007) template.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left">While the Discovery Questionnaire and Persona Analysis examples were initially written for Skype for Business Online, a majority of the content is relevant to Microsoft Teams. Feel free to modify and remove items that are not relevant to the project goals.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

You can identify technical risks as part of an environmental assessment and adoption readiness evaluation and develop a mitigation plan for each identified risk. This information should be incorporated as part of the risk plan.

Map operational roles
---------------------

Planning for operations and identifying the teams that will operate the Audio Conferencing service is an important step, as operations must start when the first pilot users are enabled. Each identified team must review and agree on the tasks and responsibilities identified and start the preparation to operate the Audio Conferencing service. The preparation might include training and readiness, additional staffing, or ensuring external providers are set up to deliver the service.

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
<td align="left">Audio Conferencing Operations</td>
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


To facilitate a more detailed operational roles mapping, including the tasks associated with each operational role, you can use the [Operational Role Mapping Workbook](https://www.skypeoperationsframework.com/Downloads?SelectedIDs=4_4_0_16) to capture the details that will provide the clarity around roles and responsibilities to support Audio Conferencing service.

Document success plan
---------------------

A success plan is the documentation created in the Envision phase that consists of business case, service readiness, adoption plan, and operational plan.

The success plan will provide the project team, which can include FastTrack or deployment partner, with sufficient information to realize the organization’s goals with Audio Conferencing service.

In general, a success plan will contain the following main sections:

-   Business case

-   Service readiness

-   Adoption plan

-   Operational plan

### Business case

Business use cases, stakeholders, OKRs and KSIs, risks, and project timelines typically make up the bulk of information required for a business case. You need to document them as part of the success plan.

### Service readiness

Environmental assessment provides the initial information required to determine technical readiness for the organization to implement Audio Conferencing.

Included here is the plan to address areas needing remediation discovered through environmental assessment. You need to include the service readiness assessment and remediation plan as part of the success plan.

### Adoption plan

Following an adoption readiness assessment, further detailed planning must be completed for the project team to come up with a comprehensive set of communication plans, training plan, and pre-launch, at-launch, and post-launch adoption activities.

Resources to support adoption activities such as flyers, welcome emails, and training materials are identified at this step, along with any customizations needed to meet organizational requirements.

The templates for adoption activities are available [here](https://www.microsoft.com/en-us/download/details.aspx?id=54244%22﷟HYPERLINK%20%22https://aka.ms/TeamsCloudVoiceResourceKit)[](https://aka.ms/TeamsCloudVoiceResourceKit).

### Operational plan

Operational roles mapping exercise will establish the roles and responsibilities, and the teams assigned to each operational role to support the implementation of Audio Conferencing.

You need to complete this and include the operational plan as part of the success plan to ensure operational readiness of the solution.

Planning for Audio Conferencing in Microsoft Teams
--------------------------------------------------

To plan for the implementation of Audio Conferencing in Microsoft Teams, a series of decisions must be made ahead of time to better prepare your organization to implement a solution that meets business requirements. These decisions will be documented into a technical implementation plan.

|  |  |
|---------|---------|
|  <iframe width="350" height="200" src="https://www.youtube.com/embed/Q3dnPyCOUKM" frameborder="0" allowfullscreen></iframe>    | |


### Availability of Audio Conferencing

Audio Conferencing is available in these [countries and regions](https://support.office.com/en-us/article/Countries-and-regions-that-are-supported-for-Skype-for-Business-Online-PSTN-Services-6ba72f37-d303-4795-aa8f-7e1845078ed7?ui=en-US&rs=en-US&ad=US).

<table>
<thead>
<tr class="header">
<td align="center">
<p><img src="media/audio_conferencing_image6.png" /></p>
<p>Important</p></td>
<td align="left">Due to legal constraints, for Audio Conferencing to be available to multinational organizations, the contract for Office 365 subscriptions must be sourced from countries and regions covered by Audio Conferencing service.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

After confirming your organization’s eligibility for obtaining the Audio Conferencing service, compile the list of user locations or offices where Audio Conferencing service will be implemented based on the list of available countries and regions.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><p>Decide which user locations or offices will implement the Audio Conferencing service.</p></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><p>Document the user locations or offices to be enabled for the Audio Conferencing service.</p></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">Office</th>
<th align="left">Location</th>
<th align="left">PSTN Conference Service</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">One Epping Road</td>
<td align="left">Australia</td>
<td align="left">Audio Conferencing</td>
</tr>
<tr class="even">
<td align="left">100 Cyberport Road</td>
<td align="left">Hong Kong SAR</td>
<td align="left">Legacy PSTN Conferencing</td>
</tr>
<tr class="odd">
<td align="left">One Marina Boulevard</td>
<td align="left">Singapore</td>
<td align="left">Audio Conferencing</td>
</tr>
<tr class="even">
<td align="left">32 London Bridge Street</td>
<td align="left">United Kingdom</td>
<td align="left">Audio Conferencing</td>
</tr>
<tr class="odd">
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">France</td>
<td align="left">Audio Conferencing</td>
</tr>
</tbody>
</table>

_Table 7 Example of Audio Conferencing service site enablement list_


### Licensing for Audio Conferencing

[Audio Conferencing license](https://support.office.com/en-us/article/Skype-for-Business-add-on-licensing-3ed752b1-5983-43f9-bcfd-760619ab40a7?ui=en-US&rs=en-US&ad=US), formerly known as Skype for Business PSTN Conferencing license, is available as part of Office 365 E5 subscription plans, or as an add-on to Office 365 E1 or Office 365 E3 subscription plans.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left"><p>PSTN or dial-in conferencing in Teams does not support 3<sup>rd</sup> party Audio Conferencing Providers (ACPs).</p>
<p>If you already use Skype for Business Online PSTN Conferencing today, you can immediately take advantage of Audio Conferencing in Teams.</p></td>
</tr>
</thead>
<tbody>
</tbody>
</table>

To provide toll-free conference bridge phone numbers and to support conferencing dial-out to International phone numbers, you need to setup [Communications Credits](https://support.office.com/en-us/article/What-is-PSTN-Consumption-billing-524dbea7-117f-493d-8005-6461f7f10059) for your organization.

<table>
<thead>
<tr class="header">
<td align="center">
<p><img src="media/audio_conferencing_image6.png" /></p>
<p>Important</p></td>
<td align="left">Some countries are serviced by toll-free conference bridge phone numbers only, and in this case the use of Communications Credits is a mandatory requirement to support dial in for such countries.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

The first consideration to make when implementing Communications Credits is to decide the initial amount of funds to be purchased. Recommended funding amounts can be referenced from the [Communications Credits](https://support.office.com/en-us/article/What-is-PSTN-Consumption-billing-524dbea7-117f-493d-8005-6461f7f10059) documentation.

If your organization chooses to use auto-recharge, a recommendation on the trigger (lowest amount of funds) is also included in the [Communications Credits](https://support.office.com/en-us/article/What-is-PSTN-Consumption-billing-524dbea7-117f-493d-8005-6461f7f10059) documentation. Auto-recharge amount needs to be determined by the actual usage. Communications Credits usage should be monitored over time and the recharge amount needs to be adjusted as required.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>If your organization has not already purchased the required Audio Conferencing licensing, decide whether Audio Conferencing licenses will be acquired by stepping up existing Office 365 subscriptions or by acquiring Audio Conferencing add-ons.</li>
<li>Decide if Communications Credits is required for Audio Conferencing implementation. If so, decide the initial amount of funds to be purchased. Where applicable, decide the trigger amount and auto-recharge amount.</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the users that will be assigned Audio Conferencing license.</li>
<li>Document the Communications Credits plan (initial amount, trigger amount, auto-recharge amount).</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">User</th>
<th align="left">Office</th>
<th align="left">Office 365 License</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Adele Vance</td>
<td align="left">One Epping Road</td>
<td align="left">Office 365 E5</td>
</tr>
<tr class="even">
<td align="left">Alex Wilber</td>
<td align="left">One Epping Road</td>
<td align="left">Office 365 E3, Audio Conferencing add-on</td>
</tr>
<tr class="odd">
<td align="left">Ben Walters</td>
<td align="left">One Epping Road</td>
<td align="left">Office 365 E3, Audio Conferencing add-on</td>
</tr>
<tr class="even">
<td align="left">Christie Cline</td>
<td align="left">One Marina Boulevard</td>
<td align="left">Office 365 E3, Audio Conferencing add-on</td>
</tr>
<tr class="odd">
<td align="left">Debra Berger</td>
<td align="left">One Marina Boulevard</td>
<td align="left">Office 365 E5</td>
</tr>
<tr class="even">
<td align="left">Lee Gu</td>
<td align="left">One Marina Boulevard</td>
<td align="left">Office 365 E5</td>
</tr>
<tr class="odd">
<td align="left">Emily Braun</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Office 365 E5</td>
</tr>
<tr class="even">
<td align="left">Lidia Holloway</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Office 365 E5</td>
</tr>
<tr class="odd">
<td align="left">Pradeep Gupta</td>
<td align="left">32 London Bridge Street</td>
<td align="left">Office 365 E5</td>
</tr>
<tr class="even">
<td align="left">Marcel Beauchamp</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Office 365 E3, Audio Conferencing add-on</td>
</tr>
<tr class="odd">
<td align="left">Rachelle Cormier</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Office 365 E5</td>
</tr>
<tr class="even">
<td align="left">Isabell Potvin</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Office 365 E3, Audio Conferencing add-on</td>
</tr>
</tbody>
</table>

_Table 8 Example of license assignment list for Audio Conferencing meeting organizers_

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


### Conference Bridge Phone Numbers

The Audio Conferencing service in Office 365 includes:

-   Multiple types of conference bridge phone numbers (Toll and Toll-Free)

-   Multiple categories of the phone number (dedicated and shared)

-   Support for multiple languages for the conference bridge (primary and secondary)

-   A default phone number for the tenant.

Full description of the included capabilities can be referenced from [Set up dial-in or PSTN conferencing for Skype for Business](https://support.office.com/en-us/article/Set-up-dial-in-or-PSTN-conferencing-for-Skype-for-Business-d01954f1-4f37-4cf5-a636-20039e5c59e9?ui=en-US&rs=en-US&ad=US) and [Phone numbers for dial-in conferencing](https://support.office.com/en-us/article/Phone-numbers-for-dial-in-conferencing-95a08f84-04e5-4f72-88a8-d6472a7c89d7?ui=en-US&rs=en-US&ad=US)**.**

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left">Dedicated conference bridge phone numbers are counted towards the limit of phone numbers that can be acquired per tenant, based on the number of applicable licenses as described in <a href="https://support.office.com/en-us/article/Getting-Skype-for-Business-service-phone-numbers-e434aeb2-af99-40e7-981e-a474f0383734">Getting Skype for Business service phone numbers</a>. Toll-Free conference bridge phone numbers require Communications Credits.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

If there are existing conference bridge phone numbers that must be transferred to the Audio Conferencing service, assuming they are meeting the country-specific requirements, then the existing conference bridge phone numbers can be transferred to Microsoft.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left">Complexity of transferring phone numbers to Microsoft varies greatly based on the countries or regions, carriers, the number of circuits involved, and many other contributing factors. To plan for phone number porting, check out the <a href="https://go.microsoft.com/fwlink/?linkid=859011">Number Porting Guide</a> for the details.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

| <iframe width="350" height="200" src="https://www.youtube.com/embed/Cjr2wkVa0lM" frameborder="0" allowfullscreen></iframe>  |  |

Additional details on transferring phone numbers to Audio Conferencing service can be found in [Transfer phone numbers to Skype for Business Online](https://support.office.com/en-us/article/Transfer-phone-numbers-to-Skype-for-Business-Online-47b3af8e-4171-4dec-8333-c956f108664e).

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>Decide whether the organization requires dedicated conference bridge phone numbers</li>
<li>Decide how the dedicated conference bridge phone numbers will be obtained for user locations or offices in-scope for the Audio Conferencing implementation (obtain from Microsoft or transfer existing phone numbers)</li>
<li>If you choose to obtain from Microsoft, decide the method to obtain phone numbers (form submission or automated) for user locations or offices in-scope for the Audio Conferencing implementation</li>
<li>Decide the language preferences to be set up for each dedicated conference bridge phone number</li>
<li>Decide the tenant default conference bridge phone number</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the master plan for phone numbers acquisition, detailing how phone numbers will be obtained for each user location or office in-scope for the Audio Conferencing implementation.</li>
<li>If applicable, complete <a href="https://support.office.com/en-us/article/Get-phone-numbers-for-Skype-for-Business-Online-6b61cb3c-361c-48a8-a9ef-d81bddde27bb?ui=en-US&amp;rs=en-US&amp;ad=US">the New Telephone Number Request form</a>, one form for each location or office</li>
<li>If you choose to transfer existing phone numbers, check out the <a href="https://go.microsoft.com/fwlink/?linkid=859011">Number Porting Guide</a> to plan it and adjust Audio Conferencing implementation timeline accordingly.</li>
<li>Document the detailed conference bridge phone number configurations (shared and dedicated conference bridge phone numbers, language preferences for each dedicated conference bridge phone number, tenant default conference bridge phone number)</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">Office</th>
<th align="left">Bridge Number Acquisition and Bridge Type</th>
<th align="left">Bridge Number</th>
<th align="left">Bridge Language</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">One Epping Road</td>
<td align="left">Acquire new, dedicated</td>
<td align="left">TBA</td>
<td align="left">English (Australia)</td>
</tr>
<tr class="even">
<td align="left">One Marina Boulevard</td>
<td align="left">Acquire new, shared</td>
<td align="left">TBA</td>
<td align="left">English (United States), Chinese (Simplified, PRC)</td>
</tr>
<tr class="odd">
<td align="left">32 London Bridge Street</td>
<td align="left">Port existing, dedicated</td>
<td align="left">+44 20 7654 8001</td>
<td align="left">English (United Kingdom)</td>
</tr>
<tr class="even">
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">Acquire new, dedicated</td>
<td align="left">TBA</td>
<td align="left">French (France), English (United Kingdom)</td>
</tr>
</tbody>
</table>

_Table 10 Example of conference bridge details_


<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left">The example table above and subsequent tables throughout this document serve as a template and will denote TBA (to be added) for information that you need to complete as part of your planning process.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

### Conference Bridge Settings

Organization-wide configuration options around Audio Conferencing meeting join experience (meeting entry and exit notification and caller name recording), meeting organizer’s PIN length, and email notification are available to further tailor the end-user experience.

-   Meeting entry and exit notifications are available in the form of recorded name, phone number, and tones.

-   PIN length is configurable from 4 to 12 digits, with a 5-digit PIN as the default.

-   Notification emails upon enablement of Audio Conferencing license or any other admin-driven changes are enabled by default. You can disable this feature and take control of your organization’s end-user communications.

For users who are assigned an Audio Conferencing license, the default toll/toll-free numbers, shown in the Audio Conferencing coordinates, are configurable to use:

-   the tenant-level default, or

-   the automatically-assigned conference bridge phone numbers, or

-   manually defined conference bridge phone numbers for each user.

User-specific conference bridge phone numbers are typically useful in global or nationwide organizations where users are distributed and must provide local numbers as the default conference bridge phone numbers in the meeting invites.

Participants joining from different cities or overseas can look up additional numbers configured at the tenant-level, but these numbers do not appear directly in the meeting invites. The meeting invites provide a link that will take participants to the Microsoft Teams Conference Dial-in Numbers page for them to lookup the closest conference bridge phone numbers available from their location.

You can also configure how unauthenticated callers are handled by each individual meeting organizer, whether to require meeting organizer to start the meeting before unauthenticated callers are admitted, or to allow unauthenticated callers to start a meeting.

Additional configurations that can be applied for each user are available to control the use of toll-free conference bridge phone numbers and dial-out from a conference.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left">These cost-related controls are currently available for preview customers only. You can enroll your organization to the preview program from <a href="https://go.microsoft.com/fwlink/?linkid=859013" class="uri">https://www.skypepreview.com</a></td>
</tr>
</thead>
<tbody>
</tbody>
</table>

With these controls, you can decide whether meeting organizers can provide toll-free conference bridge phone numbers for meetings organized by them, and to control whether participants can dial out from the meetings organized by them. The level of dial-out control spans from disallowing dial out, only allowing dial out to domestic numbers, to allowing dial out to both domestic and international numbers.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>Decide whether the organization requires entry and exit notifications, and if yes, the type of notification to be implemented (tones, phone number, or recorded name).</li>
<li>Decide the Audio Conferencing PIN length that meets the organizational security requirements.</li>
<li>Decide if the organization wants to take control of end-user communications related to Audio Conferencing service.</li>
<li>Decide the conference bridge phone numbers to be assigned to each meeting organizer.</li>
<li>Decide whether some meeting organizers require the ability to use toll-free conference bridge phone numbers for their meeings</li>
<li>Decide whether some meeting organizers require the ability to allow unauthenticated callers to start a meeting.</li>
<li>Decide whether some meeting organizers require conference dial out to be controlled.</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the detailed conference bridge settings (entry and exit notifications, PIN length, configuration change email notification).</li>
<li>Document the conference bridge phone numbers to be assinged to each meeting organizer and the corresponding setting to control unauthenticated caller’s policy, and toll-free and dial out controls.</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left"><strong>Enable meeting entry and exit notifications</strong></th>
<td align="left">Enabled</td>
</tr>
</thead>
<thead>
<tr class="header">
<th align="left"><strong>Entry/exit announcement type</strong></th>
<td align="left">Tones</td>
</tr>
<tr class="header">
<th align="left"><strong>Ask callers to record their name before joining the meeting</strong></th>
<td align="left">Disabled</td>
</tr>
<tr class="header">
<th align="left"><strong>PIN length</strong></th>
<td align="left">5</td>
</tr>
<tr class="header">
<th align="left"><strong>Automatically send emails to users if their dial-in settings change</strong></th>
<td align="left">Disabled</td>
</tr>
</tbody>
</table>

_Table 11 Example of conference bridge settings_


<table>
<thead>
<tr class="header">
<th align="left">User</th>
<th align="left">Office</th>
<th align="left">Default toll number</th>
<th align="left">Default toll-free number</th>
<th align="left">Allow toll-free</th>
<th align="left">Unauthenticated callers bypass lobby</th>
<th align="left">Conference dial out</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Adele Vance</td>
<td align="left">One Epping Road</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Enabled</td>
<td align="left">International and domestic</td>
</tr>
<tr class="even">
<td align="left">Alex Wilber</td>
<td align="left">One Epping Road</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">No</td>
<td align="left">Disabled</td>
<td align="left">Not allowed</td>
</tr>
<tr class="odd">
<td align="left">Ben Walters</td>
<td align="left">One Epping Road</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">No</td>
<td align="left">Disabled</td>
<td align="left">Not allowed</td>
</tr>
<tr class="even">
<td align="left">Christie Cline</td>
<td align="left">One Marina Boulevard</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Disabled</td>
<td align="left">Domestic</td>
</tr>
<tr class="odd">
<td align="left">Debra Berger</td>
<td align="left">One Marina Boulevard</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Enabled</td>
<td align="left">Domestic</td>
</tr>
<tr class="even">
<td align="left">Lee Gu</td>
<td align="left">One Marina Boulevard</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Enabled</td>
<td align="left">Domestic</td>
</tr>
<tr class="odd">
<td align="left">Emily Braun</td>
<td align="left">32 London Bridge Street</td>
<td align="left">+44 20 7654 8001</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Enabled</td>
<td align="left">Not allowed</td>
</tr>
<tr class="even">
<td align="left">Lidia Holloway</td>
<td align="left">32 London Bridge Street</td>
<td align="left">+44 20 7654 8001</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Disabled</td>
<td align="left">Not allowed</td>
</tr>
<tr class="odd">
<td align="left">Pradeep Gupta</td>
<td align="left">32 London Bridge Street</td>
<td align="left">+44 20 7654 8001</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Disabled</td>
<td align="left">Not allowed</td>
</tr>
<tr class="even">
<td align="left">Marcel Beauchamp</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">No</td>
<td align="left">Disabled</td>
<td align="left">Domestic</td>
</tr>
<tr class="odd">
<td align="left">Rachelle Cormier</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">Yes</td>
<td align="left">Enabled</td>
<td align="left">International and domestic</td>
</tr>
<tr class="even">
<td align="left">Isabell Potvin</td>
<td align="left">39 quai du Président Roosevelt</td>
<td align="left">TBA</td>
<td align="left">TBA</td>
<td align="left">No</td>
<td align="left">Disabled</td>
<td align="left">Domestic</td>
</tr>
</tbody>
</table>

_Table 12 Example of conference bridge settings assignments_


### Dial Plans

A [Dial Plan](https://support.office.com/en-US/article/What-are-PSTN-Calling-dial-plans-2f0cfb59-1ca1-4e31-84ce-09d0b1a7ce1b), a Phone System feature of Office 365, is a set of normalization rules that translates dialed phone numbers into an alternate format (typically [E.164](https://go.microsoft.com/fwlink/?linkid=859014) format) for call authorization and call routing. Audio Conferencing service leverages the same capabilities used by Phone System to translate dialed phone numbers in conference dial out scenarios.

A dial plan allows users to dial phone numbers the way they are accustomed to, such as omitting area code for local calls, omitting country code for domestic calls, or even using short digit dialing when performing conference dial out.

Within the Phone System feature of Office 365, there are two types of dial plans:

-   **Service dial plan**. This is the default dial plan and applied to users based on Office 365 usage location, and it cannot be modified.

<!-- -->

-   **Tenant dial plan**. This is a customizable dial plan within a tenant, and further divided into two types:

    -   **Tenant-global dial plan**—the dial plan applies to all users within the tenant.

    -   **Tenant-user dial plan**—the dial plan applies only to specific users.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left">Check out the <a href="https://support.office.com/en-US/article/What-are-PSTN-Calling-dial-plans-2f0cfb59-1ca1-4e31-84ce-09d0b1a7ce1b">Calling Plan dial plans</a> documentation for further details and examples.</td>
</tr>
</thead>
<tbody>
</tbody>
</table>

The effective dial plan assigned to users is the combination of service dial plan (based on user’s Office 365 usage location) and tenant dial plan (can be either tenant-global dial plan or tenant-user dial plan).

![](media/audio_conferencing_image8.png)

There is a maximum of 25 normalization rules in each tenant dial plan, and thus duplication with normalization rules already available as part of service dial plan needs to be avoided.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Points</td>
<td align="left"><ul><li>Decide if your organization requires customized dial plans (business requirements, adoption requirements, etc.).</li>
<li>If applicable, decide the scope of tenant dial plan (tenant-global or tenant-user) to support the requirements for customized dial plans.</li>
<li>If applicable, decide the tenant dial plans that will be created to support user locations or offices in-scope for the Audio Conferencing implementation.</li>
<li>If applicable, decide which user require customized dial plan and the tenant dial plan to be assigned for each user.</li></ul></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><ul><li>Document the customized dial plans and the associated normalization rules to be configured as part of Audio Conferencing implementation.</li>
<li>Document the users to be assigned with customized dial plan and the tenant dial plan to be assigned for each user.</li></ul></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left">Tenant Dial Plan Name/Description</th>
<th align="left">Normalization Rules Name/Description</th>
<th align="left">Pattern</th>
<th align="left">Translation</th>
<th align="left">IsInternalExtension</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>AU-NSW-NorthRyde-OER</strong></p>
<p><em>One Epping Road North Ryde, NSW, AU Dial Plan</em></p></td>
<td align="left"><p><strong>AU-NSW-NorthRyde-OER-Internal</strong></p>
<p><em>Internal number (x7000 - x7999) for One Epping Road office, North Ryde, NSW, Australia</em></p></td>
<td align="left">^(7\d{3})$</td>
<td align="left">+6123218$1</td>
<td align="left">True</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"><p><strong>AU-NSW-Local</strong></p>
<p><em>Local number normalization for NSW, Australia</em></p></td>
<td align="left">^([2-9]\d{7})$</td>
<td align="left">+612$1</td>
<td align="left">False</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><p><strong>AU-TollFree</strong></p>
<p><em>Toll Free number normalization for Australia</em></p></td>
<td align="left">^(1[38]\d{4,8})\d*$</td>
<td align="left">+61$1</td>
<td align="left">False</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"><p><strong>AU-Service</strong></p>
<p><em>Service number normalization for Australia</em></p></td>
<td align="left">^(000|1[0125]\d{1,8})$</td>
<td align="left">$1</td>
<td align="left">False</td>
</tr>
<tr class="odd">
<td align="left"><p><strong>SG-Singapore-OMB</strong></p>
<p><em>OMB Singapore, SG Dial Plan</em></p></td>
<td align="left"><p><strong>SG-OMB-Internal</strong></p>
<p><em>Internal number (x8000 – x8999) for OMB office, Singapore</em></p></td>
<td align="left">^(8\d{3})$</td>
<td align="left">+656888$1</td>
<td align="left">True</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"><p><strong>SG-TollFree</strong></p>
<p><em>Toll Free number normalization for Singapore</em></p></td>
<td align="left">^(1?800\d{7})\d*$</td>
<td align="left">+65$1</td>
<td align="left">False</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><p><strong>SG-Service</strong></p>
<p><em>Service number normalization for Singapore</em></p></td>
<td align="left">^(1\d{3,4}|9\d{2})$</td>
<td align="left">$1</td>
<td align="left">False</td>
</tr>
<tr class="even">
<td align="left"><p><strong>FR-Paris-Issy-39qdPR</strong></p>
<p><em>39 quai du Président Roosevelt Issy-les-Moulineaux, France Dial Plan</em></p></td>
<td align="left"><p><strong>FR-39qdPR-Internal</strong></p>
<p><em>Internal number (x7000 – x7999) for 39 quai du Président Roosevelt office, Issy-les-Moulineaux, France</em></p></td>
<td align="left">^(7\d{3})$</td>
<td align="left">+3315885$1</td>
<td align="left">True</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><p><strong>FR-TollFree</strong></p>
<p><em>Toll Free number normalization for France</em></p></td>
<td align="left">^0?(80\d{7})\d*$</td>
<td align="left">+33$1</td>
<td align="left">False</td>
</tr>
<tr class="even">
<td align="left"></td>
<td align="left"><p><strong>FR-Service</strong></p>
<p><em>Service number normalization for France</em></p></td>
<td align="left"><p>^(1\d{1,2}|11[68]\d{3}|</p>
<p>10\d{2}|3\d{3})$</p></td>
<td align="left">$1</td>
<td align="left">False</td>
</tr>
</tbody>
</table>

_Table 13 Example of tenant dial plans_


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
<td align="left">Adele Vance</td>
<td align="left">One Epping Road</td>
<td align="left">Tenant dial plan</td>
<td align="left">AU-NSW-NorthRyde-OER</td>
</tr>
<tr class="even">
<td align="left">Alex Wilber</td>
<td align="left">One Epping Road</td>
<td align="left">Tenant dial plan</td>
<td align="left">AU-NSW-NorthRyde-OER</td>
</tr>
<tr class="odd">
<td align="left">Ben Walters</td>
<td align="left">One Epping Road</td>
<td align="left">Tenant dial plan</td>
<td align="left">AU-NSW-NorthRyde-OER</td>
</tr>
<tr class="even">
<td align="left">Christie Cline</td>
<td align="left">One Marina Boulevard</td>
<td align="left">Tenant dial plan</td>
<td align="left">SG-Singapore-OMB</td>
</tr>
<tr class="odd">
<td align="left">Debra Berger</td>
<td align="left">One Marina Boulevard</td>
<td align="left">Tenant dial plan</td>
<td align="left">SG-Singapore-OMB</td>
</tr>
<tr class="even">
<td align="left">Lee Gu</td>
<td align="left">One Marina Boulevard</td>
<td align="left">Tenant dial plan</td>
<td align="left">SG-Singapore-OMB</td>
</tr>
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

_Table 14 Example of dial plan assignments_


### Microsoft Teams Configurations

Since Audio Conferencing is only available for scheduled meetings, tenant-level configurations that govern meeting scheduling (private and channel meetings) must be enabled.

<table>
<thead>
<tr class="header">
<td align="center"><p><img src="media/audio_conferencing_image1.png" /></p>
<p>Note</p></td>
<td align="left"><p>Currently, if your organization has compliance requirements to ensure all meeting discussions are discoverable, you should disable private meetings if the organizer has an Exchange on-premises mailbox.</p>
<p>In another use case, if all meetings in the organization must be visible <strong>to invited parties</strong> only, to avoid disclosing meeting information to uninvited parties, we recommend that you disable the ability to schedule meetings in <strong>channels</strong>.</p></td>
</tr>
</thead>
<tbody>
</tbody>
</table>

The settings, available as tenant-level configurations, are applicable to all users in the organization, and will impact all meeting scheduling in Teams, not specific to Teams meetings **with** Audio Conferencing.

<table>
<thead>
<tr class="header">
<td align="left"><img src="media/audio_conferencing_image7.png" /></td>
<td align="left">Decision Point</td>
<td align="left"><p>Decide if the organization requires to enable or disable scheduling of private meetings.</p>
<p>Decide if the organization requires to enable or disable scheduling of channel meetings.</p></td>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><img src="media/audio_conferencing_image9.png" /></td>
<td align="left">Next Steps</td>
<td align="left"><p>Document the meeting scheduling configurations for Microsoft Teams.</p></td>
</tr>
</tbody>
</table>

<table>
<thead>
<tr class="header">
<th align="left"><strong>Allow scheduling for private meetings</strong></th>
<td align="left">Enabled</td>
</tr>
</thead>
<thead>
<tr class="odd">
<th align="left"><strong>Allow scheduling for channel meetings</strong></th>
<td align="left">Disabled</td>
</tr>
</tbody>
</table>

_Table 15 Example of Microsoft Teams meetings configurations_


Document technical implementation plan
--------------------------------------

Use the decision points above to document your technical implementation plan.

This technical implementation plan will provide the project team, which can include FastTrack or a deployment partner, with the information required to execute the technical onboarding for the implementation of Audio Conferencing.

In general, a technical implementation plan will contain the following main sections:

-   Audio Conferencing service site enablement list

-   License assignment list for Audio Conferencing meeting organizers

-   Communications Credits planning numbers

-   Conference bridge details

-   Conference bridge settings

-   Conference bridge settings assignments

-   Tenant dial plans

-   Dial plan assignments

-   Microsoft Teams meetings configurations

With the completion of success plan and technical implementation plan, you are now ready to take your organization to the next steps along the Office 365 customer journey.

Onboard
=======

*Coming soon.*

Drive Value
===========

*Coming soon.*
