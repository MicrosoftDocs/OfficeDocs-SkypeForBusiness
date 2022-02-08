---
title: Teams Only mode considerations
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.date: 01/09/2019
ms.topic: conceptual
audience: admin
ms.service: msteams
ms.reviewer: landerl
description: Admin can learn about how to prepare for an upgrade to Microsoft Teams Only mode in the Microsoft Teams admin center. 
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- CSH
ms.custom: 
 - Teams-upgrade-guidance
 - ms.teamsadmincenter.orgwidesettings.teamsupgrade.upgradetoteams
 - seo-marvel-apr2020
ms.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Teams Only mode considerations

Administrators of Microsoft 365 or Office 365 organizations can upgrade either individual users or the entire tenant to Teams Only mode.  

[!INCLUDE [sfbo-retirement-skype](../Skype/Hub/includes/sfbo-retirement.md)]

Upgrading to Teams Only mode offers users the full benefits of Microsoft Teams, the hub for teamwork in Microsoft 365 or Office 365, via a single client experience. Users in Teams Only mode will receive all calls and chats in Teams, regardless of whether the sender is using Skype for Business or Teams, and benefit from interop and federation support.

Although thousands of customers have successfully upgraded to Microsoft Teams, there are considerations that may influence your organization's upgrade timeline and user experience along the way. For the best user experience, confirm that Teams meets your collaboration and communication requirements, make sure that your network is ready to support Teams, and implement your user readiness plan before upgrading users to Teams. 

> [!IMPORTANT]
> If you are just starting your upgrade planning, be sure to review our [Getting started with your Microsoft Teams upgrade](upgrade-start-here.md) guide. 

**Coexistence considerations**: Organizations already using Skype for Business Online and/or Skype for Business Server can introduce Teams into their environment at a pace that meets their needs. Organizations can incrementally roll out Teams to a desired set of users as needed, and users who use Teams can communicate with users who use Skype for Business and vice versa. To manage this experience, administrators use coexistence modes, which define the end-user client experience, the routing behavior of incoming chats and calls, and whether new meetings are scheduled in Teams or Skype for Business. Users can federate with users in other organizations if the user is upgraded to **Teams Only**; however, the best experience is provided when both users use Teams. Users who are upgraded to Teams Only can still join Skype for Business meetings. 

> [!IMPORTANT]
> For more detailed information about coexistence, please refer to [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md). For more information about Teams and Skype (Consumer), see [Teams and Skype interoperability](teams-skype-interop.md).


**User-specific considerations**: Some user scenarios are still evolving, and administrators may decide to temporarily postpone the upgrade of certain users while upgrading other users in the organization. In particular, we are still working on addressing scenarios for users whose primary device is VDI-based. For site announcements, monitor the [Microsoft 365 Roadmap](https://www.microsoft.com/microsoft-365/roadmap).

> [!NOTE]
> Before you move to Teams Only mode you need to replace or update devices that don't support Teams. 

> [!IMPORTANT]
> **Remember**: The move to Teams is more than a technical migration. A successful upgrade assesses both technical readiness and end-user readiness. Review our Skype for Business to Teams [upgrade guidance](upgrade-framework.md) for more information on planning an implementing your upgrade to Teams.  
