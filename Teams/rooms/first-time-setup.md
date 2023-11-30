---
title: Set up Microsoft Teams Rooms devices through one-time passwords
ms.author: v-smandalika
author: v-smandalika
manager: serdars
audience: ITPro
ms.reviewer: sohailta
ms.date: 10/26/2023
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
description: Read this article to learn about how to set up Microsoft Teams Rooms devices for the first time.
---

# Set up Microsoft Teams Rooms devices through one-time passwords

This article describes how you can set up Microsoft Teams devices for the first time.

You can set up Microsoft Teams Rooms devices for the first time through any of the following methods:

- [Set up devices through one-time password](#set-up-devices-through-one-time-password)
- [Set up devices manually](#set-up-devices-manually)

## Set up devices through one-time password

To set up devices by using a one-time password, perform the following steps:

1. Sign in to the Microsoft Teams Rooms portal.
1. Unbox the Microsoft Teams Rooms device(s) that you want to deploy. The "welcome" page appears.

   :::image type="content" source="../media/welcome-screen.png" alt-text="Screenshot that shows the welcome screen a user sees when unboxing a device as part of the OOBE." lightbox="../media/welcome-screen.png":::


1. Select **Get started**. The **End user agreement** page appears.

   :::image type="content" source="../media/eula-screen.png" alt-text="Screenshot that shows the End user agreement screen a user sees." lightbox="../media/eula-screen.png":::


   On selecting **Get started**, you might be presented with a page that contains a message stating that the device verification information couldn't be found. For information on how to troubleshoot in this scenario, see [Device verification failure and troubleshooting](#device-verification-failure-and-troubleshooting).

1. Select **Accept**. The page on which you're to enter the one-time password appears.

   :::image type="content" source="../media/otp-screen.png" alt-text="Screenshot that shows the one-time password the user has to enter to sign in the device." lightbox="../media/otp-screen.png":::

   For information on how to procure the one-time password from the IT administrator, see [Create a one-time password](create-otp.md#create-a-one-time-password).

1. Enter the one-time password provided to you by the IT administrator, and select **Continue**.

   :::image type="content" source="../media/enter-otp-select-continue.png" alt-text="Screenshot that shows the boxes in which you must enter the OTP to sign in the device." lightbox="../media/enter-otp-select-continue.png":::

   > [!NOTE]
   > If you don't have a one-time password, you can do the device setup manually. For more information, see [Set up devices manually](#set-up-devices-manually).

   The page displaying the sign-in status of the device appears.

   :::image type="content" source="../media/otp-status.png" alt-text="Screenshot that shows the status of the device sign in after the OTP has been entered." lightbox="../media/otp-status.png":::

   The notification message on the page indicates whether the one-time password has been approved automatically or is pending for approval from the IT administrator.

   Once the one-time password is approved - either automatically or by the IT administrator - you'll see the page displayed in the following screenshot:

   :::image type="content" source="../media/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/device-signed-in-notification.png":::

## Set up devices manually

You can set up Teams Rooms devices manually if you don't have a one-time password.

The process of setting up devices manually (without an OTP) is the same as the Out Of Box Experience (OOBE), that is, the same as specified in [Set up devices through one-time password](#set-up-devices-through-one-time-password), with the difference being that you won't see:

- The page containing a notification message about device verification, which appeared when setting up the device through a one-time password.
- The **End user agreement** page.

To set up the Microsoft Teams Rooms devices manually, perform the following steps:

1. Repeat Steps 1-4 in [Set up devices through one-time password](#set-up-devices-through-one-time-password).
1. Select **Manual setup** from the one-time password screen.

   :::image type="content" source="../media/manual-setup-option.png" alt-text="Screenshot that shows the OTP screen in which the Manual setup option is available to select." lightbox="../media/manual-setup-option.png":::

   The **Account setup** page appears.

1. Enter your username and password in the **Email** and **Password** fields, respectively, and enable the **Modern authentication** option.

   :::image type="content" source="../media/account-information-manual-setup.png" alt-text="Screenshot that shows the Account screen in which the user must enter credentials." lightbox="../media/account-information-manual-setup.png":::

1. Select **Finish**. The page displayed in the following screenshot appears, indicating that the manual setup process has been successfully completed, and that the device has successfully signed in.

   :::image type="content" source="../media/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/device-signed-in-notification.png":::

### Device verification failure and troubleshooting

The device verification is an automatic process. However, sometimes the process fails, in which case, you'll see the following page:

:::image type="content" source="../media/device-verification-screen.png" alt-text="Screenshot that shows the error that occurred in the device verification process." lightbox="../media/device-verification-screen.png":::

If the device verification process fails, you can implement the following troubleshooting options:

- Insert an HDMI Ingest module that came with the device
- Contact your IT administrator
