---
title: "Support for dispatchable location information"
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
audience: Admin
appliesto:
- Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- NOCSH
description: "Learn how MIcrosoft supports dispatchable location information to support emergency calling. "
ms.custom: seo-marvel-mar2020
---

# Dispatchable location information

This article describes Microsoft's support for ensuring that a caller's location information sent to the Public Safety Answering Point (PSAP) is accurate regardless of the caller's location--onsite or working from home.

In addition to 

In particular, Microsoft has made changes to support the following:  

- Off-premises devices associated with an Multi-Line-Telephone-Syste (MLTS) must provide to the appropriate PSAP automated dispatchable location if technically feasible

- Enhanced location information may be coordinate-based, and it must consist of the best available location that can be obtained from any available technology or combination of technologies at reasonable cost.”

Goals:

Provide the most precise emergency location possible for Teams users at all times

Allow users to roam without  being required to constantly update their location – doing so is not realistic

Relies upon:

Location services provided by the respective operating systems
Our emergency calling routing partners
The end users

Enhancements to location requests;

- A new setting in Teams Calling Policy enables the off premise location experience

- Teams clients will continue to send location requests to the service with IP address, BSSID, and LLDP network information

- If given permission, will now include geo codes from the operating system

- Service returns a single emergency address with the following precedence:
   - Derived from tenant admin defined emergency addresses associated with either IP Address, BSSID, or LLDP 
   - Derived from the geocodes (if available)
   - Derived from the user/phone number when statically assigned
   - If no match, then null

## Location logic 

### Connecting to a new network

- If an admin defined dynamic location is returned from the service, then it is used – a user is not allowed to change it
- If an admin defined dynamic location is NOT returned from the service AND Teams had NOT obtained geo codes
- End user is allowed to enter an emergency address which is saved with reference to the connected network
- If an admin defined dynamic location is NOT returned from the service AND Teams HAD obtained geo codes, the emergency address derived from the geo codes is returned from the service 
   - End user is allowed to edit/correct this address which is then saved with reference to the connected network
- Automatic geo code based addresses are not going to be precisely accurate – safeguards are in place

### Connecting to a known network  

- If an admin defined dynamic location is returned from the service, then it is used – a user is not allowed to change it
- Else the location which had previously been saved with the associated connected network will be used – a user can remote/edit this if necessary
- It is possible to save a location against many BSSID’s such as might be present in an office building – not particularly practical however

## Emergency address classification and routing

| Type of emergency address | Emergency routing method |
| :------------| :-------|
| Emergency address defined by administrator | Direct to PSAP |
| Emergency address derived from geo codes without confirmation for accuracy by the user | Screened and Transferred to PSAP |
| Emergency address derived from geo codes with confirmation for accuracy by the user | Direct to PSAP |
|  Emergency address derived from geo codes and edited and confirmed by the user | Screened and Transferred to PSAP |
| Emergency address edited from scratch and confirmed by the user | Screened and Transferred to PSAP |
| Emergency address edited by map string match and confirmed by the end user
| Direct to PSAP |
| Emergency address statically assigned to the user/number | Screened and Transferred to PSAP |
| Null |  Screened and Transferred to PSAP |


## Notes

WFH experience described is for Teams desktop on Windows and Mac
Teams mobile supports automatic location detection but not the user entered / confirmed / stored experience described
Teams phones do not support the WFH experience
Privacy settings can conflict with automatic location detection - Mobile Device Management systems can be leveraged
Teams Emergency Policy will support a customizable disclaimer
The location refresh timer is ~2 minutes when roaming between networks














DRAFT


ensure that “dispatchable location” information is conveyed with 911 calls so that first responders can more quickly locate the caller. Dispatchable location information includes the street address of the caller and additional information, such as room or floor number, necessary to adequately locate the caller.


RAY BAUM’s Act is broad in scope, but the aspect most commonly focused on is Section 506 which refers to the rules adopted by the FCC requiring enterprises utilizing multi-line telephone systems (MLTS) to provide automated dispatchable location for all 911 calls.

Dispatchable location information provided to the public safety answering point (PSAP) includes a valid civic address, plus other information such as building, floor, suite, or room number “necessary to adequately identify the location of the calling party.” Dispatchable location can include “dynamic” or “nomadic” location information or more granular-level “fixed” location information.





Regardless of the [PSTN connectivity option](pstn-connectivity.md) you choose&mdash;Microsoft Calling Plans, Operator Connect, or Direct Routing&mdash;emergency locations can be associated with a phone number.

However, depending on your PSTN connectivity option, how you manage emergency locations and location requirements may vary. For more information, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

This article describes how to add, change, or remove an emergency location for your organization. 




## Related topics

- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Add, change, or remove a place for an emergency location in your organization](add-change-remove-emergency-place-organization.md)
- [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)
- [Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)