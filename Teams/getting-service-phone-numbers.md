---
title: "Get service phone numbers for Calling Plans"
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: mikedav, jastark, oscarr, makolomi, julienp
ms.date: 06/07/2024
ms.topic: article
ms.assetid: e434aeb2-af99-40e7-981e-a474f0383734
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
  - ContentFreshnessFY24
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
  - seo-marvel-mar2020
description: Learn how to get new phone numbers and port or transfer existing numbers for Audio Conferencing, Auto Attendants, and Call Queues (service numbers) for Teams.
---

# Service phone numbers for Calling Plans

In addition to [getting phone numbers for your users](./getting-phone-numbers-for-your-users.md), you can get toll or toll-free phone numbers for services such as Audio Conferencing (for conference bridges), Auto Attendants, and Call Queues (also called service numbers). Service phone numbers have a higher concurrent calling capacity than user or subscriber phone numbers. For example, a service number can handle hundreds of calls simultaneously, whereas a user's phone number can only handle a few calls simultaneously.
  
> [!NOTE]
> You have to first set up Communications Credits before you can get toll-free numbers. To learn more, see [Set up Communications Credits for your organization](./set-up-communications-credits-for-your-organization.md).
  
There are three ways to get service numbers:
  
- **Use the Microsoft Teams admin center.** For some countries and regions, you can get service numbers using the Microsoft Teams admin center. See [Get new service numbers](#get-new-service-numbers).

- **Port your existing numbers.** You can port or transfer existing numbers from your current service provider or phone carrier. You'll need to download and fill out a Letter of Authorization (LOA) and send it back to us. This form can also be used to request new numbers. For more information, see [Transfer phone numbers to Teams](./phone-number-calling-plans/transfer-phone-numbers-to-teams.md) or [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization).  
  
- **Use a request form for new numbers.** Sometimes you won't be able to get your new phone numbers using the Microsoft Teams admin center, or you'll need specific phone numbers or area codes. If so, you'll need to download a LOA form and send it back to us. You can also use this form to port or transfer existing numbers from your current service provider or phone carrier. For more information, see [Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization).
  
> [!NOTE]
> Service numbers are needed so you can get a higher concurrent call capacity for a specific number. When you're transferring the number over to us, you can [contact the TNS service desk](manage-phone-numbers-for-your-organization/contact-tns-service-desk.md) to make sure the service number you're transferring has a high concurrent call capacity.
  
## Get new service numbers

To get new service numbers, in the Teams admin center:

1. In the left navigation, go to **Voice** > **Phone numbers**, and then select **Add**.

2. Enter a name for the order and add a description.

3. On the **Location and quantity** page, complete the following steps:
    - Under **Country or region**, select a country or region.
    - Under **Number type**, select the type of service number you want.
    - Under **Location**, select a location. If you need to create a new location, select **Add a location**.
    - Under **Area code**, select an area code. 
    - Under **Quantity**, enter the number of numbers you want for your organization, and then select **Next** to select your numbers.

4. Select the numbers you want. You have 10 minutes to select your phone numbers and place your order. If you take more than 10 minutes, the phone numbers will be returned to the pool of numbers.

5. When you're ready to place your order, select **Place order**.

## Port or transfer existing service numbers

To transfer your phone numbers from your current service provider or carrier to Teams, you can use the porting wizard in the Microsoft Teams admin center. Follow the steps in [Transfer phone numbers to Teams](./phone-number-calling-plans/transfer-phone-numbers-to-teams.md).

If you experience issues with the porting wizard, you can [manually submit a port order](phone-number-calling-plans/manually-submit-port-order.md) or go to [Manage phone numbers for your organization](manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md), select your country or region, and then download a Letter of Authorization (LOA). You'll have to submit separate port orders for each type of service number (for example, toll vs. toll-free) you'll be transferring by using an LOA. In the LOA, you must select the correct type of service number. Make sure you specify you're transferring a service number (and not a user or subscriber number), or the concurrent calling capacity may not be enough to handle call volumes.  

> [!NOTE]
> For more information about LOAs to port/transfer existing phone numbers and additional documentation requirements, see [Manage phone numbers for Calling Plan](/microsoftteams/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization).
>
>To port/transfer 999 or fewer phone numbers for your users, upload the completed and signed LOAs in the Microsoft Teams admin center for further processing. You can also purchase extra phone numbers in the Microsoft Teams admin center.
>
> To port/transfer more than 999 phone numbers or if you experience issues with the porting process in the Microsoft Teams admin center, you can [manually submit a port order](/microsoftteams/phone-number-calling-plans/manually-submit-port-order) to the TNS Service Desk for your region.

## View the phone numbers for your organization

In the Teams admin center, in the left navigation, go to **Voice** > **Phone numbers** to view the numbers for your organization, including location, number type, and status information.

## Assign service phone numbers

After you get your service numbers, assign each number to an Audio Conferencing bridge. See [Change the phone numbers on your Audio Conferencing bridge](./change-the-phone-numbers-on-your-audio-conferencing-bridge.md).

## Related articles

[Here's what you get with Phone System](./here-s-what-you-get-with-phone-system.md)

[Transferring phone numbers common questions](./phone-number-calling-plans/port-order-overview.md)

[Different kinds of phone numbers used for Calling Plans](./different-kinds-of-phone-numbers-used-for-calling-plans.md)

[Manage phone numbers for your organization](/microsoftteams/manage-phone-numbers-for-your-organization)

[Country and region availability for Audio Conferencing and Calling Plans](./country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
