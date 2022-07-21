---
title: "Phone numbers and licensing changes"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: jenstr
ms.topic: conceptual
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: 

description: Learn how licensing changes can affect phone number management.
---

# How licensing affects phone number management

This article describes how licensing changes can affect phone number management. 

For general information on managing phone numbers, see [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md).

For general information on Teams add-on liensing, see [Microsoft Teams add-on licenses](/teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

Removing and assigning licenses can affect phone number assignment and impact a user's ability to make and receive Public Switched Telephone Network (PSTN) calls in Microsoft Teams.

## Remove a license

If you have a user with an assigned phone number and you remove one or more of the prerequisites licenses, removing the license will also unassign the phone number from the user. Without an assigned phone number, the user's ability to make and receive PSTN calls in Microsoft Teams is impacted.

Depending on the user's PSTN connectivity option, removing a license has different impacts on the telephony parameters:

- **Removing a Microsoft 365 Calling Plan license from a user with a Calling Plan phone number** will:
  - Copy any value in OnPremLineUri to LineUri
  - Set EnterpriseVoiceEnabled to False
  - Set phone number assignment status to Unassigned in the phone number database


- **Removing a Microsoft 365 Phone System license from a user with an Operator Connect phone number** will:
  - Clear LineUri
  - Set EnterpriseVoiceEnabled to False
  - Set the phone number’s assignment status to Unassigned in the phone number database


- **Removing a Microsoft 365 Phone System license from a user with a Direct Routing phone number** will:
  - Clear LineUri
  - Set EnterpriseVoiceEnabled to False
  - Remove the phone number from the phone number database



## Change a license

If you need to change a license for a user, you need to ensure that the licensing changes are done at the same time. 

If you first remove the old license and save the change, and then add the new license and save that change, the phone number will be unassigned, and the user might lose the ability to make and receive PSTN calls in Microsoft Teams. After the new license has been assigned, you’ll have to assign the phone number again to the user.

For example, assume you want to assign Microsoft 365 E5 license to a user who currently has a Microsoft 365 E3 license. Using the Microsoft 365 admin center, you must add the new license and remove the old license at the same time, and then save the changes once. This method will ensure that the user keeps their assigned phone number and can continue making and receiving PSTN calls in Microsoft Teams. 

If you use PowerShell cmdlets, Set-MsolUserLicense or Set-MgUserLicense, you should  execute the cmdlet once and use both the -AddLicenses and the -RemoveLicenses parameters






