---
title: Set up the common area phones for Microsoft Teams
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: prashibadkur
ms.date: 08/27/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - M365-voice
  - m365initiative-voice
  - Tier1
search.appverid: MET150
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
  - seo-marvel-mar2020
  - admindeeplinkMAC
  - admindeeplinkTEAMS
description: Learn how to set up common area phones for lobbies, reception areas, and conference rooms.
---

# Set up common area phones for Microsoft Teams

A common area phone is typically placed in an area like a lobby, reception area, or a conference room and is available to many people to make a call. Common area phones are signed in with resource accounts tied to a **Microsoft Teams Shared Devices** license.

This article provides an overview of how to deploy and configure Teams phone devices as common area phones for shared spaces. For a more complete meeting room experience, including video, consider a dedicated **Teams Rooms** license with a Teams Rooms device instead. For more information about Teams Rooms, see [Microsoft Teams Rooms](../rooms/index.md).

## Step 1 - Buy the licenses

First, you need to purchase a **Teams Shared Devices** license and make sure that you have a certified phone. To search for and learn more about certified Teams Phones, go to [Teams Phones certified hardware](../devices/teams-phones-certified-hardware.md?tabs=certified-phones).

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Purchase services**.

2. If the **View by category** section isn't already displayed, go to **Purchase from Microsoft**, and select **View products**. Then select **Collaboration and communication**.  

3. In the product list, find **Microsoft Teams Shared Devices**, and select **Details**.

4. Enter the number of licenses you need, and select **Buy**.

## Step 2 - Create a new resource account and assign licenses

### Using the Microsoft 365 admin center

If you're deploying more than one common area phones at once, learn how to create accounts and assign licenses [using PowerShell](#using-powershell).

If you're deploying one device:

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Users** > **Active Users** > **Add a user**.

2. Enter a username like `Main` for the first name and `Reception` for the second name.

3. Enter a display name if it doesn't autogenerate one like `Main Reception`.

4. Enter a username like `MainReception` or `Mainlobby`.

5. Manually set the password for your common area phone. To set the password, uncheck **Automatically create a password** and **require this user to change their password when they first sign in**.  

    > [!IMPORTANT]
    > Manually setting a password for common area phones is highly recommended to prevent sign-in issues for your end users.

6. Select the usage location of the device and assign the **Teams Shared Devices** license to the account. If any other licenses are needed, like Callings Plans, assign them.

> [!NOTE]
> You don't need to add a license with Phone System features. It's included with the **Teams Shared Devices** license.
>
> If you aren't using Microsoft Phone System with Direct Routing or Operator Connect, you may want to add **Calling Plans** licenses. For more information on licenses, see [Microsoft Teams add-on licensing](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

### Using PowerShell

Use PowerShell when you want to create and assign licenses for more than one user account at once. For more information, see [Create Microsoft 365 user accounts with PowerShell](/microsoft-365/enterprise/create-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true) and [Assign Microsoft 365 licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true).

> [!NOTE]
> Common area phones can be impacted by conditional access rules and other identity configurations, like user interactive Multi-Factor Authentication (MFA). For more information, see [Authentication best practices for Teams Phones](authentication-best-practices-phones.md).

## Step 3 - Set policies for common area phones

Use policies to control which features are available to users on common area phones.

### IP phone policies

