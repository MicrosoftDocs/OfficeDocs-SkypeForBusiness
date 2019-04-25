---
title: Define success in Audio Conferencing, Phone System with Calling Plans, or Phone System Direct Routing - Microsoft Teams
author: rmw2890
ms.author: Rowille
manager: serdars
ms.date: 06/07/2018
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.reviewer: rowille
description: Measure the results of your Audio Conferencing, Phone System with Calling Plans, or Phone System Direct Routing deployment, and verify you've achieved the outcomes you wanted.
MS.collection: 
- Teams_ITAdmin_PracticalGuidance
- M365-collaboration
localization_priority: Normal
appliesto:
- Microsoft Teams
---

# Define my success

This article gives an overview of the requirements for defining success for the deployment of Audio Conferencing, Phone System with Calling Plans, or Phone System Direct Routing for your organization. By properly defining what success looks like, you can measure your results as you progress through your deployment and verify that the outcomes you achieve are the ones you wanted.

<!--ENDOFSECTION-->

**Audio Conferencing** provides organizations with additional entry points to any meetings (ad hoc or scheduled) by allowing meeting participants to join via public switched telephone network (PSTN) by dialing in using traditional landline, private branch exchange (PBX), or mobile phones. This is useful when the organizer or participants aren’t in front of a computer, or when data connections are unavailable or too unreliable to support voice communications—such as in a remote area with spotty mobile data coverage, or connected to a free, public Wi-Fi service with limited bandwidth, or when meeting participants prefer to dial in to the meeting by using a telephony endpoint that’s readily accessible to them.

**Phone System with Calling Plans (“Calling Plans”)** gives organizations a way to modernize their workplace by enabling users to make business-related phone calls from their computers and mobile devices. Workplace modernization can be part of any number of scenarios—an activity-based working implementation, a major office move, an office fit-out refresh, retiring a legacy PBX solution, the conclusion of a PSTN service provider contract, and so on. With Calling Plans, Microsoft facilitates connectivity to the PSTN.

**Phone System Direct Routing (“Direct Routing”)** gives organizations the same benefits listed above for Calling Plans, except that PSTN connectivity is facilitated by a third-party provider rather than Microsoft. This allows for deployment in countries where Calling Plans aren’t available, or in deployments where an existing PSTN service provider contract needs to be maintained or interoperability with certain on-premises systems is required. One additional scenario to consider Direct Routing is telephony system interoperability. While users are being transitioned to Calling in Teams, some users might remain on legacy PBXs. Direct Routing enables both use cases to coexist. The call traffic between the users on legacy systems and Teams users stay within the organization.

<!--ENDOFSECTION-->

## Define business use cases for Audio Conferencing, Calling Plans, or Direct Routing

To begin with, core project stakeholders need to define business use cases that support the implementation of Audio Conferencing, Calling Plans, or Direct Routing.

Business use cases are meant to define and document expected and measurable business outcomes, and include the following:

-   Description of the current business process

-   Challenges with the existing business process

-   How technology can help overcome these challenges

-   The expected and measurable business outcomes if these challenges are overcome

> [!TIP]
> The following is an example of a completed business use case for Audio Conferencing:
> 
> |         |
> |---------|
> |**Description of current business process**<br>Contoso currently relies on PSTN conferencing services provided by the incumbent local telephony provider chargeable by meeting minutes for internal meetings and meetings involving external parties.|
> |**Challenges with existing business process**<br>Contoso spends roughly USD1 million per year for the current PSTN conferencing service, with 75% of the cost incurred for internal meetings. The use of traditional telephony endpoints to join the meetings hosted by the PSTN conferencing service isn’t aligned with the plan for the organization to adopt Teams as a modern communications and collaboration platform.|
> |**How technology can overcome these challenges**<br>With the adoption of Microsoft Teams as a modern communications and collaboration platform, internal users are expected to primarily join meetings by using their PCs equipped with optimized headsets and meeting-room devices. The Audio Conferencing service will be available to support external participants or to support situations where the use of PC audio isn’t favorable for the internal participants.|
> |**Expected, measurable, business outcomes**<br>The move to Teams as a modern communications and collaboration platform, combined with the Audio Conferencing service, will greatly reduce the cost to deliver the PSTN conferencing service.|

<br>

