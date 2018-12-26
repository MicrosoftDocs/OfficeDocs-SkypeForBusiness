---
title: Teams Only mode considerations
author: dearbeen
ms.author: dearbeen
manager: serdars
ms.date: 12/26/2018
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

While thousands of customers have successfully upgraded to Microsoft Teams, there are a few considerations that may influence your organization’s upgrade timeline and user experience. Prior to upgrading users to Teams Only mode, review the below scenarios for applicability and take the recommended next actions to help ensure a positive upgrade to Teams. 

**Tenant-wide considerations**: We are working on enabling Teams in the following environment; however, in the meantime administrators shouldn’t upgrade any users in their organization if either of the following is true:

- The Skype for Business tenant is hosted in one of the following environments:
    - Government Community Cloud High
    - Government Community Cloud DoD
    - Office 365 operated by 21Vianet
    - Office 365 Germany

- The Skype for Business tenant is hosted in France or South Korea AND Teams residency is required in the region.

**User-specific considerations**: Some user scenarios are still evolving, and administrators may decide to temporarily postpone the upgrade for these users, but may proceed with upgrading other users in the organization. Please monitor the [Office 365 Roadmap](https://www.microsoft.com/en-us/microsoft-365/roadmap) site for announcements.

| Scenario | Notes |
|----------|-------|
|User’s primary work device is a Mac, and user needs to see colleagues' availability in Outlook. | Outlook presence in Teams is not yet fully supported for Mac devices. |
| User is regularly conducting meetings with customers or external partners in different international regions. | External attendees whose tenant resides in a different geo-location don’t see IM chat while in a federated meeting. |
| User is conducting Skype for Business Broadcast meetings. |  While Teams live events (replacing Skype Broadcast) is already in public preview, this user may need to stay on Skype for Business until general availability of Teams live events.
| User uses Skype for Business Audio Conferencing in India and/or Hong Kong. | |
| User’s primary device is VDI-based. |

**Coexistence considerations**: The following experiences do not preclude upgrading users, but administrators should be aware of them. 

- Interoperability between Microsoft Teams and Skype for Business allows upgraded Teams users to continue communicating with colleagues within and outside of their organizations through basic chat, VoIP and PSTN calls, and meetings. At the same time administrators should be aware that:
    -   An upgraded to Teams user conducting a 1:1 chat or VoIP call with Skype for Business users can’t add a third user to messaging or to a VoIP call session. 
    - An upgraded to Teams user can’t share a desktop or application with a Skype for Business user. 
    - An upgraded to Teams user conducting a 1:1 chat with a Skype for Business user can’t attach a file to the chat. 

- An upgraded to Teams user can’t communicate with a Skype for Consumer user who is not using Microsoft Teams. 

**Remember**: The move to Teams is more than a technical migration. For a successful upgrade assesses both technical readiness and end-user readiness. Review our Skype for Business to Teams [upgrade guidance](upgrade-framework.md) for more information on planning an implementing your upgrade to Teams.  