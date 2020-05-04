---
title:  Presenter and attendee capabilities in a Teams live event
author: cichur
ms.author: v-cichur
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
description: Learn about the Presenter and attendee capabilities a Teams live event.
appliesto: 
- Microsoft Teams
localization_priority: Priority
---
Presenter and attendee capabilities in a Teams live event
======================================================

Microsoft Teams live events support many attendee types. Attendees can access various live event features based on their roles inside or outside of an organization.

The available meeting features are:

- Chat (includes photos and stickers)
- Meeting Notes
- Whiteboard
- Recording
- Files
- Schedule a meeting (for meetings only)

This article describes those attendee capabilities and what access they have to live event features.

## Presenters and organizers

Presenters and organizers include the following:

- Presenters from my organization
- Presenters from other organizations (Live Events restriction) - this includes anonymous and external attendees. Presenters are designated by the organizer and require a personal invite from the organizer.

Presenters and organizers have access to every feature in a meeting or live event.

## Attendees

There are several types of live event attendees.

### In-tenant attendee

The in-tenant attendee belongs to the organization and has credentials for the tenant. Learn more about this attendee in [Security and Microsoft Teams](teams-security-guide.md#participant-types).

| Live event |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
|  **Feature**       | Pre-meeting | In-meeting | Post-meeting |
| Chat | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes |Yes |
| Whiteboard | Yes | Yes |Yes |
| Recording | N/A |Yes | Yes |
| Files | Yes | Yes | Yes |
|||||||

|Meeting  |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes |Yes |
| Whiteboard | Yes | Yes |Yes |
| Recording | N/A |Yes | Yes |
| Files | Yes | Yes | Yes |
| Schedule a meeting | Yes | N/A | N/A |
|||||||

### Guest attendee

A guest attendee is someone from another organization who has been invited to access Teams or other resources in your organization's tenant, based on the Azure Active Directory B2B platform. Guest users can be invited to join regular meetings and channel meetings. Read more about a guest attendee in [What the guest experience is like](guest-experience.md#comparison-of-team-member-and-guest-capabilities).

| Live event  | | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes | Yes |
| Whiteboard | No | No | No |
| Recording | N/A | No | No |
| Files | No | No | No |
|||||||

| Meeting |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat | Yes | Yes | Yes |
| Meeting Notes | Yes | Yes | Yes |
| Whiteboard | No | No |No |
| Recording | N/A |No | No |
| Files | Yes | Yes | Yes |
| Schedule a meeting | No | N/A | N/A |
|||||||

### External (federated) attendee

An external attendee is someone using Teams in another organization who has been invited to join a meeting, but does not otherwise have access to other shared resources from your organization. External user participants appear in the meeting roster with the same identity name as they have in their own organization. Read more about an external attendee in [Communicate with users from other organizations](communicate-with-users-from-other-organizations.md#external-access).

| Live event |  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
|  **Feature**         | Pre-meeting | In-meeting | Post-meeting |
| Chat | No| Yes | Yes |
| Meeting Notes | No | No | No |
| Whiteboard | No| No | No |
| Recording | N/A | No | No |
| Files | Yes | Yes | Yes |
|||||||

| Meeting (Can be added to a team as a guest only) ||
|-|-|-|
| **Feature** |||
| Chat | N/A |
| Meeting Notes | N/A |  
| Whiteboard | N/A |
| Recording | N/A |  
| Files | N/A |
| Schedule a meeting | N/A |
|||

### Anonymous attendee

The anonymous attendee is like an external user, but their identity is not projected into the meeting. At join time, they manually enter a nickname. Learn more about an anonymous attendee in [Security and Microsoft Teams](teams-security-guide.md#participant-types).

| Live event|  | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat | No | Yes | No |
| Meeting Notes | N/A | No | N/A |
| Whiteboard | N/A | No | N/A |
| Recording | N/A | No | N/A |
| Files | N/A | No | N/A |
|||||||

| Meeting  | | |||
|---------|----------------|----------------|---------------------|------------|--------------|
| **Feature**        | Pre-meeting | In-meeting | Post-meeting |
| Chat | N/A | No | N/A |
| Meeting Notes | N/A | No | N/A |
| Whiteboard | N/A | No | N/A |
| Recording | N/A | No | N/A |
| Files | N/A | No | N/A |
| Schedule a meeting | N/A | N/A | N/A |
|||||||

## Related topics

[Security and Microsoft Teams](teams-security-guide.md)

[Guest access in Teams](guest-access.md)