> [!TIP]
> The following is an example of a completed business use case for Calling Plans:
> 
> |         |
> |---------|
> |**Description of current business process**<br>Standard configuration of Contoso’s office workspaces includes a desktop phone for every desk. Each employee has been given a direct inward dialing (DID) phone number. The desktop phones are connected to a PBX system, and connected to PSTN via a session initiation protocol (SIP) trunk. Employees can only make and receive phone calls at their assigned desktop phones.|
> |**Challenges with existing business process**<br>Usage analysis of the desktop phones shows that only 10% of the desktop phones are actively used, with the rest configured either to forward calls to mobile phones or to simultaneously ring to mobile phones. Maintaining the existing PBX system and associated desktop phones contributes to 20% of Contoso’s monthly telephony service cost.|
> |**How technology can overcome these challenges**<br>Calling Plans will allow a user’s personal computer to receive and place phone calls over the data network by leveraging the native Microsoft Teams app. This removes the need to roll out and maintain desktop phones, and opens the opportunity to decommission the existing PBX system, because the phone service can be delivered via the cloud over the network with no dependency on a traditional phone system.|
> |**Expected, measurable, business outcomes**<br>Removing maintenance requirements and decommissioning legacy PBX and desktop phones will deliver a 20% reduction in monthly telephony service expenses. Calling Plans will simplify office workspaces, allowing Contoso to expand its operations by establishing new offices with minimal upfront telephony costs.|

<br>

> [!TIP]
> The following is an example of a completed business use case for Direct Routing:
> 
> |         |
> |---------|
> |**Description of current business process**<br>Standard configuration of Contoso’s office workspaces includes a desktop phone for every desk. Each employee has been given a direct inward dialing (DID) phone number. The desktop phones are connected to a PBX system, and connected to PSTN via a session initiation protocol (SIP) trunk. Employees can only make and receive phone calls at their assigned desktop phones.|
> |**Challenges with existing business process**<br>Usage analysis of the desktop phones shows that only 10% of the desktop phones are actively used, with the rest configured either to forward calls to mobile phones or to simultaneously ring to mobile phones. Maintaining the existing PBX system and associated desktop phones contributes to 20% of Contoso’s monthly telephony service cost.|
> |**How technology can overcome these challenges**<br>The SIP trunk provider contract was recently signed and will be in place for three years. Direct Routing allows PSTN connectivity to be provided by the SIP trunk provider and also will allow a user’s personal computer to receive and place phone calls over the data network by leveraging the native Microsoft Teams app. This removes the need to roll out and maintain desktop phones, and opens the opportunity to decommission the existing PBX system, while maintaining a limited on-premises session border controller (SBC) footprint.|
> |**Expected, measurable, business outcomes**<br>Removing maintenance requirements and decommissioning legacy PBX and desktop phones will deliver a 20% reduction in monthly telephony service expenses. Direct Routing will simplify office workspaces, allowing Contoso to expand its operations by establishing new offices with minimal upfront telephony costs.|

In addition to defining your business use cases, to set the project boundaries you should aim to drive clarity around:

-   **Organizational scope:** The implementation of Audio Conferencing, Calling Plans, or Direct Routing might encompass the whole organization or just specific business units.

-   **Project timeline:** The specific timeline the project will run.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>What are all the business use cases for Audio Conferencing you can identify in your organization?</li><li>What are all the business use cases for Calling Plans you can identify in your organization?</li><li>What are all the business use cases for Direct Routing you can identify in your organization?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document all business use cases for Audio Conferencing for your organization.</li><li>Document all business use cases for Calling Plans for your organization.</li><li>Document all business use cases for Direct Routing for your organization.</li></ul>|

<!--ENDOFSECTION-->

## Identify key stakeholders

The business use cases defined in the previous step include an organizational scope for the Audio Conferencing, Calling Plans, or Direct Routing implementation. Based on that, you can complete the comprehensive stakeholder matrix to include the right people to involve in the project.

