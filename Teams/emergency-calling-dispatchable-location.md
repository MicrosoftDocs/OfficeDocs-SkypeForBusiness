---
title: "Support for emergency calling location information"
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

# Support for emergency calling location information in the United States

This article describes Microsoft's support for 911 emergency calling location information in the United States. This support ensures that the most precise dispatchable location information possible is provided for Teams users making emergency calls. Regardless of the caller's location--onsite or working from home--a  caller's location information sent to the Public Safety Answering Point (PSAP) must be accurate.

This article includes information about Microsoft's compliance with the RAY BAUM’S Act for Multi Line Telephone Systems (MLTS). The RAY BAUM'S Act extends the Kari’s Law requirements, which went into effect in early 2021. For more information about the RAY BAUM'S Act and Kari's Law, see [Dispatchable Location for 911 Calls](https://www.fcc.gov/911-dispatchable-location) and [Multi-line Telephone Systems – Kari’s Law and RAY BAUM’S Act 911 Direct Dialing, Notification, and Dispatchable Location Requirements](https://www.fcc.gov/mlts-911-requirements). 

Users working at home can now set their own emergency addresses if applicable. This article describes how you can configure user policies so that your end users can set their emergency addresses.

Although this information applies to emergency 911 calling in the United States, note that user-entered locations will be conveyed to the screening center in Canada as well.

This article contains the following sections:

- [Support for emergency calling location information](#support-for-emergency-calling-location-information)
- [Enhancements to location requests](#enhancements-to-location-requests)
- [Emergency address classification and routing](#emergency-address-classification-and-routing)
- [Enable end users to configure their emergency address](#enable-end-users-to-configure-their-emergency-address)
- [Notes and restrictions](#notes-and-restrictions)


## Support for emergency calling location information

Microsoft has made changes to support the following:  

- Off-premises devices associated with a Multi-Line-Telephone-System (MLTS) must provide automated dispatchable location information to the appropriate PSAP if technically feasible.

- Enhanced location information may be coordinate-based. The information must consist of the best available location that can be obtained from any available technology, or combination of technologies, at reasonable cost.

- Users must be allowed to roam without having to constantly update their location.

To support these requirements, Microsoft is using information and location services provided by:

- The respective operating systems
- Emergency calling routing partners
- End users

## Enhancements to location requests

The following enhancements have been made to location requests:

- A new setting in Teams Calling Policy that enables the off-premises work-from-home location experience for end users.

- Teams clients will continue to send location requests to the service with IP address, Basic Service Set Identifiers (BSSID), and (Link Layer Discovery Protocol (LLDP) network information.

- If given permission, location requests will now include geo codes from the operating system.

**QUESTION FOR ROY:  We keep saying "the service"...   Should we just say Teams instead?**

- The service returns a single emergency address with the following precedence:

   - Derived from the tenant-admin-defined emergency addresses associated with either the IP address, BSSID, or LLDP. For more information about tenant-admin-defined dynamic addresses, see [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

   - Derived from the geocodes (if available).

   - Derived from the user/phone number when statically assigned.

If there is no match, then no emergency address is returned.


## Emergency address classification and routing

The following table shows the types of emerency addresses and associated routing methods. The sections following the table describe location logic when:

- [Connecting to a new network](#connecting-to-a-new-network)
- [Connecting to a known network](#connecting-to-a-known-network)


| Type of emergency address | Emergency routing method |
| :------------| :-------|
| Emergency address defined by administrator. | Direct to PSAP. |
| Emergency address derived from geo codes without confirmation for accuracy by the user | Screened and Transferred to PSAP. |
| Emergency address derived from geo codes with confirmation for accuracy by the user. | Direct to PSAP. |
| Emergency address derived from geo codes and edited and confirmed by the user. | Screened and Transferred to PSAP. |
| Emergency address edited from scratch and confirmed by the user. | Screened and Transferred to PSAP. |
| Emergency address edited by map string match and confirmed by the end user. | Direct to PSAP. |
| Emergency address statically assigned to the user/number. | Screened and Transferred to PSAP. |
| Null |  Screened and Transferred to PSAP. |

### Connecting to a new network

- If an admin-defined dynamic location is returned from the service, then this location is used.  A user is not allowed to change the location.

- If an admin-defined dynamic location is NOT returned from the service AND Teams had NOT obtained geo codes, then an end user is allowed to enter an emergency address which is saved with reference to the connected network.

- If an admin-defined dynamic location is NOT returned from the service AND Teams HAD obtained geo codes, the emergency address derived from the geo codes is returned from the service. The end user is allowed to edit this address, which is then saved with reference to the connected network.

Note that while safeguards are in place, automatic geo code based addresses are not going to be precisely accurate.  **(DO WE NEED TO CLARIFY WHAT THIS MEANS?  HOW NOT ACCURATE ARE THEY?)**

### Connecting to a known network  

- If an admin-defined dynamic location is returned from the service, then this location is used.  A user is not allowed to change the location.

- If an admin-defined dynamic location IS NOT returned from the service, the location that was previously saved with the associated connected network will be used. A user can edit this location if necessary.

- It is possible to save a location against many BSSID’s, such as might be present in an office building. **(BUT MICROSOFT DOES NOT RECOMMNEND DOING THIS?  ie NOT PRACTICAL?)**


## Enable end users to configure their emergency address

Teams users who are working at home--outside of the defined emergency addresses on the corporate network--can now configure their emergency address in Microsoft Teams. 

The Teams client stores the address locally on the device and maps it to the local network. On the next sign-in from the same network location, the client will automatically display the registered address. 

To enable this feature for your end users, you must use PowerShell to configure the 
TeamsEmergencyCallingPolicy for the user and set the ExternalLocationLookupMode parameter to Enabled, as shown in the following example:


``` PowerShell
New-CsTeamsEmergencyCallingPolicy -Identity E911WFH -ExternalLocationLookupMode Enabled
```

```PowerShell
Grant-CsTeamsEmergencyCallingPolicy -PolicyName E911WFH -Identity user@contoso.com
```

After enabling this feature for your end users, from the Calls tab, the user can add, edit, or confirm an emergency address and display the address after it is set. 

Teams uses the appropriate geo location services to assist the user in entering their emergency address as follows:

- If the Teams client is connected to Microsoft 365 on a network location not defined as an emergency address on the corporate network, the Teams client will prompt the user to Add an emergency address. This address will then appear on the Calls tab for that user.

- If no emergency address is configured by the user for this network location, Teams will use the Azure Maps service to try to locate an address based on information on the client; that is, using the Windows Location Service and the default location. If Teams can locate an address, it will display the address, and the user can edit or confirm the location.

- If the Teams client is connected to the corporate network with a defined emergency address, Teams will show that emergency address, indicating that it is a work location and cannot be edited.

On Windows, you can manage the Windows Location Service and whether applications have access to the location by using group policy or by using [mobile device management (MDM)](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-privacy#privacy-letappsaccesslocation).




## Notes and restrictions

Please keep the following in mind:

- The work-from-home experience described is for Teams desktop on Windows and Mac.

- Teams phones do not support the work-from-home experience.

- Teams mobile supports automatic location detection but not the user entered experience described.

- Privacy settings can conflict with automatic location detection - Mobile Device Management systems can be leveraged.

- Teams Emergency Policy will support a customizable disclaimer.

- The location refresh timer is approximately two minutes when roaming between networks.

## Related topics

