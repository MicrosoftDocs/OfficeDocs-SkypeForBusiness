---
title: Create a resource account using the Microsoft 365 admin center
description: If you prefer to use a graphical user interface, you can create a resource account for your Microsoft Teams Rooms and collaboration bars for Microsoft Teams using the Microsoft 365 Admin Center.
ms.assetid: 
ms.reviewer: payurevi
manager: ericwe
audience: ITPro
keywords: create device account, Microsoft 365 UI, Microsoft 365 admin center
ms.sitesec: library
ms.service: msteams
author: flinchbot
ms.author: mitressl
ms.topic: article
ms.date: 04/10/2020
ms.localizationpriority: medium
---

# Create a resource account using the Microsoft 365 admin center
In this article, you will learn how to create a resource account using the Microsoft 365 admin center.

If you prefer to use PowerShell to create resource accounts, [see this article.](resource-account-ps.md) 

## Requirements

Before you deploy collaboration bars for Microsoft Teams, be sure you have met the requirements. For more information, see [Deploy collaboration bars for Microsoft Teams](collab-bar-deploy.md).

- If you need PSTN capabilities for the collaboration bar, you will need Phone System license.

- Your resource accounts must have Exchange mailboxes. As these are resource accounts, no Exchange license is required. We recommend the usage of the Meeting Rooms license for resource accounts.

### <a href="" id="create-device-acct-m365-admin-ctr"></a>Create a resource account in the Microsoft 365 admin center

1.  Sign in to Microsoft 365 by visiting https://admin.microsoft.com


2.  Provide the admin credentials for your Microsoft 365 tenant. This will take you to your Microsoft 365 admin center.

:::image type="content" source="../media/collaboration-bar-m365-admin-center.png" alt-text="Microsoft 365 admin center":::

3. In the admin center, navigate to **Resources** in the left panel, and then click **Rooms & equipment**.

:::image type="content" source="../media/collaboration-bar-m365-resources-rooms.png" alt-text="Microsoft 365 admin center - Resources":::
    
4. Click **Add a resource mailbox** to create a new room account. Enter a display name and email address for the account, and then click **Add**. We recommend you standardize on a naming convention for all of your resource accounts.

:::image type="content" source="../media/collaboration-bars-admin-resources.png" alt-text="Microsoft 365 admin center - Add resources":::

5. Navigate to the **Users** section in admin center and, in the **Active users** list, you will see the room you just created.

:::image type="content" source="../media/collaboration-bars-M3565-admin-active-users.png" alt-text="Microsoft 365 admin center - See active users":::

6. Click on the name of the room and an account properties panel will appear on the right.

:::image type="content" source="../media/collaboration-bar-m365-admin-center-active-user-settings.png" alt-text="Microsoft 365 admin center - User properties":::

7. Now you need to assign a password to the resource account. In the panel, you can see the account properties and several optional actions. Click the **Reset password** key icon under the username to change the password. Unselect **Require this user to change their password when they first sign in**. It is not possible to change the password via the device sign-in process. Click **Reset**.

:::image type="content" source="../media/collaboration-bar-m365-admin-center-active-user-password.png" alt-text="Microsoft 365 admin center - Reset password":::


8. In the **Licenses and Apps** section, set **Select location** to the country where the device will be installed. Scroll down and check the box next to the license to be assigned - such as Meeting Room - and then click **Save changes**. The license may vary depending on your organization.

:::image type="content" source="../media/collaboration-bar-m365-admin-center-active-user-assign-license.png" alt-text="Microsoft 365 admin center - Assign license":::

