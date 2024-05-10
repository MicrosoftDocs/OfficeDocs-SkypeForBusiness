---
title: Transfer phone numbers to Microsoft Teams
author: CarolynRowe
ms.author: crowe
manager: pamgreen
ms.reviewer: parththakkar
ms.date: 03/26/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
audience: Admin
f1.keywords:
- NOCSH
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - highpri
  - Tier1
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to use the porting wizard to transfer your phone number from your current service provider to Microsoft Teams.
ms.custom: seo-marvel-mar2020
---

# Transfer phone numbers to Microsoft Teams

This article is for administrators and IT professionals. The article describes how to transfer phone numbers from your current service provider to Microsoft Teams. This article applies to Microsoft Calling Plans and services.

To transfer your phone numbers, you can use the porting step-by-step guide in the Microsoft Teams admin center. After you port your phone numbers to Teams, Microsoft becomes your service provider. For more information, see [How many phone numbers can you get?](../how-many-phone-numbers-can-you-get.md)

Before you start, review the information in [What's a port order](port-order-overview.md). If you have any of the following types of numbers that you need to transfer to Teams, you'll need to download the correct forms and send them to us:

- Dial-in conferencing bridges
- Auto attendants or other service numbers
- Toll-free phone numbers
- More than 999 user (subscriber) phone numbers that you need to transfer to Teams

For more information about submitting the necessary forms, see [Manage phone numbers for Calling Plans and services](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

> [!NOTE]
> We process port orders for transferring phone numbers only on United States business days and not on public holidays or weekends.
>
> Porting availability for Toll-free phone numbers may vary by country and region. For more information, see your [country or region specific articles](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md).

## Create a port order and transfer your phone numbers to Teams

1. In the left navigation of the Microsoft Teams admin center, go to **Voice** > **Phone numbers**. Select **Numbers**, and then select **Port** to start the porting wizard.

2. Review the information on the **Get started** page, and then when you're ready, select **Next**.

3. On the **Select location and number type** page, specify the following, and then select **Next**:

    - **Country or region**: Country or region where you're getting numbers.
    - **Phone number type**: Type of number, such as geographic or toll-free numbers.
    - **Numbers assigned to**: What the numbers are assigned to. For example, users, or conferencing or voice features.

4. On the **Add account information** page, complete the following, and then select **Next**.

    > [!NOTE]
    > The information displayed on this page is determined by the country or region and number type. Each country and region has different regulations on the information that's required to port numbers. What you see on this page may be different from what's described here.

    - **Order details**: 
        - **Order name**: Name of your order
        - **Notification emails**: Email addresses to receive order notifications. If you enter multiple email addresses, separate each with a semicolon.
        - **Transferred date**: Transfer date issued by your current service provider.
    - **Phone number details**
        - **Port type**: Whether you're doing a full-port to transfer all your numbers or a partial-port to transfer some of your numbers.
    - **Person requesting details**  
        - Your organization name and contact details of the person requesting the transfer.
    - **Current provider's details**
        - **Billing telephone number (BTN)**: Your BTN in E.164 format, which requires a + sign to prepend the number. For example, for a North America number, use +1XXXYYYZZZZ format.
        - Other details including the name of your current service provider, your account number, and your service address.
            
5. On the **Add numbers** page, select **Select a file**, browse to and select the CSV file that contains the phone numbers that you want to transfer, and then select **Next**.  

    > [!NOTE]
    > The CSV file must have only one column with a header named **PhoneNumber**. Each phone number must be on a separate row and can be digits only or in E.164 format.

6. On the **Complete your order** page, select **Upload a signed Letter of Authorization** to upload a scanned copy of the signed Letter of Authorization (LOA).

    If you haven't already downloaded and signed the LOA, do the following:
    
    1. Select **Download the template** to download the LOA for your country or region. 
    2. Print the LOA.
    3. Have the LOA signed by the person who is authorized to make changes to the account.
    4. Scan the signed LOA, and then select **Upload a signed Letter of Authorization** to upload it.

7. Review your order details, and then select **Submit**. You must submit the order for it to be processed.

For more information about LOAs to port/transfer existing phone numbers and additional documentation requirements, see [Manage phone numbers for Calling Plan](/microsoftteams/manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization).
    
To port/transfer more than 999 phone numbers, or if you experience issues with the porting process in the Microsoft Teams admin center, you can [manually submit a port order](/microsoftteams/phone-number-calling-plans/manually-submit-port-order) to the TNS Service Desk for your region.

## What happens next

When we receive your port order, you'll receive an email that verifies your request. Your request is updated daily, and you'll be notified of its progress and status in email. If your port request is rejected by the carrier, contact the [TNS Service Desk](../manage-phone-numbers-for-your-organization/contact-tns-service-desk.md) for assistance.

To view the status of your port order, in the left navigation of the Microsoft Teams admin center, go to  **Voice** > **Port orders**, and then select **Order history**. Each port order status is listed in the **Status** column. To learn more, see [What's the status of your port orders?](port-order-status.md)


## Report phone number issues

If you notice any issues with the ported numbers within the first 24-48 hours after the port is completed, contact the [TNS Service Desk](../manage-phone-numbers-for-your-organization/contact-tns-service-desk.md). For any issues beyond 48 hours, contact the Microsoft Support Team.

## Related articles

- [What's a port order?](port-order-overview.md)
- [Different kinds of phone numbers used for Calling Plans](../different-kinds-of-phone-numbers-used-for-calling-plans.md)
- [Manage phone numbers for your organization](../manage-phone-numbers-for-your-organization/manage-phone-numbers-for-your-organization.md)
- [Emergency calling terms and conditions](../emergency-calling-terms-and-conditions.md)
- [Emergency Calling disclaimer label](https://download.microsoft.com/download/9/9/0/990e24c1-eb49-4b52-9306-dbd4c864ed91/emergency-calling-label-(en-us)-(v.1.0).zip)
