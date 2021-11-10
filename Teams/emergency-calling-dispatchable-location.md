---
title: "Support for dispatchable location information"
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
description: "Learn how MIcrosoft supports dispatchable location information to support emergency calling."
ms.custom: seo-marvel-mar2020
---

# Dispatchable location information for emergency calling

This article describes Microsoft's support for ensuring that the most precise emergency location information possible is provided for Teams users. Regardless of the caller's location--onsite or working from home--a  caller's location information sent to the Public Safety Answering Point (PSAP) must be accurate.

This article includes information about how Microsoft is adhering to the Ray Baum’s Act compliance date for Multi Line Telephone Systems (Jan 6th, 2022). The Ray Baum act extends the Kari’s Law requirements, which went into effect in early 2021. For more information about the Ray Baum Act and Kari's Law, see [Dispatchable Location for 911 Calls](https://www.fcc.gov/911-dispatchable-location).

This article also describes how you can configure user policies so that your end users working from home can now set their own emergency addresses if applicable.

**QUESTION FOR ROY: RAY BAUM ACT IS FOR U.S. 911 CALLING...  Note that this information only applies to emergency 911 calling in the United States.  (True?)   but does some of this apply to Canada, etc.  What should the disclaimer say?**

This article contains the following sections:

- [Support for dispatchable location information for emergency calling](#support-for-dispatchable-location-information-for-emergency-calling)
- [Enhancements to location requests](#enhancements-to-location-requests)
- [Emergency address classification and routing](#emergency-address-classification-and-routing)
- [Enable end users to configure their emergency address](#enable-end-users-to-configure-their-emergency-address)
- [Notes and restrictions](#notes-and-restrictions)


## Support for dispatchable location information for emergency calling

Microsoft has made changes to support the following:  

- Off-premises devices associated with a Multi-Line-Telephone-System (MLTS) must provide automated dispatchable location information to the appropriate PSAP if technically feasible.

- Enhanced location information may be coordinate-based, and it must consist of the best available location that can be obtained from any available technology or combination of technologies at reasonable cost.

- Allow users to roam without being required to constantly update their location.

To support these requirements, Microsoft is using information and location services provided by:

- The respective operating systems
- Emergency calling routing partners
- End users

## Enhancements to location requests

The following enhancements have been made to location requests:

- A new setting in Teams Calling Policy that enables the off-premises location experience.

- Teams clients will continue to send location requests to the service with IP address, BSSID, and LLDP network information.

- If given permission, location requests will now include geo codes from the operating system.

- The service returns a single emergency address with the following precedence:

   - Derived from the tenant-admin-defined emergency addresses associated with either the IP address, BSSID, or LLDP.
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
|  Emergency address derived from geo codes and edited and confirmed by the user. | Screened and Transferred to PSAP. |
| Emergency address edited from scratch and confirmed by the user. | Screened and Transferred to PSAP. |
| Emergency address edited by map string match and confirmed by the end user.
| Direct to PSAP. |
| Emergency address statically assigned to the user/number. | Screened and Transferred to PSAP. |
| Null |  Screened and Transferred to PSAP. |

### Connecting to a new network

- If an admin-defined dynamic location is returned from the service, then this location is used.  A user is not allowed to change the location.

- If an admin-defined dynamic location is NOT returned from the service AND Teams had NOT obtained geo codes, then an end user is allowed to enter an emergency address which is saved with reference to the connected network.

- If an admin-defined dynamic location is NOT returned from the service AND Teams HAD obtained geo codes, the emergency address derived from the geo codes is returned from the service. The end user is allowed to edit this address, which is then saved with reference to the connected network.

Note that while safeguards are in place, automatic geo code based addresses are not going to be precisely accurate.  (DO WE NEED TO CLARIFY WHAT THIS MEANS?  HOW NOT ACCURATE ARE THEY?)

### Connecting to a known network  

- If an admin-defined dynamic location is returned from the service, then this location is used.  A user is not allowed to change the location.

- If an admin-defined dynamic location IS NOT returned from the service, the location that was previously saved with the associated connected network will be used. A user can edit this location if necessary.

- It is possible to save a location against many BSSID’s, such as might be present in an office building. BUT MICROSOFT DOES NOT RECOMMNEND DOING THIS?  ie NOT PRACTICAL?

## Enable end users to configure their emergency address

Teams users who are working at home--outside of the defined emergency addresses on the corporate network--can now configure their emergency address in Microsoft Teams.   

The emergency address is stored locally on the device and used when the user makes an emergency call.

On the Calls tab, the user can enter the emergency address and display the address after it is set. Teams uses the appropriate geo location services to assist the user in entering their emergency address.

To enable this feature for your end users, you must configure the 
TeamsEmergencyCallingPolicy for the user and set the ExternalLocationLookupMode parameter to Enabled.

For example...

``` PowerShell
New-CsTeamsEmergencyCallingPolicy -Identity E911WFH -ExternalLocationLookupMode Enabled
```

```PowerShell
Grant-CsTeamsEmergencyCallingPolicy -PolicyName E911WFH -Identity user@contoso.com
```

Please note that setting the ExternalLocationLookupMode parameter is currently only available via the Teams PS module.




## Notes and restrictions

Please keep the following in mind:

- The WFH experience described is for Teams desktop on Windows and Mac.

- Teams phones do not support the WFH experience.

- Teams mobile supports automatic location detection but not the user entered experience described.

- Privacy settings can conflict with automatic location detection - Mobile Device Management systems can be leveraged.

- Teams Emergency Policy will support a customizable disclaimer.

- The location refresh timer is approximately two minutes when roaming between networks.














DRAFT


ensure that “dispatchable location” information is conveyed with 911 calls so that first responders can more quickly locate the caller. Dispatchable location information includes the street address of the caller and additional information, such as room or floor number, necessary to adequately locate the caller.


RAY BAUM’s Act is broad in scope, but the aspect most commonly focused on is Section 506 which refers to the rules adopted by the FCC requiring enterprises utilizing multi-line telephone systems (MLTS) to provide automated dispatchable location for all 911 calls.

Dispatchable location information provided to the public safety answering point (PSAP) includes a valid civic address, plus other information such as building, floor, suite, or room number “necessary to adequately identify the location of the calling party.” Dispatchable location can include “dynamic” or “nomadic” location information or more granular-level “fixed” location information.





Regardless of the [PSTN connectivity option](pstn-connectivity.md) you choose&mdash;Microsoft Calling Plans, Operator Connect, or Direct Routing&mdash;emergency locations can be associated with a phone number.



RAY BAUM’s Act is broad in scope, but the aspect most commonly focused on is Section 506 which refers to the rules adopted by the FCC requiring enterprises utilizing multi-line telephone systems (MLTS) to provide automated dispatchable location for all 911 calls.


## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Add, change, or remove a place for an emergency location in your organization](add-change-remove-emergency-place-organization.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)