---
title: Plan and manage emergency calling
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: roykuntz
ms.date: 04/14/2023
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

This article describes concepts you'll need to know to manage emergency calling&mdash;it introduces information about [emergency addresses](#emergency-address), [dynamic emergency calling](#dynamic-emergency-calling), and [emergency call routing](#emergency-call-routing).

Be aware that how you configure emergency calling will differ depending on your Public Switched Telephone Network (PSTN) connectivity option. If you need help with deciding which Microsoft voice solution is right for you, read [Plan your Teams voice solution](cloud-voice-landing-page.md) and [PSTN connectivity options](pstn-connectivity.md) first.  

## Emergency address

Assigning an emergency address to each of your users ensures that the most precise dispatchable location information possible is provided for Teams users making emergency calls.

The following table provides critical concepts and definitions for emergency calling:

|  | Definition | Example |
|---|---|---|
| **Emergency address** | A civic address&mdash;the physical or street address of a place of business for your organization. | 12345 North Main Street, Redmond, WA 98052 |
| **Place** | Typically a floor, building, wing, or office number. Place is associated with an emergency address to give a more exact location within a building. You can have an unlimited number of places associated with an emergency address. For example, if your organization has multiple buildings, you might want to include place information for each building and every floor within each building. | 4th floor |
| **Emergency location** | A location is a civic address&mdash;with an optional place. If your business has more than one physical location, it's likely that you'll need more than one emergency location.</br></br> When you create an emergency address, a unique location ID is automatically created for this address. If you add a place to an emergency address&mdash;for example, if you add a floor to a building address&mdash;a location ID is created for the combination of the emergency address and place.  In this example, there will be two location IDs: one for the civic address; one for the joined civic address and associated place. </br></br>When you assign an emergency location to a user or site, it's this unique location ID that's associated with the user or site. | 12345 North Main Street, Redmond, WA 98052, 4th floor |
| **Registered address** | An emergency address that is assigned to each user. A registered address is sometimes referred to as a "static emergency address" or "address of record".|**User A**:</br>12345 North Main Street, Redmond, WA 98052 </br></br>**User B**:</br>6789 17th St NW, Atlanta, GA 30363 |

### Emergency address validation

To assign an emergency address to a user or to a network identifier, you must ensure that the emergency address is marked as "validated." Address validation ensures that the address is legitimate, and that it cannot be modified after it is assigned.

If you define an emergency address by using the address map search feature in the Teams admin center, the address is automatically marked as validated. Because you cannot modify a validated emergency address&mdash;if the format or representation of the address changes, you must create a new address with the updated format.

### Emergency address geo codes

Each emergency address can have a geo code (latitude and longitude) associated with it. These geo codes are used in some countries/regions to assist in routing emergency calls with dynamic locations.

If you define an emergency address by using the address map search feature in the Teams admin center, the geo code is automatically associated with an emergency address. You can also associate geo codes with an address if you define the address by using PowerShell.

Microsoft recommends that you create emergency addresses by using the map search feature in Teams admin center, which will ensure that the addresses are formatted, validated, and have the appropriate geo codes.

> [!IMPORTANT]
> To assign an emergency location to a network identifier for dynamic emergency calling, the emergency address must contain an appropriate geo code.

## Dynamic emergency calling

Dynamic emergency calling for Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, and Direct Routing provides the capability to configure and route emergency calls and notify security personnel based on the current location of the Teams client. Read more about [how to plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

## Emergency call routing

Emergency call routing determines how an emergency call is routed to the Public Safety Answering Point (PSAP). Call routing depends on several factors including the emergency calling network of the country/region in which the call originates and which [PSTN connectivity option](pstn-connectivity.md) you’ve chosen. For example, Direct Routing requires configuring [specific call routing polices](manage-emergency-call-routing-policies.md). With other PSTN connectivity options, the carrier handles a lot of the configuration for call routing.

## Security desk notification

Security desk notification is available with both Microsoft Calling Plans, Operator Connect, and Direct Routing.

You use a Teams emergency calling policy ([TeamsEmergencyCallingPolicy](/powershell/module/skype/set-csteamsemergencycallingpolicy)) to configure who should be notified during an emergency call and how they are notified: chat only, conferenced in and muted, or conferenced in and muted but with the ability to unmute. You can also specify an external PSTN number to call and join the emergency call. Note that the PSTN party is not allowed to unmute.

An emergency calling policy can be granted to a Teams user account, assigned to a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If an emergency calling policy is associated with a network site, then the site policy is used to configure security desk notification.

- If there is no emergency calling policy associated with the site, or if the client is connected at an undefined site, then the emergency calling policy associated with the user account is used to configure security desk notification.

- If the Teams client is unable to obtain an emergency calling policy, then the user is not enabled for security desk notification.

During an emergency call, a security desk is conferenced into the call and the experience of the security desk user is controlled based upon the Teams emergency calling policy. A group chat is started with each security desk member, and the location of the emergency caller is shared via an important message notification. If a conference option is configured as part of the policy, each security desk user is additionally called as part of the conference.

## Create a custom emergency service disclaimer

Administrators have the ability to add a custom banner in the tenant for their users to enable E911. Users can dismiss the banner when they confirm their address, and the banner will reappear when Teams is restarted. To enable this feature, you would set the Emergency service disclaimer under the Teams emergency calling policy and enter a string message to be displayed to users. This field is optional when setting up a custom policy, and the string field is limited to 250 characters. Read more on [how to manage emergency calling policies](manage-emergency-calling-policies.md).

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
