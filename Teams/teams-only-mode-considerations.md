---
title: Teams Only mode considerations
author: dearbeen
ms.author: dearbeen
manager: serdars
ms.date: 01/08/2019
ms.topic: article
ms.service: msteams
ms.reviewer: dearbeen
description: Prepare for your upgrade to Microsoft Teams Only mode 
localization_priority: Normal
search.appverid: MET150
ms.custom: Teams-upgrade-guidance
MS.collection: Teams_ITAdmin_JourneyFromSfB
appliesto:
- Microsoft Teams
---

# Teams Only mode considerations



> [!IMPORTANT]
> [!INCLUDE [upgrade-disclaimer](includes/upgrade-disclaimer.md)]

While thousands of customers have successfully upgraded to Microsoft Teams, there are a few considerations that may influence your organization’s upgrade timeline and user experience. If you're just starting your upgrade planning journey, be sure to review our full upgrade guidance and planning resources. Start here. If your organization is ready to **upgrade users to Teams Only mode**, review the scenarios below for applicability, and take the recommended next actions to help ensure a positive upgrade to Teams. 

**Tenant-wide considerations**: We are working on enabling Teams in the following environments; however, in the meantime administrators shouldn’t upgrade any users in their organization if:

- The Skype for Business tenant is hosted in one of the following environments:

    - Government Community Cloud High
    - Government Community Cloud DoD
    - Office 365 operated by 21Vianet
    - Office 365 Germany

- The Skype for Business tenant is hosted in South Korea **and** the organization requires Teams data to be stored in South Korea. Currently, organizations with Skype for Business data stored in South Korea that upgrade to Teams will have their Teams data stored in the Asia datacenter region, not in the South Korea datacenter region.

**User-specific considerations**: Some user scenarios are still evolving, and administrators may decide to temporarily postpone the upgrade of certain users while upgrading other users in the organization. We are working on addressing these scenarios; please monitor the [Office 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap) site for announcements.

| Scenario | Notes |
|----------|-------|
|User’s primary work device is a Mac, and user needs to see colleagues' availability in Outlook. | Outlook presence in Teams is not yet fully supported for Mac devices. |
| User is regularly conducting meetings with customers or external partners in different international regions. | External attendees whose tenant resides in a different geo-location don’t see IM chat while in a **federated** meeting. Participants can still join the meeting as anonymous users. |
| User is conducting Skype for Business Broadcast meetings. |  While Teams live events (replacing Skype Broadcast) is already in public preview, this user may need to stay on Skype for Business until general availability of Teams live events.
| User uses Skype for Business Audio Conferencing in India and/or Hong Kong. | |
| User’s primary device is VDI-based. | |
|||

**Coexistence considerations**: The following experiences do not preclude upgrading users, but administrators should be aware of them. 

- Teams Only users who have federation can participate in 1:1 chat and calling with external users. For a richer experience these users will need to schedule a meeting either from Skype for Business or Teams, depending on the user’s default client. 

- An upgraded to Teams user can’t communicate with a Skype for Consumer user who is not using Microsoft Teams. 

For more detailed information about coexistence, please refer to [Understand Microsoft Teams and Skype for Business coexistence and interoperability](teams-and-skypeforbusiness-coexistence-and-interoperability.md). 

**Remember**: The move to Teams is more than a technical migration. For a successful upgrade assesses both technical readiness and end-user readiness. Review our Skype for Business to Teams [upgrade guidance](upgrade-framework.md) for more information on planning an implementing your upgrade to Teams.  
