---
title: Considerations for Direct Routing
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz
ms.date: 05/08/2024
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
ms.custom:
  - Direct Routing
description: "Learn about emergency calling considerations for Teams Phone Direct Routing."
---

# Considerations for Direct Routing

This article describes considerations for emergency calling for Direct Routing users. Before reading this article, make sure you've read emergency calling concepts and definitions in [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

To find out if Direct Routing is the right solution for your business, see [PSTN connectivity options](pstn-connectivity.md) and [Plan Direct Routing](direct-routing-plan.md).

## Emergency call enablement for Direct Routing

For Direct Routing, you define emergency calling policies for users by using a [Teams emergency call routing policy](manage-emergency-call-routing-policies.md) to define emergency numbers and their associated routing destination.

You can assign an emergency call routing policy to a Direct Routing user account, a network site, or both. When a Teams client starts or changes a network connection, Teams performs a lookup of the network site where the client is located as follows:

- If an emergency call routing policy is associated with the site, then the site policy is used to configure emergency calling.

- If there is no emergency call routing policy associated with the site, if the client is connected at an undefined site, or if the dialed number does not match any of the emergency numbers defined in the emergency call routing policy associated with the site, then the emergency call routing policy associated with the user account is used to configure emergency calling.

- If the Teams client is unable to obtain an emergency call routing policy, then the user isn't enabled for emergency calling.

## Dynamic emergency calling for Direct Routing

Dynamic emergency calling for Direct Routing provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to automatically route to the appropriate Public Safety Answering Point (PSAP), or to notify security desk personnel, varies depending on the country/region of the Teams user.

For Direct Routing users, dynamic location for routing emergency calls is supported only in the United States as follows:

- If a Teams client for a United States Direct Routing user dynamically acquires an emergency address within the United States, that address is used for emergency routing instead of the registered address, and the call is automatically routed to the PSAP in the serving area of the address.

- If a Teams client for a United States Direct Routing user doesn't dynamically acquire an emergency address within the United States, then the registered emergency address is used to help screen and route the call. Calls from Common Area Phones route directly to the PSAP. Otherwise, the call is screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.

Dynamic location for routing emergency calls is supported in Canada the same as in the United States with the following exception: all emergency calls are screened nationally before being transferred to the PSAP.

For more information, see [Configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

## Emergency call routing for Direct Routing

The emergency call routing policy for Direct Routing references an online PSTN usage, which must have the appropriate Direct Routing configuration to properly route the emergency calls to the appropriate PSTN gateway(s). In particular, you must ensure that there is an OnlineVoiceRoute for the emergency dial string. For more information, see [Configure Direct Routing](direct-routing-configure.md).

> [!NOTE]
> Teams clients no longer prepend the "+" sign to emergency numbers; that is, +911. Consequently, Teams emergency calls no longer send a "+" preceding the 911 number. Be sure your voice route patterns reflect this change.

The ability to dynamically route emergency calls for Direct Routing users varies depending on the emergency calling network within a given country/region. There are two solutions available:

- [Emergency Routing Service Providers (US only)](#emergency-routing-service-providers)
- [Emergency Location Identification Number applications](#emergency-location-identification-number-applications)

### Emergency Routing Service Providers

In the United States, there are numerous certified Emergency Routing Service Providers (ERSPs) that can automatically route emergency calls based upon the location of the caller.

- If an Emergency Routing Service Provider is integrated into a Direct Routing deployment, emergency calls with a dynamically acquired location are automatically routed to the Public Safety Answering Point (PSAP) serving that location.

- Emergency calls without a dynamically acquired location are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center based upon the updated location.

For more information, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).

### Emergency Location Identification Number applications

Session Border Controllers (SBCs) can include Emergency Location Identification Number (ELIN) applications. If an SBC ELIN application is integrated into a Direct Routing deployment, you must configure the emergency addresses and associated telephone numbers in the ELIN application, and then upload the ELIN records to the emergency calling database in the respective PSTN. Teams emergency locations with an ELIN identifier must match those within the ELIN application.

When an emergency call with a dynamically acquired location is routed to the appropriate SBC, the ELIN application:

- Parses the emergency location of the caller.
- Matches the location to an ELIN record.
- Substitutes the emergency caller's number with the ELIN phone number.
- Routes the call to the PSAP serving that location, and then the dispatchers obtain the location from the uploaded ELIN record.

Upon a call back to the emergency number, the ELIN application will do the reverse called number substitution to that of the original emergency caller.

For more information, see [Session Border Controllers certified for Direct Routing](direct-routing-border-controllers.md).

## Related topics

- [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies](manage-emergency-call-routing-policies.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
- [Plan Direct Routing](direct-routing-plan.md)
