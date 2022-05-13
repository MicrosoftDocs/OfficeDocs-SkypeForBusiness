---
title: Plan and manage emergency calling
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: roykuntz
ms.topic: article
ms.assetid: 589bf5f5-490a-4215-8588-99bab7d33e31
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
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

This article describes concepts you'll need to know to manage emergency calling&mdash;it includes information about emergency addresses, dynamic emergency addresses, and emergency call routing. This article uses the following terminology:

- **Emergency address** - A civic address&mdash;the physical or street address of a place of business for your organization.

  For example, the address *12345 North Main Street, Redmond, WA 98052* is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller.

- **Place** - Typically a floor, building, wing, or office number. Place is associated with an emergency address to give a more exact location within a building. You can have an unlimited number of places associated with an emergency address. For example, if your organization has multiple buildings, you might want to include place information for each building and every floor within each building.  

- **Emergency location** - A location is a civic address&mdash;with an optional place. If your business has more than one physical location, it's likely that you'll need more than one emergency location. 

  When you create an emergency address, a unique location ID is automatically created for this address. If you add a place to an emergency address&mdash;for example, if you add a floor to a building address&mdash;a location ID is created for the combination of the emergency address and place.  In this example, there will be two location IDs: one for the civic address; one for the joined civic address and associated place.

  When you assign an emergency location to a user or site, it's this unique location ID that's associated with the user or site.

- **Registered address** - An emergency address that is assigned to each user. A registered address is sometimes referred to as a static emergency address or address of record. (Currently, registered addresses are not supported for Direct Routing. Check back soon for updates.)

>[!Note]
>There are some differences in how you manage emergency calling depending on whether you are using Microsoft Calling Plans, Operator Connect, or Direct Routing for your [PSTN connectivity](pstn-connectivity.md). These considerations are described throughout this article.

## Emergency address validation

To assign an emergency address to a user or to a network identifier, you must ensure that the emergency address is marked as "validated." Address validation ensures that the address is legitimate, and that it cannot be modified after it is assigned. 

If you define an emergency address by using the address map search feature in the Teams admin center, the address is automatically marked as validated. Because you cannot modify a validated emergency address&mdash;if the format or representation of the address changes, you must create a new address with the updated format.


## Emergency address geo codes

Each emergency address can have a geo code (latitude and longitude) associated with it. These geo codes are used in some countries to assist in routing emergency calls with dynamic locations. 

If you define an emergency address by using the address map search feature in the Teams admin center, the geo code is automatically associated with an emergency address. You can also associate geo codes with an address if you define the address by using PowerShell. 

Microsoft recommends that you create emergency addresses by using the map search feature in Teams admin center, which will ensure that the addresses are formatted, validated, and have the appropriate geo codes. 

>[!Important]
>To assign an emergency location to a network identifier for dynamic emergency calling, the emergency address must contain an appropriate geo code.


## Considerations for Calling Plans

The following sections describe how to manage emergency calling for Microsoft Calling Plan users. To find out if Microsoft Calling Plans are the right solution for your business, see [PSTN connectivity options](pstn-connectivity.md).


### Emergency call enablement for Calling Plans

Each Calling Plan user is automatically enabled for emergency calling and is required to have a registered emergency address associated with their assigned telephone number. 

When the location is associated to the telephone number depends on the country/region:

- In the United States and Canada, for example, an emergency location is required when a number is assigned to a user.

- For other countries&mdash;such as in Europe, the Middle East, and Africa (EMEA)&mdash;an emergency location is required when you get the phone number from Microsoft 365, or when it's transferred from another service provider or carrier.


### Dynamic emergency calling for Calling Plans

Dynamic emergency calling for Calling Plans provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) or to notify security desk personnel varies depending on the country of usage of the Teams user.  

Dynamic location for routing emergency calls is supported in the United States as follows. 

- If a Teams client for a United States Calling Plan user dynamically acquires an emergency address within the United States, that address is used for emergency routing instead of the registered address, and the call will be automatically routed to the PSAP in the serving area of the address.

- If a Teams client for a United States Calling Plan user doesn't dynamically acquire an emergency address within the United States, then the registered emergency address is used to help screen and route the call. However, the call will be screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.

Dynamic location for routing emergency calls is supported in Canada the same as in the United States with the following exception: all emergency calls will be screened nationally before being transferred to the PSAP.

