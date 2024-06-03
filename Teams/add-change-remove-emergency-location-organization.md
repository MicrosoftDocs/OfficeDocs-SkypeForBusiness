---
title: Manage emergency locations
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jastark, roykuntz
ms.date: 10/11/2023
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
description: Learn how to add, change, or remove an emergency location for your organization and how to assign a location to your users.
ms.custom: seo-marvel-mar2020
---

# Manage emergency locations for your organization

This article describes how to add, change, or remove an emergency location for your organization. It also describes how to assign an emergency location to your users.

Regardless of the [PSTN connectivity option](pstn-connectivity.md) you choose&mdash;Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, or Direct Routing&mdash;an emergency location may be assigned to a phone number.

However, depending on your PSTN connectivity option, how you manage emergency locations and location requirements may vary. For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

This article applies to Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing.
  
## Add an emergency location

You can add emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.

To activate a phone number in Microsoft 365 in Belgium, France, Germany, Ireland, Netherlands, and Spain, the address set up in the emergency location must match the phone number's area code.

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
1. Click **Add**.
1. Enter a name and description for the location.
1. Select the country or region, and then enter the address.
1. If the address isn't found and you want to manually edit the address, turn on **Edit the address manually**.
1. Click **Save**.

### Using PowerShell

See [New-CsOnlineLisCivicAddress](/powershell/module/teams/new-csonlineliscivicaddress).

### Required information for Microsoft Calling Plans

For Microsoft Calling Plans, all countries require the following information:

- House or building name or number 
- Street name or number
- City or town
- Postal code or zip code
- Latitude
- Longitude
- Organization or Company name

In addition, some countries require additional information, as shown in the following table:

| Addition information required | Country |
| :------------|:-------|
| State or Province | Canada, Israel, Italy, United States |
| Company tax ID | Belgium, Czech Republic, Italy, Netherlands, Norway, Poland, Portugal, Romania, Singapore, Slovakia, Spain, Sweden |
| Street type | Italy |



## Change an emergency location

You can change emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.

You can only update the address information for an emergency location if the address hasn't been validated. If an address has already been validated and you need to change the address, you must delete the location and then create a new location with the correct address.

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, select the location that you want to change, and then click **Edit**.
3. Make the changes you want.
4. Click **Save**.

### Using PowerShell

See [Set-CsOnlineLisCivicAddress](/powershell/module/teams/set-csonlineliscivicaddress).

## Remove an emergency location

You can remove emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.

You can remove a location only if no users or phone numbers are assigned to it. If numbers or users are assigned to the location, you need to remove them first.

### Using the Microsoft Teams admin center

1. In the left navigation of the Microsoft Teams admin center, click **Locations** > **Emergency addresses**.
2. In the list, select the location that you want to remove, and then click **Delete**.

### Using PowerShell

See [Remove-CsOnlineLisCivicAddress](/powershell/module/teams/remove-csonlineliscivicaddress).

## Assign an emergency location

You can assign emergency locations for your organization in the Microsoft Teams admin center or by using PowerShell.

To assign an emergency location, be sure the location, users, and phone numbers are all in the same country/region.

### Using the Microsoft Teams admin center

#### Calling Plans, Operator Connect, Teams Phone Mobile

1. In the left navigation of the Microsoft Teams admin center, click **Voice** > **Phone numbers**.

1. On the **Phone numbers** page, click the **Numbers** tab, select a user number in the list, and then click **Edit**.

1. On the **Edit** pane, under **Emergency location**, do one of the following:

   - To assign an emergency location, search for, and select an emergency location. For information on assigning places, see [Add places to emergency locations](add-change-remove-emergency-location-organization.md).

   - To change the emergency location that's already assigned to the user, click **X** to remove the existing location, and then search for and select the location you want to assign.

1. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this setting is **On**.

1. Click **Apply**.

#### Direct Routing

For Direct Routing users, you can assign a Direct Routing phone number and then optionally an emergency location.

1. In the left navigation of the Microsoft Teams admin center, click **Users** > **Manage Users**.

1. On the **Manage users** page, select the user you want to update.

1. Under the **Account** tab, next to **General information**, click **Edit**.

1. From the **Assign phone number** panel, select **Direct Routing** for the **Phone number type**.

1. For **Assigned phone number**, enter the direct routing number and then the extension for **Phone number extension**.

1. For **Emergency location**, search for, and select an emergency location.

1. Depending on whether you want to send an email to the user with their phone number information, turn off or turn on **Email user with telephone number information**. By default, this setting is **On**.

1. Click **Apply**.

### Using PowerShell

For Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Calling, see [Set-CsPhoneNumberAssignment](/powershell/module/teams/set-csphonenumberassignment).

## Related topics

- [Add places to emergency locations](add-change-remove-emergency-place-organization.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)
