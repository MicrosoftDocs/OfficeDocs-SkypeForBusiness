---
title: Add places to emergency locations
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: jastark, roykuntz
ms.date: 06/26/2023
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
description: Learn how to add a place for an emergency location and assign a place to your users.
ms.custom: seo-marvel-mar2020
---

# Add places to emergency locations

This article is about adding places to an emergency location. It also describes how to assign a place for an emergency location to a user or phone number. Before reading this article, be sure you've read [Manage emergency locations](add-change-remove-emergency-location-organization.md).

Depending on the number of physical locations in your organization, you can add places for buildings, floors, and offices to create a more specific emergency location.

This article applies to Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing.

You can manage emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.
  
## Add a place to an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, click the name of the location for which you want to add a place.
3. On the **Places** tab, click **Add**.
4. Enter a place name, and then click **Apply**.

### Using PowerShell

See [New-CsOnlineLisLocation](/powershell/module/teams/new-csonlinelislocation).

## Change a place for an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, click the name of the location for which you want to change a place.
3. On the **Places** tab, select the place you want to change, and then click **Edit**.
4. Update the place information, and then click **Apply**.

### Using PowerShell

See [Set-CsOnlineLisLocation](/powershell/module/teams/set-csonlinelislocation). If you need to update the Emergency Location Identification Number (ELIN), don't set the ELIN attribute to an empty or null string - otherwise, you will receive an error.

## Remove a place from an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, click the name of the location for which you want to remove a place.
3. On the **Places** tab, select the place you want to remove, and then click **Delete**.

### Using PowerShell

See [Remove-CsOnlineLisLocation](/powershell/module/teams/remove-csonlinelislocation).

## Assign a place to your users

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Phone numbers**.

2. On the **Phone numbers** page, click the **Numbers** tab, select a user number in the list, and then click **Edit**.

3. On the **Edit** pane, under **Emergency location**, do one of the following:

    - To assign a place, search for the location or place, and then select the place in the search results.

    - To change the place that's already assigned to the user, click **X** to remove the existing location and place, search for and then select the place you want to assign.

4. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this setting is **On**.

5. Click **Apply**.

### Using PowerShell

See [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment).

## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency locations](add-change-remove-emergency-location-organization.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)
