---
title: Manage VOD publishing for webinars and town halls
ms.reviewer: sachung
ms.date: 12/4/2023
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

Video on demand (VOD) for Microsoft Teams allows webinar and town hall organizers to quickly publish and share event recordings. When your organizers record webinars and town halls, the recordings are uploaded to OneDrive. Once the recording is published, it’s copied from OneDrive into Azure Media Services (AMS) and made available to attendees. Once the organizer publishes a recording, all attendees automatically receive an email with a link to view the recording.

As an admin, you can manage which types of town halls and webinars organizers can publish recordings for.

For more information on publishing webinar and town halls for your end users, see [Manage webinar recordings in Microsoft Teams](https://prod.support.services.microsoft.com/office/manage-webinar-recordings-in-microsoft-teams-8cf1ba61-c9d8-4628-8b5d-0dcdb8503144) and [Manage town hall recordings in Microsoft Teams](https://prod.support.services.microsoft.com/office/manage-town-hall-recordings-in-microsoft-teams-88ac3af7-db67-4556-a202-b73a1d6c2e46).

## Manage VOD publishing permissions using the Teams admin center

You can use the Teams admin center to manage VOD publishing permissions for webinars and town halls.

1. Open the Teams admin center.
2. Select **Meetings** from the navigation pane.
3. Under **Meetings**, select **Events Policies**.
4. Either select an existing policy or create a new one.
5. Choose one of the following values for **Allowed webinar types for recordings** and **Allowed town hall types for recordings**:

    - Not allowed
    - Invite only
    - Your organization

6. Select Save.

## Manage VOD publishing permissions using PowerShell

You can use PowerShell to manage VOD publishing permissions for webinars and town halls.

### Webinars

To manage VOD publishing permissions for webinars, use the **`-AllowedWebinarTypesForRecordingPublish`** parameter within the PowerShell [CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

The following table lists the values that you can set for webinar publishing permissions along with the corresponding behaviors.

|Setting value| Behavior|
|---------|---------------|
|None| Organizers with this policy can't publish any webinar recordings. |
|EveryoneInCompanyIncludingGuests| Organizers with this policy can only publish recordings for private webinars. These organizers can't publish any recordings for public webinars.|
|Everyone| **This is the default.** Organizers with this policy can publish any webinar recordings.|

> [!NOTE]
> Guests can't view private webinar recordings.

To prevent organizers from publishing any webinar recordings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedWebinarTypesForRecordingPublish None
```

To only allow organizers to publish private webinar recordings, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedWebinarTypesForRecordingPublish EveryoneInCompanyIncludingGuests
```

### Town halls

To manage VOD publishing permissions for town halls, use the **`-AllowedTownhallTypesForRecordingPublish`** parameter within the PowerShell [CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

The following table lists the values that you can set for town hall publishing permissions along with the corresponding behaviors.

|Setting value| Behavior|
|---------|---------------|
|None| Organizers with this policy can't publish any town hall recordings. |
|InviteOnly| Organizers with this policy can only publish recordings for invite-only town halls. These organizers can't publish any recordings for public town halls.|
|EveryoneInCompanyIncludingGuests| Organizers with this policy can only publish recordings for private and invite-only town halls. These organizers can't publish any recordings for public town halls.|
|Everyone| **This is the default.** Organizers with this policy can publish any town hall recordings.|

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

- [Issues that affect Teams webinars](/microsoftteams/troubleshoot/meetings/issues-with-webinars)
- [Plan for webinars](plan-webinars.md)
- [Plan for town halls](plan-town-halls.md)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)
