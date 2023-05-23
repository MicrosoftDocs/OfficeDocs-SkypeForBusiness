---
title: Add places to emergency locations
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jastark, roykuntz
ms.date: 05/22/2023
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
description: Learn how to add, change, or remove a place for an emergency location and assign a place for your users.
ms.custom: seo-marvel-mar2020
---

# Add places to emergency locations

Depending on the number of physical locations in your organization, you can add *places* for buildings, floors, and offices to create a more specific emergency location.

Depending on your PSTN connectivity option, however, how you manage emergency locations and location requirements may vary. Regardless of the [PSTN connectivity option](pstn-connectivity.md) you choose&mdash;Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, or Direct Routing&mdash;an emergency location needs to be assigned to each phone number or user. For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

This article describes how to add, change, or remove a *place* for an emergency location for your organization and how to [assign a place for your users](#assign-a-place-for-your-users).

This article applies to Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing.

If an Session Border Control (SBC) Emergency Location Identifier Number (ELIN) application is integrated into a Direct Routing deployment, you must configure the emergency addresses and associated telephone numbers in the ELIN application, and then upload the ELIN records to the emergency calling database in the respective PSTN. For more information, see [Considerations for Direct Routing](considerations-direct-routing.md).

You can manage emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.
  
## Add a place to an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, click the name of the location for which you want to add a place.
3. On the **Places** tab, click **Add**.
4. Enter a place name, and then click **Apply**.

### Using PowerShell

See [New-CsOnlineLisLocation](/powershell/module/skype/new-csonlinelislocation).

## Change a place for an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, click the name of the location for which you want to change a place.
3. On the **Places** tab, select the place you want to change, and then click **Edit**.
4. Update the place information, and then click **Apply**.

### Using PowerShell

See [Set-CsOnlineLisLocation](/powershell/module/skype/set-csonlinelislocation).

## Remove a place from an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, click the name of the location for which you want to remove a place.
3. On the **Places** tab, select the place you want to remove, and then click **Delete**.

### Using PowerShell

See [Remove-CsOnlineLisLocation](/powershell/module/skype/remove-csonlinelislocation).

## Assign a place for your users

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Phone numbers**.

2. On the **Phone numbers** page, click the **Numbers** tab, select a user number in the list, and then click **Edit**.

3. On the **Edit** pane, under **Emergency location**, do one of the following:

    - To assign a place, search for the location or place, and then select the place in the search results.

    - To change the place that's already assigned to the user, click **X** to remove the existing location and place, search for and then select the place you want to assign.

4. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this is on.

5. Click **Apply**.

### Using PowerShell

See [Set-CsOnlineLisLocation](/powershell/module/skype/set-csonlinelislocation).

## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency locations](add-change-remove-emergency-location-organization.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)
