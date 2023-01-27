---
title: Plan for meetings with external participants in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: conceptual
ms.service: msteams
ms.reviewer: rafarrbronisevsky, alsolom
audience: admin
search.appverid: MET150
ms.localizationpriority: normal
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.orgwidesettings.guestaccess.overview
  - chat-teams-channels-revamp
ms.collection: 
  - Teams_ITAdmin_GuestAccess
  - M365-collaboration
  - m365initiative-externalcollab
appliesto: 
  - Microsoft Teams
description: Learn how to plan for meetings with people outside your organization in Microsoft Teams.
---

# Plan for meetings with external participants in Microsoft Teams

External access is for other AAD orgs

Guests can be used for non-AAD orgs to validate participants

If neither of those is used, then the participant is anonymous

Validating external meeting participants

Lobby implications

## Types of meeting participants

External participants in Teams meetings have one of three possible identities:
- **Guests** - people who have an [Azure AD B2B collaboration guest account](/azure/active-directory/external-identities/what-is-b2b) in your directory
- **People from trusted organizations** - people in other Microsoft 365 organizations with which you have a two-way trust relationship and who are assigned a meeting policy that allows them to communicate with trusted organizations
- **Anonymous** - People who's identity can't be validated by Teams

Both guests and people from trusted organizations can be validated by Teams. Guests are validated in your own directory and people in trusted organizations are validated by Azure AD in an organization that you have a trust relationship with.

## Meetings with other Microsoft 365 organizations




## Meetings with non-Microsoft 365 organizations




[Manage external meetings and chat with people and organizations using Microsoft identities](trusted-organizations-external-meetings-chat.md)

[Use guest access and external access to collaborate with people outside your organization](communicate-with-users-from-other-organizations.md)

[Control who can bypass the meeting lobby in Microsoft Teams](who-can-bypass-meeting-lobby.md)

[Manage anonymous participant access to Teams meetings](anonymous-users-in-meetings.md)


## Related topics

[Add Azure Active Directory B2B collaboration users in the Azure portal](/azure/active-directory/external-identities/add-users-administrator)