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

How you remove and assign licenses to users can impact a user's ability to make and receive Public Switched Telephone Network (PSTN) calls in Microsoft Teams. This article describes how you can manage licensing changes to ensure your users' ability to make and receive PSTN calls is not impacted.

For general information on managing phone numbers, see [Manage phone numbers for your organization](manage-phone-numbers-landing-page.md). For general information on Teams add-on licensing, see [Microsoft Teams add-on licenses](/teams-add-on-licensing/microsoft-teams-add-on-licensing.md).



## Remove a license

If you have a user with an assigned phone number and you remove one or more of the prerequisites licenses, removing the license will also unassign the phone number from the user. Without an assigned phone number, the user's ability to make and receive PSTN calls in Microsoft Teams is impacted.

Depending on the user's [PSTN connectivity option](pstn-connectivity.md), removing a license has the following impact on telephony parameters:

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

If you need to change a license for a user that involves one of the prerequisite licenses, you should ensure that the licensing changes are made and saved at the same time. This method will ensure that the user keeps their assigned phone number and can continue making and receiving PSTN calls in Microsoft Teams. 

For example, assume you want to assign a Microsoft 365 E5 license to a user who currently has a Microsoft 365 E3 license. 

- If you are using Teams admin center, in the **Licenses and apps** tab on the user details, ensure that the old license is removed and the new license is added before you click **Save changes**. 

- If you are using the PowerShell cmdlets, [Set-MsolUserLicense](/powershell/module/msonline/set-msoluserlicense) or [Set-MgUserLicense](/powershell/module/microsoft.graph.users.actions/set-mguserlicense), execute the cmdlet once and use both the -AddLicenses and the -RemoveLicenses parameters.

(If you remove the old license and save the change, and then add the new license and save the change, the phone number will be unassigned and the user might lose the ability to make and receive PSTN calls in Microsoft Teams. After assigning the new license, you’ll need to re-assign the phone number to the user.)










