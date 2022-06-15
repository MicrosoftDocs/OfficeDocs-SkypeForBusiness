---
title: Manage meeting policies for content sharing
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: sonua, shalenc
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
appliesto: 
  - Microsoft Teams
f1.keywords:
- CSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.contentsharing
  - seo-marvel-apr2020
description: Learn to manage meeting policy settings in Teams for content sharing.
---


# Meeting policy settings - Content sharing

<a name="bkcontentsharing"> </a>

This article describes the following meeting policy settings related to content sharing:

- [Screen sharing mode](#screen-sharing-mode)
- [Allow a participant to give or request control](#allow-a-participant-to-give-or-request-control)
- [Allow an external participant to give or request control](#allow-an-external-participant-to-give-or-request-control)
- [PowerPoint Live](#powerpoint-live)
- [Whiteboard](#whiteboard)
- [Shared notes](#shared-notes)

## Screen sharing mode

This setting is a combination of a per-organizer and per-user policies. This setting controls whether desktop and window sharing is allowed in the user's meeting. Meeting participants who don't have any policies assigned (for example, anonymous, guest, B2B, and federated participants) inherit the policy of the meeting organizer.

|Setting value |Behavior  |
|---------|---------|
|**Entire screen**    | Full desktop sharing and application sharing are allowed in the meeting |
|**Single application**   | Application sharing is allowed in the meeting        |
|**Disabled**     |Screen sharing and application sharing turned off in the meeting.       |

Let's look at the following example.

|User |Meeting policy |Screen sharing mode |
|---------|---------|---------|
|Daniela  | Global   | Entire screen |
|Amanda   | Location1MeetingPolicy  | Disabled |

Meetings hosted by Daniela allow meeting participants to share their entire screen or a specific application. If Amanda joins Daniela's meeting, Amanda can't share her screen or a specific application as her policy setting is disabled. In meetings hosted by Amanda, no one is allowed to share their screen or a single application, regardless of the screen sharing mode policy assigned to them.  Consequently, Daniela can't share her screen or a single application in Amanda's meetings.  

Currently, users can't play video or share their screen in a Teams meeting if they're using Google Chrome.

## Allow a participant to give or request control

This setting is a per-user policy. This setting controls whether the user can give control of the shared desktop or window to other meeting participants. To give control, hover over the top of the screen.

If this setting is turned on for the user, the **Give Control** option is displayed in the top bar in a sharing session.

![Screenshot showing the Give Control option.](media/meeting-policies-give-control.png)

If the setting is turned off for the user, the **Give Control** option isn't available.

![Screenshot showing that the Give Control option is not available.](media/meeting-policies-give-control-not-available.png)

Let's look at the following example.

|User |Meeting policy  |Allow participant to give or request control |
|---------|---------|---------|
|Daniela   | Global   | On       |
|Babek    | Location1MeetingPolicy        | Off   |

Daniela can give control of the shared desktop or window to other participants in a meeting organized by Babek. However, Babek can't give control to other participants.

To use PowerShell to control who can give control or accept requests for control, use the AllowParticipantGiveRequestControl cmdlet.

> [!NOTE]
> To give and take control of shared content during sharing, both parties must be using the Teams desktop client. Control isn't supported when either party is running Teams in a browser. This is due to a technical limitation that we're planning to fix.

## Allow an external participant to give or request control

This setting is a per-user policy. Whether an organization has set this policy for a user doesn't control what external participants can do, regardless of what the meeting organizer has set. This parameter controls whether external participants can be given control or request control of the sharer's screen, depending on what the sharer has set within their organization's meeting policies. External participants in Teams meetings can be categorized as follows:  

- Anonymous user
- Guest users  
- B2B user
- Federated user  

Whether federated users can give control to external users while sharing is controlled by the **Allow an external participant to give or request control** setting in their organization.

To use PowerShell to control whether external participants can give control or accept requests for control, use the AllowExternalParticipantGiveRequestControl cmdlet.

### PowerPoint Live

This is a per-user policy. This setting controls whether the user can share PowerPoint slide decks in a meeting. External users, including anonymous, guest, and federated users, inherit the policy of the meeting organizer.

Let's look at the following example.

|User |Meeting policy  |PowerPoint Live |
|---------|---------|---------|
|Daniela   | Global   | On       |
|Amanda   | Location1MeetingPolicy        | Off   |

Amanda can't share PowerPoint slide decks in meetings even if she's the meeting organizer. Daniela can share PowerPoint slide decks even if the meeting is organized by Amanda. Amanda can view the PowerPoint slide decks shared by others in the meeting, even though she can't share PowerPoint slide decks.

## Whiteboard

This setting is a per-user policy. This setting controls whether a user can share the whiteboard in a meeting. External users, including anonymous, B2B, and federated users, inherit the policy of the meeting organizer.

Let's look at the following example.

|User |Meeting policy  |Whiteboard|
|---------|---------|---------|
|Daniela   | Global   | On       |
|Amanda   | Location1MeetingPolicy        | Off   |

Amanda can't share the whiteboard in a meeting even if she's the meeting organizer. Daniela can share the whiteboard even if a meeting is organized by Amanda.

When whiteboard is enabled, your users will have the option to use [annotation](/office/use-annotation-while-sharing-your-screen-in-teams), a feature that allows participants to  collaborate while sharing their screen in a Teams meeting. If whiteboard is disabled, users will not have access to annotation.

## Shared notes

This setting is a per-user policy. This setting controls whether a user can create and share notes in a meeting. External users, including anonymous, B2B, and federated users, inherit the policy of the meeting organizer. The **Meeting Notes** tab is currently only supported in meetings that have fewer than 20 participants.

Let's look at the following example.

|User |Meeting policy  |Shared notes |
|---------|---------|---------|
|Daniela   | Global   | On       |
|Amanda   | Location1MeetingPolicy | Off |

Daniela can take notes in Amanda's meetings and Amanda can't take notes in any meetings.




## Related topics

- [Teams PowerShell overview](teams-powershell-overview.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Remove the RestrictedAnonymousAccess Teams meeting policy from users](meeting-policies-restricted-anonymous-access.md)
