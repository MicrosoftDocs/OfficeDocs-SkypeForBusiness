---
title: "Add, change, remove emergency locations"
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
description: "Learn how to add, change, or remove an emergency location for your organization in the Microsoft Teams admin center. "
ms.custom: seo-marvel-mar2020
---

# Add, change, or remove an emergency location for your organization

An emergency location must be associated with a phone number, but when this happens can vary between countries and regions. For example, in the United States, you need to associate an emergency location when you assign the phone number to the user. In the United Kingdom, you need to associate an emergency location to the phone number when you get the phone numbers from Microsoft 365 or Office 365 or transfer phone numbers from your current service provider.

No matter which country or region you are in, you can add a place or places to an emergency location and remove an emergency location. Depending on the number of physical locations in your organization, you can create places for buildings, floors, and offices. See [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).
  
To learn how to get a Calling Plan and how much they cost, see [Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

You manage emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.
  
## Add an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. Click **Add**.
3. Enter a name and description for the location.
4. Select the country or region, and then enter the address.

   > [!NOTE]
   > In Belgium, France, Germany, Ireland, Netherlands, and Spain, it's important to understand that to successfully activate a phone number in Microsoft 365 or Office 365, the address set up in the emergency location, which is used to acquire the number, must match the phone number's area code.

5. If the address isn't found and you want to manually edit the address, turn on **Edit the address manually**.
6. Click **Save**.

### Using PowerShell

See [New-CsOnlineLisCivicAddress](/powershell/module/skype/new-csonlineliscivicaddress).
    
## Change an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, select the location that you want to change, and then click **Edit**.
3. Make the changes you want.
4. Click **Save**.

> [!NOTE]
> You can change the address information for a location only if the address isn't validated. If the address is already validated, and you need to change the address, delete the location, and then create a new location with the correct address.

### Using PowerShell

See [Set-CsOnlineLisCivicAddress](/powershell/module/skype/set-csonlineliscivicaddress).
    
## Remove an emergency location

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, select the location that you want to remove, and then click **Delete**.

### Using PowerShell

See [Remove-CsOnlineLisCivicAddress](/powershell/module/skype/remove-csonlineliscivicaddress).

## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Add, change, or remove a place for an emergency location in your organization](add-change-remove-emergency-place-organization.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)