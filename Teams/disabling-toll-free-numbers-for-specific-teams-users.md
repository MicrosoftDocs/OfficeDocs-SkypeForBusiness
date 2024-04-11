---
title: "Disabling toll-free numbers for specific Teams users"
ms.author: jtremper
author: jacktremper
manager: pamgreen
ms.reviewer: oscarr
ms.date: 02/22/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
  - Tier1
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

By default, all users in your organization are enabled for using toll-free numbers, if available, participants can use those numbers to join their meetings. If this isn't the desired behavior for some users in your organization, you can restrict specific users from using those numbers in their meetings via a toll-free number enablement control.

When toll-free numbers are disabled for a given organizer:

- A toll-free number is no longer included in their meeting invites.
- Toll-free numbers are no longer listed on the "Find a local number" page that is referenced in their meeting invites.
- Participants can't join the meeting of the given organizer if they dial any toll-free number of the organization.
- Participants can continue joining meetings of the organizer using toll numbers.

## Disabling toll-free numbers for specific users

You can disable toll-free numbers for specific users by changing the setting for *AllowTollFreeDialIn* to **Off** within the *TeamsAudioConferencingPolicy* assigned to those users. Once turned off any new meetings created by such users don't include any Toll free numbers. [Audio Conferencing policy settings for toll and toll-free numbers](audio-conferencing-toll-free-numbers-policy.md) has more information.

> [!IMPORTANT]
> Old and previously scheduled recurring meetings may still show toll-free numbers and participants won't be able to join such meetings using a toll-free number. You can reschedule all old and recurring meetings for these users and remove toll-free numbers from them using MMS.

> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
