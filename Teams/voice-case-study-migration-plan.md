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

In the decision to migrate from Skype for Business to Teams, Contoso wanted to provide an easy transition experience for end users. Instead of switching everyone to Teams at the same time, they decided to set up hybrid connectivity, and use the overlapping capabilities method to move users to Teams. This allowed users in Teams and Skype for Business on-premises to share presence and communicate. As users entered the pilot for Phone System, they were moved to Teams Only mode.

Contoso leveraged overlapping capabilities method during the transition. As users entered the pilot for phone system they moved to Teams only mode. 

To understand fundamental concepts about migration, methods, and modes, Contoso read the following articles--[Upgrade from Skype for Business to Teams](upgrade-to-teams-on-prem-overview.md) and [Migration and interoperability guidance](migration-interop-guidance-for-teams-with-skype.md)--and attended the Ignite 2019 session [Designing your path from Skype for Business to Teams](https://myignite.techcommunity.microsoft.com/sessions/81820?source=sessions). Contoso learned about:

- Fundamental concepts such as interoperability, federation, and upgrade behavior 

- Coexistence modes and management based on TeamsUpgradePolicy 

- End user experience for: 

  - Chat and Calling 

  - Meeting scheduling 

  - Availability of collaboration functionality in Teams clients 

To plan and configure hybrid connectivity, the first step in moving their on-premises environment to the cloud, Contoso read
[Plan hybrid connectivity](https://docs.microsoft.com/SkypeForBusiness/hybrid/plan-hybrid-connectivity) and 
 [Configure hybrid connectivity](https://docs.microsoft.com/SkypeForBusiness/hybrid/configure-hybrid-connectivity) to understand how to: 

  - Configure their on-premises environment service to federate with Office 365. 

  - Configure their on-premises environment to trust Office 365 and enable shared SIP address space with Office 365 

  - Enable shared SIP address space in their Office 365 tenant.

  - Leverage Islands mode during the technical pilot.

  - Switch users to TeamsOnly mode once the user is enabled for Phone System. TeamsOnly mode is required for  Calling Plan and Direct Routing. 
