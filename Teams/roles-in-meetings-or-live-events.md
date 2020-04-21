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

Microsoft Teams meetings and live events support many user types. Users can access various meeting and event features based on their roles inside or outside of an organization. 

## Presenters and organizers

Presenters and organizers include the following:

- Presenters from my organization
- Presenters from other organizations (Live Events restriction) - covers B2B and anonymous/external

Presenters and organizers have access to everything in a meeting or live event.

## Attendees

The types of users who can be attendees are described as the following:

- In-tenant user - belongs to the organization and has credentials for the tenant.
- Anonymous user - does not have an organizational identity and isn't a member of the tenant.
- Guest user - is invited to join the meeting by a member of the tenant.
- B2B user - is a business-to-business member who's invited to the meeting by a tenant member. 
- External (federation) user - has valid credentials with external partners and is treated as authenticated by Teams, but is still Anonymous to the meeting organizer tenant.

Attendees are defined as the following:

- Attendees from my organization invited to the meeting (in-tenant user)
- Attendees from my organization not invited to the meeting [for channel meetings]
- Attendees from my organization in the team/channel, including B2B guests/B2B users in the team/channel
- Attendees from my organization not in the team/channel
- B2B guests in my tenant, B2B users, and elevated guests in my tenant
- External signed-in users
- Anonymous users

During a channel meeting, attendees have different capabilities, depending on what kind of attendee they are.

- Attendee from my organization: Can do everything attendees are allowed to do. To learn more, read [Roles in a Teams meeting](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019?ui=en-us&amp;amp;rs=en-us&amp;amp;).
- Attendee who's a member of my organization but not a member of my team:
  - Can chat, edit meeting notes, and collaborate on shared files, but can't schedule meetings, use the whiteboard, or record meetings.
- Attendee from an external (federation) organization:
  - Can't participate in meetings at all. External users can only chat. If you want someone from an external domain to join a meeting, add them as a guest.
- Attendee who's an anonymous/B2C user:  
  - Can attend a meeting but can't participate in chat, meeting notes, use the whiteboard, record meetings, or collaborate on files.

  During a live meeting, attendees have different capabilities, depending on what kind of attendee they are.

- Attendee from my organization: Can do everything attendees are allowed to do. To learn more, read [Roles in a Teams meeting](https://support.microsoft.com/en-us/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019?ui=en-us&amp;amp;rs=en-us&amp;amp;).
- Attendee who's a member of my organization but not a member of my team:
  - Can chat, edit meeting notes, and collaborate on shared files, but can't schedule meetings, use the whiteboard, or record meetings.
- Attendee from an external (federation) organization:
  - Can access only chat and files.
- Attendee who's an anonymous/B2C user:  
  - Can can only access chat.

  Chat meeting after a meeting has ended

  An in-tenant user can access the chat, meeting notes, whiteboard, recording, and files. A guest user can access the chat. All other users have no access.

## Related topics

[Security and Microsoft Teams](teams-security-guide.md)

[Guest access in Teams](guest-access.md)
