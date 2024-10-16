---
title: Set up an Android mobile phone as a common area phone
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: prashibadkur
ms.date: 08/25/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - M365-collaboration
  - Teams_ITAdmin_Devices
  - Tier1
ms.localizationpriority: medium
search.appverid: MET150
f1.keywords:
- NOCSH
- appliesto: 
  - Microsoft Teams
description: Learn how to set up common area Android phones
---

# Set up an Android mobile phone as a common area phone

A Teams Android mobile app signed in with an account tied to **Microsoft Teams Shared Device** license is used as a shared device by frontline workers to make and receive calls as part of their daily work using Teams.

  > [!IMPORTANT]
  > To use this feature you must have version 1.0.0.2023143401 (2023143401) or later installed on the Android mobile phone.

## Step 1 - Buy the licenses

First, you need to purchase a **Teams Shared Devices** license.

  > [!NOTE]
  > Chat is not supported with a **Teams Shared Devices** license.

To purchase the license:

1. Sign in to [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), and select **Billing > Purchase services**.
1. If the **View by category** section isn't already displayed, go to **Purchase from Microsoft** and select **View products**, and then select **Collaboration and communication**.
1. In the product list, find **Microsoft Teams Shared Devices**, and select **Details**.
1. Enter the number of licenses you need, and select **Buy**.

  > [!NOTE]
  > If you're using Intune in your environment and have conditional access rules that require device compliance, you'll need to assign an **Microsoft Entra ID P1** and an **Intune** license to the device account that was used to sign in to the Teams mobile app.
  > Teams-shared devices can be impacted by conditional access rules and other identity configurations, such as Multi-Factor Authentication. For more information, see [Authentication best practices for Teams Android devices](../devices/authentication-best-practices-for-android-devices.md).

## Step 2 - Create a new user account and assign licenses

### Using the Microsoft 365 admin center

  > [!NOTE]
  > If you're deploying more than one phone at a time, you can use only [PowerShell](../set-up-common-area-phones.md) to create accounts and assign licenses.
  > You can use Microsoft 365 admin center to create accounts and assign licenses only if you're deploying one device at a time.

1. Sign in to [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), and select **Users > Active Users > Add a user**.
1. Enter a username like **Main** for the first name and **Reception** for the second name.
1. Enter a display name if it doesn't autogenerate one, for example, **Main Reception**.
1. Enter a username like **BakeryPhone** or **DutyManager**.
1. Manually set the password for your common area phone. To set the password, clear the **Automatically create a password and require this user to change their password when they first sign in** checkbox.

> [!IMPORTANT]
> Manually setting a password for common area phones is recommended to prevent sign-in issues for your end users.

6. Select the usage location of the device and assign the **Teams Shared Devices** license to the account. If any other licenses are needed, such as **Callings Plans**, assign those licenses too to the account.

> [!NOTE]
>
> When you assign a **Teams Shared Device** license to a device, you don't need to assign an additional Phone System license to get other features. To get inbound and outbound calling minutes with Microsoft Phone System you must add a Calling Plan and set up billing. However, if you are using Operator Connect or Direct Routing, you don't need a Calling Plan. For more information on licenses, see [Microsoft Teams add-on licensing](../teams-add-on-licensing/microsoft-teams-add-on-licensing.md). 

### Using PowerShell

Use PowerShell when you want to create and assign licenses for more than
one user account at a time. For more information, see [Create Microsoft 365 user accounts with PowerShell](/microsoft-365/enterprise/create-user-accounts-with-microsoft-365-powershell) and [Assign Microsoft 365 licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell).

## Step 3 - Set policies

To set up different policies as required, see:

1. [Calling policies in Teams](../teams-calling-policy.md)
1. [Configure Call park and retrieve](..//call-park-and-retrieve.md)

## Step 4 - Acquire and assign phone numbers

To acquire and assign phone numbers based on your PSTN connectivity option, see [Manage telephone numbers for your organization](../manage-phone-numbers-landing-page.md).

## Step 5 - Sign in

Once you create and configure the account, you can sign in to the Teams app on the Android mobile phone using the account tied to **Teams Shared Device** license.

:::image type="content" source="../media/teamsshareddevicelicenseonandroidmobile.png" alt-text="Screenshot showing the Teams app on an Android mobile device." lightbox="../media/teamsshareddevicelicenseonandroidmobile.png":::
