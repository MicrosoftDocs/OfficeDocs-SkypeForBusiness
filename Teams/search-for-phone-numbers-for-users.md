---
title: "Search for telephone numbers for users"
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.reviewer: davlick, roykuntz, jastark
ms.topic: article
ms.assetid: cc22c49a-c644-4151-a2fc-a1474148f8ba
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Skype for Business
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Calling Plans
description: "See how to search for telephone numbers that you can assign to your users, by country or region and city, and specify the quantity of numbers you need."
---

# Search for telephone numbers for users

When you are setting up users in your organization to make and receive telephone calls using Microsoft-supplied telephone numbers, you must first use the **Microsoft Teams admin center** and acquire telephone numbers to be assigned to users. The telephone number you assign to a user will be a telephone number that you have previously acquired for your organization; the number will be listed in the drop-down list when you edit the properties of the user and click **Assign**.
  
Before you can assign Microsoft-supplied telephone numbers to your users, you must use the **Get new numbers** page to search for telephone numbers that are available to you. You can search by **Country (Market)**, **Number type**, and **Location**. You will then see a list of operators that supply numbers in that country.

If you select Microsoft as your operator, you can acquire the numbers from the Teams admin center by entering the quantity of telephone numbers you will need for your users. The page will automatically limit the quantity based on how many you still have available to acquire. If you select an Operator Connect operator, you will be directed to the landing page of your selected operator to complete the number order.

How you acquire and manage telephone numbers differs depending on your PSTN connectivity option: Microsoft Calling Plans, Operator Connect, or Direct Routing.

This article applies to [Microsoft Calling Plans](#search-for-telephone-numbers-for-microsoft-calling-plans) and [Operator Connect](#search-for-telephone-numbers-for-operator-connect). For more information about all options, see [Manage telephone numbers for your organization](/microsoftteams/manage-phone-numbers-landing-page).

## Search for telephone numbers for Microsoft Calling Plans

To search for telephone numbers for your users:
  
1. Go to the **Microsoft Teams admin center**.

2. In the left navigation select **Voice** > **Phone numbers** > **Get new numbers**.
  
    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Teams admin center, you must first buy at least one **Enterprise E5 or E3 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.  

3. On the **Select location and quantity** page, select a location from the **Country (Market)** drop-down list.

4. Select **User** from the **Number type** drop-down list.

5. Depending on the Country (Market) you have selected, you will now have different options available for you to use for locating the telephone numbers you require.  

6. Under **Quantity**, enter the number of phone numbers that you want for your organization, and then click **Next**. You have 10 minutes to select your phone numbers. If you take more than 10 minutes, the numbers will be returned to the pool of phone numbers.

    > [!NOTE]
    > You can see the number of telephone numbers available to you (which is based on the number of licenses), listed next to **Quantity**.
  
7. On the **Get numbers** page, select the telephone numbers you want, click **Acquire numbers**, and then click **Next**.

    > [!IMPORTANT]
    > You can acquire more telephone numbers than you have Microsoft licenses. To determine how many telephone numbers you can acquire, take your number of Microsoft Calling Plan licenses, add 10 percent of the number of licenses, then add 10, and then remove however many you have already acquired. For example, if you have 100 Microsoft **Domestic Calling Plan** and/or **International Calling Plan** licenses, you can reserve 120 telephone numbers, assuming that you have not already acquired some telephone numbers for those 100 users. For more details, see [How many telephone numbers can you get?](./how-many-phone-numbers-can-you-get.md).

8. On the **Confirmation** page, verify your choices, and then click **Place order**.

9. When you return to the **Phone numbers** page, select the telephone number or numbers that you want to assign and then click **Edit** to assign it to a user.

## Search for telephone numbers for Operator Connect

1. Go to the **Microsoft Teams admin center**.

2. In the left navigation select **Voice** > **Phone numbers** > **Get new numbers**.
  
    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Teams admin center, you must first buy at least one **Enterprise E5 or E3 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.  

3. On the **Select location and quantity** page, select a location from the **Country (Market)** drop-down list.

4. Select **User** from the **Number type** drop-down list.

5. Depending on the Country (Market) you have selected, you will now have different options available for you to use for locating the telephone numbers you require. You can filter to show only operators that you have added by selecting **Show my operators**.

6. If you have already provided consent to the operator, you will be directed to the landing page of the operator to complete the order process.

7. If you have not provided consent to the operator, you will be directed to enable your operator on the chosen operator page in the Teams admin center. For more information, see [Enable an operator](operator-connect-configure.md#enable-an-operator).

8. After your order is complete, your operator will upload phone numbers to your tenant, and you can assign them to users.  

## Related topics

[Manage telephone numbers for your organization](manage-phone-numbers-landing-page.md)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Emergency Calling disclaimer label](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/emergency-calling/emergency-calling-label-(en-us)-(v.1.0).zip?raw=true)
