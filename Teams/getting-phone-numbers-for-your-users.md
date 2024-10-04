---
title: "Get phone numbers for your users"
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: mikedav, roykuntz, jastark
ms.date: 08/29/2023
ms.topic: article
ms.assetid: aa2ec464-3481-4bbb-8c14-e13e18093df5
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
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
description: "Learn how to get new, port, or transfer existing numbers for Teams, and how to show the changes to your users."
---

# Get phone numbers for your users

Before you can set up users in your organization to make and receive phone calls, you must get phone numbers for them.
  
There are three ways to get user numbers:

- **Use the Microsoft Teams admin center.** For some countries and regions, you can get numbers for your users using the Microsoft Teams admin center. See [Get new phone numbers for your users](#get-new-phone-numbers-for-your-users).

- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier. For more information, see [Transfer phone numbers to Teams](./phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization).  
  
- **Use a request form for new numbers.** Sometimes (depending on your country or region) you won't be able to get your new phone numbers using the Microsoft Teams admin center or you'll need specific phone numbers or area codes. For more information, see [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization).
  
> [!NOTE]
> If you need help setting up phone numbers for your organization, [contact Support Contact for Business Products - Admin Help](/microsoft-365/admin/contact-support-for-business-products).

## Get new phone numbers for your users

**Using the Microsoft Teams admin center**

You must be a Teams service admin to make these changes. See [Use Teams administrator roles to manage Teams](./using-admin-roles.md) to read about getting admin roles and permissions.

1. Sign into the [Microsoft Teams admin center](https://admin.teams.microsoft.com).

2. In the left navigation, go to **Voice** > **Phone numbers**, and then select **Add**.

3. Enter a name for the order and add a description.

4. On the Location and quantity page, do the following:
    1. Under **Country or region**, select a country or region.
    1. Under **Number type**, select **User (subscriber)**.
    1. Under **Operator**, select an operator.
    1. Under **Quantity**, enter the number of numbers that you want for your organization.
    1. Under **Search for new numbers**, select a location by searching for city name, area code, or postal code. If you need to create a new location, select **Add a location**.
    1. Under **Area code**, select an area code.
    1. Select **Next** to select your numbers.

5. Select the numbers you want. You have 10 minutes to select your phone numbers and place your order. If you take more than 10 minutes, the phone numbers will be returned to the pool of numbers.

6. When you're ready to place your order, select **Place order**.

    > [!IMPORTANT]
    > The number of phone numbers for users (subscribers) is equal to the total number of **Domestic Calling Plan** and **International Calling Plan** licenses you have assigned multiplied by 1.1, plus 10 additional phone numbers. For example, if you have 50 users in total with a Domestic Calling Plan and/or International Calling Plan, you can acquire **65** phone numbers **(50 x 1.1 + 10)**. Note that if you have a Pay-As-You-Go Calling Plan, you can only acquire 1 phone number per license assigned.
    >
    > For details, see [How many phone numbers can you get?](./how-many-phone-numbers-can-you-get.md). If you need to get more phone numbers than this, [contact Support Contact for Business Products - Admin Help](/microsoft-365/admin/contact-support-for-business-products).
  
## Port or transfer phone numbers from your service provider or phone carrier
  
- If you need 999 or fewer phone numbers for your users, use the porting wizard in the Microsoft Teams admin center. Follow the steps in [Transfer phone numbers to Teams](./phone-number-calling-plans/transfer-phone-numbers-to-teams.md). If you need assistance with this process, you can [manually submit a port order](phone-number-calling-plans/manually-submit-port-order.md) or see [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization) to download the correct Letter of Authorization (LOA).

- If you need to port more than 999 phone numbers, you can [manually submit a port order](phone-number-calling-plans/manually-submit-port-order.md) or see [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization) to download the correct Letter of Authorization (LOA). Complete and sign the LOA documents, and then contact [the TNS service desk](manage-phone-numbers-for-your-organization/contact-tns-service-desk.md) for your region.

> [!NOTE]
> For more information about LOAs to port/transfer existing phone numbers and additional documentation requirements, see [Manage phone numbers for Calling Plan](/microsoftteams/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization).
>
>To port/transfer 999 or fewer phone numbers for your users, upload the completed and signed LOAs in the Microsoft Teams admin center for further processing.
>
> To port/transfer more than 999 phone numbers or if you experience issues with the porting process in the Microsoft Teams admin center, you can [manually submit a port order](/microsoftteams/phone-number-calling-plans/manually-submit-port-order) to the TNS Service Desk for your region.

## View the phone numbers for your organization

**Using the Microsoft Teams admin center**

In the left navigation of the admin center, go to **Voice** > **Phone numbers** to view the numbers for your organization, including number provider, location, number type, and status information.

**Using the Teams PowerShell cmdlet**

Use [Get-CsPhoneNumberAssignment](https://learn.microsoft.com/en-us/powershell/module/teams/get-csphonenumberassignment) cmdlet to quickly view a list of upto 500 phone numbers in PowerShell. You can also download the full list of all the acquired phone numbers using Teams PowerShell cmdlet [Export-CsAcquiredPhoneNumber](https://learn.microsoft.com/en-us/powershell/module/teams/export-csacquiredphonenumber).
  
## Assign phone numbers to users

After you get your phone numbers, you'll need to assign a number to each of your users. For more information, see [Manage phone numbers for users](./assign-change-or-remove-a-phone-number-for-a-user.md).

This video shows the steps to assign a phone number to a user.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RW1ccJJ?autoplay=false]

## Related articles

[Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)

[Different kinds of phone numbers used for Calling Plans](./different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Emergency Calling disclaimer label](https://download.microsoft.com/download/9/9/0/990e24c1-eb49-4b52-9306-dbd4c864ed91/emergency-calling-label-(en-us)-(v.1.0).zip)
