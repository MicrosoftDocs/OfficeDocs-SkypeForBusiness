---
title: Practical Guidance for Phone System with Calling Plans in Microsoft Teams
author: arachmanGitHub
ms.author: MyAdvisor
manager: serdars
ms.date: 08/21/2018
ms.topic: article
ms.service: msteams
ms.reviewer: MyAdvisor
description: Practical guidance for planning, deploying, and managing Phone System with Calling Plans in Microsoft Teams using the Envision (Plan), Onboard (Deliver), Drive Value (Operate) framework.
localization_priority: Normal
search.appverid: MET150
appliesto: 
- Microsoft Teams
redirect_url: https://docs.microsoft.com/MicrosoftTeams/cloud-voice-deployment
---

Practical Guidance for Phone System with Calling Plans in Microsoft Teams
=========================================================================

Phone System is an Office 365 feature that provides the ability to manage call routing, policies, and user provisioning. This includes phone calling management system, call routing, and call control.

Office 365 Calling Plans is an add-on service for the Phone System feature, delivered through Teams and Skype for Business Online. Calling Plans provide the people in your business with a primary phone number and lets them make and receive phone calls outside of your organization over the public switched telephone network (PSTN).

To learn more, read [Here's what you get with Phone System in Office 365](https://docs.microsoft.com/SkypeForBusiness/what-is-phone-system-in-office-365/here-s-what-you-get-with-phone-system) and [What are Calling Plans in Office 365?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-calling-plans-in-office-365)

This practical guidance takes you through the Office 365 FastTrack customer journey framework and its three phases - Envision, Onboard, and Drive Value - to help you plan, deliver, and operate a successful Phone System with Calling Plans implementation.

> [!TIP]
> In this practical guidance, we are providing example outputs for each activity and key discussion. The examples throughout this document are enclosed inside TIP callouts and they serve as a template that you can reuse. You'll see "TBA" (to be added) for information that you need to complete as part of your planning process.

Envision <a name="Envision_PhoneSystemWithCallingPlans"> </a>
========

The Envision phase provides the foundation for the Office 365 customer journey and is applicable to all workloads, including Phone System with Calling Plans.

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

> [!TIP]
> The following is an example of a completed business use case:
> 
> |         |
> |---------|
> |**Description of current business process**<p>Standard configuration of Contoso’s office workspaces includes a desktop phone for every desk. Each employee will be provided with a direct inward dialing (DID) phone number. The desktop phones are connected to a PBX system and connected to PSTN via session initiation protocol (SIP) trunk. Employees can only make and receive phone calls at their assigned desktop phones.|
> |**Challenges with existing business process**<p>Usage analysis of the desktop phones shows that only 10% of the desktop phones are actively used, with the rest either configured to forward calls to mobile phones, or configured to simultaneously ring to mobile phones. Maintenance of existing PBX system and the associated desktop phones contributes to 20% of monthly telephony service cost.|
> |**How technology can overcome these challenges**<p>Phone System with Calling Plans will allow end user’s personal computer to receive and place phone calls over data network by leveraging the native Microsoft Teams app, removing the necessity to roll out and maintain desktop phones, and opens the opportunity to decommission the existing PBX system, as the phone service can be delivered via the cloud over the network with no dependency on traditional phone system.|
> |**Expected, measurable, business outcomes**<p>Removing requirements to maintain and decommissioning existing legacy PBX and desktop phones, will deliver a 20% reduction of monthly telephony service expense. Phone System with Calling Plans will simplify office workspaces, allowing Contoso to expand its operations by establishing new offices with minimal upfront telephony costs.|

During the Envision phase, in addition to defining your business use cases, you should also get clarity around these items:
- Organizational scope
- Project timelines

Identify key stakeholders
-------------------------

The business use cases defined in the previous step will include organizational scope of Phone System with Calling Plans implementation. Based on that, you can complete the comprehensive stakeholder matrix to include the right people to be involved in the project.

> [!TIP]
> Below is an example of stakeholder matrix template that you can use to document the project stakeholders:
> 
> |                 Role                  |                                                                                                                                                                                                                                                                Description                                                                                                                                                                                                                                                                 | Name, contact information, location |
> |---------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------|
> |       Project Executive Sponsor       | <ul><li>Ultimate authority and accountability for the project and delivery on project objectives</li><li>Help resolve issues escalated by Project Lead</li><li>Sponsors communication within the company about project goals</li><li>Responsible for making key strategic decisions</li><li>Responsible for availability of required resources and budget</li><li>Leading Quarterly Business Reviews (QBR)</li><li>Buy-In and support of awareness campaign effort</li><li>Serving as the Project Sponsor to the program rollout</li></ul> |                 TBA                 |
> |             Project Lead              |                   <ul><li>Managing and leading project team</li><li>Coordinates partners and working teams engaged in the project</li><li>Accountable for creating and managing project plans to meet quarterly key results</li><li>Resolving cross-functional issues</li><li>Providing regular updates to the project sponsors</li><li>Incorporating Adoption aspects into the all-up project plan</li><li>Leading Monthly Business and Operational Reviews (MBR), contributing to Quarterly Business Reviews</li></ul>                   |                 TBA                 |
> |     Collaboration Lead/Architect      |                                                                       <ul><li>Responsible for execution on collaboration strategy defined by company executives</li><li>Analyzing and choosing collaboration products for the company that meets business goals</li><li>Responsible for the design of the operations for collaboration products</li><li>Defines operation and support model</li><li>Contributing to Monthly and Quarterly Business Reviews</li><ul>                                                                        |                 TBA                 |
> |              Consultant               |                                                                                                                                                                                                               <ul><li>Responsible for configuration services</li><li>Contributes in overall solution architecture</li></ul>                                                                                                                                                                                                                |                 TBA                 |
> |            Project Manager            |                                                      <ul><li>Developing and maintaining project plan</li><li>Managing project deliverables in line with project plan and budget</li><li>Recording and managing project issues, including escalations</li><li>Conducting weekly stand up calls</li><li>Liaises with, and provides updates to project executive sponsors</li><li>Working with the Architect to define the Change Management approach and Communication Plans</li></ul>                                                       |                 TBA                 |
> | Change Management/Adoption Specialist |                                                                                       <ul><li>Provide input on Discovery phase into adoption and training processes</li><li>Participate in adoption strategy workshop</li><li>Developing and responsible for adoption strategy</li><li>Developing and executing communication plan</li><li>Responsible for delivering trainings to end users</li><li>Collect feedback and conduct surveys</li></ul>                                                                                        |                 TBA                 |
> |             Network Lead              |                                                                                                                                                              <ul><li>Providing input on Discovery phase into network design</li><li>Participating in planning during Envisioning workshop</li><li>Coordinates work of networking team during the project execution</li></ul>                                                                                                                                                               |                 TBA                 |
> |             Security Lead             |                                                                                                                                                        <ul><li>Providing input on Discovery phase into security design and processes</li><li>Participating in planning during Envisioning workshop</li><li>Coordinates work of security team during the project execution</li></ul>                                                                                                                                                        |                 TBA                 |
> |            Telephony Lead             |                                                                                                                                                              <ul><li>Providing input on Discovery phase into telephony design</li><li>Participating in planning during envisioning workshop</li><li>Coordinates work of telephony team during the project execution</li></ul>                                                                                                                                                              |                 TBA                 |
> |             Desktop Lead              |                                                                                                                                                          <ul><li>Providing input on Discovery phase into clients and update process</li><li>Participating in planning during envisioning workshop</li><li>Coordinates work of desktop team during the project execution</li></ul>                                                                                                                                                          |                 TBA                 |
> |        Support/Help Desk Lead         |                                                                                                                          <ul><li>Providing input on Discovery phase into operational and support model</li><li>Participating in planning during envisioning workshop</li><li>Participating into support model planning</li><li>Coordinates work of support teams/resources during the project execution</li></ul>                                                                                                                          |                 TBA                 |
> |     Business Unit Representatives     |                                                                                                                                                                                                      <ul><li>Contribute in End User based adoption guides and materials</li><li>Contribute to and review Business Use Cases</li></ul>                                                                                                                                                                                                      |                 TBA                 |
> |            Deployment Lead            |                                                                                                                                                           <ul><li>Ensure that deployment prerequisites are met</li><li>Engage customer resources to engage on prepare and deploy stage activities</li><li>Participate in meetings to review prepare and deploy status</li></ul>                                                                                                                                                            |                 TBA                 |
> |               IT Admins               |                                                                                                                                                                                                                           <ul><li>IT Pros responsible for assistance with test planning and execution</li></ul>                                                                                                                                                                                                                            |                 TBA                 |
> |             Service Owner             |                                                                                                                                                                                     <ul><li>Is responsible for the operation of the Phone System with Calling Plans service all up</li><li>Owner of Phone System with Calling Plans service</li></ul>                                                                                                                                                                                      |                 TBA                 |
> |           Quality Champions           |                                                                                                      <ul><li>Drives quality, reliability and user feedback</li><li>Identifies the quality trends and drive remediation with the respective teams</li><li>Reports through the steering committee back to leadership</li><li>Reports on quality, reliability, and user sentiment through Rate My Call and Net Promoter Score</li></ul>                                                                                                       |                 TBA                 |

Define objectives and key results, key success indicators, and risks
--------------------------------------------------------------------

With the project stakeholders assembled, business use cases, organizational scope and project timelines can be translated into your objectives and key results (OKRs) and the measures of project success can be defined into a list of key success indicators (KSIs).

Full participation from project stakeholders when defining the OKRs and KSIs will ensure sense of ownership and they are aligned to organizational business requirements.

OKRs will contain the list of objectives set in the beginning of the project, with measurable key results defined in a quarterly basis. The key results are reviewed monthly to track status of the overall project, and based on progress, adjustment to the quarterly plans can be made as needed.

> [!TIP]
> Example of OKRs relevant to Phone System with Calling Plans implementation can be referenced below:
> <br>
> 
> **Vision: Increase productivity by maximizing Office 365 investments**
> 
> |Objectives  |Key Results  |To Do  |
> |---------|---------|---------|
> |Deploy Phone System with Calling Plans in European branch offices by end of fiscal year 2018|FY18Q3: Deploy Phone System with Calling Plans in London office|Envision<ul><li>Create success plan</li><li>Create detailed technical implementation plan</li></ul><p>Onboard<ul><li>Execute success plan</li><li>Execute technical implementation plan</li></ul>|
> |Decommission legacy PBX in London office by end of fiscal year 2018|FY18Q4: Decommission legacy PBX in London office|Drive Value<ul><li>Boost user engagement and drive adoption</li><li>Manage and prepare change</li><li>Measure, share success, and iterate</li>|

KSIs measure quality and success of the key results and complement the binary nature of OKRs (achieved or not achieved), by detailing the good and/or bad results. When defining KSIs, we recommend leveraging the “specific, measurable, assignable, realistic, time-related” or SMART criteria.

> [!TIP]
> The following is an example of KSI relevant to this project:
> 
> |Type  |KSI question & criteria  |How measured  |Success criteria  |Measured  |Responsible  |
> |---------|---------|---------|---------|---------|---------|
> |Usage/adoption|Call quality is equal to or better than the previous solution|Survey|80% of users agree or strongly agree|After enablement and quarterly|Information Technology team|
> |Usage/adoption|Microsoft Teams made the communication process easier|Survey|80% of users agree or strongly agree|After enablement and quarterly|Change Management team|
> |Usage/adoption|Users actively use the solution|Office 365 reports, Call Quality Dashboard|80% of users are active daily users|Daily|Change Management team|
> |Usage/quality|Percentage of poor calls/conferences should be minimal|Call Quality Dashboard|< 5% of poor calls per month|Daily|Information Technology team|
> |Usage/support|I know how to get technical support|Survey|90% of users agree or strongly agree|After enablement and quarterly|Change Management team|
> |Usage/support|I am satisfied with the quality of technical support|Survey|80% of users agree or strongly agree|After each incident|Information Technology team|
> |Financial|Reduction of monthly telephony service expense|Financial system|Meet defined ROI|Based on ROI|Change Management team|

You need to identify business risks as part of this exercise and define a mitigation plan for each identified risk. Capture this information in a risk plan.

> [!TIP]
> Your risk plan can be documented as the example below:
> 
> |Risk  |Likelihood  |Impact  |Overall  |Mitigation plan  |
> |---------|---------|---------|---------|---------|
> |Upcoming merger will add up to 1,000 people|High|High|High|<ul><li>For merged companies, separate OKR with own process (Envision, Onboard, Drive Value)</li><li>Do not include them in existing OKRs</li></ul>|
> |Telephone number porting will delay project completion|High|High|High|<ul><li>Prepare all the required information to support telephone number porting ahead of time (i.e.: customer service record, billing details, Letter of Authorization)</li><li>Adjust project timeline to accommodate turnaround time of telephone number porting execution</li><li>Use temporary telephone numbers with Caller ID manipulation</li></ul>|
> |Planned network redesign|High|Medium|Medium|<ul><li>Before implementing Teams as modern communications and collaboration platform, run network readiness assessment for sites in scope of the project</li></ul>|

Assess environment and evaluate adoption readiness
--------------------------------------------------

To achieve the intended OKRs, you may have to define the high-level architecture of the solution. It takes environmental discovery to evaluate all aspects relating to IT and telephony infrastructure, networking, and operations.

All matters related to end-user computing, such as readiness assessment of the personal computers and mobile devices to support Phone System with Calling Plans business use cases, from hardware requirements to software requirements, will be included as part of the environmental discovery.

Environmental discovery can also reveal whether you need to [transfer phone numbers to Microsoft](https://docs.microsoft.com/skypeforbusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365). This will help your organization adjust the project plan accordingly and prepare the necessary information required for number porting. To perform environmental discovery, use the [Discovery Questionnaire](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_1_0_3).

Environmental discovery must include network readiness assessment to ensure the network is ready to support the implementation of Phone System with Calling Plans.

Network readiness to support Phone System with Calling Plans can be determined by leveraging the information captured through the environmental discovery (such as details of internet connectivity and WAN topology, site links and available bandwidth) and persona analysis data (that can be translated into an expected usage of each workload) into the [My Advisor Network Planning](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner) tool. To further confirm network readiness, perform a real-time media traffic simulation using these solutions:
- From Microsoft: [Skype for Business Network Assessment Tool](https://www.microsoft.com/download/details.aspx?id=53885)
- From partners: [Network Readiness Assessment tools partners](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Partners?ToolPartners)

The results of network readiness assessment will paint a clearer picture of the required network optimization or remediation required for successful implementation of Phone System with Calling Plans.

Adoption readiness can be evaluated by executing persona analysis to come up with a list of personas in the organization who can be targeted for the implementation of the Phone System with Calling Plans. The persona analysis includes the identification of additional peripherals or devices required to realize the intended business outcomes.

To perform persona analysis, you can conduct a workshop by involving relevant project stakeholders, leveraging the [Persona Alignment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_2_0_7) workshop deck and [Persona Feature Matrix](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_2_0_8). The result of persona analysis workshop can be summarized into a report using the [Persona Analysis Report](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Downloads?SelectedIDs=4_2_0_9) template.

> [!NOTE]
> While the Discovery Questionnaire and Persona Analysis examples were initially written for Skype for Business Online, a majority of the content is relevant to Teams. Feel free to modify and remove items that are not relevant to your project goals.

You can identify technical risks as part of an environmental assessment and adoption readiness evaluation and develop a mitigation plan for each identified risk. This information should be incorporated as part of the risk plan.

Map operational roles
---------------------

Planning for operations and identifying the teams that will operate the Phone System with Calling Plans service is an important step, as operations must start when the first pilot users are enabled. Each identified team must review and agree on the tasks and responsibilities identified and start the preparation to operate Phone System with Calling Plans service. The preparation might include training and readiness, additional staffing, or ensuring external providers are set up to deliver the service.

> [!TIP]
> The following is an example of a template to document the result of operational roles mapping exercise that you performed to support this project:
> 
> |Operational Role  |Description  |Team  |Contact Details  |
> |---------|---------|---------|---------|
> |Service Owner|Service owner, interface to business divisions, strategy|TBA|TBA|
> |Phone System with Calling Plans Operations|Daily operations, user and device account move/add/change, monitoring|TBA|TBA|
> |Tenant Admin|Change tenant-wide settings, enable new features|TBA|TBA|
> |Help Desk|Interface for end-users to get support|TBA|TBA|
> |Network Operations|Runs LAN, WAN, Wi-Fi, and Internet Access|TBA|TBA|
> |Client & Endpoints Team|Manage desktop deployments|TBA|TBA|
> |Identity Operations|Manage identity infrastructure (AD, ADFS, Azure AD)|TBA|TBA|
> |Adoption/change management|Manage awareness, training and adoption for the solution|TBA|TBA|
> |Exchange Operations|Manages the Exchange environment|TBA|TBA|

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

<br>
Technical planning for Phone System with Calling Plans
------------------------------------------------------
<a name="technical-planning-for-phone-system-with-calling-plans"> </a>
To plan for the technical implementation of Phone System with Calling Plans, a series of decisions must be made ahead of time to better prepare your organization to implement a solution that meets business requirements. These decisions will be documented into a technical implementation plan.

## Availability of Calling Plans

To find out where the Calling Plans service is available, read [Countries and region availability for Audio Conferencing and Calling Plans](https://docs.microsoft.com/en-uscountry-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

> [!IMPORTANT]
> Due to legal constraints, for Calling Plans to be available to multinational organizations, the contract for Office 365 subscriptions must be sourced from countries and regions covered by Calling Plans service, or where Calling Plans service is commercially available from.

After confirming your organization’s eligibility for obtaining the Calling Plans add-on, compile the list of user locations or offices where Calling Plans service will be implemented based on the list of available countries and regions.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision Points|<ul><li>Decide which user locations or offices where Calling Plans service will be implemented</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next Steps|<ul><li>Document the user locations or offices to be enabled for Calling Plans service</li></ul>|

> [!TIP]
> Below is an example of a Phone System with Calling Plans site enablement list template:
> 
> |Office   |Location |Phone System Service  |
> |---------|---------|---------|
> |One Epping Road|Australia|Legacy PSTN service|
> |100 Cyberport Road|Hong Kong SAR|Legacy PSTN service|
> |One Marina Boulevard|Singapore|Legacy PSTN service|
> |32 London Bridge Street|United Kingdom|Phone System with Calling Plans|
> |39 quai du Président Roosevelt|France|Phone System with Calling Plans|

## Licensing for Calling Plans

Calling Plan is an add-on to the Phone System feature in Office 365, so you must have a Phone System license enabled in order to use Calling Plans.

[Phone System license](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/skype-for-business-and-microsoft-teams-add-on-licensing) is available as part of Office 365 E5 subscription plans, or as an add-on to Office 365 E1 or Office 365 E3 subscription plans.
There are two types of [Calling Plan licenses](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-calling-plans-in-office-365):

-   Domestic Calling Plan
-   International and Domestic Calling Plan

> [!NOTE]
> What is considered “domestic” for a specific user is determined by the user’s assigned Office 365 usage location.

Each Calling Plan type provides an allocation of calling minutes that users can use per month, either to make domestic calls or international calls. Domestic Calling Plan costs less compared to International and Domestic Calling Plan. To find out how many minutes are available for each country/region, see the "Calling Plans" section of [Countries and region availability for Audio Conferencing and Calling Plans](https://docs.microsoft.com/en-uscountry-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).

Typically, not everybody in an organization requires the ability to make international calls. The flexibility of subscribing and assigning the most appropriate Calling Plan type for individual user’s business requirements allows your organization to control the costs of Calling Plans implementation.

For each Office 365 tenant, the combined number of calling minutes are pooled by country or region, and per Calling Plan type. When the monthly calling minutes cap for the tenant is reached, Calling Plans service (except for emergency calling) will be suspended for the remainder of the month. Calling Plans services will resume automatically on the first day of the next calendar month.

To enable users to make outbound calls after the calling minutes are exhausted without having to wait until the next month billing cycle, you can setup Communications Credits for your organization. [Communications Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits) also gives the ability for users assigned with Domestic Calling Plan to make international calls charged by a “pay-per-minute” model.

The first consideration to make when implementing Communications Credits is to decide the initial amount of funds to be purchased. Recommended funding amounts can be referenced from [Communications Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits) article.

If your organization chooses to use auto-recharge, a recommendation on the trigger (lowest amount of funds) is also included in the [Communications Credits](https://docs.microsoft.com/SkypeForBusiness/skype-for-business-and-microsoft-teams-add-on-licensing/what-are-communications-credits) article. Auto-recharge amount needs to be determined by the actual usage. Communications Credits usage should be monitored over time and recharge amount needs to be adjusted as required.

The use of Communications Credits can be controlled at per user basis, allowing you to ensure the capability is assigned to individuals in the organization that have proper business needs.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision Points|<ul><li>If your organization does not have the required Phone System license, decide whether Phone System license will be acquired by stepping up existing Office 365 subscriptions or by acquiring Phone System add-ons</li><li>Decide which users require Domestic Calling Plan license and which users require Domestic and International Calling Plan license</li><li>Decide if Communications Credits is required for Calling Plans implementation. If so, decide the initial amount of funds to be purchased. Where applicable, decide the trigger amount and auto-recharge amount.</li><li>Decide which users require the use of Communications Credits license</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next Steps|<ul><li>Document the users to be assigned with Phone System license along with Domestic Calling Plan license, and users to be assigned with Phone System license with Domestic and International Calling Plan license</li><li>Document the Communications Credits plan (initial amount, trigger amount, auto-recharge amount)</li><li>Document the users to be enabled for Communications Credits license</li></ul>|

> [!TIP]
> You can document the license assignment list for Phone System with Calling Plans users using the following example:
> 
> |User  |Office  |Office 365 License  |Communications Credits  |
> |---------|---------|---------|---------|
> |Emily Braun|32 London Bridge Street|Office 365 E5, International and Domestic Calling Plan|Enabled|
> |Lidia Holloway|32 London Bridge Street|Office 365 E5, Domestic Calling Plan|Disabled|
> |Pradeep Gupta|32 London Bridge Street|Office 365 E5, Domestic Calling Plan|Enabled|
> |Marcel Beauchamp|39 quai du Président Roosevelt|Office 365 E3, Phone System add-on, Domestic Calling Plan|Disabled|
> |Rachelle Cormier|39 quai du Président Roosevelt|Office 365 E5, International and Domestic Calling Plan|Enabled|
> |Isabell Potvin|39 quai du Président Roosevelt|Office 365 E3, Phone System add-on, Domestic Calling Plan|Disabled|

<br>

> [!TIP]
> Your Communications Credits planning numbers can be documented as the following:
> |         |         |
> |---------|---------|
> |Initial amount|$ 1,000|
> |Trigger amount|$ 400|
> |Auto-recharge amount|TBA|

## Phone Numbers and Emergency Locations

With Calling Plans in Office 365, every user in your organization needs to have a unique Direct Inward Dialing (DID) phone number and a corresponding [validated emergency address](https://docs.microsoft.com/skypeforbusiness/what-are-calling-plans-in-office-365/what-are-emergency-locations-addresses-and-call-routing).

Phone numbers can be [obtained directly from Microsoft](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization), or existing phone numbers can be [transferred (ported) to Microsoft](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/transfer-phone-numbers-to-office-365).

> [!NOTE]
> Complexity of transferring phone numbers to Microsoft varies greatly based on the countries or regions, carriers, the number of circuits involved, and many other contributing factors. To plan for phone number porting, check out the [Number Porting Guide](https://go.microsoft.com/fwlink/?linkid=859011) for the details.

To obtain phone numbers from Microsoft directly, use any of these options:

- [Skype for Business admin center](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/getting-phone-numbers-for-your-users)
- [Remote Windows PowerShell cmdlets](https://docs.microsoft.com/powershell/module/skype/?view=skype-ps)
- [Submit a New Telephone Number Request form](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization).

The New Telephone Number Request form works best for a planned phone number acquisition, because you can request a contiguous block of phone numbers. Obtaining phone numbers using Skype for Business admin center or remote Windows PowerShell are not available in every country or region.

The first two methods - using Skype for Business admin center or remote Windows PowerShell - will work for one-off, instantaneous, phone number acquisition, and when contiguous blocks of phone numbers are not required.

> [!NOTE]
> There is a limit on the [number of the phone numbers](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/how-many-phone-numbers-can-you-get) that can be acquired from Microsoft based on the number of Calling Plan licenses subscribed by your organization. For user (subscriber) phone numbers, the formula is (Number of Domestic Calling Plan + Domestic and International Calling Plan licenses) x 1.1 +10. For example, if you have 50 users with Calling Plan licenses, you can acquire 65 phone numbers ((50 x 1.1) + 10).

When you are configuring phone numbers for Calling Plans, it is required that an emergency address be assigned to each telephone number prior to assignment to a user. This is required to support emergency calling. The emergency address must be validated to ensure the emergency address is recognized that it is in a correct format that can be used by emergency response services.

> [!IMPORTANT]
> Emergency Services Calling operates differently with Calling Plans service than on traditional telephone services. It is important that you understand these differences and communicate them to all users. Check [Emergency calling terms and conditions](https://docs.microsoft.com/SkypeForBusiness/legal-and-regulatory/emergency-calling-terms-and-conditions) for further details.

In addition to validated emergency address, emergency locations can be defined and associated with validated emergency address to give a more exact location within an address. An emergency location is typically building number, floor, building wing, or office number where the user is located.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision Points|<ul><li>Decide how phone numbers will be obtained for user locations or offices in-scope for the Calling Plans implementation (obtain from Microsoft or transfer existing phone numbers)</li><li>If you choose to obtain from Microsoft, decide the method to obtain phone numbers (form submission or automated) for user locations or offices in-scope for the Calling Plans implementation</li><li>Decide the granularity of emergency locations information to be collected for user locations or offices in-scope for the Calling Plans implementation</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next Steps|<ul><li>Document the master plan for phone numbers acquisition, detailing how phone numbers will be obtained for each user location or office in-scope for the Calling Plans implementation</li><li>If applicable, complete <a href="https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization">the New Telephone Number Request form</a>, one form for each location or office</li><li>If you choose to transfer existing phone numbers, check out the <a href="https://go.microsoft.com/fwlink/?linkid=859011">Number Porting Guide</a> to plan it and adjust Calling Plans implementation timeline accordingly</li><li>Document the detailed emergency address and emergency locations for each user location or office in-scope for the Calling Plans implementation</li></ul>

> [!TIP]
> The details of phone number acquisition, phone numbers, and emergency location details can be documented using the following template:
> 
> |User  |Emergency Location and Address  |Phone Number Acquisition  |Phone Number  |
> |---------|---------|---------|---------|
> |Emily Braun|1034/32 London Bridge Street, London, SE1, United Kingdom|Port existing|+44 20 7946 0034|
> |Lidia Holloway|1023/32 London Bridge Street, London, SE1, United Kingdom|Port existing|+44 20 7946 0065|
> |Pradeep Gupta|1023/32 London Bridge Street, London, SE1, United Kingdom|Port existing|+44 20 7946 0023|
> |Marcel Beauchamp|07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France|Acquire new|TBA|
> |Rachelle Cormier|07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France|Acquire new|TBA|
> |Isabell Potvin|07E15D/39 quai du Président Roosevelt, 92130 Issy-les-Moulineaux, France|Acquire new|TBA|

## Voicemail

Phone System voicemail, powered by Azure Voicemail Services, supports voicemail deposits to Exchange mailbox only and does not support third-party email systems.

Phone System voicemail by default will work with Exchange Online, however it has a minimum [supported Exchange on-premises version and deployment model](https://support.microsoft.com/help/3195158/customer-issues-between-exum-and-azure-voicemail) to allow delivery of voicemail messages to user mailboxes in the on-premises Exchange deployment.

Phone System voicemail features voicemail transcription and by default it is enabled for all users in your organization. In some cases, your business may have requirements to disable voicemail transcription for specific users or throughout the organization.

> [!NOTE]
> A fallback mechanism has been implemented so that Phone System voicemail can resend messages using SMTP, which means users with a mailbox on a third-party email system will receive their voicemail messages. There is no guaranteed service uptime or other voicemail features, such as changing voicemail greetings and other settings.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision Points|<ul><li>Decide whether Phone System voicemail will be enabled for the Calling Plans implementation</li><li>If using Exchange On-premises and existing deployment does not meet the requirements to support Phone System voicemail, decide the available options (upgrade and setup for Phone System voicemail support, or migrate to Exchange Online, leverage fallback mechanism)</li><li>Decide if voicemail transcription is to be enabled/disabled throughout the organization or to specific users</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next Steps|<ul><li>If applicable, document the Exchange decision points to support Phone System voicemail</li><li>If voicemail and voicemail transcription are not going to be enabled for all users, document the users to be enabled for voicemail and voicemail transcription</li></ul>|

> [!TIP]
> Phone System voicemail details for the Phone System with Calling Plans implementation can be documented as the following:
> 
> |User  |Exchange Mailbox  |Enable Voicemail  |Voicemail Transcription  |
> |---------|---------|---------|---------|
> |Emily Braun|Online|Yes|Enabled|
> |Lidia Holloway|Online|Yes|Enabled|
> |Pradeep Gupta|On-premises|Yes|Enabled|
> |Marcel Beauchamp|On-premises|Yes|Disabled|
> |Rachelle Cormier|Online|Yes|Disabled|
> |Isabell Potvin|On-premises|Yes|Disabled|

## Calling identity

By default, all outbound calls use the assigned phone number as calling identity (Caller ID). The recipient of the call can quickly identify the caller and decide whether to accept or reject the call. In some cases, there are legitimate business requirements to mask the Caller ID to protect the identity of callers by using the office main line number—this is typically a service number serviced by [Auto Attendant](https://docs.microsoft.com/SkypeForBusiness/what-is-phone-system-in-office-365/what-are-phone-system-auto-attendants) configuration—as Caller ID, or to block Caller ID presentation altogether.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision Points|<ul><li>Decide whether Caller ID manipulation is required for Calling Plans implementation</li><li>If applicable, decide the types of Caller ID manipulation (mask with service number or anonymize) to be implemented</li><li>If applicable, decide which user require Caller ID manipulation, and the type of Caller ID manipulation to be assigned to each user</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next Steps|<ul><li>Document the users to be assigned with Caller ID manipulation and Caller ID manipulation type applicable for each user</li></ul>|

> [!TIP]
> The following is an example of Caller ID masking details documentation template:
> 
> |User  |Enable outbound Caller ID masking  |Caller ID masking type  |Allow user override  | Enable inbound Caller ID masking  |
> |---------|---------|---------|---------|---------|
> |Emily Braun|No|N/A|Yes|No|
> |Lidia Holloway|Yes|Service number (OrgAA, +44 20 7946 0000)|No|Yes|
> |Pradeep Gupta|No|N/A|Yes|No|
> |Marcel Beauchamp|Yes|Service number (OrgAA, TBA)|No|Yes|
> |Rachelle Cormier|Yes|Anonymize|Yes|No|
> |Isabell Potvin|Yes|Service number (OrgAA, TBA)|No|Yes|

## Dial plans

A [Dial Plan](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-dial-plans), in the Phone System feature of Office 365, is a set of normalization rules that translates dialed phone numbers into an alternate format (typically [E.164](https://go.microsoft.com/fwlink/?linkid=859014) format) for call authorization and call routing. 

A dial plan allows users to dial phone numbers the way they are accustomed to, such as omitting area code for local calls, omitting country code for domestic calls, or even using short digit dialing when placing a phone call.

Within the Phone System feature of Office 365, there are two types of dial plans:

-   **Service dial plan**. This is the default dial plan and applied to users based on Office 365 usage location, and it cannot be modified.
-   **Tenant dial plan**. This is a customizable dial plan within a tenant, and further divided into two types:
    -   **Tenant-global dial plan**—the dial plan applies to all users within the tenant.
    -   **Tenant-user dial plan**—the dial plan applies only to specific users.

> [!NOTE]
> Check out [What are dial plans?](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/what-are-dial-plans) for further details and examples.

The effective dial plan assigned to users is the combination of service dial plan (based on user’s Office 365 usage location) and tenant dial plan (can be either tenant-global dial plan or tenant-user dial plan).

![Table shows three combinations of service and tenant dial plans.](media/audio_conferencing_image8.png)

There is a maximum of 25 normalization rules in each tenant dial plan, and thus duplication with normalization rules already available as part of service dial plan needs to be avoided.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision Points|<ul><li>Decide if your organization requires customized dial plans (business requirements, adoption requirements, etc.)</li><li>If applicable, decide the scope of tenant dial plan (tenant-global or tenant-user) to support the requirements for customized dial plans</li><li>If applicable, decide the tenant dial plans that will be created to support user locations or offices in-scope for the Calling Plans implementation</li><li>If applicable, decide which user require customized dial plan and the tenant dial plan to be assigned for each user</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next Steps|<ul><li>Document the customized dial plans and the associated normalization rules to be configured as part of Calling Plans implementation</li><li>Document the users to be assigned with customized dial plan and the tenant dial plan to be assigned for each user</li></ul>|

> [!TIP]
> If it is applicable to your project, you can use the following template to document the tenant dial plans configurations:
> 
> |Tenant Dial Plan Name<br>_Description  |Normalization Rules Name<br>_Description_  |Pattern<br>Translation<br>IsInternalExtension  |
> |---------|---------|---------|
> |**FR-Paris-Issy-39qdPR**<br>_39 quai du Président Roosevelt Issy-les-Moulineaux, France Dial Plan_|**FR-39qdPR-Internal**<br>_Internal number (x7000 – x7999) for 39 quai du Président Roosevelt office, Issy-les-Moulineaux, France_|^(7\d{3})$<br>+3319999$1<br>True|
> ||**FR-TollFree**<br>_Toll Free number normalization for France_|^0?(80\d{7})\d*$<br>+33$1<br>False|
> ||**FR-Service**<br>_Service number normalization for France_|^(1\d{1,2}\|11[68]\d{3}\|10\d{2}\|3\d{3})$<br>$1<br>False|

<br>

> [!TIP]
> The example template below can be leveraged to document dial plan assignments to support your project:
> |User  |Office  |Dial Plan Type  |Dial Plan Name  |
> |---------|---------|---------|---------|
> |Emily Braun|32 London Bridge Street|Service dial plan|N/A|
> |Lidia Holloway|32 London Bridge Street|Service dial plan|N/A|
> |Pradeep Gupta|32 London Bridge Street|Service dial plan|N/A|
> |Marcel Beauchamp|39 quai du Président Roosevelt|Tenant dial plan|FR-Paris-Issy-39qdPR|
> |Rachelle Cormier|39 quai du Président Roosevelt|Tenant dial plan|FR-Paris-Issy-39qdPR|
> |Isabell Potvin|39 quai du Président Roosevelt|Tenant dial plan|FR-Paris-Issy-39qdPR|

## Document technical implementation plan

Use the decision points above to document your technical implementation plan.
This technical implementation plan will provide the project team, which can include FastTrack or deployment partner, with the information required to execute the technical onboarding for the implementation of Phone System with Calling Plans.

In general, a technical implementation plan will contain the following main sections:

-   Phone System with Calling Plans site enablement list

-   License assignment for Phone System with Calling Plans users

-   Communications Credits planning numbers

-   Phone number acquisition, phone numbers, and emergency location details

-   Voicemail configuration details

-   Caller ID masking configuration details

-   Tenant dial plans

-   Dial plan assignments

<br>
With the completion of success plan and technical implementation plan, you are now ready to take your organization to the next steps along the Office 365 customer journey.

<br>
Onboard
=======

*Coming soon.*

<br>
Drive Value
===========

*Coming soon.*

<br>
## See also

[Set up Calling Plans](https://docs.microsoft.com/SkypeForBusiness/what-are-calling-plans-in-office-365/set-up-calling-plans)

[Quick start guide: Configuring Calling Plans in Microsoft Teams](https://docs.microsoft.com/MicrosoftTeams/configuring-teams-calling-quickstartguide)
