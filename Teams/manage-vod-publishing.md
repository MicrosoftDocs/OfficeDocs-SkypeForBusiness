---
title: Manage VOD publishing for webinars and town halls
ms.reviewer: sachung
ms.date: 11/3/2023
ms.author: wlibebe
author: wlibebe
ms.topic: article
manager: serdars
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

Video on demand (VOD) for Microsoft Teams allows webinar and town hall organizers to quickly publish and share recordings. When your users record webinars and town halls, the recordings are uploaded to OneDrive. Once the video is published, it’s copied from OneDrive into Azure Media Services (AMS) and made available to attendees. Once the organizer publishes a recording, all attendees automatically receive an email with a link to view the recording.

As an admin, you can control which types of town halls and webinars can have their recordings published.

For more information on publishing webinar and town halls for your end users, see [Manage webinar recordings in Microsoft Teams](https://prod.support.services.microsoft.com/office/manage-webinar-recordings-in-microsoft-teams-8cf1ba61-c9d8-4628-8b5d-0dcdb8503144) and [Manage town hall recordings in Microsoft Teams](https://prod.support.services.microsoft.com/office/manage-town-hall-recordings-in-microsoft-teams-88ac3af7-db67-4556-a202-b73a1d6c2e46).

## Manage VOD publishing permissions using PowerShell

You  must use PowerShell to manage VOD publishing permissions for webinars and town halls.

### Webinars

To manage VOD publishing permissions for webinars, use the **`-AllowedWebinarTypesForRecordingPublish`** parameter within the PowerShell [CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

The following table lists the values that you can set for webinar publishing permissions along with the corresponding behavior.

|Setting value| Behavior|
|---------|---------------|
|None| Recordings can’t be published for any webinar. |
|EveryoneInCompanyIncludingGuests| Only private webinar recordings can be published. Public webinar recordings can’t be published.|
|Everyone| **This is the default.** All webinar recordings can be published.|

>[!NOTE]
> Private webinars can't be viewed by guests.

To prevent any webinar recordings from being published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedWebinarTypesForRecordingPublish None
```

To only allow private webinar recordings to be published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedWebinarTypesForRecordingPublish EveryoneInCompanyIncludingGuests
```

### Town halls

To manage VOD publishing permissions for town halls, use the **`-AllowedTownhallTypesForRecordingPublish`** parameter within the PowerShell [CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy) cmdlet.

The following table lists the values that you can set for town hall publishing permissions along with the corresponding behavior.

|Setting value| Behavior|
|---------|---------------|
|None| Recordings can’t be published for any town hall. |
|InviteOnly| Town hall recordings can only be published if they're invite-only.|
|EveryoneInCompanyIncludingGuests| Only private and invite only town hall recordings can be published. Public town hall recordings can’t be published.|
|Everyone| **This is the default.** All town hall recordings can be published.|

For town hall recordings to only be published if they're invite-only, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedTownhallTypesForRecordingPublish InviteOnly
```

To prevent any town hall recordings from being published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedTownhallTypesForRecordingPublish None
```

To only allow private and invite only town hall recordings to be published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowedTownhallTypesForRecordingPublish EveryoneInCompanyIncludingGuests
```

## Related articles

- [Set up webinars](set-up-webinars.md)
- [Set up town halls](set-up-town-halls.md)
- [Set-CsTeamsEventsPolicy](/powershell/module/teams/set-csteamseventspolicy)
- [New-CsTeamsEventsPolicy](/powershell/module/teams/new-csteamseventspolicy)
- [Grant-CsTeamsEventsPolicy](/powershell/module/teams/grant-csteamseventspolicy)
- [Get-CsTeamsEventsPolicy](/powershell/module/teams/get-csteamseventspolicy)
- [Remove-CsTeamsEventsPolicy](/powershell/module/teams/remove-csteamseventspolicy)