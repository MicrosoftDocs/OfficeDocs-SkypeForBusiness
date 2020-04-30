---
title: Teams voice Contoso case study
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 01/28/2019
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
  - M365-voice
ms.reviewer: crowe
search.appverid: MET150
f1.keywords: ms.teamsadmincenter.directrouting.overview
f1.keywords:
- NOCSH
description: Teams voice case study for multi-national corporation
appliesto: 
  - Microsoft Teams
---

# Overview

This article introduces a case study for how a fictional multi-national corporation, Contoso, implemented a Teams voice solution for their organization.

The Contoso Corporation is a representative global manufacturing conglomerate with its headquarters in Paris, France. The overall goal of Contoso is to accelerate their digital transformation by using cloud services to bring together its employees, partners, data, and processes to create customer value and maintain its competitive advantage in a digital-first world. 

Contoso has deployed Microsoft 365 Enterprise and addressed major design decisions and implementation details for networking, identity, Windows 10 Enterprise, Office 365 ProPlus, mobile device management, information protection, security, migration from Skype for Business to Teams, Phone System, and Audio Conferencing.  

The articles in the Teams library focus on how Contoso migrated their on-premises users to Teams for unified communication, collaboration, and voice. For background information and details about Contoso, see all the core articles starting with the [Contoso Overview](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-overview?view=o365-worldwide). 

You'll find information on the following:  

- [Contoso's IT infrastructure needs](https://docs.microsoft.com/microsoft-365/enterprise/contoso-infra-needs?view=o365-worldwide)
- [Networking](https://docs.microsoft.com/microsoft-365/enterprise/contoso-networking?view=o365-worldwide)
- [Identity](https://docs.microsoft.com/microsoft-365/enterprise/contoso-identity?view=o365-worldwide)
- [Windows 10 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/contoso-win10?view=o365-worldwide)
- [Office 365 Pro Plus](https://docs.microsoft.com/microsoft-365/enterprise/contoso-o365pp?view=o365-worldwide)
- [Mobile device management](https://docs.microsoft.com/microsoft-365/enterprise/contoso-mdm?view=o365-worldwide)
- [Information protection](https://docs.microsoft.com/microsoft-365/enterprise/contoso-info-protect?view=o365-worldwide)
- [Summary of Microsoft 365 Enterprise security](https://docs.microsoft.com/microsoft-365/enterprise/contoso-security-summary?view=o365-worldwide)
- [Team for a top-secret project](https://docs.microsoft.com/microsoft-365/enterprise/contoso-team-for-top-secret-project?view=o365-worldwide)
- [SharePoint Online site for highly confidential digital assets](https://docs.microsoft.com/microsoft-365/enterprise/contoso-sharepoint-online-site-for-highly-confidential-assets?view=o365-worldwide)


## Contoso business goals for Teams

To migrate their on-premises users to Teams for unified communication, collaboration, and voice, Contoso decided on the following business goals:

- Teams enablement 

  Contoso's unified communication and collaboration team enabled Teams with the correct policies to govern and enable secure internal and external collaboration. 

- Skype for Business to Teams migration 

  Skype for Business was widely deployed within Contoso. With the need to get off of legacy systems, Contoso decided to migrate their Skype for Business users to Teams. 

- Phone System  

  Skype for Business with enterprise voice was widely deployed within Contoso. With the need to get off of legacy systems that were the next hop for their mediation servers, Contoso migrated their Skype for Business enterprise voice users to Phone System. Sites leveraged Microsoft Calling Plan, Phone System Direct Routing, or a combination of both. 

- Location-Based Routing 

  With office locations in telephony-regulated countries, Contoso needed to recreate the Location-Based Routing that was present in Skype for Business in Teams Phone System.

- Emergency Calling 

  Where Direct Routing was implemented, Contoso set up up emergency calling with approved third parties.  

- Audio Conferencing 

  Contoso set up Audio Conferencing service numbers that were hosted on their SIP trunk to their PSTN provider.  

- Local Media Optimization 

  Contoso took advantage of Local Media Optimization in locations where they had one direct route trunk to Office 365 Phone System that was leveraged by remote sites.  

## Migration plan from Skype for Business to Teams

In the decision to migrate from Skype for Business to Teams, Contoso wanted to provide an easy transition experience for end users. Instead of switching everyone to Teams at the same time, they decided to set up hybrid connectivity, and **move the Teams-enabled users to Skype for Business Online (??)**. This allowed users in Teams and Skype for Business on-premises to share presence and communicate.  

**QUESTION:  DOES THIS MEAN THEY ARE USING THE OVERLAPPING CAPABILITIES METHOD OR THE SELECT CAPABILITIES METHOD?  WE SHOULD USE THE SAME TERMINOLOGY AS THE CORE DOCS**

Contoso read the following articles--[Upgrade from Skype for Business to Teams — for IT administrators](upgrade-to-teams-on-prem-overview.md) and [Migration and interoperability guidance for organizations using Teams together with Skype for Business](migration-interop-guidance-for-teams-with-skype.md)--and attended the Ignite 2019 session [Designing your path from Skype for Business to Teams](https://myignite.techcommunity.microsoft.com/sessions/81820?source=sessions) to understand the following:

- Fundamental concepts such as interop, federation, and upgrade behavior 

- Coexistence modes and management based on TeamsUpgradePolicy 

- End user experience for: 

  - Chat and Calling 

  - Meeting Scheduling 

  - Availability of collaboration functionality in Teams clients 

To plan and configure hybrid connectivity, the first step in moving their on-premises environment to the cloud, Contoso read
[Plan hybrid connectivity](https://docs.microsoft.com/en-us/SkypeForBusiness/hybrid/plan-hybrid-connectivity) and 
 [Configure hybrid connectivity between Skype for Business Server and Office 365](https://docs.microsoft.com/en-us/SkypeForBusiness/hybrid/configure-hybrid-connectivity.md) to understand how to: 

  - Configure their on-premises environment service to federate with Office 365. 

  - Configure their on-premises environment to trust Office 365 and enable shared SIP address space with Office 365 

  - Enable shared SIP address space in their Office 365 tenant.

  - Leverage Islands mode during the technical pilot.

  - Switch users over to Teams Only mode once the user is enabled for Phone System. Teams Only mode is required for  Calling Plan and Direct Routing. 
