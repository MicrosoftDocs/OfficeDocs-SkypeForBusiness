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

# Contoso case study: Teams migration plan

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
