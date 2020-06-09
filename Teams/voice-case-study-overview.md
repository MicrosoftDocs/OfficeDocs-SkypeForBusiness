---
title: Teams voice Contoso case study
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 06/09/2020
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

# Contoso case study: Teams overview

This article introduces a case study for how a fictional multi-national corporation, Contoso, implemented a Teams voice solution for their organization.

Contoso has deployed Microsoft 365 Enterprise and addressed major design decisions and implementation details for the following: networking, identity, Windows 10 Enterprise, Office 365 ProPlus, mobile device management, information protection, security, migration from Skype for Business to Teams, Phone System, and Audio Conferencing.  

This article focuses on how Contoso migrated their on-premises users to Teams for unified communication, collaboration, and voice. For background information and details about how Contoso accelerated their digital transformation by using Microsoft's cloud services, see all the core articles starting with the [Contoso Overview](https://docs.microsoft.com/microsoft-365/enterprise/contoso-overview?view=o365-worldwide). 

In the core articles, you'll find information on the following:  

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

For information about planning an upgrade, you'll want to start with [Getting started with your Microsoft Teams upgrade](upgrade-start-here.md).

## Contoso business goals for Teams

To migrate their on-premises users to Teams for unified communication, collaboration, and voice, Contoso decided on the following business goals:

- Teams enablement 

  Contoso's unified communication and collaboration team enabled Teams with the correct policies to govern and enable secure internal and external collaboration. 

- Skype for Business to Teams migration 

  Skype for Business was widely deployed within Contoso. With the need to get off of legacy systems, Contoso decided to migrate their Skype for Business users to Teams. For more information, see [Contoso case study: Teams migration plan](voice-case-study-migration-plan.md).

- Phone System  

  Skype for Business with enterprise voice was widely deployed within Contoso. With the need to get off of legacy systems that were the next hop for their mediation servers, Contoso migrated their Skype for Business enterprise voice users to Phone System. Contoso sites leveraged Microsoft Calling Plan, Phone System Direct Routing, or a combination of both. For more information, see [Contoso case study: Phone System](voice-case-study-phone-system.md).

- Location-Based Routing 

  With office locations in telephony-regulated countries, Contoso needed to recreate the Location-Based Routing that was present in Skype for Business in their Phone System deployment. For more information, see [Contoso case study: Location-Based Routing](voice-case-study-location-based-routing.md).

- Emergency Calling 

  Where Direct Routing was implemented, Contoso set up up emergency calling with approved third parties. For more information, see [Contoso case study: Emergency Calling](voice-case-study-emergency-calling.md).

- Audio Conferencing 

  Contoso set up Audio Conferencing service numbers that were hosted on their SIP trunk to their PSTN provider. For more information, see [Contoso case study: Audio Conferencing](voice-case-study-audio-conferencing.md). 

- Local Media Optimization 

  Contoso took advantage of Local Media Optimization in locations where they had one direct route trunk to Microsoft Phone System that was leveraged by remote sites. For more information, see [Plan for Local Media Optimization](direct-routing-media-optimization.md) and [Configure Local Media Optimization](direct-routing-media-optimization-configure.md).

- Auto Attendants and Call Queues.

  As a result of Covid-19, Contoso wanted to provide receptionist support while their staff was working remotely. Contoso leveraged auto attendants and call queues to manage incoming calls to their receptionist's phone number. For more information, see [Contoso case study: Auto Attendants and Call Queues](voice-case-study-call-queues.md).  


