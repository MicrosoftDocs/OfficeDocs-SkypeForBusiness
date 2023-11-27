---
title: "Search for telephone numbers for users"
ms.author: crowe
author: CarolynRowe
manager: pamgreen
ms.reviewer: davlick, roykuntz, jastark
ms.date: 11/28/2017
ms.topic: article
ms.assetid: cc22c49a-c644-4151-a2fc-a1474148f8ba
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
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
description: "Learn how to search for telephone numbers that you can assign to your users."
---

# Search for telephone numbers for users

When you're setting up users in your organization to make and receive telephone calls using Microsoft-supplied telephone numbers, you must first use the **Microsoft Teams admin center** and acquire telephone numbers to be assigned to users. The telephone number you assign to a user is a telephone number that you previously acquired for your organization. The number is listed in the drop-down list when you edit the properties of the user and select **Assign**.
  
Before you can assign Microsoft-supplied telephone numbers to your users, you must use the **Get new numbers** page to search for telephone numbers that are available to you. You can search by **Country (Market)**, **Number type**, and **Location**. You'll then see a list of operators that supply numbers in that country.

If you select Microsoft as your operator, you can acquire the numbers from the Teams admin center by entering the quantity of telephone numbers you'll need for your users. The page automatically limits the quantity based on how many you still have available to acquire. If you select an Operator Connect operator, you'll be directed to the landing page of your selected operator to complete the number order.

How you acquire and manage telephone numbers differs depending on your PSTN connectivity option: Microsoft Calling Plans, Operator Connect, Teams Phone Mobile, or Direct Routing.

This article applies to [Microsoft Calling Plans](#search-for-telephone-numbers-for-microsoft-calling-plans), [Operator Connect](#search-for-telephone-numbers-for-operator-connect-or-teams-phone-mobile), and [Teams Phone Mobile](#search-for-telephone-numbers-for-operator-connect-or-teams-phone-mobile). For more information about all options, see [Manage telephone numbers for your organization](/microsoftteams/manage-phone-numbers-landing-page).

## Search for telephone numbers for Microsoft Calling Plans

To search for telephone numbers for your users:
  
1. Go to the **Microsoft Teams admin center**.

2. In the left navigation, select **Voice** > **Phone numbers** > **Get new numbers**.
  
    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Teams admin center, you must first buy at least one **Enterprise E5 or E3 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.  

3. On the **Select location and quantity** page, select a location from the **Country (Market)** drop-down list.

4. Select **User** from the **Number type** drop-down list.

5. Depending on the Country (Market) you select, you have different options available for locating the telephone numbers you require.  

6. Under **Quantity**, enter the number of phone numbers that you want for your organization, and then select **Next**. You have 10 minutes to select your phone numbers. If you take more than 10 minutes, the numbers are returned to the pool of phone numbers.

    > [!NOTE]
    > You can see the number of telephone numbers available to you (which is based on the number of licenses), listed next to **Quantity**.
  
7. On the **Get numbers** page, select the telephone numbers you want, select **Acquire numbers**, and then select **Next**.

    > [!IMPORTANT]
    > You can acquire more telephone numbers than you have Microsoft licenses. To determine how many telephone numbers you can acquire, take your number of Microsoft Calling Plan licenses, add 10 percent of the number of licenses, then add 10, and then remove however many you have already acquired. For example, if you have 100 Microsoft **Domestic Calling Plan** and/or **International Calling Plan** licenses, you can reserve 120 telephone numbers, assuming that you have not already acquired some telephone numbers for those 100 users. For more details, see [How many telephone numbers can you get?](./how-many-phone-numbers-can-you-get.md).

8. On the **Confirmation** page, verify your choices, and then select **Place order**.

9. When you return to the **Phone numbers** page, select the telephone number or numbers that you want to assign and then select **Edit** to assign it to a user.

## Search for telephone numbers for Operator Connect or Teams Phone Mobile

1. Go to the **Microsoft Teams admin center**.

2. In the left navigation select **Voice** > **Phone numbers** > **Get new numbers**.
  
    > [!IMPORTANT]
    > For you to see the **Voice** option in the left navigation in the Teams admin center, you must first buy at least one **Enterprise E5 or E3 license**, one **Phone System** add-on license, or one **Audio Conferencing** add-on license.  

3. On the **Select location and quantity** page, select a location from the **Country (Market)** drop-down list.

4. Select **User** from the **Number type** drop-down list.

5. Depending on the Country (Market) you have selected, you will now have different options available for you to use for locating the telephone numbers you require. You can filter to show only operators that you have added by selecting **Show my operators**.

6. If you've already provided consent to the operator, you'll be directed to the landing page of the operator to complete the order process.

7. If you haven't provided consent to the operator, you'll be directed to enable your operator on the chosen operator page in the Teams admin center. For more information, see [Enable an operator](operator-connect-configure.md#enable-an-operator).

8. After your order is complete, your operator will upload phone numbers to your tenant, and you can assign them to users.  

## Related topics

[Manage telephone numbers for your organization](manage-phone-numbers-landing-page.md)

[Emergency calling terms and conditions](./emergency-calling-terms-and-conditions.md)

[Emergency Calling disclaimer label](https://download.microsoft.com/download/9/9/0/990e24c1-eb49-4b52-9306-dbd4c864ed91/emergency-calling-label-(en-us)-(v.1.0).zip)