> [!TIP]
> Below is an example of stakeholder matrix template that you can use to document the project stakeholders:
> 
> |Role  |Description  |Name, contact information, location  |
> |---------|---------|---------|
> |Project Executive Sponsor|<ul><li>Take ultimate authority and accountability for the project and delivery on project objectives.</li><li>Help resolve issues escalated by the Project Lead.</li><li>Sponsor communication within the company about project goals.</li><li>Make key strategic decisions.</li><li>Ensure the availability of required resources and budget.</li><li>Lead quarterly business reviews (QBRs).</li><li>Drive buy-in and support of awareness campaign efforts.</li><li>Serve as the Project Sponsor to the program rollout.</li></ul>|TBA|
> |Project Lead|<ul><li>Manage and lead the project team.</li><li>Coordinate partners and working teams engaged in the project.</li><li>Be accountable for creating and managing project plans to meet quarterly key results.</li><li>Resolve cross-functional issues.</li><li>Provide regular updates to project sponsors.</li><li>Incorporate adoption aspects into the all-up project plan.</li><li>Lead monthly Business and Operational Reviews (MBRs), contribute to QBRs.</li></ul>|TBA|
> |Collaboration Lead/Architect|<ul><li>Execute on the collaboration strategy defined by company executives.</li><li>Analyze and choose collaboration products that meet business goals for the company.</li><li>Design operations for collaboration products.</li><li>Define operation and support models.</li><li>Contribute to monthly and quarterly business reviews.</li></ul>|TBA|
> |Consultant|<ul><li>Be responsible for configuration services</li><li>Contribute to the overall solution architecture.</li></ul>|TBA|
> |Project Manager|<ul><li>Develop and maintain the project plan.</li><li>Manage project deliverables in line with the project plan and budget.</li><li>Record and manage project issues, including escalations.</li><li>Conduct weekly standup calls.</li><li>Liaise with, and provide updates to, project executive sponsors.</li><li>Work with the architect to define the change management approach and communication plans.</li></ul>|TBA|
> |Change Management/Adoption Specialist|<ul><li>Provide input during the Discovery phase into adoption and training processes.</li><li>Participate in the adoption strategy workshop.</li><li>Develop and take responsibility for the adoption strategy.</li><li>Develop and execute the communication plan.</li><li>Deliver trainings to users.</li><li>Collect feedback and conduct surveys.</li></ul>|TBA|
> |Network Lead|<ul><li>Provide input during the Discovery phase into network design.</li><li>Participate in planning during the Envision phase workshop.</li><li>Coordinate the work of the networking team during project execution.</li></ul>|TBA|
> |Security Lead|<ul><li>Provide input during the Discovery phase into security design and processes.</li><li>Participate in planning during the Envision phase workshop.</li><li>Coordinate the work of the security team during project execution.</li></ul>|TBA|
> |Telephony Lead|<ul><li>Provide input during the Discovery phase into telephony design.</li><li>Participate in planning during the Envision phase workshop.</li><li>Coordinate the work of the telephony team during project execution.</li></ul>|TBA|
> |Desktop Lead|<ul><li>Provide input during the Discovery phase into the clients and update process.</li><li>Participate in planning during the Envision workshop.</li><li>Coordinate the work of the desktop team during project execution.</li></ul>|TBA|
> |Support/Help Desk Lead|<ul><li>Provide input during the Discovery phase into operational and support models.</li><li>Participate in planning during the Envision phase workshop.</li><li>Participate in support model planning.</li><li>Coordinate the work of support teams and resources during project execution.</li></ul>|TBA|
> |Business Unit Representatives|<ul><li>Contribute to user-based adoption guides and materials.</li><li>Contribute to and review business use cases.</li></ul>|TBA|
> |Deployment Lead|<ul><li>Ensure that deployment prerequisites are met.</li><li>Engage resources to be involved in the Onboard phase activities.</li><li>Participate in meetings to review and prepare reports on deployment status.</li></ul>|TBA|
> |IT Admins|<ul><li>Assist with test planning and execution. This role is for IT pros.</li></ul>|TBA|
> |Service Owner|<ul><li>Be responsible for the operation of the Audio Conferencing, Calling Plans, or Direct Routing service, all up.</li><li>Own the Audio Conferencing, Calling Plans,or Direct Routing service.</li></ul>|TBA|
> |Quality Champions|<ul><li>Drive quality, reliability, and user feedback.</li><li>Identify quality trends and drive remediation with the respective teams.</li><li>Report through the steering committee back to leadership.</li><li>Report on quality, reliability, and user sentiment through Rate My Call and Net Promoter Score.</li></ul>|TBA|

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Who will fill each key stakeholder role for your organization?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document all key stakeholders, and communicate the responsibilities and expectations of the role to each assigned individual.</li></ul>|

