---
title: "Assign, change places for emergency locations for users"
author: cichur
ms.author: v-cichur
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
description: In this article, you will learn how to assign or change the place for an emergency location for users in your organization.
ms.custom: seo-marvel-apr2020
---

# Assign or change the place for an emergency location for a user

Each active phone number must have an associated emergency location when you assign the phone number to a user. (You associate the address when you get a phone number in Office 365 or when you transfer a phone number.) When you associate the number with an emergency location, you can also add a place to provide a more exact location within a physical location. A place can be the floor, building wing, or office number where the user is located. You can have an unlimited number of places for a given emergency location, and you can change the place if the user moves to a different office or building. For example, if the user moves from floor 34 to floor 35.
  
To learn how to get Calling Plans and how much they cost, see [Teams add-on licensing](teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
  
You can assign or change the place for an emergency location for a user in the Microsoft Teams admin center or by using PowerShell.

## Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Phone numbers**.

2. On the **Phone numbers** page, click the **Numbers** tab, select a user number in the list, and then click **Edit**.

3. On the **Edit** pane, under **Emergency location**, do one of the following:

    - To assign a place, search for the location or place, and then select the place in the search results.

    - To change the place that's already assigned to the user, click **X** to remove the existing location and place, search for and then select the place you want to assign.

4. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this is on.

5. Click **Apply**.

## Using PowerShell

See [Set-CsOnlineLisLocation](/powershell/module/skype/set-csonlinelislocation).
    
## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Add, change, or remove a place for an emergency location in your organization](add-change-remove-emergency-place-organization.md)
- [Assign or change an emergency location for a user](assign-change-emergency-location-user.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)