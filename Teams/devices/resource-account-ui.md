---
title: Create a resource account using the Microsoft 365 admin center
description: If you prefer to use a graphical user interface, you can create a resource account for your Microsoft Teams Rooms and collaboration bars for Microsoft Teams using the Microsoft 365 Admin Center.
ms.reviewer: payurevi
manager: serdars
audience: ITPro
keywords: create device account, Microsoft 365 UI, Microsoft 365 admin center
ms.sitesec: library
ms.service: msteams
author: flinchbot
ms.author: mitressl
ms.topic: article
ms.localizationpriority: medium
---

# Create a Microsoft 365 resource account using the Microsoft 365 admin center

Microsoft 365 resource accounts are mailbox and Teams accounts that are dedicated to specific resources, such as a room, projector, and so on. These resource accounts can automatically respond to meeting invites using rules you define when they're created. For example, if you have a common resource such as a conference room, you can set up a resource account for that conference room that will automatically accept or decline meeting invites depending on its calendar availability.

<!-- The steps in this article show you how to set up a resource account using the Microsoft 365 admin center. If you'd rather use PowerShell to create resource accounts, [Create a resource account using the PowerShell](resource-account-ps.md). -->

[!INCLUDE [m365-teams-resource-account-difference](../includes/m365-teams-resource-account-difference.md)]

## Licensing

Before you create a Microsoft 365 resource account, check to see what kind of license it needs. If you'll only use a resource account to book a resource (that is, invite the resource to your meeting and have it automatically accept or decline the invitation), you don't need to assign a license to a resource account. You'll need to assign a license to the resource account in the following situations:

- **Teams meeting** If you want the resource (such as a Microsoft Teams Rooms console, collaboration bar, and so on) to join a Teams meeting so attendees can use it to present video and audio through it, you need a Meeting Room license. 
- **PSTN calls** If you want the resource to make or receive calls to or from an external phone numbers (called a Public Switched Telephone Network or PSTN call), you need a Microsoft 365 Phone System or Microsoft 365 Business Voice license.

For more information about Meeting Room, Phone System, and Business Voice licenses, see [Microsoft Teams add-on licenses](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md)

## <a href="" id="create-device-acct-m365-admin-ctr"></a>Create a resource account in the Microsoft 365 admin center

1. Sign in to Microsoft 365 by visiting https://admin.microsoft.com
2. Provide the admin credentials for your Microsoft 365 tenant. This will take you to your Microsoft 365 admin center.

:::image type="content" source="../media/collaboration-bar-m365-admin-center.png" alt-text="Microsoft 365 admin center":::
3. In the admin center, navigate to **Resources** in the left panel (you might need to select **Show all** first), and then select **Rooms & equipment**.

:::image type="content" source="../media/collaboration-bar-m365-resources-rooms.png" alt-text="Microsoft 365 admin center - Resources":::
4. Select **Add a resource mailbox** to create a new room account. Enter a display name and email address for the account, select **Add**, and then select **Close**. We recommend you standardize on a naming convention for all of your resource accounts.

> [!NOTE]
> By default, resource accounts are set up with the following settings. If you want to change them, select **Set scheduling options** before you select **Close**. If you want to change them later, navigate to **Resources** > **Rooms & equipment**, select the resource account and then select **Edit** under **Booking options**.
>
> - Allow repeat meetings
> - Automatically decline meetings outside of the following limits
>   - Booking window (days): 180
>   - Maximum duration (hours): 24
> - Auto accept meeting requests

:::image type="content" source="../media/collaboration-bars-admin-resources.png" alt-text="Microsoft 365 admin center - Add resources":::
5. Navigate to the **Users** section in admin center and, in the **Active users** list, you will see the room you just created.

:::image type="content" source="../media/collaboration-bars-M3565-admin-active-users.png" alt-text="Microsoft 365 admin center - See active users":::
6. Select on the name of the room and an account properties panel will appear on the right.

:::image type="content" source="../media/collaboration-bar-m365-admin-center-active-user-settings.png" alt-text="Microsoft 365 admin center - User properties":::
7. Now you need to assign a password to the resource account. In the panel, you can see the account properties and several optional actions. Select the **Reset password** key icon under the username to change the password. Unselect **Require this user to change their password when they first sign in**. It is not possible to change the password via the device sign-in process. Select **Reset**.

:::image type="content" source="../media/collaboration-bar-m365-admin-center-active-user-password.png" alt-text="Microsoft 365 admin center - Reset password":::
8. In the **Licenses and Apps** section, set **Select location** to the country or region where the device will be installed. Scroll down and check the box next to the license to be assigned - such as Meeting Room - and then select **Save changes**. The license may vary depending on your organization.

:::image type="content" source="../media/collaboration-bar-m365-admin-center-active-user-assign-license.png" alt-text="Microsoft 365 admin center - Assign license":::
