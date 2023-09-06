---
title: Manage VOD publishing for webinars and town halls
ms.reviewer: sachung
ms.date: 09/06/2023
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

Video on demand (VOD) for Microsoft Teams allows webinar and town hall organizers to quickly publish and share recordings. When your users record webinars and town halls, the recordings are uploaded to OneDrive. Once the video is published, it’s copied from OneDrive into Azure Media Services (AMS) and made available to attendees through the event portal page for webinars and the meeting chat and details page for town halls.

As an admin, you can control which types of town halls and webinars can have their recordings published.

## Manage VOD publishing permissions using PowerShell

You  must use PowerShell to manage VOD publishing permissions for webinars and town halls.

The following table lists the values that you can set for webinar and town hall publishing permissions along with the corresponding behavior.

|Setting value| Behavior|
|---------|---------------|
|None| Recordings can’t be published for any webinar or town hall. |
|InviteOnly| Webinar and town hall recordings can only be published if they are invite-only.|
|EveryoneInCompanyIncludingGuests| Only private and invite only webinar recordings can be published. Public webinar recordings can’t be published.|
|Everyone| **This is the default.** All webinar and town hall recordings can be published.|

## Webinars

To manage VOD publishing permissions for webinars, use the – **`-AllowWebinarRecordingPublishing`** parameter within the PowerShell CsTeamsEventsPolicy cmdlet.

For webinar recordings to only be published if they are invite-only, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinarRecordingPublishing InviteOnly
```

To prevent any webinar recordings from being published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinarRecordingPublishing None
```

To only allow private and invite only webinar recordings to be published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowWebinarRecordingPublishing EveryoneInCompanyIncludingGuests
```

## Town halls

To manage VOD publishing permissions for town halls, use the – **`-AllowTownhallRecordingPublishing`** parameter within the PowerShell CsTeamsEventsPolicy cmdlet.

For town hall recordings to only be published if they are invite-only, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhallRecordingPublishing InviteOnly
```

To prevent any town hall recordings from being published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhallRecordingPublishing None
```

To only allow private and invite only town hall recordings to be published, use the following script:

```powershell
Set-CsTeamsEventsPolicy -Identity <policy name> -AllowTownhallRecordingPublishing EveryoneInCompanyIncludingGuests
```