---
title: "Emergency addresses for remote locations"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: roykuntz
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
description: "Learn how Microsoft supports dispatchable location information to support emergency calling."
ms.custom: seo-marvel-mar2020
---

# Emergency addresses for remote locations

This article describes Microsoft's support for 911 emergency calling location information in the United States. This support ensures that the most precise dispatchable location information possible is provided for Teams users making emergency calls. Regardless of the caller's location--onsite or working from home--a  caller's location information sent to the Public Safety Answering Point (PSAP) must be accurate.

This article includes information about Microsoft's compliance with the RAY BAUM’S Act for Multi Line Telephone Systems (MLTS). The RAY BAUM'S Act extends the Kari’s Law requirements, which went into effect in early 2021. For more information about the RAY BAUM'S Act and Kari's Law, see [Dispatchable Location for 911 Calls](https://www.fcc.gov/911-dispatchable-location) and [Multi-line Telephone Systems – Kari’s Law and RAY BAUM’S Act 911 Direct Dialing, Notification, and Dispatchable Location Requirements](https://www.fcc.gov/mlts-911-requirements). 

Users working at home can now set their own emergency addresses if applicable. This article describes how you can configure user policies so that your end users can set their emergency addresses.

Although this information applies to emergency 911 calling in the United States, user-entered locations will be conveyed to the screening center in Canada as well.

This article contains the following sections:

- [Support for emergency calling location information](#support-for-emergency-calling-location-information)
- [Location precedence](#location-precedence)
- [Emergency address classification and routing](#emergency-address-classification-and-routing)
- [Enable end users to configure their emergency address](#enable-end-users-to-configure-their-emergency-address)
- [Notes and restrictions](#notes-and-restrictions)


## Support for emergency calling location information

To support these requirements, Teams uses the location services provided by the respective operating system to suggest an address--if granted permission by the administrator or user. The end user can confirm the location of a suggested address, edit it, or manually enter a new one. A confirmed, edited, or manually entered address is then saved on the Teams client so that the user-confirmed address is automatically used when the client is connected to that network. The user-saved addresses are automatically cleared when the Teams client is signed out.


## Location precedence

Emergency addresses for Teams can be categorized by different types. The following list shows the location precedence used when an emergency number is dialed:

1. A dynamically acquired address defined by the tenant administer in the Location Information Service.

2. An address the end user confirmed, edited, or manually entered which is associated to the local network the Teams client is connected to.

3. An address automatically suggested by the operating system.

4. An address the administrator statically assigns to the user.


## Emergency address classification and routing

The following table shows the types of emergency addresses and associated routing methods for each type: whether the call is automatically routed to the serving PSAP or screened for accuracy before transferring to the serving PSAP. This routing behavior is supported in the United States for all Calling Plan users, Operator Connect partners, and Direct Routing certified emergency calling service providers.


| Type of emergency address | Emergency routing method |
| :------------| :-------|
| Dynamically acquired emergency address defined by administrator. | Direct to PSAP. |
| Emergency address obtained from the operating system **without confirmation for accuracy** by the user. | Screened and Transferred to PSAP. |
| Emergency address obtained from the operating system **with confirmation for accuracy** by the user.| Direct to PSAP. |
| Emergency address obtained from the operating system and edited and confirmed by the user. | Screened and Transferred to PSAP. |
| Emergency address entered and confirmed by the user. | Screened and Transferred to PSAP. |
| Emergency address statically assigned to the user/number. | Screened and Transferred to PSAP. |
| Null | Screened and Transferred to PSAP. |


## Enable end users to configure their emergency address

To enable this feature for your end users, use the New-CsTeamsEmergencyCallingPolicy PowerShell cmdlet, and set the ExternalLocationLookupMode parameter to Enabled. See the following example: 


``` PowerShell
New-CsTeamsEmergencyCallingPolicy -Identity E911WFH -ExternalLocationLookupMode Enabled
```

```PowerShell
Grant-CsTeamsEmergencyCallingPolicy -PolicyName E911WFH -Identity user@contoso.com
```

After enabling this feature for your end users, from the Calls tab, the user can add, edit, or confirm an emergency address and display the address after it is set. For more information on how end users can set location services, see [Work from Home Emergency 911: enable location services](https://support.microsoft.com/office/work-from-home-emergency-911-enable-location-services-583dd649-87fc-4b23-aed6-f4e2279297f9?storagetype=live).

On Windows, you can manage the Windows location service, and whether applications have access to the location, by using group policy or by using [mobile device management (MDM)](/windows/client-management/mdm/policy-csp-privacy#privacy-letappsaccesslocation).

For more information about Windows location service, see [Windows location service and privacy](https://support.microsoft.com/windows/windows-location-service-and-privacy-3a8eee0a-5b0b-dc07-eede-2a5ca1c49088).



## Notes and restrictions

Keep the following in mind:

- The work-from-home experience described is for Teams desktop on Windows and Mac.

- Teams phones do not support the work-from-home experience.

- Teams mobile supports automatic location detection but not the user entered experience described.

- Privacy settings can conflict with automatic location detection - Mobile Device Management systems can be used.


## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)

- [Work from Home Emergency 911: enable location services](https://support.microsoft.com/office/work-from-home-emergency-911-enable-location-services-583dd649-87fc-4b23-aed6-f4e2279297f9?storagetype=live)

