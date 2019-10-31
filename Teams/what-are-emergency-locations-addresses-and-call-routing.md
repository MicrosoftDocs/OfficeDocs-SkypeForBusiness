---
title: "What are emergency locations, places, and call routing?"
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
description: "Learn what emergency locations, places, and emergency call routing are, and how to plan and assign them to your users. "
---

# What are emergency locations, places, and call routing?

When you configure Calling Plans, you have to assign an emergency location to each phone number either when you acquire the phone number or when you assign it to a user in order to support emergency calling. Before you can assign an emergency location to a phone number, you must add and validate an emergency location. Validation ensures that the emergency location is recognized and that it's in a correct format that can be used by emergency response services. If you want, you can add a place within the emergency location to provide a more specific location for the user. For example, the place could be a floor, wing, or office that's linked to a specific emergency location. Although emergency locations are validated, places aren't.
  
## What are emergency locations?

An emergency location is required for active telephone numbers and when it's required depends on the country/region. In the United States, an emergency location is required when a number is assigned to a user. For other countries, such as in Europe, the Middle East, and Africa (EMEA), an emergency location is required when you get the phone number from Teams or when it's transferred from another service provider or carrier to Teams.
  
An emergency location may be referred to as a civic address, street address, or a physical address with the optional place. It's the street or civic address of a place of business for your organization. For example, the address  *12345 North Main Street, Redmond, WA 98052*  is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller. It's likely that you'll need more than one emergency location if your business has more than one physical business location.
  
Validating an emergency address involves making sure that it's legitimate and correctly formatted for emergency response services. It's possible to add and save an emergency location that isn't validated, but only validated locations can be associated with a user. After an emergency location is validated and saved, you can assign it to a user. To change an emergency location that's saved and validated, you'll need to create a new one.
  
## What are places?

A place is associated with an emergency location to give a more exact location within a building. A place is typically a floor, building wing, or office number where the user is located. You can have an unlimited number of places associated with an emergency address.
  
When you assign an emergency location to a user, it's actually a location ID that's referenced when you assign the location. The location ID includes the referenced emergency address (the street or civic address). A default place is included with an emergency location for cases in which in-building places aren't needed.
  
## What is emergency call routing?

Emergency locations and places are used during the process of routing emergency calls to the appropriate dispatch center when dispatching emergency first responders. When a Teams user dials an emergency number, how the call is routed to the serving Public Safety Answering Point (PSAP) varies by country and region. In some countries, such as the United States and the United Kingdom, the calls are first screened to determine the current location of the user before connecting the call to the appropriate dispatch center. In other countries and regions, calls are routed directly to the dispatch center serving the phone number associated with the emergency caller.
  
## Create, add, and assign emergency locations and places to your users

1. **Plan for emergency locations**. The first step is to plan for your emergency locations. List all your physical addresses. Then, based on that, determine whether places for the emergency locations are needed and if so, what they are. For example, if a business has three office buildings each with four floors, it's likely that there needs to be three emergency locations, with floors one to four listed as a place for each.
    
2. **Add your emergency locations**. The next step is to add your emergency locations. To learn more, see [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md).
    
    > [!IMPORTANT]
    > Validating a street or civic address involves making sure that it's legitimate and correctly formatted. It's possible that a partially correct emergency address, such as a mistyped name of the city, may still pass validation. The validation process uses all parts of a given address to determine whether it contains enough information to route the call to the appropriate emergency dispatch center. If so, it will be returned as validated and then can be assigned to a phone number.
  
3. **Get phone numbers**. The next step is to get phone numbers for your users. You can do this by getting new phone numbers from Office 365 or by "porting" or transferring your existing phone numbers over to Office 365. To see the complete steps, see [Transfer phone numbers to Office 365](transfer-phone-numbers-to-office-365.md).
    
4. **Assign phone numbers**. The last step is to enable users to make and receive phone calls. To do this, you must assign a phone number to each user. See [Assign, change, or remove a phone number for a user](/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user) to assign a phone number.

> [!NOTE]
> If you need to get more phone numbers than this, [contact the PSTN service desk](manage-phone-numbers-for-your-organization/contact-pstn-service-desk.md).

    
## Related topics

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)