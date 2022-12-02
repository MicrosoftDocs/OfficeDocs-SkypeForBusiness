--- 
title: Turn off the meeting lobby in Microsoft Teams
ms.author: mikeplum
author: MikePlumleyMSFT
ms.reviewer: rbronisevsky
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
description: Learn how to turn off the meeting lobby in Microsoft Teams and allow all participants to join the meeting directly
---

# Turn off the meeting lobby in Microsoft Teams


Who can bypass = everyone
dial-in can bypass = on
anonymous / dial-in can start a meeting

===========================

This is a per-organizer policy. This setting controls whether people join a meeting directly or wait in the lobby until they're admitted by an authenticated user. This setting doesn't apply to dial-in users.


 Meeting organizers can click **Meeting Options** in the meeting invitation to change this setting for each meeting they schedule.

> [!NOTE]
> In the meeting options the setting is labeled "Who can bypass the lobby". If you change the default setting for any user, it will apply to all new meetings organized by that user and any prior meetings where the user didn't modify Meeting options.
  
|Setting value  |Join behavior |
|---------|---------|
|**Everyone**   |All meeting participants join the meeting directly without waiting in the lobby. This includes authenticated users, users from trusted organizations, guests, and anonymous users.     |
|**People in my organization and guests**     |Authenticated users within the organization, including guests, join the meeting directly without waiting in the lobby. Users from trusted organizations and anonymous users wait in the lobby. This is the default setting.    |
|**People in my organization, trusted organizations, and guests**     |Authenticated users within the organization, including guests and the users from trusted organizations, join the meeting directly without waiting in the lobby.  Anonymous users wait in the lobby.   |
|**People in my organization**    |Authenticated users from within the organization join the meeting directly without waiting in the lobby.  Users from trusted organizations, guests, and anonymous users wait in the lobby.          |
|**Organizer only**    |Only meeting organizers can join the meeting directly without waiting in the lobby. Everyone else, including authenticated users within the organization, guests, users from trusted organizations, and anonymous users must wait in the lobby. On the Teams client meeting options page, it appears as "Only me".          |
|**Invited users only**    |Only invited users and meeting organizers can join the meeting directly without waiting in the lobby. Everyone else, including authenticated users within the organization, guests, users from trusted organizations, and anonymous users must wait in the lobby. On the Teams client meeting options page, it appears as "People I invite". Users added as a part of a distribution group will have to go through the lobby.      |

 > [!NOTE]
> Trusted organizations are domains that you allow federated communications with in Teams. If you enable **Allow all external domains** for external access in the Teams admin center, any authenticated user within any Teams organization will be trusted. If you choose to specify external domains that are allowed and block all others, the allowed domains become trusted organizations. Any blocked domain is considered to not be a trusted organization.

## Dial-in users can bypass the lobby

This is a per-organizer policy. This setting controls whether people who dial in by phone join the meeting directly or wait in the lobby regardless of the **Automatically admit people** setting. By default, this setting is turned off. When this setting is turned off, dial-in users will wait in the lobby until an organization user joins the meeting with a Teams client and admits them. When this setting is turned on, dial-in users will automatically join the meeting when an organization user joins the meeting with a Teams client.

> [!NOTE]
> If a dial-in user joins a meeting before an organization user joins the meeting, they will be placed in the lobby until an organization user joins the meeting using a Teams client and admits them. If you change the default setting for any user, it will apply to all new meetings organized by that user and any prior meetings where the user didn't modify Meeting options.

## Related topics