The Teams IP Phone policy can only be modified if the account signing into the phone is licensed with something other than a **Teams Shared Devices** license.  If licensed with a Microsoft 365 E3 or E5 subscription, or an Office 365 Enterprise E1, E3, or E5 subscription, you can modify the IP Phone policy.  If you're using a **Teams Rooms** license on your common area phone account, it will only let you use `MeetingRoomSignIn` mode. `MeetingRoomSignIn` mode isn't available on most common area phones. For more information about supported overrides for the phone interface, see [Set Microsoft Teams Android devices user interface](/microsoftteams/devices/teams-android-devices-user-interface#override-automatic-user-interface-detection).

Using the Teams IP Phone policy, set the [SignInMode parameter](/powershell/module/teams/new-csteamsipphonepolicy#parameters) to `CommonAreaPhoneSignIn` to enable the common area phone experience on the Teams phone device.

To configure other parameters, consider creating an [IP phone policy](/powershell/module/teams/new-csteamsipphonepolicy). For example, if a common area phone is used in a public area, set an IP phone policy to restrict searching your organization's Global Address Book and block hot-desking. To learn more, see [Set Teams Android devices user interface](/microsoftteams/devices/Teams-Android-devices-user-interface).

### Calling policies

Use calling policies to enable private calls, using call forwarding, or simultaneous ring on common area phones. To learn more, see [Configure calling policies in Teams](../teams-calling-policy.md).

By default, call park isn't enabled for common area phones. You'll need to create a policy to enable it. To learn more, see [Call park and retrieve in Microsoft Teams](../call-park-and-retrieve.md).

> [!NOTE]
> After you assign a policy, sign out of the phone and sign back in. It may take up to an hour for a policy assignment to take effect.

## Step 4 - Acquire and assign phone numbers

See [Manage telephone numbers for your organization](../manage-phone-numbers-landing-page.md) to learn how to acquire and assign phone numbers based on your PSTN connectivity option.

## Step 5 - Sign in the Teams PHone

Once you create and configure a user account, you can sign into a phone. Depending on how many phones you're deploying, you have three sign-in options:

- [Local sign-in](#local-sign-in).
- [Sign in from another device](#sign-in-from-another-device).
- [Sign in using the Teams admin center](#sign-in-using-the-teams-admin-center).

### Local sign-in

To sign in locally with a username and password:

1. Turn on the common area phone.
2. Select **Sign in on this device**.
3. Follow the sign-in directions on the device. Once signed in, the phone will display the common area phone user experience.

> [!NOTE]
> If you are using a custom setup policy that unpins the calling app, the dial pad doesn't appear on the common area phone. For more information about Teams setup policies, see [Manage app setup policies in Microsoft Teams](../teams-app-setup-policies.md).

### Sign in from another device

You can also sign into to a common area phone from another device using a code. When you sign in this way, you'll enter the username and password on another device, rather than on the phone itself. For more information see [Remote sign in and sign out for Teams Phones](remote-sign-in-and-sign-out-phones.md).

1. On your common area phone, find the code displayed on the sign-in screen.
2. On another device, go to [https://www.microsoft.com/devicelogin](https://www.microsoft.com/devicelogin).
3. Enter the code and follow the instructions to complete signing in.

### Sign in using the Teams admin center

As an admin, you can remotely provision and sign into common area phones from the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851). This method is the most efficient sign-in method when you're deploying a large number of phones at once. See [Remote provisioning and sign in for Teams Android Phones](remote-provision-remote-login-phones.md) to learn more.

## Step 6 - Set up Advanced calling on common area phones (optional)

By default, the basic calling experience will be on the common area phone's home screen, but you can turn on an advanced calling experience.

The following advanced calling features are available for supported Teams phone device models with a **Teams Shared Devices** license and the latest Teams updates (minimum version: 1449/1.0.94.2022061702):

- [Call park and retrieve](../call-park-and-retrieve.md).
- [Cloud-based voicemail through Exchange Online Plan 2](../set-up-phone-system-voicemail.md).
  - To disable cloud-based voicemail, see [Voicemail user settings using PowerShell](/powershell/module/teams/set-csonlinevoicemailusersettings).
- [Call queues](../create-a-phone-system-call-queue.md).
- [Auto attendants](../create-a-phone-system-auto-attendant.md).
- [Group call pickup](../call-sharing-and-group-call-pickup.md).
- [Forwarding rules](../user-call-settings.md).

To use these advanced calling features on a supported Teams phone device model, you can turn on the **Advanced calling** toggle in the [Teams admin center](https://admin.teams.microsoft.com/) or on your Teams phone device that is signed into your Teams Shared Devices account. Once you turn on advanced calling home screen experience on the phone, the device will update.

Turning on advanced calling capabilities requires you to purchase hardware models that can support all required capabilities.

### Turn on Advanced calling in Teams admin center

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com/dashboard) with a Microsoft 365 admin account.
1. From the left-side menu, navigate to **Teams devices** > **Phones** > and select the **Configuration profiles** tab.
1. From the list, select the configuration profile assigned to your common area phone.
1. Under the **Calling settings** section, find the **Advanced calling** toggle.
1. Turn on the toggle.
1. At the bottom of the page, select the **Save** button.

### Turn on Advanced calling from a Teams phone device

1. After signing into your Teams phone device, navigate to **Settings** > **Device settings** > **Admin only** > **Calling**.
1. Find the **Advanced calling** toggle and turn it on.

## Step 7 - Set up Hotline/PLAR on common area phones (optional)

You can set up common area phones as hotline phones also known as PLAR (Private Line Auto Ringdown) phones. You can program this phone to autodial a pre-configured PSTN number or a directory contact when the phone handset is picked up.

### Turn on Hotline in the Teams admin center

1. Sign into the [Teams admin center](https://admin.teams.microsoft.com/dashboard) with a Microsoft 365 admin account.
1. From the left navigation, select **Teams devices**, select **Phones** and then select the **Configuration profiles** tab.
1. From the list, select the configuration profile assigned to your common area phone.
1. Under the **Call settings** section, turn on the **Enable hotline** toggle and then select **Save**.

 > [!NOTE]
 > Verify the Advanced Calling setting is disabled when you are enabling the hotline setting in Teams admin center. Also verify the Team app version on the Android phone is version 1449/1.0.94.2023082303 or later.

### Turn on Hotline from a Teams phone device

1. Sign into your Teams phone device and select **Settings** > **Device settings** > **Admin only** > **Calling** > **Hotline**.
1. Enter a contact or phone number to be autodialed.
1. Enter the display name you want to show on the phone's home screen.
1. Select **Save**.

## Next steps

Now that you've set up and signed in common area phones for your organization, you can manage them in the Teams admin center. See [Microsoft Teams: Managing your devices](../devices/device-management.md) to learn more.

## Related articles

- [Update Microsoft Teams devices remotely](../devices/remote-update.md).
- [Manage Microsoft Teams device tags](../devices/manage-device-tags.md).
- [Microsoft Teams device health monitoring](../alerts/device-health-status.md).
