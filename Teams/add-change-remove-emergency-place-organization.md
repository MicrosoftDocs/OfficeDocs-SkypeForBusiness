---
title: Add, change, remove places for emergency locations
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
  - m365initiative-voice
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - NOCSH
description: Learn how to add, change, or remove a place for an emergency location for your organization.
ms.custom: seo-marvel-mar2020
---

# Add, change, or remove a place for an emergency location in your organization

Depending on the number of physical locations in your organization, you can add *places* for buildings, floors, and offices to create a more specific emergency location.

Depending on your PSTN connectivity option, however, how you manage emergency locations and location requirements may vary. For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

This article describes how to add, change, or remove a *place* for an emergency location for your organization.

This article applies to Microsoft Calling Plans, Operator Connect, Operator Connect Mobile (Public preview release), and Direct Routing.

You manage emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.
  
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
    
## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)