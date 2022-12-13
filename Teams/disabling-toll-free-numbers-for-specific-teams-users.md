---
title: "Disabling toll-free numbers for specific Teams users"
ms.author: heidip
author: MicrosoftHeidi
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - M365-collaboration
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: Learn how to control how organizers can use toll-free numbers for their Audio Conferencing Bridge meetings.
---

# Disabling toll-free numbers for specific Teams users

If your organization has toll-free numbers in its Microsoft Audio Conferencing Bridge, you can allow or prevent their usage in the meetings of specific organizers.  

By default, all users in your organization are enabled for using toll-free numbers, meaning that those numbers, if available, can be used by participants to join their meetings. If this is not the desired behavior for some users in your organization, you can restrict specific users from using those numbers in their meetings via a toll-free number enablement control.

When toll-free numbers are disabled for a given organizer:

- A toll-free number will no longer be included in his or her meeting invites.
- Toll-free numbers will no longer be listed on the "Find a local number" page that is referenced in his or her meeting invites.
- Participants won't be able to join the meeting of the given organizer if they dial any toll-free number of the organization.
- Participants can continue joining meetings of the organizer using toll numbers.

## Disabling toll-free numbers for specific users

You can disable toll-free numbers for specific users by changing the setting for *AllowTollFreeDialIn* to **Off** within the *TeamsAudioConferencingPolicy* assigned to those users. Once turned off any new meetings created by such users will not include any Toll free numbers. [Audio Conferencing policy settings for toll and toll-free numbers](audio-conferencing-toll-free-numbers-policy.md) has more information.

> [!IMPORTANT]
> Old and previously scheduled recurring meetings may still show toll-free numbers and participants won't be able to join such meetings using a toll-free number. You can reschedule all old and recurring meetings for these users and remove toll-free numbers from them using MMS.

> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
