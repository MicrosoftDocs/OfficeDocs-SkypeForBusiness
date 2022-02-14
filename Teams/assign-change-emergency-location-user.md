---
title: Assign or change an emergency location for a user
author: CarolynRowe
ms.author: crowe
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
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: In this article, you will learn about how to assign or change an emergency location for users in your organization.
ms.custom: seo-marvel-apr2020 
---

# Assign or change an emergency location for a user

Regardless of the [PSTN connectivity option](pstn-connectivity.md) you choose&mdash;Microsoft Calling Plans, Operator Connect, or Direct Routing&mdash;an emergency location needs to be assigned to each phone number or user.

Depending on your PSTN connectivity option, however, how you manage and assign emergency locations for a user may vary. For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

This article describes how to assign or change an emergency location for a user. 

This article applies to Calling Plans and Operator Connect.
  
You can assign or change an emergency location for a user in the Microsoft Teams admin center or by using PowerShell.

## Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Phone numbers**.

2. On the **Phone numbers** page, click the **Numbers** tab, select a user number in the list, and then click **Edit**.

3. On the **Edit** pane, under **Emergency location**, do one of the following:

   - To assign an emergency location, search for, and select an emergency location.

   - To change the emergency location that's already assigned to the user, click **X** to remove the existing location, and then search for and select the location you want to assign.

4. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this is on.

5. Click **Apply**.

## Using PowerShell

See [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment). 

    
## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign or change a place for an emergency location for a user](assign-change-emergency-place-user.md)
- [Add, change, or remove a place for an emergency location in your organization](add-change-remove-emergency-place-organization.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)
