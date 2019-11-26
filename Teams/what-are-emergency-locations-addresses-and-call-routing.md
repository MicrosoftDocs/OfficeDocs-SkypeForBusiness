---
title: "Plan emergency calling, emergency addresses, emergency call routing, dynamic emergency calling"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 589bf5f5-490a-4215-8588-99bab7d33e31
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Microsoft Teams
localization_priority: Normal
f1keywords: 
  - ms.teamsadmincenter.locations.emergencyaddresses.overview
  - ms.lync.lac.AddressAndLocation
ms.custom: 
  - Calling Plans
  - Direct Routing
description: "Learn about emergency calling, including information about emergency addresses, emergency call routing, and dynamic emergency calling."
---

# Manage emergency calling

This article describes concepts you'll need to know to manage emergency calling--it includes information about emergency addresses, dynamic emergency addresses, and emergency call routing. This article uses the following terminology:

- **Emergency Address** - A civic address--the physical or street address of a place of business for your organization.

  For example, the address  *12345 North Main Street, Redmond, WA 98052* is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller.

- **Place** - Typically a floor, building, wing, or office number. Place is associated with an emergency address to give a more exact location within a building. You can have an unlimited number of places associated with an emergency address. For example, if your organization has multiple buildings, you might want to include place information for each building and for every floor within each building.  

- **Emergency Location** - A location is a civic address--with an optional place. If your business has more than one physical location, it's likely that you'll need more than one emergency location. 

  When you create an emergency address, a unique location ID is automatically created for this address.  If you add a place to an emergency address--for example, if you add a floor to a building address--a location ID is created for the combination of the emergency address and place.  In this example, there will be two location IDs: one for the civic address; one for the joined civic address and associated place.

  When you assign an emergency location to a user or site, it's this unique location ID that's associated with the user or site.

- **Registered address** - An emergency address that is assigned to each Calling Plan user; it is sometimes referred to as a static emergency address or address of record.  (Registered addresses do not apply to Direct Routing users.)

You create emergency addresses for Calling Plan users by using the Teams admin center.  

>[!Note]
>There are some differences in how you manage emergency calling depending on whether you are using Phone System Calling Plans or Phone System Direct Routing for your PSTN connectivity. These considerations are described throughout this article.

## Emergency address validation

To assign an emergency address to a user or to a network identifier, you must ensure that the emergency address is marked as “validated.”  Address validation ensures that the address is legitimate, and that it cannot be modified after it is assigned. 

If you define an emergency address by using the address map search feature in the Teams admin center, the address is automatically marked as validated. You cannot modify a validated emergency address. Therefore, if the format or representation of the address changes, you must create a new address with the updated format.


## Emergency address geo codes

Each emergency address can have a geo code (latitude and longitude) associated with it. These geo codes are used in some countries to assist in routing emergency calls with dynamic locations. 

If you define an emergency address by using the address map search feature in the Teams admin center, the geo code is automatically associated with an emergency address. You can also associate geo codes with an address if you define the address by using PowerShell. However, Microsoft recommends that you create emergency addresses for Calling Plan by using the map search feature in Teams admin center, which will ensure that the addresses are formatted, validated, and have the appropriate geo codes.  

>[!Important]
>To assign an emergency location to a network identifier for dynamic emergency calling, the emergency address must contain an appropriate geo code.


## Considerations for Calling Plans

To find out whether Calling Plans is available in your area, see [Country and region availability for Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md).


### Emergency call enablement

Each Calling Plan user is automatically enabled for emergency calling and is required to have a registered emergency address associated with their assigned telephone number. 

When the location must be associated to the telephone number depends on the country/region:

- In the United States and Canada, for example, an emergency location is required when a number is assigned to a user.

- For other countries--such as in Europe, the Middle East, and Africa (EMEA)--an emergency location is required when you get the phone number from Office 365 or when it's transferred from another service provider or carrier.

### Dynamic emergency calling

Dynamic emergency calling for Microsoft Calling Plans provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) or to notify security desk personnel varies depending on the country of usage of the Teams user.  

At this time, only Calling Plan users in the United States can leverage dynamic locations for routing emergency calls as follows:

- If a Teams client for a United States Calling Plan user dynamically acquires an emergency address within the United States, that address is used for emergency routing instead of the registered address, and the call will be automatically routed to the PSAP in the serving area of the address.

- If a Teams client for a United States Calling Plan user doesn’t dynamically acquire an emergency address within the United States, then the registered emergency address is used to help screen and route the call. However, the call will be screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.

In the United States, you must configure the civic address that is part of the emergency locations that are assigned to network identifiers--and include the associated geo codes. For more information, see [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).


### Emergency call routing

When a Teams Calling Plan user dials an emergency number, how the call is routed to the PSAP depends on the following:

- Whether the emergency address is dynamically determined by the Teams client.

- Whether the emergency address is the registered address associated with the user's phone number.

- The emergency calling network of that country.

  **In the United States:**

  - If a Teams client is located at a tenant-defined dynamic emergency location, emergency calls from that client are automatically routed to the PSAP serving that geographic location. 

  - If a Teams client is not located at a tenant-defined dynamic emergency location, emergency calls from that client are screened by a national call center to determine the location of the caller before transferring the call to the PSAP serving that geographic location.

  - If an emergency caller is unable to update their emergency location to the screening center, the call will be transferred to the PSAP serving the caller's registered address.

  **In Canada, Ireland, and the United Kingdom**, emergency calls are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center. 

  **In France, Germany, and Spain**, emergency calls are routed directly to the PSAP serving the emergency address associated with the number regardless of the location of the caller.

  **In the Netherands**, emergency calls are routed directly to the PSAP for the local area code of the number regardless of the location of the caller.

  **In Australia**, emergency addresses are configured and routed by the carrier partner.

  **In Japan**, emergency calling is not supported.


