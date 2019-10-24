---
title: Manually submit a port order
ms.author: tonysmit
author: tonysmit
manager: serdars
ms.reviewer: mikedav, roykuntz, jastark
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: M365-voice
audience: Admin
appliesto:
- Microsoft Teams
localization_priority: Normal
f1keywords:
ms.custom:
- Calling Plans
description: Learn how to manually submit a port order request.
---

# Manually submit a port order

If you have service numbers for dial-in conferencing bridges, auto attendants or other service numbers, toll-free phone numbers or if you have more than 999 user (subscriber) phone numbers that you want to transfer to Microsoft Teams, you need to [manage phone numbers for your organization](../manage-phone-numbers-for-your-organization).

In some countries and regions, you also have to manually submit a service request if you want to get phone numbers, release the numbers, or change addresses. To see what's required for each country and region or to learn more about number porting, see [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization). 

Use the steps in this article to manually create and submit a port order in scenarios where you can't do so by using the [porting wizard in the Microsoft Teams admin center](transfer-phone-numbers-to-teams.md). 

## Manually create and submit a port order

### If your organization has 150 or less users

#### Submit a service request in the Microsoft 365 admin center

1. In the left navigation of the Microsoft 365 admin center, go to **Support** > **New service request**.  If you don't see **Support** listed, add it by going to **Customize navigation** in the left navigation, and then select the **Support** check box.
2. In the **Need help?** pane, select **Contact support**.
3. In the **Contact support** pane, do the following:

    1. Enter a title (for example, Port order request) and description for your request, confirm your phone number and email address, and select your preferred contact method.
    2. Under **Attachments**, click **Add a file**, and then upload your completed [Letter of Authorization (LOA)](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md#letters-of-authorization-loas-for-transferring-numbers).
    3. Click **Contact me**.

#### Send your Letter of Authorization directly to the PSTN service desk

Download the [Letter of Authorization (LOA)](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md#letters-of-authorization-loas-for-transferring-numbers), complete the form, and then send it to the [PSTN service desk](../manage-phone-numbers-for-your-organization/contact-pstn-service-desk.md) for your region:

    - In the U.S., [send your request](mailto:ptn@microsoft.com).
    - In Europe, [send your request](mailto:ptneu@microsoft.com).
    - In Asia, [send your request](mailto:ptnapac@microsoft.com).

### If your organization has more than 150 users

1. Sign in as an administrator to Office 365 with your work or school account.
    
2. In the admin center, in the left navigation, click **Support** > **New service request**.
    
3. Under **Service requests**, click **Add**.
    
4. On the **Create a service request** page, click **Online collaboration**.
    
5. On the **Identify the issue** page, select and enter in the following:
    
   - **Feature:** Select **Domestic Calling Plan** and/or **Domestic and International Plan**.
    
   - **Symptom:** Enter **Emergency Calling**.
    
   - **Issue summary:** Enter **Address validation**.
    
   - **Issue details:** Enter any details about the address(s) you want to validate such as the:
    
      - Street number
    
      - Street name
    
      - Town or city
    
      - Country or region
    
     > [!IMPORTANT]
     > **Put the country/region where we offer Calling Plans in Office 365 that you are trying to validate an emergency address in when you are assigning phone number.**
  
      - Postal or zip code
    
6. Click **Next** page, click **Yes, continue** to continue.
    
7. On the **Add details** page, select and enter the following:
    
   - **Is your service unavailable?** Select **No**.
    
   - **How many users are affected?** Select **Some users**.
    
   - **Enter an email address of someone affected by this issue** or leave blank.
    
   - **Select Domain(s) you want to list**
    
   - **Attach a file** if you have multiple addresses you need validated.
    
   - Click **Next**.
    
   - Enter your contact phone number.
    
8. Review the information, and then click **Submit request**.
    
> [!TIP]
> The reference number will be listed on the **Service requests** page in the Microsoft 365 admin center.
  
## What else should you know about number porting?

- To use Calling Plans you must purchase and assign licenses to your users. See [Teams add-on licensing](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md).
    
- You must assign the new phone numbers you have to each of your users. See[Assign, change, or remove a phone number for a user](../assign-change-or-remove-a-phone-number-for-a-user).

## Related topics

- [What's a port order?](port-order-overview.md)
- [Different kinds of phone numbers used for Calling Plans](../different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md)
- [Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
