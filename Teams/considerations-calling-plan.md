---
title: Considerations for Calling Plans
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
  - Calling Plans
description: "Learn about emergency calling considerations for Microsoft Calling Plans."
---

# Considerations for Calling Plans

This article describes emergency calling considerations for Microsoft Calling Plan users. Before reading this article, see emergency calling concepts and definitions in [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

To find out if Microsoft Calling Plans are the right solution for your business, see [PSTN connectivity options](pstn-connectivity.md) and [Microsoft Calling Plans for Teams](calling-plans-for-office-365.md).

## Emergency call enablement for Calling Plans

Each Calling Plan user is automatically enabled for emergency calling and is required to have a registered emergency address associated with their assigned telephone number.

When the location is associated to the telephone number depends on the country/region:

- In the United States and Canada, an emergency location is required when a number is assigned to a user.

- For other countries/regions&mdash;such as in Europe, the Middle East, and Africa (EMEA)&mdash;an emergency location is required when you get the phone number from Microsoft 365, or when the number is transferred from another service provider or carrier.

## Dynamic emergency calling for Calling Plans

Dynamic emergency calling for Calling Plans provides the capability to configure and route emergency calls based on the current location of the Teams client. The ability to automatically route to the appropriate Public Safety Answering Point (PSAP), or to notify security desk personnel, varies depending on the country/region of the Teams user.

Dynamic location for routing emergency calls is supported in the United States as follows.

- If a Teams client for a United States Calling Plan user dynamically acquires an emergency address within the United States, that address is used for emergency routing instead of the registered address. The call is automatically routed to the PSAP in the serving area of the address.

- If a Teams client for a United States Calling Plan user doesn't dynamically acquire an emergency address within the United States, then the registered emergency address is used to help screen and route the call. Calls from Common Area Phones will route directly to the PSAP. Otherwise, the call is screened to determine if an updated address is required before connecting the caller to the appropriate PSAP.

Dynamic location for routing emergency calls is supported in Canada the same as in the United States with the following exception: all emergency calls are screened nationally before being transferred to the PSAP.

For more information, see [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md).

## Emergency call routing for Calling Plans

When a Calling Plan user dials an emergency number, how the call is routed to the PSAP depends on the following:

- Whether the emergency address is dynamically determined by the Teams client

- Whether the emergency address is the registered address associated with the user's phone number

- The emergency calling network of that country/region

For example:

**In the United States:**

- If a Teams client is located at a tenant-defined dynamic emergency location, emergency calls from that client are automatically routed to the PSAP serving that geographic location.

- If a Teams client isn't located at a tenant-defined dynamic emergency location and the client isn't a Common Area Phone, emergency calls from that client are screened by a national call center to determine the location of the caller before transferring the call to the PSAP serving that geographic location.

- If an emergency caller is unable to update their emergency location to the screening center, the call is transferred to the PSAP serving the caller's registered address.

**In Canada, Ireland, and the United Kingdom**, emergency calls are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center.

**For information about how emergency calls are routed in all countries/regions**, see [Emergency call routing for different countries](emergency-calling-availability.md).

For more information, see:

- [Calling Plans](calling-plan-landing-page.md)
- [Set up Calling Plans](set-up-calling-plans.md)
- [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

## Related topics

- [Plan and manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Manage emergency calling policies](manage-emergency-calling-policies.md)
- [Manage emergency call routing policies](manage-emergency-call-routing-policies.md)
- [Plan and configure dynamic emergency calling](configure-dynamic-emergency-calling.md)
- [Microsoft Calling Plans for Teams](calling-plans-for-office-365.md)
