---
title: Create a one-time password
ms.author: tonysmit
author: mstonysmith
manager: serdars
audience: ITPro
ms.reviewer: kramachandra
ms.date: 09/12/2024
ms.topic: quickstart
ms.service: msteams
ms.subservice: itpro-rooms
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
ms.custom: seo-marvel-apr2020
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: This article is for the IT administrator to learn about how to create a one-time password that will be shared with the system installer personnel.
---

# Create a one-time password

A one-time password (OTP) is used to provide authentication when someone is setting up and deploying Teams Rooms consoles that run on Windows without the need for a specific username and password used on the device. The one-time password is created in the Microsoft Teams Rooms Pro Management portal and only used for a single sign in session. Each Teams Rooms console you're deploying in your organization will need its own one-time password, else, its credentials will need to be added during a manual setup.

When someone is adding Microsoft Teams Rooms consoles to your organization, the one-time password will be used for device authentication instead of a username and password that in the past was required to set up the console.

## How to create a one-time password

To create a one-time password, perform the following steps:

1. Sign in to the Teams Rooms Pro Management portal.
1. On the left navigation pane, select **Planning > Resource Accounts**. The **Resource Accounts** page appears.
1. Select **Generate OTP** wizard on the command bar.

   The **Account selection** page appears.

1. Select the resource accounts for which you want to create a one-time password, and then select **Next**.

   > [!NOTE]
   > You must select a resource account for which the value in the **Readiness status** column is **No action needed**.
   > You can also search for specific resource accounts using the search bar. You just have to ensure that whatever is the resource account that you've searched for, that resource account should have the value **No action needed** in its **Readiness status** column.

   The **Configuration** page appears.

   :::image type="content" source="../media//mtr-devices/configuration-screen.png" alt-text="Screenshot that shows the Configuration page." lightbox="../media/mtr-devices/configuration-screen.png":::
  
1. Select if you would like to **Automatically generate passwords for all selected accounts** OR **Upload sign in data from CSV file**.

    1. Select the **Automatically generate passwords for all selected accounts** option if you want to reset/delete the existing password for the resource accounts for which you're   generating a one-time password.
    2. Select **Upload sign in data from CSV file** if you want to retain the existing password for the resource accounts in which you're generating a one-time password.

1. Select **Next**. The **Review** page appears.

   :::image type="content" source="../media//mtr-devices/review-screen.png" alt-text="Screenshot that shows the Review page." lightbox="../media/mtr-devices/review-screen.png":::

1. Review the settings you have configured, and then select **Generate**.

   > [!NOTE]
   > On the **Review** page, if you want to edit the **Auto generate passwords** setting, select the **Edit** icon next to **Configuration** or if you want to change the resource accounts for which you want to create a one-time password, select the **Edit** icon next to **Account selection**. Then, select **Generate**.

1. Once you've generated the OTP you're presented with the option to download the OTPs with or without the resource account passwords so you can save this information and share it with whomever might be setting up your devices.

## Verify and approve/reject one-time password

You can verify and approve a one-time password that was entered by the setup personnel while trying to sign in their Teams Rooms console into the app.

To verify and approve a one-time password, do the following:

1. Sign in to the Teams Rooms Pro Management portal.
1. On the left navigation pane, select **Planning > Resource Accounts**. The **Resource Accounts** page appears.
1. Select a resource account that has the value **Awaiting OTP Approval**.

   :::image type="content" source="../media/mtr-devices/resource-account-provisioning-status.png" alt-text="Screenshot that shows the page on which you select a resource account that has awaiting one-time password approval as its provisioning status." lightbox="../media/mtr-devices/resource-account-provisioning-status.png":::

   The page displaying the details of the chosen resource account appears.

1. Select the **OTP** tab. The page displaying the details of the one-time password appears.
1. Verify the details such as:
   - The date when this one-time password was entered on the device, which is displayed in the **Requested date** column.
   - The expiration date, which is displayed in the **Expiration date** column.
   - The device-related information such as make, model, and serial number, which is displayed in the **Device information** pane.
1. Select the **Approve the request** button, if you want to approve the one-time password request.
1. Select the **Reject the request** button, if you want to reject the one-time password request.
    1. Provide the reason for rejecting the one-time password request by choosing a value from the **Reason for rejection** drop-down.

   :::image type="content" source="../media/mtr-devices/select-reason-for-rejection.png" alt-text="Screenshot that shows the page on which you choose the reason for rejecting the OTP request." lightbox="../media/mtr-devices/select-reason-for-rejection.png":::

1. Select **Submit**.

## Modify the one-time passcode expiration or enable OTP auto approval

By default the OTP is valid for 8 hours, however you can adjust the validity period of the OTP to be up to 2 weeks (336 hours).  You can also choose to automatically approve OTPs instead of needing to select the approve button as the IT admin.

To change these settings:
1. Sign in to the Teams Rooms Pro Management portal.
2. In the left navigation pane, select **Planning > Resource Accounts**. The **Resource Accounts** page appears.
3. Select **Preferences** on the command bar.
4. Adjust the OTP expiration by selecting from the predefined hours or set a custom expiration (between 1 hour and 336 hours).
5. You can also toggle **OTP Auto approval** on or off.
6. Select **Save** when you're done to save your changes.