For more information, see:

- [Calling Plans](calling-plan-landing-page.md)

- [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

- [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

## Considerations for Direct Routing

If Calling Plans are not available in your area or you want to keep your existing carrier, consider [Direct Routing](direct-routing-landing-page.md). For more information, see [Configure Direct Routing](direct-routing-configure.md) and [Manage emergency call routing policies](manage-emergency-call-routing-policies.md).

### Emergency call enablement and configuration

You must define emergency calling policies for Direct Routing users by using the TeamsEmergencyCallRoutingPolicy to define emergency numbers and their associated routing destination. (Note that registered emergency locations are not supported for Direct Routing users.)

You can assign a TeamsEmergencyCallRoutingPolicy to a Teams Direct Routing user account, a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located as follows:

- If a TeamsEmergencyCallRoutingPolicy is associated with the site, then the site policy is used to configure emergency calling.

- If there is no TeamsEmergencyCallRoutingPolicy associated with the site, or if the client is connected at an undefined site, then the TeamsEmergencyCallRoutingPolicy associated with the user account is used to configure emergency calling. 

- If the Teams client is unable to obtain an TeamsEmergencyCallRoutingPolicy, then the user is not enabled for emergency calling.

### Dynamic emergency calling

Teams clients for Direct Routing users can acquire a dynamic emergency address, which can be used to dynamically route calls based upon the location of the caller. For more information, see [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Emergency call routing

The TeamsEmergencyCallRoutingPolicy references an online PSTN Usage, which must have the appropriate Direct Routing configuration to properly route the emergency calls to the appropriate PSTN gateway(s). In particular, you must ensure that there is an OnlineVoiceRoute for the emergency dial string. For more information, see [Configure Direct Routing](direct-routing-configure.md#configure-voice-routing). 

(Note: In Skype for Business Server, the emergency number was prefixed with a “+” which required a voice route to be defined to match “+911” for instance. Teams clients do not prepend the “+” with emergency numbers.)

The ability to dynamically route emergency calls for Direct Routing users varies depending on the emergency calling network within a given country. There are two solutions available:

- Emergency Routing Service Providers (US only) 
- Emergency Location Identification Number (ELIN) gateway applications

#### Emergency Routing Service Providers

In the United States, there are numerous certified Emergency Routing Service Providers (ERSPs) that can automatically route emergency calls based upon the location of the caller.

- If an Emergency Routing Service Provider is integrated into a Direct Routing deployment, emergency calls with a dynamically acquired location will be automatically routed to the Public Safety Answering Point (PSAP) serving that location.

-  Emergency calls without a dynamically acquired location are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center based upon the updated location.

For more information, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).


#### Emergency Location Identification Number (ELIN) applications

Session Border Controllers (SBCs) can include Emergency Location Identification Number (ELIN) applications. If an SBC ELIN application is integrated into a Direct Routing deployment, you must configure the emergency addresses and associated telephone numbers in the ELIN application, and then upload the ELIN records to the emergency calling database in the respective PSTN.  Teams emergency locations with an ELIN identifier must match those within the ELIN application.

When an emergency call with a dynamically acquired location is routed to the appropriate SBC, the ELIN application:

- Parses the emergency location of the caller.
- Matches the location to an ELIN record.
- Substitutes the emergency caller's number with the ELIN phone number.
- Routes the call to the PSAP serving that location, and then the dispatchers obtain the location from the uploaded ELIN record.

Upon a call back to the emergency number, the ELIN application will do the reverse called number substitution to that of the original emergency caller. 

For more information, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).


## Security desk notification

Security desk notification is available with both Microsoft Calling Plans and Phone System Direct Routing.

You use the TeamsEmergencyCallingPolicy to configure who should be notified during an emergency call and how they are notified: chat only, conferenced in and muted, or conferenced in and muted but with the ability to unmute.  You can also specify an external PSTN number of a user or group to call and join the emergency call. 

A TeamsEmergencyCallingPolicy can be granted to a Teams user account, assigned to a network site, or both.  When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If a TeamsEmergencyCallingPolicy is associated with a network site, then the site policy is used to configure security desk notification.

- If there is no TeamsEmergencyCallingPolicy associated with the site, or if the client is connected at an undefined site, then the TeamsEmergencyCallingPolicy associated with the user account is used to configure security desk notification.  

- If the Teams client is unable to obtain an TeamsEmergencyCallingPolicy, then the user is not enabled for security desk notification.

During an emergency call, a security desk is conferenced into the call and the experience of the security desk user is controlled based upon the TeamsEmergencyCallingPolicy. A group chat is started with each security desk member, and the location of the emergency caller is shared via an important message notification.  If a conference option is configured as part of the policy, each security desk user is additionally called as part of the conference.

    
## Related topics

- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies ](manage-emergency-call-routing-policies.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign or change an emergency location for your user](assign-change-emergency-location-user.md)
- [Plan and onfigure dynamic emergency calling](configure-dynamic-emergency-calling.md)