<!--ENDOFSECTION-->

## Define OKRs, KSIs, and risks

With the project stakeholders assembled, you can translate business use cases, organizational scope, and project timelines into objectives and key results (OKRs), and the measures of project success can be defined as a list of key success indicators (KSIs).

Full participation from project stakeholders in defining OKRs and KSIs is essential to help ensure they feel a sense of ownership and align these measures of success to organizational business requirements.

OKRs contain the objectives you set in the beginning of the project, and you define measurable key results on a quarterly basis. You review key results monthly to track the status of the overall project, and—based on progress—you adjust quarterly plans as needed.

> [!TIP]
> Examples of OKRs relevant to an Audio Conferencing implementation can be referenced below:
> <br>
> 
> **Vision: Increase productivity by maximizing Office 365 investments**
> 
> |Objectives  |Key results  |To do  |
> |---------|---------|---------|
> |Deploy Audio Conferencing in Teams by end of fiscal year 2018|FY18Q1: Deploy Audio Conferencing in Teams globally|Envision<ul><li>Create success plan</li><li>Create detailed technical implementation plan</li></ul><p>Onboard<ul><li>Execute success plan</li><li>Execute technical implementation plan</li></ul>|
> |Decommission legacy PSTN Conferencing service globally by mid of fiscal year 2018|FY18Q2: Decommission legacy PSTN Conferencing service globally|Drive Value<ul><li>Boost user engagement and drive adoption</li><li>Manage and prepare change</li><li>Measure, share success, and iterate</li>|

<br>

> [!TIP]
> Examples of OKRs relevant to a Calling Plans implementation can be referenced below:
> <br>
> 
> **Vision: Increase productivity by maximizing Office 365 investments**
> 
> |Objectives  |Key results  |To do  |
> |---------|---------|---------|
> |Deploy Calling Plans in European branch offices by end of fiscal year 2018|FY18Q3: Deploy Calling Plans in London office|Envision<ul><li>Create success plan</li><li>Create detailed technical implementation plan</li></ul><p>Onboard<ul><li>Execute success plan</li><li>Execute technical implementation plan</li></ul>|
> |Decommission legacy PBX in London office by end of fiscal year 2018|FY18Q4: Decommission legacy PBX in London office|Drive Value<ul><li>Boost user engagement and drive adoption</li><li>Manage and prepare change</li><li>Measure, share success, and iterate</li>|
> 
> [!TIP]
> Examples of OKRs relevant to a Direct Routing implementation can be referenced below:
> <br>
> 
> **Vision: Increase productivity by maximizing Office 365 investments**
> 
> |Objectives  |Key results  |To do  |
> |---------|---------|---------|
> |Deploy Direct Routing in Canadian branch offices by end of fiscal year 2018|FY18Q3: Deploy Direct Routing in Toronto office|Envision<ul><li>Create success plan</li><li>Create detailed technical implementation plan</li></ul><p>Onboard<ul><li>Execute success plan</li><li>Execute technical implementation plan</li></ul>|
> |Decommission legacy PBX in Toronto office by end of fiscal year 2018|FY18Q4: Decommission legacy PBX in Toronto office|Drive Value<ul><li>Boost user engagement and drive adoption</li><li>Manage and prepare change</li><li>Measure, share success, and iterate</li>|

<br>

KSIs measure quality and success of the key results, and complement the binary nature of OKRs (achieved or not achieved) by detailing good and/or bad results.

When defining KSIs, we recommend that you use “specific, measurable, assignable, realistic, time-related” (SMART) criteria:

-   Specific: target a specific area for improvement

-   Measurable: quantify, or at least suggest an indicator of, progress

-   Assignable: specify who will do it

-   Realistic: state what results can realistically be achieved, given available resources

-   Time-related: specify when the results can be achieved

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
> |Financial|Reduction of legacy conferencing minutes|Financial system|Meet defined ROI|Based on ROI|Change Management team|

You need to identify business risks as part of this exercise, and define a mitigation plan for each identified risk. This information can be captured into a risks register.

