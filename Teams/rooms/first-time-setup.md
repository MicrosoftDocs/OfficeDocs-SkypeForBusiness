---
title: Setting up Microsoft Teams Rooms devices for the first time
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

# Setting up Microsoft Teams Rooms devices for the first time

This article describes how you can set up Microsoft Teams devices for the first time.

You can set up Microsoft Teams Rooms devices for the first time through any of the following methods:

- [Set up devices through OTP](#set-up-devices-through-otp)
- [Set up devices manually](#set-up-devices-manually)

## Set up devices through OTP

To set up devices by using an OTP, perform the following steps:

1. Sign in to Microsoft Teams Rooms portal.
1. Unbox the Microsoft Teams Rooms device(s) that you want to deploy. The "welcome" screen appears.

   :::image type="content" source="../media/welcome-screen.png" alt-text="Screenshot that shows the welcome screen a user sees when unboxing a device as part of the OOBE." lightbox="../media/welcome-screen.png":::


1. Select **Get started**. The **End user agreement** screen appears.

   :::image type="content" source="../media/eula-screen.png" alt-text="Screenshot that shows the End user agreement screen a user sees." lightbox="../media/eula-screen.png":::


   On selecting **Get started**, you might be presented with a screen that contains a message stating that the device verification process is a failure. For information on how to troubleshoot in this scenario, see [Device verification failure and troubleshooting](#device-verification-failure-and-troubleshooting).

1. Select **Accept**. The screen on which you're to enter the OTP (one-time passcode) appears.

   :::image type="content" source="../media/otp-screen.png" alt-text="Screenshot that shows the OTP the user has to enter to sign in the device." lightbox="../media/otp-screen.png":::

1. Enter the OTP provided to you by the IT administrator, and select **Continue**.

   :::image type="content" source="../media/enter-otp-select-continue.png" alt-text="Screenshot that shows the boxes in which you must enter the OTP to sign in the device." lightbox="../media/enter-otp-select-continue.png":::

   > [!NOTE]
   > If you don't have an OTP, you can do the device setup manually. For more information, see [Set up devices manually](#set-up-devices-manually).

   The screen displaying the status of the device sign in appears.

   :::image type="content" source="../media/otp-status.png" alt-text="Screenshot that shows the status of the device sign in after the OTP has been entered." lightbox="../media/otp-status.png":::

   This screen indicates whether the OTP has been approved automatically or whether the OTP is pending for approval from the IT administrator.

   Once the OTP is approved - either automatically or by the IT administrator - you'll see the following screen:

   :::image type="content" source="../media/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/device-signed-in-notification.png":::

## Set up devices manually

You can set up Teams Rooms devices manually if you don't have an OTP.

The process of setting up devices manually (without an OTP) is the same as the Out Of Box Experience (OOBE), that is, the same as specified in [Set up devices through OTP](#set-up-devices-through-otp), with the difference being that you won't see:

- The screen containing a notification regarding device verification, which appeared when setting up the device through an OTP.
- The **End user agreement** screen.

To set up the Microsoft Teams Rooms devices manually, perform the following steps:

1. Repeat Steps 1-4 in [Set up devices through OTP](#set-up-devices-through-otp).
1. Select **Manual setup** from the OTP screen.

   :::image type="content" source="../media/manual-setup-option.png" alt-text="Screenshot that shows the OTP screen in which the Manual setup option is available to select." lightbox="../media/manual-setup-option.png":::

   The **Account** screen appears.

1. Enter your username and password in the **Email** and **Password** fields, respectively, and enable the **Modern authentication** option.

   :::image type="content" source="../media/account-information-manual-setup.png" alt-text="Screenshot that shows the Account screen in which the user must enter credentials." lightbox="../media/account-information-manual-setup.png":::

1. Select **Next**.  The **Advanced** screen appears.
1. Enter details such as your Exchange address and the domains to be configured.

   :::image type="content" source="../media/advanced-screen.png" alt-text="Screenshot that shows the Advanced screen in which the user must enter details." lightbox="../media/advanced-screen.png":::

1. Select **Next**. The **Finish** screen appears.

   :::image type="content" source="../media/finish-screen.png" alt-text="Screenshot that shows the Finish screen in which the user can complete the manual setup process." lightbox="../media/finish-screen.png":::

1. Select **Finish**.  The following screen appears, indicating that the manual setup process has been successfully completed, and that the device has successfully signed in.

   :::image type="content" source="../media/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/device-signed-in-notification.png":::

### Device verification failure and troubleshooting

The device verification is actually an automatic process. However, sometimes the process fails, in which case, you'll see the following screen:

:::image type="content" source="../media/device-verification-screen.png" alt-text="Screenshot that shows the error that occurred in the device verification process." lightbox="../media/device-verification-screen.png":::

If the device verification process fails, you can implement the following troubleshooting options:

- Insert an HDMI cable, and restart the device
- Contact your IT administrator

