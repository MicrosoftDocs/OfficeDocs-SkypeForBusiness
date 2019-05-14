---
title: Microsoft Teams Upgrade | Environment Evaluation, Discovery Questions
author: lanachin
ms.author: v-lanac
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Use this guidance to learn about the requirements for properly evaluating your current environment for upgrading to Teams.
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

![Stages of the upgrade journey, with emphasis on the Technical Readiness stage](media/upgrade-banner-tech-readiness.png "Stages of the upgrade journey, with emphasis on the Technical Readiness stage")

This article is part of the Technical Readiness stage of your upgrade journey, an activity you complete in parallel with the User Readiness stage. Before proceeding, confirm that you’ve completed these activities from previous stages:

- [Enlisted your project stakeholders](upgrade-enlist-stakeholders.md)
- [Defined your project scope](https://aka.ms/SkypetoTeams-Scope)
- [Understood coexistence and interoperability of Skype for Business and Teams](https://aka.ms/SkypeToTeams-Coexist)
- [Chosen your upgrade journey](upgrade-and-coexistence-of-skypeforbusiness-and-teams.md)

# Evaluate your environment before upgrading to Teams

This article gives an overview of the requirements for properly evaluating your current environment for operating Teams. By evaluating your environment, you identify risks and requirements that will influence your overall deployment. By identifying these items beforehand, you can adjust your planning to drive success.

## Introduction to the Discovery Questionnaire

To achieve your objective key results (OKRs), you previously made key service decisions. The next step is to perform environmental discovery to evaluate all aspects relating to your IT infrastructure, networking, and operations to confirm that your organization is ready to implement the solution. Discovery is one of the very first, key steps that you take when planning for your journey to Teams. Environmental discovery must include a network readiness assessment to ensure your network can support upgrading to Teams. You perform a detailed discovery of your environment to better understand its current state and to reveal any difficulties or—even more important—possible blockers to the execution of your Teams rollout.

You identify technical risks as part of an environmental assessment and adoption readiness evaluation, and develop a mitigation plan for each identified risk. You should incorporate this information in the risk register.

All matters related to your existing collaboration infrastructure and Office 365 tenant, networking, endpoints, operations, and adoption and readiness are included as part of the environmental discovery questionnaire. The questionnaire is divided into multiple sections to confirm your organization’s readiness for your Teams deployment in several major areas. Work with your project team to provide the requested information with as much detail as possible to facilitate your planning activities.

> [!TIP]
> You can start by copying the questionnaire into a Microsoft Word document. Try to answer all questions and capture all details as you move through.

## Project team

Ensure that you’ve engaged the right people for your project team. Verify the steps you completed in [Enlist your project stakekholders](upgrade-enlist-stakeholders.md).

## Office 365 tenant details

We highly recommend that you have an active Office 365 tenant as you work with this questionnaire. If you haven’t activated or configured an Office 365 tenant yet, see [Plan your setup of Office 365 for business](https://support.office.com/article/plan-your-setup-of-office-365-for-business-eb926624-018b-4486-bf11-5fba6ee4d645).

Use the following table to capture information about the Office 365 tenant.

> | Question | Answer | Comments |
> |---|---|---|
> | Note the production Office 365 tenant <br>name and ID in the Answer column <br/>If you have more than one tenant <br>associated with your organization, <br>note all the IDs. | Tenant Name: <br/>Tenant ID:| |
> | In what regions are the tenants deployed?| | |
> | Are these tenants Office 365 Multitenant or <br>Dedicated? | <input type="checkbox"> Multitenant<br/> <input type="checkbox"> Dedicated | |
> | Which Microsoft Online products are in use today? <br/>Note the number of users enabled for each <br>service in the Comments column. | <input type="checkbox"> Microsoft Teams <br/> <input type="checkbox"> Skype for Business <br>&nbsp; &nbsp; &nbsp;Online <br/> <input type="checkbox"> Exchange Online <br/> <input type="checkbox"> SharePoint Online <br/> <input type="checkbox"> OneDrive for Business <br/> <input type="checkbox"> Yammer <br/> <input type="checkbox"> Other| |
> | What license level is enabled for Skype for <br>Business Online users? | <input type="checkbox"> E1/G1 <br/> <input type="checkbox"> E2/G2 <br/> <input type="checkbox"> E3/G3 <br/> <input type="checkbox"> E4/G4 E5 <br/> <input type="checkbox"> Standalone | The number of users <br>for each SKU: |
> | What is the current Active Directory forest <br>functional level in the environment? <br/>If there’s more than one forest, note the details <br>in the Comments column. | <input type="checkbox"> Windows Server 2000 <br/> <input type="checkbox"> Windows Server 2003 <br/> <input type="checkbox"> Windows Server 2008<br/> <input type="checkbox"> Windows Server 2008 R2 <br/> <input type="checkbox"> Windows Server 2012 <br/> <input type="checkbox"> Windows Server 2012 R2 <br/> <input type="checkbox"> Windows Server 2016| |
> | What are you using for directory <br>synchronization today? |<input type="checkbox"> No sync (cloud only) <br/> <input type="checkbox"> Azure Active Directory <br>&nbsp; &nbsp; &nbsp;Connect <br/> <input type="checkbox"> Other (Specify in the <br>&nbsp; &nbsp; &nbsp;Comments column.)| |
> | Is federated identity currently deployed? <br/>(Active Directory Federation Services or <br>third-party) | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | If you’re using federated identity, what is the <br>federation infrastructure? | <input type="checkbox"> Windows 2008 R2 AD FS <br/> <input type="checkbox"> Windows 2012 AD FS <br/> <input type="checkbox"> Windows 2012 R2 AD FS <br/> <input type="checkbox"> Windows 2016 AD FS <br/> <input type="checkbox"> Third-party federation <br>&nbsp; &nbsp; &nbsp;gateway <br>&nbsp; &nbsp; &nbsp;(Note the details in the <br>&nbsp; &nbsp; &nbsp;Comments column.) | |
> | If you currently maintain an active Office 365 <br>tenant, is the SMTP/SIP domain of your <br>targeted users associated with the tenant? | <input type="checkbox"> N/A – No Office 365 <br>&nbsp; &nbsp; &nbsp;tenant in place <br/> <input type="checkbox"> No, users’ SMTP/SIP <br>&nbsp; &nbsp; &nbsp;domain isn’t associated <br>&nbsp; &nbsp; &nbsp;with any tenants in <br>&nbsp; &nbsp; &nbsp;Office 365 <br/> <input type="checkbox"> Yes, users’ SMTP/SIP <br>&nbsp; &nbsp; &nbsp;domain is associated <br>&nbsp; &nbsp; &nbsp;with an existing tenant <br>&nbsp; &nbsp; &nbsp;in Office 365 | |
> | Do user UPNs match their primary SMTP address? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No <br/> <input type="checkbox"> Inconsistently | |

## Existing collaboration platform summary

Use the following table to capture information about your existing collaboration platform deployment.

> | Question | Answer | Comments |
> |---|---|---|
> | Is Microsoft Teams deployed? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Is Skype for Business deployed? <br/>For on-premises and hybrid deployments, make sure <br>you note the version and cumulative update (CU) <br>details in the Comments column. | <input type="checkbox"> Yes, Office 365 <br/> <input type="checkbox"> Yes, hybrid (with Office 365) <br/> <input type="checkbox"> Yes, on-premises <br/> <input type="checkbox"> Yes, online, dedicated <br>&nbsp; &nbsp; &nbsp;(Microsoft) <br/> <input type="checkbox"> Yes, hosted, dedicated <br>&nbsp; &nbsp; &nbsp;(third party) <br/> <input type="checkbox"> Yes, hosted, shared (third party) <br/> <input type="checkbox"> No, other | |
> | Is Exchange deployed? <br/>For on-premises and hybrid deployments, make sure <br>you note the version and CU details in the Comments <br>column. | <input type="checkbox"> Yes, Office 365 <br/> <input type="checkbox"> Yes, hybrid (with Office 365) <br/> <input type="checkbox"> Yes, on-premises <br/> <input type="checkbox"> Yes, online, dedicated <br>&nbsp; &nbsp; &nbsp;(Microsoft) <br/> <input type="checkbox"> Yes, hosted, dedicated <br>&nbsp; &nbsp; &nbsp;(third party) <br/> <input type="checkbox"> Yes, hosted, shared <br>&nbsp; &nbsp; &nbsp;(third party) <br/> <input type="checkbox"> No, other | |
> | Is SharePoint deployed? <br/>For on-premises and hybrid deployments, make sure <br>you note the version and CU details in the Comments <br>column. | <input type="checkbox"> Yes, Office 365 <br/> <input type="checkbox"> Yes, hybrid (with Office 365) <br/> <input type="checkbox"> Yes, on-premises <br/> <input type="checkbox"> Yes, online, dedicated <br>&nbsp; &nbsp; &nbsp;(Microsoft) <br/> <input type="checkbox"> Yes, hosted, dedicated <br>&nbsp; &nbsp; &nbsp;(third party) <br/> <input type="checkbox"> Yes, hosted, shared <br>&nbsp; &nbsp; &nbsp;(third party) <br/> <input type="checkbox"> No, other | |
> | Is Office 365 OneDrive for Business deployed? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Do you have any other third-party platforms deployed <br>and in use today? If so, note the number of users of <br>these platforms and the usage details in the Comments <br>column. | <input type="checkbox"> Cisco WebEx <br/> <input type="checkbox"> Slack <br/> <input type="checkbox"> Other (Specify in the Comments <br>&nbsp; &nbsp; &nbsp;column.) | Number of users: <br/>Details:|
> | Are you planning to move users from these third-party <br>platforms to Teams? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | What is the current telephony and conferencing solution <br>of the users who are in scope for this initiative? | | |
> | Do you have [SBCs that support Direct Routing](direct-routing-plan.md#supported-session-border-controllers-sbcs) deployed for your offices that are in scope for this initiative? <br>If Yes, note the details in the Comments column.| <input type="checkbox"> Yes <br/> <input type="checkbox"> No ||

## Collaboration platform deployment details

### Microsoft Teams (if applicable)

If applicable, capture the details of your Teams deployment by using the sample table below. If you haven’t deployed Teams, skip this section.

> | Question | Answer | Comments |
> |---|---|---|
> | What types of users are enabled for Teams? | <input type="checkbox"> All users in the organization <br/> <input type="checkbox"> Specific users/user groups <br>&nbsp; &nbsp; &nbsp;(Specify in the Comments column) ||
> | Which Teams features and modalities are in use? | <input type="checkbox"> Channel-based conversations <br/> <input type="checkbox"> Private chat <br/> <input type="checkbox"> Guest access <br/> <input type="checkbox"> Channel meetings <br/> <input type="checkbox"> Private meetings <br/> <input type="checkbox"> Private calling <br/> <input type="checkbox"> Ad-hoc channel meetup <br/> <input type="checkbox"> Videos in meetings <br/> <input type="checkbox"> Screen sharing in meetings <br/> <input type="checkbox"> Audio conferencing <br/><input type="checkbox"> Applications (apps)<br> &nbsp; &nbsp; &nbsp;<input type="checkbox"> Tabs<br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> Bots <br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> Connectors<br><input type="checkbox"> Custom cloud storage integration <br>&nbsp; &nbsp; &nbsp; (Box, Dropbox, ShareFile, Google Drive) <br/> <input type="checkbox"> Channel email integration <br/> <input type="checkbox"> Other (Specify in the Comments column.) | |
> | What applications have you deployed to Teams? | | |
> | Have you specifically blocked any Teams capabilities? <br/>If Yes, note the details in the Comments column. | <input type="checkbox"> Yes <br/> <input type="checkbox"> No ||
> | Which Teams clients are in use? | <input type="checkbox"> Web <br/> <input type="checkbox"> Windows <br/> <input type="checkbox"> Mac <br/> <input type="checkbox"> iOS <br/> <input type="checkbox"> Android <br/> <input type="checkbox"> Windows Mobile | |
> | Who has permissions to create teams? | <input type="checkbox"> Everyone in the organization <br>&nbsp; &nbsp; &nbsp;(This is the default setting) <br/> <input type="checkbox"> Specific people <br>&nbsp; &nbsp; &nbsp;(Specify in the Comments column.) | |
> | Are you using security and compliance features in Teams? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |

### Skype for Business Online (if applicable)

If applicable, capture the details of your Skype for Business Online deployment by using the sample table below. If you haven’t deployed Skype for Business Online deployment, skip this section.

> | Question | Answer | Comments |
> |---|---|---|
> | What types of users are enabled for Skype <br>for Business Online? | <input type="checkbox"> All users in the organization <br/> <input type="checkbox"> Specific users/user groups <br>&nbsp; &nbsp; &nbsp;(Specify in the Comments column) | |
> | What modalities and features are currently <br>in use today? | <input type="checkbox"> Instant Messaging and Presence (IM/P)<br/> <input type="checkbox"> Meetings <br/> <input type="checkbox"> Federation <br/> <input type="checkbox"> Meeting Recording <br/> <input type="checkbox"> Microsoft Audio Conferencing <br/> <input type="checkbox"> Third-party audio conferencing <br>&nbsp; &nbsp; &nbsp;(Note the details in the Comments column.) <br/> <input type="checkbox"> Calling Plans (formerly PSTN calling) <br/> <input type="checkbox"> Organizational Auto Attendants <br/> <input type="checkbox"> Call Queues | |
> | Have you specifically blocked any Skype for <br>Business Online capabilities? <br>If Yes, note the details in the Comments column. | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | What method are you using or plan to use to <br>connect Phone System (formerly Cloud PBX) to <br>the PSTN? <br/>Select all that apply. | <input type="checkbox"> Calling Plans (formerly PSTN calling) <br/> <input type="checkbox"> On-premises PSTN connectivity (leveraging existing <br>&nbsp; &nbsp; &nbsp;Skype for Business 2015 or Lync Server 2013 <br>&nbsp; &nbsp; &nbsp;deployment) <br/> <input type="checkbox"> On-premises PSTN connectivity (using Cloud Connector) | |
> | Have you ported any phone numbers to Microsoft? <br/>This is applicable to Calling Plans and Audio <br>Conferencing features. | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |

### Skype for Business on-premises (if applicable)

If applicable, capture the details of your Skype for Business deployment by using the sample table below. If you haven’t deployed Skype for Business on-premises, skip this section.

> | Question | Answer | Comments |
> |---|---|---|
> | What versions of Lync or Skype for Business currently <br>are deployed on-premises? | <input type="checkbox"> Office Communications Server 2007 “R1” <br/> <input type="checkbox"> Office Communications Server 2007 R2 <br/> <input type="checkbox"> Lync Server 2010 <br/> <input type="checkbox"> Lync Server 2013 <br/> <input type="checkbox"> Skype for Business Server 2015 <br/> <input type="checkbox"> Skype for Business Server 2019 <br/> <input type="checkbox"> Skype for Business Cloud Connector Edition | |
> | Is hybrid with Skype for Business Online configured? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Is this environment hosted and managed by a third party? <br/>If Yes, note the details in the Comments column. | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | What modalities and features are currently in use <br>today? | <input type="checkbox"> Instant Messaging and Presence (IM/P) <br/> <input type="checkbox"> Meetings <br/> <input type="checkbox"> Federation <br/> <input type="checkbox"> Meeting Recording <br/> <input type="checkbox"> Persistent Chat / Group Chat <br/> <input type="checkbox"> Microsoft Audio Conferencing <br>&nbsp; &nbsp; &nbsp;(formerly Dial in Conferencing) on your <br>&nbsp; &nbsp; &nbsp;on-premises Lync Server or <br>&nbsp; &nbsp; &nbsp;Skype for Business deployment <br/> <input type="checkbox"> Third-party audio conferencing <br>&nbsp; &nbsp; &nbsp;(Note the details in the Comments column) <br/> <input type="checkbox"> Enterprise Voice using on-premises PSTN <br>&nbsp; &nbsp; &nbsp;connectivity <br/> <input type="checkbox"> Calling Plans (formerly PSTN calling) via <br>&nbsp; &nbsp; &nbsp;Hybrid with Skype for Business Online | |
> | Which version(s) of Edge Server do you have deployed? | <input type="checkbox"> Office Communications Server 2007 “R1” <br/> <input type="checkbox"> Office Communications Server 2007 R2 <br/> <input type="checkbox"> Lync Server 2010 <br/> <input type="checkbox"> Lync Server 2013 <br/> <input type="checkbox"> Skype for Business Server 2015 <br/> <input type="checkbox"> Skype for Business Server 2019 | |
> | Do you have Lync or Skype for Business Edge deployed <br>into more than one datacenter? <br/>If Yes, note the details in the Comments column. | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Select services that your Edge role provides today. | <input type="checkbox"> External user access (corporate users) <br/> <input type="checkbox"> Remote user access (anonymous external <br>&nbsp; &nbsp; &nbsp;meeting participants) <br/> <input type="checkbox"> Federation <br/> <input type="checkbox"> Media relay | |
> | Which of the following voice calling features do you <br>currently have dependencies on? <br/>Note any additional dependencies in the Comments <br>column. | <input type="checkbox"> Busy options <br/> <input type="checkbox"> Call park <br/> <input type="checkbox"> Call pickup or group call pickup <br/> <input type="checkbox"> Common area phones, or “hot desking” <br/> <input type="checkbox"> Response groups or hunt groups <br/> <input type="checkbox"> Shared line appearance <br/> <input type="checkbox"> Private line <br/> <input type="checkbox"> Voicemail <br/> <input type="checkbox"> Call via work <br/> <input type="checkbox"> Emergency or information numbers <br>&nbsp; &nbsp; &nbsp;(911, 811, 411) <br/> <input type="checkbox"> Extension dialing <br/> <input type="checkbox"> Auto Attendant <br/> <input type="checkbox"> Subscriber access <br/> <input type="checkbox"> Analog devices <br/> <input type="checkbox"> Fax <br/> <input type="checkbox"> Caller ID masking or altering <br/> <input type="checkbox"> Location-based routing <br/> <input type="checkbox"> Least-cost routing <br/> <input type="checkbox"> Elevator phones | |

## Networking and access to Office 365 services

Use the following table to capture your organization’s networking details and how your users are (or will be) connected to Office 365 services.

> | Question | Answer | Comments |
> |---|---|---|
> | How do (or how will) the users in scope for migration <br>access Teams when they’re in the office? <br/>Select all that apply. | <input type="checkbox"> Routed NAT connection <br/> <input type="checkbox"> Proxy server <br/> <input type="checkbox"> Public Wi-Fi <br/> <input type="checkbox"> Managed (not public) Wi-Fi <br/> <input type="checkbox"> ExpressRoute (Microsoft peering) ||
> | If access to Office 365 is through a proxy server, is there <br>any way to bypass the proxy? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Is ExpressRoute being used today? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No <br/> <input type="checkbox"> No, but it’s being planned | |
> | Have you performed a Network Readiness Assessment? <br/>For more information, see [Network Readiness Assessment](https://myadvisor.fasttrack.microsoft.com/CloudVoice/Offers?pageState=NetworkReadiness). | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Are users required to use a VPN when connecting to <br>corporate resources remotely? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | If a VPN is used, can Teams traffic be excluded from <br>the VPN to access Office 365 Services directly? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Does your network support QoS? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Can you prioritize Teams audio and video traffic <br>to drive a high-quality experience? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Do all locations within a region have internet egress, <br>or is internet egress centralized for the entire region? | <input type="checkbox"> Regional access to the internet <br/> <input type="checkbox"> Centralized access to the internet | |

> [!TIP]
> To calculate the amount of bandwidth and other network requirements for your cloud voice deployment, depending your organization’s details and estimated usage, visit [Network Planner](https://myadvisor.fasttrack.microsoft.com/CloudVoice/NetworkPlanner) in [MyAdvisor](https://myadvisor.fasttrack.microsoft.com/).

## Endpoints

Use the following table to capture the details of the clients and endpoints in use.

> | Question | Answer | Comments |
> |---|---|---|
> | What desktop OS are the users using? | <input type="checkbox"> Windows XP <br/> <input type="checkbox"> Windows 7 <br/> <input type="checkbox"> Windows 8 <br/> <input type="checkbox"> Windows 10 <br/> <input type="checkbox"> Mac (Specify the version in the Comments column.) <br/> <input type="checkbox"> Other (Note the details in the Comments column.) | |
> | What version of Microsoft Office is deployed <br>to these devices? | <input type="checkbox"> Office 2003 <br/> <input type="checkbox"> Office 2007 <br/> <input type="checkbox"> Office 2010 <br/> <input type="checkbox"> Office 2013 <br/> <input type="checkbox"> Office 2016 <br/> <input type="checkbox"> Office for Mac 2011 <br/> <input type="checkbox"> Office for Mac 2016 <br/> <input type="checkbox"> Other (Note the details in the Comments column.) | |
> | Which Office deployment technology is in use <br>in your organization? | <input type="checkbox"> MSI <br/> <input type="checkbox"> Click-to-Run | |
> | What are the allowed and supported mobile <br>platforms in use? <br/>Select all that apply. | <input type="checkbox"> Windows <br/> <input type="checkbox"> Mobile <br/> <input type="checkbox"> iOS <br/> <input type="checkbox"> Android <br/> <input type="checkbox"> Other (Note the details in the Comments column.) | |
> | How are mobile devices provided? <br/>Select all that apply. | <input type="checkbox"> Corporate devices <br/> <input type="checkbox"> Bring your own device | |
> | What devices do users currently use to access <br>voice and conferencing services <br>(handsets, headsets, phones, video)? | | |

## Operations

Use the following table to capture the details of the operational aspects of your environment.

> | Question | Answer | Comments |
> |---|---|---|
> | What is your operations model for your Lync Server, <br>Skype for Business Server, or Office 365 deployment <br>today? | | |
> | Can you outline the current support arrangement for <br>Lync Server, Skype for Business Server, or Office 365? | | |
> | If you’re deploying to multiple countries or regions, <br>does each country/region have its own IT/telephony <br>staff to work with, or will this be managed centrally? | <input type="checkbox"> Regional operations and support <br/> <input type="checkbox"> Centralized operations and support | |
> | Are you following the [Call Quality Methodology](quality-of-experience-review-guide.md)? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No | |
> | Have you assigned an individual or team to the <br>Quality Champion role for the collaboration platform <br>in use? | <input type="checkbox"> Yes <br/> <input type="checkbox"> No ||
> | How do you monitor your Lync Server, Skype for <br>Business Server, or Office 365 deployment? | | |
> | Do you experience call quality issues? | <input type="checkbox"> Yes<br/> <input type="checkbox"> No | |
> | How and when do you provide training to your <br>helpdesk on new services and capabilities? | | |

## Adoption and readiness

Use the following table and capture the current adoption and readiness state of your organization.

>
> | Question | Answer | Comments |
> |---|---|---|
> | What is your current active usage of <br>Skype for Business? | **__** % total active users versus enabled users | |
> | How is your organization using <br>Skype for Business? | 1:1 conversations <br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> IM <br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> Calling <br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> Sharing<br> Meetings <br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> Conferencing<br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> Sharing<br>&nbsp; &nbsp; &nbsp;<input type="checkbox"> Calling | |
> | Does your organization have a User Adoption <br>and Change Management team? | <input type="checkbox"> Yes<br/> <input type="checkbox"> No | |
> | How do you currently measure success for technology <br>rollouts like Skype for Business? | | |
> | What percentage of your user base would you say has <br>adopted Skype for Business? | | |
> | What is user sentiment around Skype for Business? | <input type="checkbox"> Good <br/> <input type="checkbox"> Neutral <br/> <input type="checkbox"> Bad | |
> | Which of the following best describes the rollout <br>strategy used for your Skype for Business <br>deployment? | <input type="checkbox"> Broad reach: Email campaign with <br>&nbsp; &nbsp; &nbsp;links to training <br/> <input type="checkbox"> Expanded: Broad reach plus a variety <br>&nbsp; &nbsp; &nbsp;of awareness campaigns (posters, <br>&nbsp; &nbsp; &nbsp;events, champions) and training <br>&nbsp; &nbsp; &nbsp;(videos, user guides, in-person) <br/> <input type="checkbox"> Tailored: Expanded, plus targeted <br>&nbsp; &nbsp; &nbsp;messaging and training by persona <br/> <input type="checkbox"> Other <br>&nbsp; &nbsp; &nbsp;(Note the details in the Comments column.) | |

<table>
<tr><td><img src="media/audio_conferencing_image7.png" alt=""/> <br/>Decision point</td><td><ul><li>Who will be responsible for completing an environment assessment?</li></ul></td></tr>
<tr><td><img src="media/audio_conferencing_image9.png" alt=""/><br/>Next step</td><td><ul><li>Document the results of the environment assessment.</li></ul></td></tr>
</table>

After you evaluate your environment, proceed to the next step: [Prepare your network](upgrade-prepare-environment-prepare-network.md).