> [!TIP]
> Your risk register can be documented as the example below:
> 
> |Risk  |Likelihood  |Impact  |Overall  |Mitigation plan  |
> |---------|---------|---------|---------|---------|
> |Upcoming merger will add up to 1,000 people|High|High|High|<ul><li>For merged companies, create a separate OKR that applies to their own project phases (Envision, Onboard, Drive Value)</li><li>Don’t include these OKRs in existing OKRs</li></ul>|
> |Telephone number porting will delay project completion|High|High|High|<ul><li>Prepare all the information required to support telephone number porting ahead of time (customer service record, billing details, Letter of Authorization)</li><li>Adjust the project timeline to accommodate the turnaround time of telephone number porting execution</li><li>Communicate the use of new dial-in conferencing numbers to external participants</li><li>Use temporary telephone numbers with Caller ID manipulation</li></ul>|
> |Planned network redesign|High|Medium|Medium|<ul><li>Before implementing Teams as a modern communications and collaboration platform, conduct a network readiness assessment for sites in scope of the project</li></ul>|
> |SBC configuration|High|High|High|<ul><li>Before implementing Teams as replacement for the existing PBX, confirm that you can meet all SBC configuration requirements</li><li>Confirm that SBC support resources have the proper skill set to configure SBC for Direct Routing</li></ul>|

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>What are your organization&#39;s OKRs and KSIs?</li><li>What risks have you identified relevant to the implementation of Audio Conferencing in your organization? What are the mitigation plans for the identified risks?</li><li>What risks have you identified relevant to the implementation of Calling Plans in your organization? What are the mitigation plans for the identified risks?</li><li>What risks have you identified relevant to the implementation of Direct Routing in your organization? What are the mitigation plans for the identified risks?</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Document the OKRs and KSIs, and establish the risks register.</li></ul>|

<!--ENDOFSECTION-->

## Establish a steering committee

A steering committee is a governing group of key stakeholders and project leaders who have been brought together to guide a project or program toward its defined business outcomes. The steering committee isn’t directly responsible for *how* the project is delivered, but rather *what* the project delivers to the business.

Every project requires an agreed-on vision and charter. To deliver the outcomes you want from the project, the vision must be clearly defined, and it needs to be monitored and maintained. This becomes the responsibility of the steering committee: to drive decisions, advise, provide strategic oversight, to serve as advocates to the organization for the project’s initiatives, and—when necessary—remove blockers.

Your organization should put significant thought into the formation of the steering committee. The committee must ensure that the project achieves the business objectives you’ve defined for driving change throughout the organization, meet periodically to discuss the current pulse of the project, and help unblock any obstacles that are encountered along the way.

The committee should define its charter to include some key objectives:

-   Keep a strong alignment between the project team and the executive sponsor or executive leadership.

-   Provide insight into the status of the project to the executive sponsor or executive leadership.

-   Allow the executive sponsor or executive leadership team to provide direction and input to the project and ensure that it aligns with overarching business goals, by adjusting project plans, objective key results (OKRs), and other project activities.

The steering committee meets at a recurring interval throughout the lifetime of a project to ensure alignment between the organizational leadership and the project team. This critical meeting ensures that the direction of the project has leadership’s full support and incorporates any feedback provided by leadership into the project to drive success. The committee uses these meetings to gain insight into project status, and to:

-   Agree on business outcomes that align to the business case, and to ensure the project is driving towards delivery of these outcomes.

-   Check and approve the project for accuracy and compliance with the business case.

-   Review and verify changes made to the business case that could affect any defined outcomes.

-   Make strategic decisions regarding the prioritization of project deliverables, and approve interim deliverables.

-   Identify, manage, and mitigate gaps, risks, and issues where additional influence is required from the committee.

-   Gather support from the executive sponsor or executive leadership team for issues that require escalation, prioritizing and resolving any conflicts between stakeholder business units. 

-   Provide formal feedback and recommendations to executive leadership, the change advisory board, or other business and IT stakeholders, as applicable.

<br>

|         |         |         |
|---------|---------|---------|
|<img src="media/audio_conferencing_image7.png" />|Decision points|<ul><li>Decide whether a steering committee is required for your organization.</li></ul>|
|<img src="media/audio_conferencing_image9.png" />|Next steps|<ul><li>Identify members of the steering committee.</li><li>Schedule steering committee meetings.</li><li>Prepare for steering committee meetings.</li><li>Hold steering committee meetings.</li><li>Take action based on steering committee meeting input.</li></ul>|

Additional detailed guidance on how to operate a proper steering committee can be found in the [steering committee guide](envision-steering-committee-complete-guide.md).

<!--ENDOFSECTION-->