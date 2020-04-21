---
title: Communicate with users from other organizations in Microsoft Teams
author: CindyChurch
ms.author: cichur
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
ms.collection: 
- Teams_ITAdmin_GuestAccess
- M365-collaboration
ms.reviewer: dansteve
search.appverid: MET150
f1.keywords:
- NOCSH
description: Learn about the roles in a Teams meeting or live event.
appliesto: 
- Microsoft Teams
localization_priority: Priority
---
Roles in a Teams meeting or live event
======================================================

Microsoft Teams meetings and live events support many user types. Users can access various meeting and live event features based on their roles inside or outside of an organization.

The available meeting features are:

- Chat
- Meeting Notes
- Whiteboard
- Recording
- Files

This article describes those user roles and what access they have to meeting and live event features.

## Presenters and organizers

Presenters and organizers include the following:

- Presenters from my organization
- Presenters from other organizations (Live Events restriction) - this includes business-to-business (B2B) and anonymous/external

Presenters and organizers have access to every feature in a meeting or live event.

## Attendees

There are several types of users who can be attendees.

### In-tenant user

The in-tenant user belongs to the organization and has credentials for the tenant. Learn more about user types in [Security and Microsoft Teams](teams-security-guide#participant-types.md).

|Meeting  |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes |Yes |
| Whiteboard | Yes | Yes |Yes |
| Recording | N/A |Yes | Yes |
| Files | Yes | Yes | Yes |
| Schedule a meeting | Yes | N/A | N/A |
|||||||

| Live event |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
|  **Feature**       | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes |Yes |
| Whiteboard | Yes | Yes |Yes |
| Recording | N/A |Yes | Yes |
| Files | Yes | Yes | Yes |
| Schedule a meeting | Yes | Yes | Yes |
|||||||

### Non-host team user

The non-host team user belongs to the organization but isn't a member of the hosting team's tenant. This user type pertains to meetings only. Read a comparison of external and guest access in [Communicate with users from other organization.](communicate-with-users-from-other-organizations#compare-external-and-guest-access.md).

| Meeting |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**       | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | No | No | No |
| Meeting Notes | No | No | No |
| Whiteboard | No | No |No |
| Recording | N/A | No | No |
| Files | No | No | No |
| Schedule a meeting | No | N/A | N/A |
|||||||

### Guest user and B2B

The guest user is invited to join the meeting by a member of the tenant. A B2B user is a business-to-business member who's invited to the meeting by a tenant member and typically attends as a guest user. Read more about guest users in [What the guest experience is like](guest-experience#comparison-of-team-member-and-guest-capabilities.md).

| Meeting |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes | Yes |
| Whiteboard | No | No |No |
| Recording | N/A |No | No |
| Files | Yes | Yes | Yes |
| Schedule a meeting | No | N/A | N/A |
|||||||

| Live event  | | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes | Yes |
| Whiteboard | No | No | No |
| Recording | N/A | No | No |
| Files | No | No | No |
| Schedule a meeting | No | No | No |
|||||||

### Anonymous user and B2C

The anonymous user doesn't have an organizational identity and isn't a member of the tenant. A business-to-customer (B2C) user is a member of an outside organization and typically attends as an anonymous user. Learn more about user types in [Security and Microsoft Teams](teams-security-guide#participant-types.md).

| Meeting  | | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | N/A | No | N/A |
| Meeting Notes | N/A | No | N/A |
| Whiteboard | N/A | No | N/A |
| Recording | N/A | No | N/A |
| Files | N/A | No | N/A |
| Schedule a meeting | N/A | N/A | N/A |
|||||||

| Live event|  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | No | Yes | No |
| Meeting Notes | N/A | No | N/A |
| Whiteboard | N/A | No | N/A |
| Recording | N/A | No | N/A |
| Files | N/A | No | N/A |
| Schedule a meeting | N/A | No | N/A |
|||||||

### External user

An external (federation) user has valid credentials with external partners and is treated as authenticated by Teams, but is still anonymous to the meeting organizer tenant. Read more about external users in [Communicate with users from other organizations](communicate-with-users-from-other-organizations#external-access.md).

| Meeting (Can be addded to a team as a guest only) ||
|-|-|-|
| **Feature** |||
| Chat (includes photos and stickers) | N/A |
| Meeting Notes | N/A |  
| Whiteboard | N/A |
| Recording | N/A |  
| Files | N/A |
| Schedule a meeting | N/A |
|||

| Live event |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
|  **Feature**         | Pre-meeting | In-meeting | Post-meeting |
| Chat (includes photos and stickers) | N/A | Yes | Yes |
| Meeting Notes | N/A | Yes | Yes |
| Whiteboard | N/A | No | No |
| Recording | N/A | N/A | No |
| Files | Yes | Yes | Yes |
| Schedule a meeting | N/A | No | N/A |
|||||||

## Related topics

[Security and Microsoft Teams](teams-security-guide.md)

[Guest access in Teams](guest-access.md)
