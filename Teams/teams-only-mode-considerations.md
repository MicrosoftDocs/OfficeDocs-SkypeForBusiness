---
title: Teams Only mode considerations
author: dearbeen
ms.author: dearbeen
manager: serdars
ms.date: 01/09/2019
ms.topic: conceptual
ms.service: msteams
ms.reviewer: dearbeen
description: Prepare for your upgrade to Microsoft Teams Only mode 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
f1keywords: ms.teamsadmincenter.orgwidesettings.teamsupgrade.upgradetoteams
MS.collection: 
- Teams_ITAdmin_JourneyFromSfB
- M365-collaboration
appliesto:
- Microsoft Teams
---

# Teams Only mode considerations

If you are an administrator on your Office 365 tenant, you will now see the option to upgrade to Teams Only mode in the Microsoft Teams admin center. With this functionality you can upgrade either individual users, or alternatively, the entire tenant.  

Upgrading to Teams Only mode offers users the full benefits of Microsoft Teams, the hub for teamwork in Office 365, via a single client experience. Additionally, users in Teams Only mode will receive all calls and chats in Teams, regardless of whether the sender is using Skype for Business or Teams, and benefit from interop and federation support.

While thousands of customers have successfully upgraded to Microsoft Teams, there are considerations that may influence your organization’s upgrade timeline and user experience along the way. In particular, having the option to upgrade doesn’t necessarily mean your organization is ready for this change. For the best user experience, confirm that Teams meets your collaboration and communication requirements, make sure that your network is ready to support Teams, and implement your user readiness plan before upgrading users to Teams. 

> [!IMPORTANT]
> If you are just starting your upgrade planning, be sure to review our full upgrade guidance and planning resources. [Start here](upgrade-introduction.md). 

**Coexistence considerations**: Organizations already using Skype for Business Online and/or Skype for Business Server can introduce Teams into their environment at a pace that meets their needs. Organizations can incrementally roll out Teams to a desired set of users as needed, and users who use Teams can communicate with users who use Skype for Business and vice versa. To manage this experience, administrators use coexistence modes, which define the end user client experience, the routing behavior of incoming chats and calls, as well as whether new meetings are scheduled in Teams or Skype for Business. Users can federate with users in other organizations if the user is upgraded to **Teams Only**; however, the best experience is provided when both users use Teams. Users who are upgraded to Teams Only can still join Skype for Business meetings. 

> [!NOTE]
> Users who are upgraded to Teams Only cannot communicate with users who are using Skype for Consumer.

> [!IMPORTANT]
> For more detailed information about coexistence please refer to [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md). 

**Tenant-wide considerations**: We are working on enabling Teams in the following environments; however, for now, administrators shouldn't upgrade any users in their organization if their Skype for Business tenant is hosted in one of the following environments:

 - Government Community Cloud High
 - Government Community Cloud DoD
 - Office 365 operated by 21Vianet
 - Office 365 Germany
 - Skype for Business tenant is hosted in South Korea **and** the organization requires Teams data to be stored in South Korea. Currently, organizations with Skype for Business data stored in South Korea that upgrade to Teams will have their Teams data stored in the Asia datacenter region, not in the South Korea datacenter region.

**User-specific considerations**: Some user scenarios are still evolving, and administrators may decide to temporarily postpone the upgrade of certain users while upgrading other users in the organization. We are working on addressing these scenarios; please monitor the [Office 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap) site for announcements.

| Scenario | Notes |
|----------|-------|
|User’s primary work device is a Mac, and user needs to see colleagues' availability in Outlook. | Outlook presence in Teams is not yet fully supported for Mac devices. |
| User is regularly conducting meetings with customers or external partners in different international regions. | External attendees whose tenant resides in a different geo-location don’t see IM chat while in a **federated** meeting. Participants can still join the meeting as anonymous users. |
| User is conducting Skype for Business Broadcast meetings. |  While Teams live events (replacing Skype Broadcast) is already in public preview, this user may need to stay on Skype for Business until general availability of Teams live events.
| User’s primary device is VDI-based. | |
|||

> [!IMPORTANT]
> **Remember**: The move to Teams is more than a technical migration. A successful upgrade assesses both technical readiness and end-user readiness. Review our Skype for Business to Teams [upgrade guidance](upgrade-framework.md) for more information on planning an implementing your upgrade to Teams.  
