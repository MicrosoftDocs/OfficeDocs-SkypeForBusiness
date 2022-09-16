---
title: Set up Microsoft Teams Phone System with Calling Plan phone numbers
author: dstrome
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
search.appverid: MET150
description: Learn how to set up Microsoft Teams Phone System with Calling Plan phone numbers for users and services in your organization.
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-voice
  - M365initiative-voice
---

# Step 2: Set up Teams Phone System phone numbers

Before you can set up users or auto attendants in your organization, you need to get phone numbers for them. There are several different types of phone numbers, however the following are the two types of numbers that you need to add in this step:

- **Service numbers** These numbers are used for auto attendants, audio conferencing, and call queues. They can be toll or toll-free numbers and can handle large amounts of calls at the same time. Your company phone number needs to be a service number because it'll be assigned to an auto attendant in a later step.
- **Subscriber numbers** These numbers are used for regular users so they can make and receive phone calls.

> [!IMPORTANT]
> Even if you want to use your existing phone numbers, you need to create and assign temporary phone numbers to your company's main phone line and your users. You'll be able to replace these temporary numbers with your existing phone numbers in a later step.

> [!NOTE]
> It may take several hours for your new phone numbers to become available in Teams.

## Set up a service number

The service number you set up now will be used in a later step for your company's main phone number.

1. Open the Microsoft Teams admin center and log in with a user that is a Global admin (this is usually the account you used to sign up for Microsoft 365).
2. In the left navigation, go to <a href="https://admin.teams.microsoft.com/phone-numbers" target="_blank">**Voice** > **Phone numbers**</a>, and then click **Add**.
3. Enter a name for the order and add a description.
4. On the Location and quantity page, do the following:
    1. Under **Country or region**, select a country or region.
    2. Under **Number type**, select one of the following options:

        - **Auto attendant (Toll)** Regular, non-toll-free, phone number. Long distance fees are charged to the caller.
        - **Auto attendant (Toll Free)** Toll-free (US and Canada) or freephone (UK) phone number. Long distances fees are charged to your company. Before you can select this option, you need to purchase Communication Credits. For more information, see [What do I need to buy to get voice capabilities for my small or medium business?](whats-business-voice.md).

    3. Under **Quantity**, select **1**.
        > [!NOTE]
        > If you get the message **You don't have enough licenses to request more numbers of this type**, make sure you've purchased Teams Phone with Calling Plan bundle licenses. For more information, see [What do I need to buy to get voice capabilities for my small or medium business?](whats-business-voice.md).
    4. Choose either **Location** or **Area code**, depending on whether you want to search for phone numbers using a location's city, or if you want to search for numbers in a specific area code.
    5. If you select **Location**:

        1. Type the city in which your emergency address is located in the [Set up emergency locations](set-up-emergency-locations.md) step, or if you need to create a new location for another office or a home office, click **Add a location**.
        2. Under **Area code**, select an area code, and then select **Next** to reserve your number.

    6. If you select **Area code**, type the area code you want to search, and then select **Next** to reserve your number.

5. Select the number you want. You have 10 minutes to select your phone number and place your order. If you take more than 10 minutes, the phone number will be returned to the pool of numbers.
6. When you're ready to place your order, click **Place order**, and then **Finish**

## Set up phone numbers for your users

1. Open the Microsoft Teams admin center and log in with a user that is a Global admin. This is usually the account you used to sign up for Microsoft 365.
2. In the left navigation, go to <a href="https://admin.teams.microsoft.com/phone-numbers" target="_blank">**Voice** > **Phone numbers**</a>, and then click **Add**.
3. Enter a name for the order and add a description.
4. On the Location and quantity page, do the following:

    1. Under **Country or region**, select a country or region.
    2. Under **Number type**, select **User (subscriber)**.
    3. Under **Quantity**, enter the number of numbers that you want for your organization.
    4. Choose either **Location** or **Area code**, depending on whether you want to search for phone numbers using a location's city, or if you want to search for numbers in a specific area code.
    5. If you select **Location**:

        1. Type the city in which your emergency address is located in the [Set up emergency locations](set-up-emergency-locations.md) step, or if you need to create a new location for another office or a home office, click **Add a location**.
        2. Under **Area code**, select an area code, and then select **Next** to reserve your number.

    6. If you select **Area code**, type the area code you want to search, and then select **Next** to reserve your number.
5. Select the numbers you want. You have 10 minutes to select your phone numbers and place your order. If you take more than 10 minutes, the phone numbers will be returned to the pool of numbers.
6. When you're ready to place your order, click **Place order**, and then **Finish**.

> [!div class="nextstepaction"]
> [Next step: Assign licenses to Teams users](set-up-licenses.md)
