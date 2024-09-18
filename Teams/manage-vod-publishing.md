---
title: Manage VOD publishing for webinars and town halls
ms.reviewer: sachung
ms.date: 9/18/2024
ms.author: wlibebe
author: wlibebe
ms.topic: article
manager: pamgreen
ms.service: msteams
ms.subservice: meetings
ms.custom: intro-overview
audience: admin
f1.keywords:
- NOCSH
ms.collection: 
- M365-collaboration
- remotework
- m365initiative-meetings
- m365initiative-meetings-enabler
- enabler-strategic
- highpri
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
description: Learn how to manage video on demand (VOD) publishing for webinars and town halls in Microsoft Teams.
---

# Manage VOD publishing for webinars and town halls

**APPLIES TO:** ✖️Meetings ✔️Webinars ✔️Town halls

Video on demand (VOD) for Microsoft Teams events allows webinar and town hall organizers to quickly publish and share event recordings. When organizers record these events, the recordings are uploaded to [OneDrive](tmr-meeting-recording-change.md#meetings-and-events). Once published, all attendees automatically receive an email with a link to view the recording. As an admin, you can manage which types of town halls and webinars organizers can publish recordings for.

For more information on publishing webinar and town halls for your users, see [Manage webinar recordings in Microsoft Teams](https://prod.support.services.microsoft.com/office/manage-webinar-recordings-in-microsoft-teams-8cf1ba61-c9d8-4628-8b5d-0dcdb8503144) and [Manage town hall recordings in Microsoft Teams](https://prod.support.services.microsoft.com/office/manage-town-hall-recordings-in-microsoft-teams-88ac3af7-db67-4556-a202-b73a1d6c2e46).

## Webinars

You can use the Teams admin center or PowerShell to manage VOD publishing permissions for webinars.

> [!NOTE]
> Guests can't view private webinar recordings.
> [!NOTE]
> The invite only option isn't supported for webinars.

The following table lists the values that you can set for webinar publishing permissions along with the corresponding behaviors:

|Teams admin center value |PowerShell value| Behavior|
|---------|---------|---------------|
|Not allowed| None| Organizers with this policy can't publish any webinar recordings. |
|Your organization| EveryoneInCompanyIncludingGuests |Organizers with this policy can only publish recordings for private webinars. These organizers can't publish any recordings for public webinars.|
|Public| Everyone| **This is the default.** Organizers with this policy can publish any webinar recordings.|

### Manage webinar VOD publishing permissions using the Teams admin center

You can use the Teams admin center To manage VOD publishing permissions for webinars in the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Choose one of the following values for **Allowed webinar types for recordings**:

    - Not allowed
    - Your organization
    - Public

6. Select Save.

## Manage webinar VOD publishing permissions using PowerShell

To manage VOD publishing permissions for webinars through PowerShell, use the **`-AllowedWebinarTypesForRecordingPublish`** parameter within the [CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

To prevent organizers from publishing any webinar recordings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedWebinarTypesForRecordingPublish None
```

To only allow organizers to publish private webinar recordings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedWebinarTypesForRecordingPublish EveryoneInCompanyIncludingGuests
```

## Town halls

You can use the Teams admin center or PowerShell to manage VOD publishing permissions for town halls.

The following table lists the values that you can set for town hall publishing permissions along with the corresponding behaviors:

|Teams admin center value |PowerShell value| Behavior|
|---------|---------|---------------|
|Not allowed| None|Organizers with this policy can't publish any town hall recordings. |
|Invite only| InviteOnly|Organizers with this policy can only publish recordings for invite-only town halls. These organizers can't publish any recordings for public town halls.|
|Your organization| EveryoneInCompanyIncludingGuests|Organizers with this policy can only publish recordings for private and invite-only town halls. These organizers can't publish any recordings for public town halls.|
|Public| Everyone|**This is the default.** Organizers with this policy can publish any town hall recordings.|

### Manage town hall VOD publishing permissions using the Teams admin center

You can use the Teams admin center To manage VOD publishing permissions for webinars in the Teams admin center, use the following steps:

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Choose one of the following values for **Allowed town hall types for recordings**:

    - Not allowed
    - Invite only
    - Your organization
    - Public

6. Select Save.

## Manage town hall VOD publishing permissions using PowerShell

To manage VOD publishing permissions for town halls, use the **`-AllowedTownhallTypesForRecordingPublish`** parameter within the PowerShell [CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

To only allow organizers to publish invite-only town hall recordings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedTownhallTypesForRecordingPublish InviteOnly
```

To prevent organizers from publishing any town hall recordings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedTownhallTypesForRecordingPublish None
```

To only allow organizers to publish private and invite-only town hall recordings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedTownhallTypesForRecordingPublish EveryoneInCompanyIncludingGuests
```

## Related articles

- [Teams meeting recording storage and permissions in OneDrive and SharePoint](tmr-meeting-recording-change.md#meetings-and-events)
- [Issues that affect Teams webinars](/microsoftteams/troubleshoot/meetings/issues-with-webinars)
- [Plan for webinars](plan-webinars.md)
- [Plan for town halls](plan-town-halls.md)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
