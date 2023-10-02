---
title: Hot desking Teams displays
author: tonysmit
ms.author: tonysmit
manager: serdars
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: admin
ms.reviewer: prashibadkur
ms.date: 07/05/2023
ms.collection: 
  - M365-collaboration
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
description: Learn how to set up and deploy hot desking for Teams Displays.
ms.localizationpriority: medium
search.appverid: MET150
appliesto: 
  - Microsoft Teams
---

# Deploy hot desking for Teams Displays

Teams Displays are used in a shared areas with hot desks, or private work areas such as phone booths or other type of private rooms. This article helps you to deploy and configure Teams Displays in hot desking mode. Hot desking lets users reserve, sign-in, collaborate with other people, and then end their session securely.

Hot desking requires two types of accounts:

- **Resource account** - used by the Teams Display for the hot desking experience and booking the space.
- **User account** - used by the user who's booked the Teams Display to sign in to access their account and settings.

## Step 1 – Buy the licenses

First, you need to purchase a  **Teams Shared Devices**  license and make sure that you have a certified Teams Display. To search for and learn more about certified displays, go to [Microsoft Teams devices](https://products.office.com/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1).

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Billing** > **Purchase services**.
2. If the  **View by category**  section isn't already displayed, go to **Purchase from Microsoft**, and select **View products**. Then select  **Collaboration and communication**.
3. In the product list, find **Microsoft Teams Shared Devices**, and select **Details**.
4. Enter the number of licenses you want and select  **Buy**.

> [!NOTE]
>
>If you're using Intune in your environment and have conditional access rules that require device compliance, you'll need to assign an  **Azure Active Directory Premium Plan 1** , and  **Intune**  license to the device account for the Teams Display.

Teams Displays can be impacted by conditional access rules and other identity configurations, like Multi-Factor Authentication (MFA). See [**Authentication best practices for Teams Android devices**](./authentication-best-practices-for-android-devices.md) to learn more.

## Step 2 - Create a new resource account and assign licenses

### Using the Microsoft 365 admin center

If you're deploying more than one Teams Display at once, learn how to create resource accounts and assign licenses [using PowerShell](../set-up-common-area-phones.md#using-powershell).

## Create the Resource Account

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Resources** > **Rooms & Equipment** > **Add a resource**.
2. Select **Room** as the resource type.
3. Enter an email like "Building5hotdesk1", then select a domain like "Contoso.com".
4. Enter a location such as "Building 5 – 1st Floor HotDesk 1".
5. Click **Save**.

> [!Important]
>
> Manually setting a password for Teams Displays is highly recommended to prevent sign-in issues.

1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Users** > **Active Users**.
2. Search for the newly created resource account and select it.
3. Select **Licenses and apps**.
4. Assign the appropriate usage location.
5. Assign a **Teams Shared Devices**  license to the account.
6. Select **Reset Password** and assign a password to the account used by the Teams Display.

### Using PowerShell

Use PowerShell when you want to create and assign licenses for more than one user account at one time. For more information, see [Create Microsoft 365 user accounts with PowerShell](/microsoft-365/enterprise/create-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true) and [Assign Microsoft 365 licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell?view=o365-worldwide&preserve-view=true).

## Step 3 - Set policies for Teams Displays

Use IP phone policies to control which features are available to Teams Displays.

### IP phone policies

To configure other parameters, consider creating an [IP phone policy](/powershell/module/skype/new-csteamsipphonepolicy).

> [!Important]
>
> Teams Displays do **not** support 'HotDeskingIdleTimeOutinMinutes' in IP Phone Policies.

## Step 4 - Sign in

Once you create and configure the resource account for the Teams Display, you must sign in to the account and set it up for hot desking.

- [Local sign in](../set-up-common-area-phones.md#local-sign-in).
- [Sign in from another device](../set-up-common-area-phones.md#sign-in-from-another-device).
- [Sign in using the Teams admin center](../set-up-common-area-phones.md#sign-in-using-the-teams-admin-center).

### Local sign in
To sign in locally with a username and password:

1. Turn on the Teams Display and connect it to your network.
2. Select  **Sign in on this device**.
3. Follow the sign-in directions on the device. Once signed in, the Teams Display will display the hot desking user experience.

### Sign in from another device
You can also sign into to a Teams Display from another device using a code. When you sign in this way, you'll enter the username and password on another device, rather than on the display itself.

1. On your Teams Display, find the code displayed on the sign in screen.
2. On another device, go to [https://www.microsoft.com/devicelogin](https://www.microsoft.com/devicelogin).
3. Enter the code and follow the instructions to finish signing in.

### Sign in using the Teams admin center
As an admin, you can remotely provision and sign into Teams Display from the [Teams admin center](https://go.microsoft.com/fwlink/p/?linkid=2066851). This method is the most efficient sign-in method when you're deploying many displays at one time. See [Remote provisioning and sign in for Teams Android devices](./remote-provision-remote-login.md) to learn more.

## Step 5 – Booking Options (Optional)

  1. In the [Microsoft 365 admin center](https://go.microsoft.com/fwlink/p/?linkid=2024339), go to **Resources** > **Rooms & Equipment**.
  2. Search for the resource account and click the **name** of the account.
  3. Select **Edit** in the **Booking options** section.
  4. Validate the **Booking options** meet your needs, and make sure that " **Auto Accept**" is checked.

> [!Note]
>
> For hot desking, we recommend the 'AllowConflicts' setting is set to '$False' on all resource mailboxes to ensure resources are booked exclusively for a single user's appointment.
