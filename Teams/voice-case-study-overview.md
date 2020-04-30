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


- [Plan Direct Routing](direct-routing-plan.md) 

# Overview

The Contoso Corporation is a fictional but representative global manufacturing conglomerate with its headquarters in Paris, France. Contoso has deployed Microsoft 365 Enterprise and addressed major design decisions and implementation details for networking, identity, Windows 10 Enterprise, Office 365 ProPlus, mobile device management, information protection, security,migration from Skype for Business to Teams, Phone System, and Audio Conferencing.  

The overall goal of Contoso for Microsoft 365 Enterprise is to accelerate their digital transformation by using cloud services to bring together its employees, partners, data, and processes to create customer value and maintain its competitive advantage in a digital-first world. 

For details on how Contoso...   see all the core Contoso articles starting with the [Contoso Overview](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-overview?view=o365-worldwide).

You'll find information on the following:  

- [Contoso's IT infrastructure needs](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-infra-needs?view=o365-worldwide)
- [Networking](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-networking?view=o365-worldwide)
- [Identity](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-identity?view=o365-worldwide)
- [Windows 10 Enterprise](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-win10?view=o365-worldwide)
- [Office 365 Pro Plus](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-o365pp?view=o365-worldwide)
- [Mobile device management](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-mdm?view=o365-worldwide)
- [Information protection](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-info-protect?view=o365-worldwide)
- [Summary of Microsoft 365 Enterprise security](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-security-summary?view=o365-worldwide)
- [Team for a top-secret project](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-team-for-top-secret-project?view=o365-worldwide)
- [SharePoint Online site for highly confidential digital assets](https://docs.microsoft.com/en-us/microsoft-365/enterprise/contoso-sharepoint-online-site-for-highly-confidential-assets?view=o365-worldwide)
- 


These articles focus on how Contoso migrated their on-premises users to Teams for unified communication, collaboration, and voice.  Contose decided on the following business goals:



- Teams Enablement 

  Contoso's unified communication and collaboration team enabled Teams with the correct policies to govern and enable secure internal and external collaboration. 

- Skype for Business to Teams Migration 

  Skype for Business was widely deployed within Contoso. With the need to get off of legacy systems, Contoso decided to migrate their Skype for Business users to Teams. 

- Phone System  

  Skype for Business with enterprise voice was widely deployed within Contoso. With the need to get off of legacy systems that were the next hop for their mediation servers, Contoso migrated their Skype for Business enterprise voice users to Phone System. Sites leveraged Microsoft Calling Plan, Phone System Direct Routing, or a combination of both. 

- Location Based Routing 

  With office locations in telephony-regulated countries, Contoso needed to recreate the location based routing that was present in Skype for Business in Phone System.

- Emergency Calling 

  Where Direct Routing was implemented, Contoso set up up emergency calling with approved third parties.  

- Audio Conferencing 

  Contoso set up Audio Conferencing service numbers that were hosted on their SIP trunk to their PSTN provider.  

- Local Media Optimization 

  Contoso took advantage of Local Media Optimization in locations where they had one direct route trunk to Office 365 Phone System that was leveraged by remote sites.  -

In the decision to migrate from Skype for Business to Teams, Contoso wanted to provide an easy transition experience for end users. Instead of switching everyone to Teams at the same time, they set up hybrid connectivity, and moved the Teams-enabled users to Skype for Business Online. This allowed users in Teams and Skype for Business on-premises to share presence and communicate.  

Contoso followed Migration and interoperability guidance for organizations using Teams together with Skype for Business and attended the Ignite 2019 session Designing your path from Skype for Business to Teams to understand the following:

- Fundamental concepts such as interop, federation, and upgrade behavior 

- Coexistence modes and management based on TeamsUpgradePolicy 

- End user experience for 

  - Chat and Calling 

  - Meeting Scheduling 

  - Availability of collaboration functionality in Teams clients 

 

Contoso decided to: 

- Follow Configure Skype for Business Hybrid to: 

  - Configure on-premises environment service to federate with Office 365 

  - Configure on-premises environment to trust Office 365 and enable on-premises environment to enable shared SIP address space 

  - Enable shared Sip address space in your Office 365 tenant 

  - Leverage islands mode during the technical pilot 

  - Switch users over to Teams Only mode once the user is enabled for Phone System. Teams only mode is required for direct routing and calling plan. 
  - 