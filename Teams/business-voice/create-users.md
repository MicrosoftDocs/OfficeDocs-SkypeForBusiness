---
title: Create Microsoft 365 users, add Teams Phone with Calling Plan bundle licenses, and assign phone numbers
author: dstrome 
ms.author: dstrome
manager: serdars
ms.topic: article
ms.service: msteams
audience: admin
f1.keywords:
- NOCSH
ms.localizationpriority: medium
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
description: Learn how to create and license Teams Phone System with Calling Plan bundle users and assign them phone numbers.
appliesto: 
- Microsoft Teams
---

# Create and license Teams Phone System with Calling Plan bundle users and assign them phone numbers

To use the Teams Phone System with Calling Plan bundle, you need a Microsoft 365 account that has Teams Phone with Calling Plan bundle licenses. When you have an account and licenses, you can start assigning phone numbers.

## Create and license users

Follow the steps in [Add users individually or in bulk](/microsoft-365/admin/add-users/add-users) and [Assign licenses to users](/microsoft-365/admin/manage/assign-licenses-to-users).

> [!NOTE]
> In the **Assign product licenses** pane,  select **Teams Phone with Calling Plan**.

## Assign phone numbers to users

After you create users and assigned them Teams Phone with Calling Plan bundle license, you can assign phone numbers to them. You need one unassigned phone number for each user that needs to make or receive calls to or from external phone numbers. If you don't have enough unassigned phone numbers, see [Get more phone numbers](#get-more-phone-numbers) later in this article.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).
2. Enter a name and description for the phone number request.
3. Select **Voice** > **Phone numbers**.
4. Select a phone number that you want to assign to a user, and then select **Edit**.
5. In the **Edit** panel, enter the name of the user that you want to assign the number to in **Assigned to**. Then select **Assign**.
6. For **Emergency location**, enter the location where the user is located, and then select **Apply**

## Get more phone numbers

If you don't have enough phone numbers to assign to new users, you can get more. It may take up to 24 hours for numbers that you order to become available.

1. Go to the [Teams admin center](https://admin.teams.microsoft.com).
2. Enter a name and description for the phone number request.
3. Select **Voice** > **Phone numbers** > **Add**.
4. Choose the country or region for the phone number.
5. For **Number type**, select **User (subscriber)**.
6. For **Location**, search for the location of the user and select it. You can also choose to **Add a location**.
7. Choose an area code, enter the number of phone numbers that you need, and then select **Next**.
8. Wait for the phone numbers to be reserved, and then view the numbers that you get. If everything looks ok, select **Place order** and then **Finish**.
