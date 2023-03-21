---
title: Plan and manage emergency calling
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: roykuntz
ms.date: 11/28/2017
ms.topic: article
ms.assetid: 589bf5f5-490a-4215-8588-99bab7d33e31
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection:
  - M365-voice
  - m365initiative-voice
  - highpri
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
description: "Learn about emergency calling, including information about emergency addresses, emergency call routing, and dynamic emergency calling."
---

# Manage emergency calling

This article describes concepts you'll need to know to manage emergency calling&mdash;it includes information about emergency addresses, dynamic emergency addresses, and emergency call routing.

This article uses the following terminology for emergency calling:


|  | Definition | Example |
|---|---|---|
| **Emergency address** | A civic address&mdash;the physical or street address of a place of business for your organization. | i.e. |
| **Place** | Typically a floor, building, wing, or office number. Place is associated with an emergency address to give a more exact location within a building. You can have an unlimited number of places associated with an emergency address. For example, if your organization has multiple buildings, you might want to include place information for each building and every floor within each building. | i.e. |
| **Emergency location** | A location is a civic address&mdash;with an optional place. If your business has more than one physical location, it's likely that you'll need more than one emergency location.</br></br> When you create an emergency address, a unique location ID is automatically created for this address. If you add a place to an emergency address&mdash;for example, if you add a floor to a building address&mdash;a location ID is created for the combination of the emergency address and place.  In this example, there will be two location IDs: one for the civic address; one for the joined civic address and associated place.</br></br>When you assign an emergency location to a user or site, it's this unique location ID that's associated with the user or site. | i.e. |
| **Registered address** | An emergency address that is assigned to each user. A registered address is sometimes referred to as a "static emergency address" or "address of record". Currently, registered addresses are not supported for Direct Routing. Check back soon for updates. | i.e. |

There are some differences in how you manage emergency calling depending on whether you are using Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, or Direct Routing for your [PSTN connectivity](pstn-connectivity.md). 

For your specific PSTN connectivity setup, read the following considerations:

- [Calling Plan considerations](considerations-calling-plan.md)
- [Operator Connect considerations](considerations-operator-connect.md)
- [Teams Phone Mobile considerations](considerations-teams-phone-mobile.md)
- [Direct Routing considerations](considerations-direct-routing.md)

## Validate an Emergency address

To assign an emergency address to a user or to a network identifier, you must ensure that the emergency address is marked as "validated." Address validation ensures that the address is legitimate, and that it cannot be modified after it is assigned.

If you define an emergency address by using the address map search feature in the Teams admin center, the address is automatically marked as validated. Because you cannot modify a validated emergency address&mdash;if the format or representation of the address changes, you must create a new address with the updated format.

## Associate a geo code with an Emergency address

Each emergency address can have a geo code (latitude and longitude) associated with it. These geo codes are used in some countries to assist in routing emergency calls with dynamic locations.

If you define an emergency address by using the address map search feature in the Teams admin center, the geo code is automatically associated with an emergency address. You can also associate geo codes with an address if you define the address by using PowerShell.

Microsoft recommends that you create emergency addresses by using the map search feature in Teams admin center, which will ensure that the addresses are formatted, validated, and have the appropriate geo codes.

>[!Important]
>To assign an emergency location to a network identifier for dynamic emergency calling, the emergency address must contain an appropriate geo code.

## Security desk notification

Security desk notification is available with both Microsoft Calling Plans, Operator Connect, and Direct Routing.

During an emergency call, a security desk is conferenced into the call and the experience of the security desk user is controlled based upon the Teams emergency calling policy. A group chat is started with each security desk member, and the location of the emergency caller is shared via an important message notification. If a conference option is configured as part of the policy, each security desk user is additionally called as part of the conference.

An emergency calling policy can be granted to a Teams user account, assigned to a network site, or both.  When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If an emergency calling policy is associated with a network site, then the site policy is used to configure security desk notification.

- If there is no emergency calling policy associated with the site, or if the client is connected at an undefined site, then the emergency calling policy associated with the user account is used to configure security desk notification.

- If the Teams client is unable to obtain an emergency calling policy, then the user is not enabled for security desk notification.

To enable security desk notification features in the Teams admin center, do the following:

1. In the Teams admin center, select **Voice** > **Emergency policies**.
1. Under the **Calling policies** section, either create a new policy or choose an existing policy to update.
1. Once you have selected a policy, the **Emergency calling policy** pane will open. You can update the following settings:

    - Name
    - Description
    - External location lookup mode
    - Notification mode
    - Emergency service disclaimer ([see below](#create-a-custom-emergency-service-disclaimer))
    - Numbers to dial for emergency calls notifications
    - Users and groups for emergency calls notifications
  
1. Hit **Apply** once you're done.

Using Microsoft PowerShell, you use the TeamsEmergencyCallingPolicy ([Set-CsTeamsEmergencyCallingPolicy](/powershell/module/skype/set-csteamsemergencycallingpolicy)) to configure who should be notified during an emergency call and how they are notified: chat only, conferenced in and muted, or conferenced in and muted but with the ability to unmute.

To create a security desk notification to select groups and users that are conferenced in and muted but with the ability to unmute, run this script:

```powershell
Set-CsTeamsEmergencyCallingPolicy -Identity "TestECP" -NotificationMode ConferenceUnMuted -NotificationGroup "group1@contoso.com;group2@contoso.com;user1@contoso.com;user2@contoso.com"
```

You can also specify an external PSTN number of a user or group to call and join the emergency call with the `-NotificationDialOutNumber` parameter and [Set-CsTeamsEmergencyCallingPolicy](/powershell/module/skype/set-csteamsemergencycallingpolicy) cmdlet. Note that the PSTN party is not allowed to unmute.

### Create a custom emergency service disclaimer

Administrators have the ability to add a custom banner in the tenant for their users to enable E911. Users can dismiss the banner when they confirm their address, and the banner will reappear when Teams is restarted.

To create a custom emergency service disclaimer in the Teams admin center, do the following:

1. In the Teams admin center, select **Voice** > **Emergency policies**.
1. Under the **Calling policies** section, either create a new policy or choose an existing policy to update.
1. Once you have selected a policy, the **Emergency calling policy** pane will open. For  **Emergency service disclaimer**, enter a string message to be displayed to users. This field is optional when setting up a custom policy; the string field is limited to 250 characters.
1. Hit **Apply** once you're done.

To create this custom emergency disclaimer with PowerShell, run the following script:

```powershell
Set-CsTeamsEmergencyCallingPolicy -Identity "TestECP" -EnhancedEmergencyServiceDisclaimer "Emergency test acknowledgement"
```

## Related topics

- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies](manage-emergency-call-routing-policies.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign or change an emergency location for your user](assign-change-emergency-location-user.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
- [Teams policies reference - Emergency policies](settings-policies-reference.md#emergency-policies)
