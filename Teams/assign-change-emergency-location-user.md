---
title: Assign or change an emergency location for a user
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: jastark, roykuntz
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
- M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1.keywords:
- NOCSH
description: In this article, you will learn about how to assign or change an emergency location for users in your organization.
ms.custom: seo-marvel-apr2020 
---

# Assign or change an emergency location for a user

When you're setting up Calling Plans, you need to assign an emergency location to each phone number or user. In European countries, the emergency location is associated with the phone number when you get it from Office 365 or when you transfer a phone number over to Office 365. In the United States, the emergency location is associated with the phone number when it's assigned to the user. The emergency address can be changed if the user that it's assigned to moves to a new location. For more about emergency addresses and locations, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).
  
To learn how to get a Calling Plan and how much they cost, see [Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

You can assign or change an emergency location for a user in the Microsoft Teams admin center or by using PowerShell.

## Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Phone numbers**.

2. On the **Phone numbers** page, select a user number in the list, and then click **Edit**.

3. On the **Edit** pane, under **Emergency location**, do one of the following:

   - To assign an emergency location, search for, and select an emergency location.

   - To change the emergency location that's already assigned to the user, click **X** to remove the existing location, and then search for and select the location you want to assign.

4. Click **Save**.

## Using PowerShell

See [Set-CsOnlineVoiceUser](https://docs.microsoft.com/powershell/module/skype/set-csonlinevoiceuser). 

    
## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Add, change, or remove a place for an emergency location in your organization](add-change-remove-emergency-place-organization.md)
- [Assign or change a place for an emergency location for a user](assign-change-emergency-place-user.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](/microsoftteams/emergency-calling-terms-and-conditions)
- [Teams PowerShell overview](teams-powershell-overview.md)