For more information, see [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Emergency call routing for Calling Plans

When a Teams Calling Plan user dials an emergency number, how the call is routed to the PSAP depends on the following:

- Whether the emergency address is dynamically determined by the Teams client.

- Whether the emergency address is the registered address associated with the user's phone number.

- The emergency calling network of that country.

For example:

**In the United States:**

- If a Teams client is located at a tenant-defined dynamic emergency location, emergency calls from that client are automatically routed to the PSAP serving that geographic location.

- If a Teams client is not located at a tenant-defined dynamic emergency location, emergency calls from that client are screened by a national call center to determine the location of the caller before transferring the call to the PSAP serving that geographic location.

- If an emergency caller is unable to update their emergency location to the screening center, the call will be transferred to the PSAP serving the caller's registered address.

**In Canada, Ireland, and the United Kingdom**, emergency calls are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center.

**In France, Germany, and Spain**, emergency calls are routed directly to the PSAP serving the emergency address associated with the number regardless of the location of the caller.

**In the Netherlands**, emergency calls are routed directly to the PSAP for the local area code of the number regardless of the location of the caller.

**In Australia**, emergency addresses are configured and routed by the carrier partner.

**In Japan**, emergency calling is not supported.


For more information, see:

- [Calling Plans](calling-plan-landing-page.md)
- [Set up Calling Plans](set-up-calling-plans.md)
- [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

## Considerations for Operator Connect

The following sections describe how to manage emergency calling for Operator Connect users. To find out whether Operator Connect is the right solution for your business, see [PSTN connectivity options](pstn-connectivity.md).

### Emergency call enablement for Operator Connect

Each Operator Connect user is automatically enabled for emergency calling. Emergency calls are routed automatically to the Operator Connect carrier for a given number.

The ability for a tenant admin to set the registered address for an Operator Connect user will depend upon the capabilities assigned to the number when the carrier uploads them into a customers inventory. Based upon this setting, the tenant administrator may or may not be required&mdash;or able&mdash;to set, modify, or delete the emergency location of a user. 

### Dynamic emergency calling for Operator Connect

Dynamic emergency calling for Operator Connect provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) or to notify security desk personnel varies depending on the country of usage of the Teams user. 

Dynamic location for routing emergency calls is supported in the United States as follows. 

- If a Teams client for a United States user dynamically acquires an emergency address within the United States, that address is used for emergency routing instead of the registered address, and the call will be automatically routed to the PSAP in the serving area of the address.

- If a Teams client for a United States user doesn't dynamically acquire an emergency address within the United States, then the registered emergency address is used to help screen and route the call. However, the call will be screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.

Dynamic location for routing emergency calls is supported in Canada the same as in the United States with the following exceptions: all emergency calls will be screened nationally before transferred to the PSAP.

For more information, see [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Emergency call routing for Operator Connect

When a Teams Operator Connect user dials an emergency number, how the call is routed to the PSAP depends on the following:

- Whether the emergency address is dynamically determined by the Teams client.

- Whether the emergency address is the registered address associated with the user's phone number.

- The emergency calling network of that country.

- In the United States and Canada, dynamic routing is part of the carrier’s service. You do not need to procure this service from another service provider.

- If a Teams client is located at a tenant-defined dynamic emergency location:

   - In the United States, emergency calls from that client are automatically routed to the PSAP serving that geographic location.
   - In Canada, all emergency calls will be screened by a national call center before transferring the call to the PSAP serving that geographic location.

- If a Teams client is not located at a tenant-defined dynamic emergency location, emergency calls from that client are screened by a national call center to determine the location of the caller before transferring the call to the PSAP serving that geographic location.

- If an emergency caller is unable to update their emergency location to the screening center, the call will be transferred to the PSAP serving the caller's registered address.


## Considerations for Direct Routing

The following sections describe how to manage emergency calling for Direct Routing users. To find out whether Direct Routing is the right solution for your business, see [PSTN connectivity options](pstn-connectivity.md).

### Emergency call enablement for Direct Routing

For Direct Routing, you must define emergency calling policies for users by using a [Teams emergency call routing policy](manage-emergency-call-routing-policies.md) to define emergency numbers and their associated routing destination. (Currently, registered emergency locations are not supported for Direct Routing users.)

You can assign an emergency call routing policy to a Direct Routing user account, a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located as follows:

- If an emergency call routing policy is associated with the site, then the site policy is used to configure emergency calling.

- If there is no emergency call routing policy associated with the site, if the client is connected at an undefined site, or if the dialed number does not match any of the emergency numbers defined in the emergency call routing policy associated with the site, then the emergency call routing policy associated with the user account is used to configure emergency calling. 

- If the Teams client is unable to obtain an emergency call routing policy, then the user is not enabled for emergency calling.


### Dynamic emergency calling for Direct Routing

Dynamic emergency calling for Direct Routing provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to do automatic routing to the appropriate Public Safety Answering Point (PSAP) or to notify security desk personnel varies depending on the country of usage of the Teams user.

For Direct Routing users, dynamic location for routing emergency calls is only supported in the United States as follows:

-	If a Teams client for a United States Direct Routing user dynamically acquires an emergency address within the United States, that address is used for emergency routing, and the call will be automatically routed to the PSAP in the serving area of the address.

-	If a Teams client for a United States Direct Routing user doesn't dynamically acquire an emergency address within the United States, the call will be screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.

Dynamic location for routing emergency calls is supported in Canada the same as in the United States with the following exception: all emergency calls will be screened nationally before being transferred to the PSAP.

For more information, see [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

### Emergency call routing for Direct Routing

The emergency call routing policy for Direct Routing references an online PSTN usage, which must have the appropriate Direct Routing configuration to properly route the emergency calls to the appropriate PSTN gateway(s). In particular, you must ensure that there is an OnlineVoiceRoute for the emergency dial string. For more information, see [Configure Direct Routing](direct-routing-configure.md). 

> [!NOTE]
> Teams clients no longer prepend the "+" sign in front of emergency numbers; that is, +911. Consequently, Teams emergency calls will no longer be sending a "+" preceding the 911 number. Be sure your voice route patterns reflect this change.

The ability to dynamically route emergency calls for Direct Routing users varies depending on the emergency calling network within a given country. There are two solutions available:

- [Emergency Routing Service Providers (US only)](#emergency-routing-service-providers)
- [Emergency Location Identification Number applications](#emergency-location-identification-number-applications)

#### Emergency Routing Service Providers

In the United States, there are numerous certified Emergency Routing Service Providers (ERSPs) that can automatically route emergency calls based upon the location of the caller.

- If an Emergency Routing Service Provider is integrated into a Direct Routing deployment, emergency calls with a dynamically acquired location will be automatically routed to the Public Safety Answering Point (PSAP) serving that location.

-  Emergency calls without a dynamically acquired location are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center based upon the updated location.

For more information, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).


#### Emergency Location Identification Number applications

Session Border Controllers (SBCs) can include Emergency Location Identification Number (ELIN) applications. If an SBC ELIN application is integrated into a Direct Routing deployment, you must configure the emergency addresses and associated telephone numbers in the ELIN application, and then upload the ELIN records to the emergency calling database in the respective PSTN. Teams emergency locations with an ELIN identifier must match those within the ELIN application.

When an emergency call with a dynamically acquired location is routed to the appropriate SBC, the ELIN application:

- Parses the emergency location of the caller.
- Matches the location to an ELIN record.
- Substitutes the emergency caller's number with the ELIN phone number.
- Routes the call to the PSAP serving that location, and then the dispatchers obtain the location from the uploaded ELIN record.

Upon a call back to the emergency number, the ELIN application will do the reverse called number substitution to that of the original emergency caller. 

For more information, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).


## Security desk notification

Security desk notification is available with both Microsoft Calling Plans, Operator Connect, and Direct Routing.

You use a Teams emergency calling policy (TeamsEmergencyCallingPolicy) to configure who should be notified during an emergency call and how they are notified: chat only, conferenced in and muted, or conferenced in and muted but with the ability to unmute. You can also specify an external PSTN number of a user or group to call and join the emergency call. Note that the PSTN party is not allowed to unmute.

An emergency calling policy can be granted to a Teams user account, assigned to a network site, or both.  When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located:

- If an emergency calling policy is associated with a network site, then the site policy is used to configure security desk notification.

- If there is no emergency calling policy associated with the site, or if the client is connected at an undefined site, then the emergency calling policy associated with the user account is used to configure security desk notification.  

- If the Teams client is unable to obtain an emergency calling policy, then the user is not enabled for security desk notification.

During an emergency call, a security desk is conferenced into the call and the experience of the security desk user is controlled based upon the Teams emergency calling policy. A group chat is started with each security desk member, and the location of the emergency caller is shared via an important message notification.  If a conference option is configured as part of the policy, each security desk user is additionally called as part of the conference.

### Custom emergency disclaimer

Administrators have the ability to add a custom banner in the tenant for their users to enable E911. Users can dismiss the banner when they confirm their address, and the banner will reappear when Teams is restarted. To enable this feature, you would set the **Emergency service disclaimer** under the Teams emergency calling policy and enter a string message to be displayed to users. This field is optional when setting up a custom policy, and the string field is limited to 250 characters.

> [!NOTE]
> Currently, this is configurable using PowerShell with the EnhancedEmergencyServicesDisclaimer policy. In the future this will also be configurable in the Teams admin center.

    
## Related topics

- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies ](manage-emergency-call-routing-policies.md)
- [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)
- [Assign or change an emergency location for your user](assign-change-emergency-location-user.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
