---
title: Set up the Common Area Phone license
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
description: "Learn how to set up Common Area Phones for lobbies, reception areas, and conference rooms "
---

# Deploy common area phones for Microsoft Teams

A common area phone is typically placed in an area like a lobby or another area that is available to many people to make a call; for example, a reception area, lobby, or conference phone. Common area phones are signed in with accounts tied to a Common Area Phone license. The TeamsIPPhone policy must also be appropriately set for the phone to have a common area user experience.

This article provides an overview of how to deploy and configure Teams phones as common area phones for shared spaces. For a more complete meeting room experience, including audio conferencing, consider purchasing the dedicated Meeting Room license with a meeting room device.

## Overview

The Common Area Phone license supports: 


| &nbsp;  |  Common Area Phone  |
|---------|---------|
|Skype for Business |   &#x2714; |
|Microsoft Teams |   &#x2714; |
|Phone System |    &#x2714; |
|Audio Conferencing |       &#x2718; &sup1;  |
|Microsoft Intune |    &#x2718; |
|Worldwide Availability |       &#x2718; &sup2;  |
|Channel Availability |    EA, EAS, CSP, GCC, EES, Web Direct  |
|      |         |

&sup1; Common Area Phones can join audio conferences via dial-in number provided by the meeting organizer

&sup2; Not available in sovereign clouds  

>[!NOTE]
> Accounts for common area phones from the Skype for Business Server can't be migrated to Microsoft Teams. Follow the steps below to recreate those accounts for Teams, and, if required, migrate your PTSN connectivity.

First, you need to purchase a Common Area Phone (CAP) license and make sure that you have a certified phone. To search for and learn more about certified phones, go to [Microsoft Teams devices](https://products.office.com/microsoft-teams/across-devices?ms.url=officecomteamsdevices&rtc=1).

## Step 1 - Buy the licenses

1. In the Microsoft 365 admin center, go to **Billing** > **Purchase services**. 

2. If the **View by category** section isn't already displayed, go to **Purchase from Microsoft**, and select **View products**. Then select **Collaboration and communication**.  

3. In the product list, find **Common Area Phone** and select **Details**.

4. Enter the number of licenses you need, and select **Buy**.

>[!NOTE]
>If you’re using Intune in your environment and have conditional access rules that require device compliance, you’ll need to assign an Azure Active Directory Premium Plan 1, and Intune license to the device account for the common area phone.
>
>Common area phones can be impacted by conditional access rules and other identity configurations, like Multi-Factor Authentication. See [Authentication best practices for Teams Android devices](devices/authentication-best-practices-for-android-devices.md) to learn more.

## Step 2 - Create a new user account for the phone and assign the licenses

### Using the Microsoft 365 admin center

1. In the Microsoft 365 admin center, go to **Users** > **Active Users** > **Add a user**.

2. Enter a username like "Main" for the first name and "Reception" for the second name.

3. Enter a display name if it doesn't autogenerate one like "Main Reception."

4. Enter a username like "MainReception" or "Mainlobby."

5. Set the password for your common area phone manually to prevent. To do this, uncheck **Automatically create a password** and **require this user to change their password when they first sign in**.  

>[!Important]
> Setting a password manually for common area phones is highly recommended to prevent sign-in issues for your end users.

6. Select the usage location of the device and assign the Common Area Phone license to the account. If any other licenses are needed, like Callings Plans, assign them.

### What add-on licenses do you need?

**Microsoft Phone System**
You don't need to add a Phone System license. It's included with the Common Area Phone license.

**Direct Routing and Operator Connect**
If you are using Microsoft Phone System Direct Routing or Operator Connect, you don't need a Calling Plan license.

**Calling Plans**
If you aren't using Microsoft Phone System Direct Routing, you may want to add Calling Plans licenses.

For more information on licenses, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

### Using PowerShell

Using PowerShell is a good option when you want to create and assign licenses to more than one user account at once. See [Create Microsoft 365 user accounts with PowerShell](/microsoft-365/enterprise/create-user-accounts-with-microsoft-365-powershell?view=o365-worldwide) and [Assign Microsoft 365 licenses to user accounts with PowerShell](/microsoft-365/enterprise/assign-licenses-to-user-accounts-with-microsoft-365-powershell?view=o365-worldwide) for more information.

## Step 3 - Policies for common area phones

### IP phone policies

Phones signed in with accounts that have been assigned a Common Area Phone license will display the common area user interface.

If you want to override a phone's default interface, consider creating an [IP phone policy](/powershell/module/skype/new-csteamsipphonepolicy?view=skype-ps). For example, if a common area phone is used in a public area, set an IP phone policy to restrict searching your organization's Global Address Book and block hotdesking. See 
[Set Teams Android devices user interface](devices/Teams-Android-devices-user-interface.md) to learn more.

### Calling policies

Call forwarding and simultaneous ring are only available to common area phones with admin permissions. See [Calling and call-forwarding in Teams](teams-calling-policy.md) to learn more.

By default, call park is not enabled for common area phones. You'll need to create a policy to enable it. See [Call park and retrieve in Microsoft Teams](call-park-and-retrieve.md) to learn more.

## Step 4 - Assign a phone number to the Common Area Phone user account

Use the Teams admin center to assign a number to the user.

1. In the Teams admin center, select **Voice** > **Phone numbers**.

3. Select a number from the list of phone numbers and click **Assign**.

4. On the **Assign** page, in the Voice user box, type the name of the user who will be using the phone, and then select the user in the **Select a voice user** drop-down list.

5. Next, you need to add an emergency address. Choose **Search by city**, **Search by description**, or **Search by location** from the drop-down list, and then enter the city, description, or location in the text box. Once you search, look under **Select emergency address** to pick the right one for you.

6. Click **Save** and your user should look like this:

   ![Screenshot shows sample user license assignment.](media/set-up-common-area-phone-image3.png)

> [!NOTE]
> Users will only show up if they have a Phone System license applied. If you just did this, then sometimes it takes a bit for the user to show up in the list.

For more information, see [Getting phone numbers for your users](getting-phone-numbers-for-your-users.md).

You can also take your phone number that you have with another carrier and "port" or transfer it over to Microsoft 365 or Office 365. See [Transfer phone numbers to Teams](phone-number-calling-plans/transfer-phone-numbers-to-teams.md).
