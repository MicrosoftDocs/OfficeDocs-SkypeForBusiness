--- 
title: Manage who can present and request control in Teams meetings
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
ms.topic: article
ms.service: msteams
ms.reviewer: 
ms.date: 03/15/2021
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier2
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.participantandguests
description: Learn to manage who can present and take control in Teams meetings.
---

# Manage who can present and request control in Teams meetings

**APPLIES TO:** ✔️Meetings ✔️Webinars

You can use Teams meeting policies to control who can present in meetings and who can request control of the presentation while a meeting is underway.

The settings described in this article are part of Teams meeting policies.

To update a Teams meeting policy
1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy that you want to edit.
1. Scroll to the **Content sharing** section.
1. Change the desired settings (described below) and select **Save**.

## Manage who can present

This setting is a per-user policy that lets you change the default value of the **Who can present?** setting in **Meeting options** in the Teams client. The **Who can present** policy setting affects all meetings, including Meet Now meetings.

The **Who can present?** setting lets meeting organizers choose who can be presenters in a meeting. To learn more, see [Change participant settings for a Teams meeting](https://support.microsoft.com/office/53261366-dbd5-45f9-aae9-a70e6354f88e) and [Roles in a Teams meeting](https://support.microsoft.com/office/c16fa7d0-1666-4dde-8686-0a0bfe16e019).

To specify the default value of the **Who can present?** setting in Teams, set to one of the following settings in the **Who can present** policy:

- **Only organizers and co-organizers**: Only the meeting organizer can be a presenter and all meeting participants are designated as attendees. This parameter corresponds to the **Only organizers and co-organizers** setting in Teams.
- **People in my organization and guests**: Authenticated users in the organization, including guests, can be presenters. This setting corresponds to the **People in my organization and guests** setting in Teams.
- **Everyone**:  All meeting participants can be presenters. This is the default value. This setting corresponds to the **Everyone** setting in Teams.

Keep in mind that after you set the default value, meeting organizers can still change this setting in Teams and choose who can present in the meetings that they schedule.

## Participants can give or request control

This setting is a per-user policy. This setting controls whether the user can give control of the shared desktop or window to other meeting participants. To give control, hover over the top of the screen.

> [!NOTE]
> This setting also affects webinars.

If this setting is turned on for the user, the **Give Control** option is displayed in the top bar in a sharing session.

![Screenshot showing the Give Control option.](media/meeting-policies-give-control.png)

If the setting is turned off for the user, the **Give Control** option isn't available.

![Screenshot showing that the Give Control option is not available.](media/meeting-policies-give-control-not-available.png)

Let's look at the following example.

| User | Meeting policy | Allow participant to give or request control |
|---|---|---|
| Daniela | Global | On |
| Babek | Location1MeetingPolicy | Off |

Daniela can give control of the shared desktop or window to other participants in a meeting organized by Babek. However, Babek can't give control to other participants.

To use PowerShell to control who can give control or accept requests for control, use the AllowParticipantGiveRequestControl cmdlet.

> [!NOTE]
> To give and take control of shared content during sharing, both parties must be using the Teams desktop client. Control isn't supported when either party is running Teams in a browser. This is due to a technical limitation that we're planning to fix.

## External participants can give or request control

This setting is a per-user policy. Whether an organization has set this policy for a user doesn't control what external participants can do, regardless of what the meeting organizer has set. This parameter controls whether external participants can be given control or request control of the sharer's screen, depending on what the sharer has set within their organization's meeting policies.

> [!NOTE]
> This setting also affects webinars.

External participants in Teams meetings can be categorized as follows:  

- Anonymous participant
- Guests
- External access users

Whether external access users can give control to other external participants while sharing is controlled by the **External participants can give or request control** setting in their organization. This setting must be turned on in both organizations for an external participant to take control in Teams meetings hosted by people in your organization.

To use PowerShell to control whether external participants can give control or accept requests for control, use the AllowExternalParticipantGiveRequestControl cmdlet.

## Related topics

- [Teams policy reference - Meetings](settings-policies-reference.md)
- [Assign policies to your users in Teams](policy-assignment-overview.md)
- [Teams PowerShell overview](teams-powershell-overview.md)
