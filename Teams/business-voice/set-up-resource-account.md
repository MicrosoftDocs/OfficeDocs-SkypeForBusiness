---
title: Set up a Microsoft 365 Business Voice resource account
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
description: Learn how to set up a Microsoft 365 Business Voice resource account for use with auto attendants.
appliesto: 
- Microsoft Teams
---

# Set up a Business Voice resource account

In Microsoft Teams, a resource account is required for each auto attendant or call queue. Resource accounts may also be assigned service telephone numbers. This is how you assign phone numbers to auto attendants and call queues allowing callers from outside Teams to reach the auto attendant or call queue.

## Obtain virtual user licenses

Resource accounts require a license in order to work with auto attendants and call queues. You can use a free *Microsoft 365 Phone System - Virtual User* license.

1. Sign in to the Microsoft 365 admin center.
2. Go to **Billing** > **Purchase services** > **Add-ons** > **See all Add-ons products**
3. Scroll to the end to find the **Microsoft 365 Phone System – Virtual User** license. Select **Details**, then **Buy**.
4. On the license purchase page, select the number of virtual user licenses you want. You need one virtual license for each auto attendant and call queue you plan to set up. We recommend selecting at least five licenses so you can easily set up more auto attendants and call queues in the future without having to purchase more licenses right away.
5. Uncheck **Automatically assign to all of your users with no licenses**.
6. Select **Check out now**.
7. Confirm your order, select **Next**, and then **Place order**.

> [!NOTE]
> Keep in mind you must still  **Buy** the license even though it has a cost of zero.

## Create a resource account

After you've received your *Microsoft 365 Phone System - Virtual User* license, you can create your resource account.

![Screenshot of add resource account user interface](../media/resource-account-add.png)

1. In the Teams admin center, expand **Org-wide settings**, and then click **Resource accounts**.
2. Select **Add**.
3. In the **Add resource account** pane, fill out **Display name**, and then **Username**. Choose a descriptive display name such as "Main line auto attendant" to describe the purpose of the resource account.
4. In **Resource account type**, select **Auto attendant**.
5. Select **Save**.

![Screenshot of a list of resource accounts](../media/resource-accounts-page.png)

## Assign a license

After you've created your resource account, you need to assign a *Microsoft 365 Phone System - Virtual User* license or *Phone System* license.

![Screenshot of assign licenses user interface in the Microsoft 365 admin center](../media/resource-account-assign-virtual-user-license.png)

1. In the Microsoft 365 admin center, go to **Users** > **Active users**.
2. Select your resource account.
1. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft 365 Phone System - Virtual User**.
1. Select **Save changes** and then **Close**.

## Assign a service number

![Screenshot of the assign service number user interface](../media/resource-account-assign-phone-number.png)

1. In the Teams admin center, go to **Org-wide settings** and then **Resource accounts**. 
1. Select the resource account you just created, and then click **Assign/unassign**.
1. In the **Phone number type** dropdown, choose **Online**.
1. In the **Assigned phone number** box, search for the number you want to use and click **Add**. Be sure to include the country code (for example, **+1** 250 555 0012)
1. Click **Save**.
    > [!NOTE]
    > You don't need to select an auto attendant under **Assign to** because the auto attendant you want to add the number to is already selected.

> [!div class="nextstepaction"]
> [Next step: Assign phone numbers to your users](set-up-assign-numbers.md)
