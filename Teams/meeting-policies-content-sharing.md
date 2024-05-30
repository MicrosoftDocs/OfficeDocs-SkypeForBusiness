---
title: Manage meeting policies for content sharing
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.topic: article
ms.service: msteams
ms.reviewer: kamila.korsec, mario.novoselec
ms.date: 5/30/2024
audience: admin
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - Tier2
  - m365initiative-meetings
appliesto: 
  - Microsoft Teams
f1.keywords:
- NOCSH
ms.custom: 
  - ms.teamsadmincenter.meetingpolicies.contentsharing
description: Learn to manage meeting policy settings in Teams for content sharing.
---

# Manage meeting policies for content sharing

**APPLIES TO:** ✔️Meetings ✔️Webinars ✔️Town halls

Content sharing settings control how users present a screen or app during a chat, meeting, webinar, or town hall. You can configure admin settings for screen sharing mode, PowerPoint sharing, whiteboard, and shared notes. (For information about how to manage who can present and who can request control, see [Manage who can present and request control in Teams meetings](meeting-who-present-request-control.md).)

For town halls, only presenters, organizers, and co-organizers can use shared notes and screen sharing.

Follow these steps to manage content sharing policies:

1. In the Teams admin center, expand **Meetings** and select **Meeting policies**.
1. Select the policy that you want to edit.
1. Scroll to the **Content sharing** section.
1. Select the settings you want to use (described in the following sections).
1. Select **Save**.

#### Use PowerShell to configure content sharing

You can also use the [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy) cmdlet to control the content sharing settings. Set the following parameters:

- ScreenSharingMode
- AllowPowerPointSharing
- AllowWhiteboard
- AllowCollaborativeAnnotations
- AllowDocumentCollaboration
- AllowSharedNotes

[Learn more about using the csTeamsMeetingPolicy cmdlet](/powershell/module/teams/set-csteamsmeetingpolicy).

## Screen sharing mode

This setting is a per-user policy. The setting controls whether a user can share a desktop and window in a Teams meeting.

|Setting value |Behavior  |
|---------|---------|
|**Entire screen**    | Full desktop sharing and application sharing are allowed in the meeting. |
|**Single application**   | Application sharing is allowed in the meeting. If your users are using Teams in a web browser and are assigned this value, this setting functions as **Not enabled**.  |
|**Not enabled**     |Screen sharing and application sharing turned off in the meeting.       |

## PowerPoint Live

This is a per-user policy. This setting controls whether the user can share PowerPoint slide decks in a meeting. External participants, including anonymous, guest, and external access users, inherit the policy of the meeting organizer.

Let's look at the following example.

|User |Meeting policy  |PowerPoint Live |
|---------|---------|---------|
|Daniela   | Global   | On       |
|Amanda   | Location1MeetingPolicy        | Off   |

Amanda can't share PowerPoint slide decks in meetings even if she's the meeting organizer. Daniela can share PowerPoint slide decks even if Amanda organizes the meeting. Amanda can view the PowerPoint slide decks shared by others in the meeting, even though she can't share PowerPoint slide decks.

## Whiteboard

Microsoft Whiteboard is a free-form, digital canvas where people, content, and ideas come together. Whiteboard integration in Microsoft Teams meetings is powered by the Whiteboard web app, which lets Teams meeting participants draw, sketch, and write together on a shared digital canvas.

Users can share a whiteboard to make it available to all participants in a Teams meeting. That same whiteboard is simultaneously available in all the Whiteboard applications on Windows 10, iOS, and the web app.

To turn the Whiteboard app on or off, see [Enable Microsoft Whiteboard for your organization](/microsoft-365/whiteboard/manage-whiteboard-access-organizations). Keep in mind that this setting enables or disables Whiteboard for your entire organization, and not just for Teams.

Whiteboards are created in the OneDrive of the person who starts the whiteboard. For more information, see [Manage data for Microsoft Whiteboard](/microsoft-365/whiteboard/manage-data-organizations).

The **Whiteboard** setting for Teams meetings is a per-user setting. This setting controls whether a user can share the Whiteboard in a meeting. External participants, including anonymous, guest, and external access users, inherit the meeting organizer's policy.

Let's look at the following example.

|User |Meeting policy  |Whiteboard|
|---------|---------|---------|
|Daniela   | Global   | On       |
|Amanda   | Location1MeetingPolicy        | Off   |

Amanda can't share the whiteboard in a meeting even if she's the meeting organizer. Daniela can share the whiteboard even if Amanda organizes a meeting.

To enable Whiteboard using PowerShell, set the **`-IsWBFluidEnabled`** parameter to $true from [Set-SPOTenant](/powershell/module/sharepoint-online/set-spotenant):

```powershell
Set-SPOTenant -IsWBFluidEnabled $true
```

For information for your end users about how to use Whiteboard, see [Use Whiteboard in Microsoft Teams](https://support.office.com/article/7a6e7218-e9dc-4ccc-89aa-b1a0bb9c31ee).

### Whiteboard on Surface Hub

Before trying to use Microsoft Whiteboard, make sure that the Whiteboard app is installed on your Surface Hub device. If Whiteboard isn't installed, on the Surface Hub device, go to the Microsoft Store app, and get [Microsoft Whiteboard](https://www.microsoft.com/p/microsoft-whiteboard/9mspc6mp8fm4?activetab=pivot:overviewtab). For more information, see [Enable Microsoft Whiteboard on Surface Hub](https://support.office.com/article/enable-microsoft-whiteboard-on-surface-hub-b5df4539-f735-42ff-b22a-0f5e21be7627).

### Collaborative annotations

To enable **Collaborative annotations**, a per-user policy, you must first enable **Whiteboard**. When you **Collaborative annotations** enable for users with an assigned policy, these users can use annotations, a feature that allows participants to collaborate while sharing their screen in a Teams meeting. If **Whiteboard** or **Collaborative annotations** are disabled, users don't have access to annotations.

To enable **Collaborative Annotations** using PowerShell, set the **`-AllowCollaborativeAnnotations`** parameter to $true from [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy):

```powershell
Set-CSTeamsMeetingPolicy -AllowCollaborativeAnnotations $true
```

## Live share

Users can edit a document from within the Teams meeting window. This allows real time coauthoring in the context of a meeting.

To enable **Collaborative annotations** using PowerShell, set the **`-AllowDocumentCollaboration`** parameter to $true from [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy):

```powershell
Set-CSTeamsMeetingPolicy -AllowDocumentCollaboration $true
```

## Shared notes

This setting is a per-user policy. This setting controls whether a user can create and share notes in a meeting. External participants, including anonymous, guests, and external access, inherit the policy of the meeting organizer. The **Meeting Notes** tab is currently only supported in meetings that have fewer than 20 participants.

Let's look at the following example.

|User |Meeting policy  |Shared notes |
|---------|---------|---------|
|Daniela   | Global   | On       |
|Amanda   | Location1MeetingPolicy | Off |

Daniela can take notes in Amanda's meetings and Amanda can't take notes in any meetings.

To enable **Shared notes** using PowerShell, set the **`-AllowSharedNotes`** parameter to $true from [Set-CsTeamsMeetingPolicy](/powershell/module/teams/set-csteamsmeetingpolicy):

```powershell
Set-CsTeamsMeetingPolicy -AllowSharedNotes $true
```

## Related articles

- [Manage who can present and request control in Teams meetings and webinars](meeting-who-present-request-control.md)
- [Teams policy reference - Content sharing](settings-policies-reference.md#content-sharing)

- [Teams PowerShell overview](teams-powershell-overview.md)

- [Assign policies to your users in Teams](policy-assignment-overview.md)
