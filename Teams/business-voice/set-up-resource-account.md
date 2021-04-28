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
2. Go to **Billing** > **Purchase services** > **Add-ons**
3. Scroll to the end to find the **Microsoft 365 Phone System – Virtual User** license. Select **Buy now**.

> [!NOTE]
> Keep in mind you must still  **Buy** the license even though it has a cost of zero.

## Create a resource account

After you've received your *Microsoft 365 Phone System - Virtual User* license, you can create your resource account.

![Screenshot of add resource account user interface](../media/resource-account-add.png)

1. In the Teams admin center, expand **Org-wide settings**, and then click **Resource accounts**.
2. Click **Add**.
3. In the **Add resource account** pane, fill out **Display name**, **Username**, and the **Resource account type**. The resource account type can be either **Auto attendant** or **Call queue**, depending how you intend to use this resource account.
4. Click **Save**.

![Screenshot of a list of resource accounts](../media/resource-accounts-page.png)

## Assign a license

After you've created your resource account, you need to assign a *Microsoft 365 Phone System - Virtual User* license or *Phone System* license.

![Screenshot of assign licenses user interface in the Microsoft 365 admin center](../media/resource-account-assign-virtual-user-license.png)

1. In the Microsoft 365 admin center, click the resource account to which you want to assign a license.
2. On the **Licenses and Apps** tab, under **Licenses**, select **Microsoft 365 Phone System - Virtual User**.
3. Click **Save changes**.

## Assign a service number

![Screenshot of the assign service number user interface](../media/resource-account-assign-phone-number.png)

1. In the Teams admin center, on the **Resource accounts** page, select the resource account you just created, and then click **Assign/unassign**.
2. In the **Phone number type** dropdown, choose **Online**.
3. In the **Assigned phone number** box, search for the number you want to use and click **Add**. Be sure to include the country code (for example, **+1** 250 555 0012)
4. Click **Save**.
    > [!NOTE]
    > You don't need to select an auto attendant under **Assign to** because the auto attendant you want to add the number to is already selected.

> [!div class="nextstepaction"]
> [Next step: Assign phone numbers to your users](set-up-assign-numbers.md)
