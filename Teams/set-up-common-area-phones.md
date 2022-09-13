---
title: Set up common area phones for Microsoft Teams
ms.author: czawideh
author: cazawideh
manager: serdars
ms.date: 1/28/2022
ms.reviewer: kponnus
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Phone System
  - seo-marvel-mar2020
  - admindeeplinkMAC
  - admindeeplinkTEAMS
description: Learn how to set up Common Area Phones for lobbies, reception areas, and conference rooms.
---

# Set up common area phones for Microsoft Teams

A common area phone is typically placed in an area like a lobby or another area that is available to many people to make a call: a reception area, lobby, or conference phone. Common area phones are signed in with accounts tied to a **Common Area Phone** license.

This article provides an overview of how to deploy and configure Teams phone devices as common area phones for shared spaces. For a more complete meeting room experience, including audio conferencing, consider purchasing a dedicated **Teams Rooms** license with a Teams Rooms device.

## Overview

The **Common Area Phone** license supports:

|                                           | Common Area Phone                                 |
|-------------------------------------------|---------------------------------------------------|
| **Microsoft Teams**                       | &#x2714;                                          |
| **Teams Phone**  &sup1;                   | &#x2714;                                          |
| **Audio Conferencing**                    | &#x2718; &sup2;                                   |
| **Microsoft Intune**                      | &#x2714;                                          |
| **Azure Active Directory Premium Plan 1** | &#x2714;                                          |
| **Exchange Online Plan 2**                | &#x2714;  &sup3;                                  |
| **Worldwide Availability**                | &#x2714;                                          |
| **Channel Availability**                  | EA, EAS, EES, CSP, Web Direct, GCC, GCC-High, DoD |

&sup1; Previously known as *Phone System*.
&sup2; Common area phones can join audio conferences via a dial-in number provided by the meeting organizer.
&sup3; Cloud-based voicemail capabilities only.

> [!NOTE]
> Accounts for common area phones objects created in Skype for Business Server can't be migrated to Microsoft Teams. Follow the steps in this article to recreate those accounts for Teams, and, if required, migrate your Public Switched Telephone Network (PSTN) connectivity.

## Step 1 - Buy the licenses

First, you need to purchase a **Common Area Phone** (CAP) license and make sure that you have a certified phone. To search for and learn more about certified phones, go to [Microsoft Teams devices](https://products.office.com/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1).

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Purchase services**.

2. If the **View by category** section isn't already displayed, go to **Purchase from Microsoft**, and select **View products**. Then select **Collaboration and communication**.  

3. In the product list, find **Common Area Phone**, and select **Details**.

4. Enter the number of licenses you need, and select **Buy**.

> [!NOTE]
> If you’re using Intune in your environment and have conditional access rules that require device compliance, you’ll need to assign an **Azure Active Directory Premium Plan 1**, and **Intune** license to the device account for the common area phone.
>
> Common area phones can be impacted by conditional access rules and other identity configurations, like Multi-Factor Authentication. See [Authentication best practices for Teams Android devices](devices/authentication-best-practices-for-android-devices.md) to learn more.

## Step 2 - Create a new user account and assign licenses

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

6. Select the usage location of the device and assign the **Common Area Phone** license to the account. If any other licenses are needed, like Callings Plans, assign them.

> [!NOTE]
> You don't need to add a license with Phone System features. It's included with the **Common Area Phone** license.
>
> If you aren't using Microsoft Phone System with Direct Routing or Operator Connect, you may want to add **Calling Plans** licenses. For more information on licenses, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

### Using PowerShell

Use PowerShell when you want to create and assign licenses for more than one user account at once. For more information, see [Create Microsoft 365 user accounts with PowerShell](/microsoft-365/enterprise/create-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true) and [Assign Microsoft 365 licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true).

## Step 3 - Set policies for common area phones

Use policies to control which features are available to users on common area phones.

> [!NOTE]
> After you assign a policy, sign out of the phone and sign back in. It may take up to an hour for a policy assignment to take effect.

### IP phone policies

Phones signed in with accounts that have been assigned a **Common Area Phone** license will display the common area user experience.

If you want to override a phone's default interface, consider creating an [IP phone policy](/powershell/module/skype/new-csteamsipphonepolicy?view=skype-ps&preserve-view=true). For example, if a common area phone is used in a public area, set an IP phone policy to restrict searching your organization's Global Address Book and block hot-desking. See [Set Teams Android devices user interface](/devices/Teams-Android-devices-user-interface) to learn more.

### Calling policies

Use calling policies to enable private calls, using call forwarding, or simultaneous ring on common area phones. See [Calling and call-forwarding in Teams](teams-calling-policy.md) to learn more.

By default, call park isn't enabled for common area phones. You'll need to create a policy to enable it. See [Call park and retrieve in Microsoft Teams](call-park-and-retrieve.md) to learn more.

## Step 4 - Acquire and assign phone numbers

See [Manage telephone numbers for your organization](manage-phone-numbers-landing-page.md) to learn how to acquire and assign phone numbers based on your PSTN connectivity option.

## Step 5 - Sign in

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
> If you are using a custom setup policy that unpins the calling app, the dial pad doesn't appear on the common area phone. For more information about Teams setup policies, see [Manage app setup policies in Microsoft Teams](teams-app-setup-policies.md).

### Sign in from another device

You can also sign into to a common area phone from another device using a code. When you sign in this way, you'll enter the username and password on another device, rather than on the phone itself.

1. On your common area phone, find the code displayed on the sign-in screen.
2. On another device, go to [https://www.microsoft.com/devicelogin](https://www.microsoft.com/devicelogin).
3. Enter the code and follow the instructions to complete signing in.

### Sign in using the Teams admin center

As an admin, you can remotely provision and sign into common area phones from the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851). This method is the most efficient sign-in method when you're deploying a large number of phones at once. See [Remote provisioning and sign in for Teams Android devices](devices/remote-provision-remote-login.md) to learn more.

## Step 6 - Set up Advanced calling on common area phones (optional)

By default, the basic calling experience will be on the common area phone's home screen, but you can turn on an advanced calling experience.

The following advanced calling features are available for supported Teams phone device models with a **Common Area Phone** license and the latest Teams updates (minimum version: 1449/1.0.94.2022061702):

- [Call park and retrieve](call-park-and-retrieve.md).
- [Cloud-based voicemail through Exchange Online Plan 2](set-up-phone-system-voicemail.md).
  - To disable cloud-based voicemail, see [Voicemail user settings using PowerShell](/powershell/module/skype/set-csonlinevoicemailusersettings).
- [Call queues](create-a-phone-system-call-queue.md).
- [Auto attendants](create-a-phone-system-auto-attendant.md).
- [Group call pick-up](call-sharing-and-group-call-pickup.md).
- [Forwarding rules](teams-calling-policy.md).

To use these advanced calling features on supported Teams phone device models, you can turn on the **Advanced calling** toggle in the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851) or on your Teams phone device that is signed into your Common Area Phone account.

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

## Next steps

Now that you've set up and signed in common area phones for your organization, you can manage them in the Teams admin center. See [Microsoft Teams: Managing your devices](devices/device-management.md) to learn more.

## Related articles

- [Update Microsoft Teams devices remotely](devices/remote-update.md).
- [Manage Microsoft Teams device tags](devices/manage-device-tags.md).
- [Microsoft Teams device health monitoring](alerts/device-health-status.md).
