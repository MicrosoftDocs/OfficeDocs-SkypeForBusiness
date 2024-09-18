---
title: Plan and manage emergency calling
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 01/22/2024
ms.topic: article
ms.assetid: 589bf5f5-490a-4215-8588-99bab7d33e31
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
- CSH
ms.custom:
  - ms.teamsadmincenter.locations.emergencyaddresses.overview
  - ms.lync.lac.AddressAndLocation
  - Calling Plans
  - Direct Routing
  - seo-marvel-mar2020
description: "Learn about concepts for managing emergency calling, including information about emergency addresses, dynamic emergency calling, and emergency call routing."
---

# Manage emergency calling

This article is for administrators and IT professionals who are managing emergency calling for their organization.

This article describes concepts about [emergency addresses](#emergency-address), [dynamic emergency calling](#dynamic-emergency-calling), and [emergency call routing](#emergency-call-routing).

How you configure emergency calling differs depending on your Public Switched Telephone Network (PSTN) connectivity option. If you need help deciding which Microsoft voice solution is right for you, see [Plan your Teams voice solution](cloud-voice-landing-page.md) and [PSTN connectivity options](pstn-connectivity.md).  

## Emergency address

Assigning an emergency address to each of your users ensures that precise dispatchable location information is provided for Teams users making emergency calls.

The following table describes concepts and definitions for emergency calling:

|  | Definition | Example |
|---|---|---|
| **Emergency address** | A civic address&mdash;the physical or street address of a place of business for your organization. | 12345 North Main Street, Redmond, WA 98052 |
| **Place** | Typically a floor, building, wing, or office number. Place is associated with an emergency address to give a more exact location within a building. You can have an unlimited number of places associated with an emergency address. For example, if your organization has multiple buildings, you might want to include place information for each building and every floor within each building. | 4th floor |
| **Emergency location** | A location is a civic address&mdash;with an optional place. If your business has more than one physical location, it's likely that you'll need more than one emergency location.</br></br> When you create an emergency address, a unique location ID is automatically created for this address. If you add a place to an emergency address&mdash;for example, if you add a floor to a building address&mdash;a location ID is created for the combination of the emergency address and place.  In this example, there will be two location IDs: one for the civic address; one for the joined civic address and associated place. </br></br>When you assign an emergency location to a user or site, it's this unique location ID that's associated with the user or site. | 12345 North Main Street, Redmond, WA 98052, 4th floor |
| **Registered address** | An emergency address that is assigned to each user. A registered address is sometimes referred to as a "static emergency address" or "address of record".|**User A**:</br>12345 North Main Street, Redmond, WA 98052 </br></br>**User B**:</br>6789 17th St NW, Atlanta, GA 30363 |

### Emergency address validation

To assign an emergency address to a user or to a network identifier, you must ensure that the emergency address is marked as "validated." Validation ensures that the address is legitimate, and that it can't be modified after it is assigned.

If you define an emergency address by using the address map search feature in the Teams admin center, the address is automatically marked as validated. If the format or representation of an address changes, you can't modify a validated emergency address. You must create a new address with the updated format.

### Emergency address geo codes

Each emergency address can have a geo code (latitude and longitude) associated with it. These geo codes are used in some countries/regions to assist in routing emergency calls with dynamic locations.

If you define an emergency address by using the address map search feature in the Teams admin center, the geo code is automatically associated with an emergency address. You can also associate geo codes with an address by using PowerShell.

Microsoft recommends that you create emergency addresses by using the map search feature in Teams admin center, which ensures that the addresses are formatted, validated, and have the appropriate geo codes.

> [!IMPORTANT]
> To assign an emergency location to a network identifier for dynamic emergency calling, the emergency address must contain an appropriate geo code.

## Dynamic emergency calling

Dynamic emergency calling for Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client. For more information, see [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

## Emergency call routing

Emergency call routing determines how an emergency call is routed to the Public Safety Answering Point (PSAP). Call routing depends on several factors including the emergency calling network of the country/region in which the call originates, the type of client that is making the call, and which [PSTN connectivity option](pstn-connectivity.md) you’ve chosen. For example, Direct Routing requires configuring [specific call routing polices](manage-emergency-call-routing-policies.md). With other PSTN connectivity options, the carrier handles a lot of the configuration for call routing.

## Emergency addresses for remote locations

End users working at home can enable location sharing. Various device management applications can also enable location sharing. Enabling location sharing to Teams varies by operating systems. For more information, see [Emergency addresses for remote locations](emergency-calling-dispatchable-location.md) and [Enable location services](https://support.microsoft.com/en-us/office/work-from-home-emergency-911-enable-location-services-583dd649-87fc-4b23-aed6-f4e2279297f9?storagetype=live).

## Security desk notifications

Security desk notifications are available with Microsoft Calling Plans, Operator Connect, and Direct Routing.

You can configure who's notified during an emergency call, and how they are notified. During an emergency call, a security desk is conferenced into the call, and the security desk user experience is determined by the Teams emergency calling policy. 

You can also configure extended notification settings per emergency number. For example, you can specify how a call to the emergency test number 933 is handled without notifying the security desk.

For more information about configuring security desk notifications, see [Configure security desk notifications](emergency-calling-security-desk-notifications.md).


## Create a custom emergency service disclaimer

You can add a custom banner in the tenant for your users to enable E911. Users can dismiss the banner when they confirm their address, and the banner will reappear when Teams is restarted. To enable this feature, you set the Emergency service disclaimer under the Teams emergency calling policy, and enter a string message to display to users. This field is optional when setting up a custom policy, and the string field is limited to 250 characters. For more information, see [Manage emergency calling policies](manage-emergency-calling-policies.md).

## Considerations for PSTN connectivity options

There are some differences in how you manage emergency calling depending on whether you're using Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, or Direct Routing for your [PSTN connectivity](pstn-connectivity.md).

For your specific PSTN connectivity setup, read the following considerations for managing emergency calling:

- [Calling Plan considerations](considerations-calling-plan.md)
- [Operator Connect considerations](considerations-operator-connect.md)
- [Teams Phone Mobile considerations](considerations-teams-phone-mobile.md)
- [Direct Routing considerations](considerations-direct-routing.md)

## Related topics

- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies](manage-emergency-call-routing-policies.md)
- [Manage an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign an emergency location for your user](assign-change-emergency-location-user.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
- [Teams policies reference - Emergency policies](settings-policies-reference.md#emergency-policies)
- [Emergency numbers country reference](emergency-numbers-reference.md)
