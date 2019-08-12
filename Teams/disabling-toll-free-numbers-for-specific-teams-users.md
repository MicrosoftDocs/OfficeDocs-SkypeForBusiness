---
title: "Disabling toll-free numbers for specific Teams users"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Administrators can control how organizers can use toll-free numbers for their meetings." 
---

# Disabling toll-free numbers for specific Teams users

If your organization has toll-free numbers in its Microsoft Audio Conferencing Bridge, you can allow or prevent their usage in the meetings of specific organizers.  

By default, all users in your organization are enabled for using toll-free numbers, meaning that those numbers, if available, can be used by participants to join their meetings. If this is not the desired behavior for some users in your organization, you can restrict specific users from using those numbers in their meetings via a toll-free number enablement control. 

When toll-free numbers are disabled for a given organizer: 
 - A toll-free number will no longer be included in his or her meeting invites. 
 - Toll-free numbers will no longer be listed on the "Find a local number" page that is referenced in his or her meeting invites. 
 - Participants won't be able to join the meeting of the given organizer if they dial any toll-free number of the organization. 
 - All meetings of the organizer will be automatically rescheduled, and the toll-free number will be removed from them.  

    > [!IMPORTANT]
    > This will resend all of the email invites of the organizer to all the participants of those meetings. 

 - Participants can continue joining meetings of the organizer using toll numbers. 

## Disabling toll-free numbers for specific users 

From the **Microsoft Teams admin center**:

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. Next to **Audio Conferencing**, click **Edit**.

3. Set **Include toll-free numbers in meeting requests from this user** to **Off**. 

4. Click **Save.** 

 
> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
 
**Using PowerShell**  

See the [Microsoft Teams PowerShell reference](https://docs.microsoft.com/powershell/module/teams/?view=teams-ps) for more information.
