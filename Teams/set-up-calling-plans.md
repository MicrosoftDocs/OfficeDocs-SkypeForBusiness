---
title: Set up Microsoft Calling Plans
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: roykuntz, jastark
ms.date: 09/24/2024
ms.topic: article
ms.assetid: 57893158-1acd-44ac-acaf-19f58264a9e0
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365solution-voice
  - m365solution-scenario
  - m365initiative-voice
  - highpri
  - Tier1
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords: 
  - CSH
ms.custom: 
  - Calling Plans
  - LIL_Placement
  - seo-marvel-mar2020
description: Learn how to set up Calling Plans, including how to buy & assign licenses, get phone numbers, and add emergency addresses & locations.
---
# Set up Microsoft Calling Plans

This article describes how to set up Microsoft Calling Plans with Teams Phone. This solution is the simplest option that connects Teams Phone to the Public Switched Telephone Network (PSTN) for external calling. With this option, **Microsoft acts as your PSTN carrier**.

This article assumes that you already have Teams Phone licenses for your users, which is a requirement for purchasing Calling Plans. If you do not have a Teams Phone license, see [Set up Teams Phone](setting-up-your-phone-system.md) and [Microsoft Teams add-on licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

For more information about all Microsoft Calling Plan options, see [Calling Plans for Teams](calling-plans-for-office-365.md).

For more information about Teams Phone, see [What is Teams Phone](what-is-phone-system-in-office-365.md).

## Step 1: Find out if Calling Plans are available in your country

Go to [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md) and select your country to get availability information about Calling Plans.

If Calling Plans aren't available in your country, see [PSTN connectivity options](pstn-connectivity.md) for other available PSTN connectivity options.
  
## Step 2: Buy and assign licenses

1. After you buy and assign **Teams Phone** licenses, you can purchase [Calling Plans for Teams Phone](calling-plans-for-office-365.md). For more information, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
  
2. Assign a Calling Plan license to the people in your organization. See [Assign Microsoft Teams add-on licenses](./teams-add-on-licensing/assign-teams-add-on-licenses.md).

   If you purchase a Pay-As-You-Go Calling Plan, you may need to purchase Communication Credits. To determine if you need to purchase Communication Credits, see [How to fund a Pay-As-You-Go Calling Plan](calling-plans-for-office-365.md#how-to-fund-a-pay-as-you-go-calling-plan).

## Step 3: Get phone numbers

There are three ways to get new user numbers:

- **Use the Teams admin center.** For some countries/regions, you can get numbers for your users by using the Teams admin center, see [Get phone numbers for your users](getting-phone-numbers-for-your-users.md).

- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier to Microsoft 365. After you port your phone numbers to Teams, Microsoft will become your service provider and will bill you for those phone numbers. For more information, see [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md).
  
- **Use a request form for new numbers.** Sometimes (depending on your country) you won't be able to get your new phone numbers using the Teams admin center, or you'll need specific phone numbers or area codes. If so, you'll need to download a form and send it back to us. For more information, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).


## Step 4: Add emergency addresses and locations for your organization
<a name="bkmk_add_addresses"> </a>

An emergency address must be associated with a phone number. When this association happens can vary among countries. For example, in the United States, you need to associate an emergency address when you assign the phone number to the user. In the United Kingdom, you need to associate an emergency address to the phone number when you're getting the phone numbers from Microsoft 365, or when transferring phone numbers from your current service provider.

For information about emergency calling and managing emergency addresses, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md).

## Step 5: Assign an emergency address and a phone number to a user
<a name="bkmk_add_addresses"> </a>

You must assign a phone number and an emergency address to each of your users. The emergency address must be created before you can associate it with a phone number. For more information, see [Manage emergency locations](assign-change-emergency-location-user.md) and [Manage phone numbers for users](assign-change-or-remove-a-phone-number-for-a-user.md).

> [!TIP]
> If you add more people to your business right before doing this step, it may take **several hours** for them to appear on the **Voice users** page.

## Step 6: Tell your users about their new phone numbers

Microsoft recommends sending mail or using your business's preferred communication method to tell the people about their new phone numbers.

In **Microsoft Teams**, users can see their phone number by selecting **Calls** in the left navigation. The phone number is shown above the dial pad.

## Run a Self-diagnostics tool

Microsoft 365 admin users have access to diagnostics that can be run within the tenant to verify a user is properly configured to make or receive PSTN calls.

> [!NOTE]
>This feature isn't available for Microsoft 365 Government, Microsoft 365 operated by 21Vianet, or Microsoft 365 Germany.

Select Run Tests, as follows. This will populate the diagnostic in the Microsoft 365 Admin Center.
>> [!div class="nextstepaction"]
>> [Run Tests: Teams PSTN](https://aka.ms/TeamsPSTNDiag)

The diagnostic performs a large range of verifications.
  
## Related articles

- [Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)
- [Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)
- [Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)
- [Teams: Emergency Calling disclaimer label](https://download.microsoft.com/download/9/9/0/990e24c1-eb49-4b52-9306-dbd4c864ed91/emergency-calling-label-(en-us)-(v.1.0).zip)
