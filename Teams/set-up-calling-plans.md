---
title: "Set up Calling Plans"
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.assetid: 57893158-1acd-44ac-acaf-19f58264a9e0
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365solution-voice
  - m365solution-scenario
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
description: Learn to set up Calling Plans, including view plans available in your region, buy & assign licenses, get phone numbers, and add emergency addresses & locations.
---
# Set up Calling Plans

Calls to other Teams users are free, but if you want your users to be able to call phones outside of your business, get a Domestic Calling Plan, an International Calling Plan, or a Pay-As-You-Go Calling Plan in Microsoft 365 based on your needs. It's easy to set up Calling Plans for your business.  For more information about Calling Plans, see [Which Calling Plan is right for you?](calling-plan-landing-page.md).

## Step 1: Find out if Calling Plans are available in your country/region

Go to [Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md) and select your country or region to get availability information about Calling Plans, as well as information about Audio Conferencing, Teams Phone, toll and toll-free numbers, and Communications Credits.

If Calling Plans are not available for your country or region, see [PSTN connectivity options](pstn-connectivity.md) for all available options.
  
## Step 2: Buy and assign licenses

1. If the Teams Phone feature isn't included in your Microsoft 365 plan, you may need to purchase **Phone System** add-on licenses. After you have **Phone System** licenses, purchase [Calling Plans for Microsoft 365](calling-plans-for-office-365.md). See [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md), and buy the licenses and plan.

    > [!TIP]
    > **Phone System** licenses and Calling Plans in Microsoft 365 go together, so to see the option to purchase Calling Plans, you must first have the **Phone System** licenses.
  
2. First assign the licenses, and then assign a Calling Plan to the people in your organization. See [Assign Microsoft Teams add-on licenses](./teams-add-on-licensing/assign-teams-add-on-licenses.md).

## Step 3: Get phone numbers

There are three ways to get new user numbers:

- **Use the Teams admin center.** For some countries/regions, you can get numbers for your users by using the Teams admin center, see [Getting phone numbers for your users](getting-phone-numbers-for-your-users.md).

- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier to Microsoft 365. For more information, see [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).
  
- **Use a request form for new numbers.** Sometimes (depending on your country/region) you won't be able to get your new phone numbers using the Teams admin center, or you will need specific phone numbers or area codes. If so, you will need to download a form and send it back to us. For more information, see [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

## Step 4: Add emergency addresses and locations for your organization
<a name="bkmk_add_addresses"> </a>

An emergency address must be associated with a phone number. When this association happens can vary among country and regions. For example, in the United States, you need to associate an emergency address when you assign the phone number to the user. In the United Kingdom, you need to associate an emergency address to the phone number when you are getting the phone numbers from Microsoft 365, or when transferring phone numbers from your current service provider.

For information about emergency calling and managing emergency addresses, see [Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md) and [Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md).

## Step 5: Assign an emergency address and a phone number to a user
<a name="bkmk_add_addresses"> </a>

When you are setting up Calling Plans in Microsoft 365, you must assign a phone number and emergency address to each of your users. The emergency address must be created before you can associate it with a phone number. For more information, see [Assign or change an emergency address](assign-change-emergency-location-user.md).

> [!TIP]
> If you add more people to your business right before doing this step, it may take **several hours** for them to appear on the **Voice users** page.

## Step 6: Tell your users about their new phone numbers

Microsoft recommends sending mail or using your business's preferred communication method to tell the people about their new phone numbers.

In **Microsoft Teams**, users can see their phone number by clicking **Calls** in the left navigation. The phone number is shown above the dial pad.

![Screen shot of the options available after clicking Calls.](media/teams-phone-number.png)

## Run a Self-diagnostics tool

Microsoft 365 admin users have access to diagnostics that can be run within the tenant to verify a user is properly configured to make or receive PSTN calls.

> [!NOTE]
>This feature isn't available for Microsoft 365 Government, Microsoft 365 operated by 21Vianet, or Microsoft 365 Germany.

Select Run Tests, as follows. This will populate the diagnostic in the Microsoft 365 Admin Center.
>> [!div class="nextstepaction"]
>> [Run Tests: Teams PSTN](https://aka.ms/TeamsPSTNDiag)

The diagnostic performs a large range of verifications.

## Do you want to automate assigning phone numbers?
<a name="bkmk_add_addresses"> </a>

If you know Windows PowerShell, you can use the following cmdlets to automate assigning phone numbers to your users.
  
- [Get-CsPhoneNumberAssignment](/powershell/module/teams/Get-CsPhoneNumberAssignment): Retrieves the telephone numbers from the tenant.

- [Set-CsPhoneNumberAssignment](/powershell/module/teams/Set-CsPhoneNumberAssignment): Sets the telephone numbers.

To learn more, see [Teams PowerShell Overview](teams-powershell-overview.md).
  
## Related topics

[Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)

[Different kinds of phone numbers used for Calling Plans](different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)

[Manage emergency calling](what-are-emergency-locations-addresses-and-call-routing.md)

[Add, change, or remove an emergency location for your organization](add-change-remove-emergency-location-organization.md)

[Emergency calling terms and conditions](emergency-calling-terms-and-conditions.md)

[Teams: Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
