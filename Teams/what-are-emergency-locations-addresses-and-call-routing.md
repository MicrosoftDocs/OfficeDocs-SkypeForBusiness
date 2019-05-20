---
title: "What are emergency locations, addresses, and call routing?"
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
- Teams_ITAdmin_Help
- M365-voice
ms.audience: Admin
appliesto:
- Skype for Business 
- Microsoft Teams
localization_priority: Normal
f1keywords:
- ms.lync.lac.AddressAndLocation
ms.custom:
- Calling Plans
description: "Learn what emergency address, location, and emergency call routing are, and how to plan and assign them to your users. "
---

# What are emergency locations, addresses, and call routing?

When you are configuring Calling Plans in Office 365, you have to assign an emergency address to each telephone number when you either get the phone number or assign it to a user to support emergency calling. And before you can assign an emergency address to a phone number, you must create and validate the emergency address. Validation ensures that the emergency address is recognized and that it is in a correct format that can be used by emergency response services. Optionally, you can add a location within the emergency address to provide a more specific location for the user. For example, the emergency location could be a floor, wing, or office that is linked to a specific emergency address. Although emergency address are validated, locations aren't.
  
## What are emergency addresses?

An emergency address is required for active telephone numbers, but when it's required depends on the country/region. In the United States, an emergency address is required when a number is assigned to a user. For other countries, such as in Europe, the Middle East, and Africa (EMEA), an emergency address is required when you get the phone number from Office 365 or when it's transferred from another service provider or carrier.
  
An emergency address may be referred to as a civic address, street address, or a physical address. It is the street or civic address of a place of business for your organization. For example, the address  *12345 North Main Street, Redmond, WA 98052*  is used to route emergency calls to the appropriate dispatch authorities and to assist in locating the emergency caller. It's likely that you will need more than one emergency address if your business has more than one physical business location.
  
Validating an emergency address involves making sure that it is legitimate and correctly formatted for emergency response services. It's possible to create and save an emergency address that isn't validated, but only validated addresses can be associated with a user. Once an emergency address is validated and saved, it can be assigned to a user. If you need to change a saved validated emergency address, you will need to create a new one.
  
## What are emergency locations?

An emergency location is associated with an emergency address to give a more exact location within a building. An emergency location is typically a floor, building wing, or office number where the user is located. You can have an unlimited number of locations associated with an emergency address. 
  
When you assign an emergency address to a user, it is actually a location ID that is referenced when you assign the address. The location ID includes the referenced emergency address (the street or civic address). A default emergency location is included with an emergency address for cases in which in-building locations aren't needed. 
  
## What is emergency call routing?

Emergency addresses and locations are used during the process of routing emergency calls to the appropriate dispatch center when dispatching emergency first responders. When a Teams or Skype for Business user dials an emergency number, how the call is routed to the serving Public Safety Answering Point (PSAP) will vary by country/region. In some countries, such as the United States and the United Kingdom, the calls will first be screened to determine the current location of the user before connecting the call to the appropriate dispatch center. In other countries/regions, calls will be routed directly to the dispatch center serving the phone number associated with the emergency caller.
  
## Create, add, and assign emergency locations and addresses to your users

1. **Plan for emergency locations**. The first step is to plan for your emergency locations. You need to list all of your physical addresses. Then, based on that, determine whether locations for the emergency addresses are needed and if so, what they are. For example, if a business has 3 office buildings each with 4 floors, it is likely that there need to be 3 emergency addresses, with floors 1-4 listed as a location for each.
    
2. **Create and validate your emergency locations**. The next step is to create and validate your emergency addresses. When you create an emergency address, you can validate it. To create an emergency address, see [Add or remove an emergency address for your organization](/SkypeForBusiness/what-are-calling-plans-in-office-365/add-or-remove-an-emergency-address-for-your-organization).
    
    > [!IMPORTANT]
    > Validating a street or civic address involves making sure that it is legitimate and correctly formatted. It is possible that a partially correct emergency address, such as a mistyped name of the city, may still pass validation. The validation process uses all parts of a given address to determine if it contains enough information to route the call to the appropriate emergency dispatch center. If so, it will be returned as validated and then can be assigned to a phone number. 
  
3. **Get phone numbers**. The next step is to get phone numbers for your users. You can do this by getting new phone numbers from Office 365 or by "porting" or transferring your existing phone numbers over to Office 365. To see the complete steps, see [Transfer phone numbers to Office 365](transfer-phone-numbers-to-office-365.md).
    
4. **Assign phone numbers**. The last step is to enable users to make and receive phone calls. To do this, you must assign a phone number to each user. See [Assign, change, or remove a phone number for a user](/microsoftteams/assign-change-or-remove-a-phone-number-for-a-user) to assign a phone number.

> [!NOTE]
> If you need to get more telephone numbers than this, please [contact support for business products - Admin Help](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b)

    
## Related topics
[What is address validation?](/SkypeForBusiness/what-are-calling-plans-in-office-365/what-is-address-validation)

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

[Skype for Business Online: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)

