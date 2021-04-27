---
title: Set up Microsoft 365 Business Voice phone numbers
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
localization_priority: Normal
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
- Teams_Business_Voice
search.appverid: MET150
description: Learn how to set up Microsoft 365 Business Voice phone numbers for users and services in your organization.
appliesto: 
- Microsoft Teams
---

# Set up Business Voice phone numbers

Before you can set up users or auto attendants in your organization, you need to get phone numbers for them. There are several different types of phone numbers, however the following are the two types of numbers that you need to add in this step:

- **Service numbers** These numbers are used for auto attendants, audio conferencing, and call queues. They can be toll or toll-free numbers and can handle large amounts of calls at the same time. Your company phone number needs to be a service number because it'll be assigned to an auto attendant in a later step.
- **Subscriber numbers** These numbers are used for regular users so they can make and receive phone calls.

> [!IMPORTANT]
> Even if you want to use your existing phone numbers, you need to create and assign temporary phone numbers to your company's main phone line and your users. You'll be able to replace these temporary numbers with your existing phone numbers in a later step.

> [!NOTE]
> It may take several hours for your new phone numbers to become available in Teams.

## Set up a service number

The service number you set up now will be used in a later step for your company's main phone number.

1. In the left navigation, go to **Voice** > **Phone numbers**, and then click **Add**.
2. Enter a name for the order and add a description.
3. On the Location and quantity page, do the following:
    1. Under **Country or region**, select a country or region.
    2. Under **Number type**, select one of the following options:

        - **Auto attendant (Toll)** Regular, non-toll-free, phone number. Long distance fees are charged to the caller.
        - **Auto attendant (Toll Free)** Toll-free (US and Canada) or freephone (UK) phone number. Long distances fees are charged to your company.

    3. Under **Location**, type the name of the location you created in the [Set up emergency locations](set-up-emergency-locations.md) step.
    4. Under **Area code**, select an area code.
    5. Under **Quantity**, select **1**, and then click **Next** to select your numbers.

4. Select the number you want. You have 10 minutes to select your phone number and place your order. If you take more than 10 minutes, the phone number will be returned to the pool of numbers.
5. When you're ready to place your order, click **Place order**.

## Set up phone numbers for your users

1. Go to the Microsoft Teams Admin Center.
2. In the left navigation, go to **Voice** > **Phone numbers**, and then click **Add**.
3. Enter a name for the order and add a description.
4. On the Location and quantity page, do the following:

    1. Under **Country or region**, select a country or region.
    2. Under **Number type**, select **User (subscriber)**.
    3. Under **Location**, select a location. You can select either the emergency location you added in the [Set up emergency locations](set-up-emergency-locations.md) step, or if you need to create a new location for another office or a home office, click **Add a location**.
    4. Under **Area code**, select an area code.
    5. Under **Quantity**, enter the number of numbers that you want for your organization, and then click **Next** to select your numbers.

5. Select the numbers you want. You have 10 minutes to select your phone numbers and place your order. If you take more than 10 minutes, the phone numbers will be returned to the pool of numbers.
6. When you're ready to place your order, click **Place order**.

> [!div class="nextstepaction"]
> [Next step: Assign licenses to Teams users](set-up-licenses.md)
