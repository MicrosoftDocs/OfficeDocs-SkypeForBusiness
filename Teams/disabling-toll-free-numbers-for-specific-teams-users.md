---
title: "Disabling toll-free numbers for specific Teams users"
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: oscarr
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: skype-for-business-online
ms.collection: 
- Adm_Skype4B_Online
- Strat_SB_PSTN
ms.audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Priority
f1keywords: None
ms.custom:
- Audio Conferencing
description: "Administrators can control how organizers can use toll-free numbers for their meetings." 
---

# Disabling toll-free numbers for specific Teams users

> [!Note]
> If you are looking for information on disabling tool-free numbers for Skype for Business users, see  [Disabling toll-free numbers for specific Skype for Business users](https://docs.microsoft.com/en-us/SkypeForBusiness/audio-conferencing-in-office-365/disabling-toll-free-numbers-for-specific-users).

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

1. In the left navigation, click **Users**, and then select the user from the list of available users.

2. At the top of the page, click **Edit**.

3. Click the menu next to **Conference Bridges**, and then click **Edit** in the drop-down list.

4. In the **Conference bridge provider** pane, turn off **Allow using toll-free numbers in the Conferencing bridge of your organization to join the meetings of this user**. 

5. Click **Apply.** 

 
> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]
 
**Using PowerShell**  

You can use the AllowTollFreeDialIn parameter of the Set-CsOnlineDialInConferencingUser cmdlet to enable or disable this control. For example: 

 - Set-CsOnlineDialInConferencingUser user@contoso.com – AllowTollFreeDialIn $false
