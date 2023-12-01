---
title: Set up Microsoft Teams Rooms consoles through one-time passwords
ms.author: tonysmit
author: tonysmit
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
  - teams-rooms-consoles
  - Tier1
ms.custom: seo-marvel-apr2020
ms.assetid: 678689e4-d547-499b-be64-7d8f16dd8668
description: Read this article to learn about how to set up Microsoft Teams Rooms consoles for the first time.
---

# Set up Microsoft Teams Rooms consoles using one-time passwords

This article describes how you can set up Microsoft Teams Rooms consoles for the first time.

During the first time you set up a console, you can set up Teams Rooms consoles using one of the two methods:

- [Set up consoles using a one-time password](#set-up-consoles-through-one-time-password)
- [Set up consoles manually](#set-up-consoles-manually)

## Set up consoles using a one-time password

To set up consoles by using a one-time password, perform the following steps:

1. Sign in to the Microsoft Teams Rooms Pro Management portal.
1. Unbox the Microsoft Teams Rooms console that you want to set up and plug it in. The **Welcome** page appears on the console.

   :::image type="content" source="../media/welcome-screen.png" alt-text="Screenshot that shows the welcome screen a user sees when unboxing a device as part of the OOBE." lightbox="../media/welcome-screen.png":::

1. On the **Welcome** page, select **Get started**. The **End user agreement** page appears.

   :::image type="content" source="../media/eula-screen.png" alt-text="Screenshot that shows the End user agreement screen a user sees." lightbox="../media/eula-screen.png":::

   On selecting **Get started**, you might see a page that has a message stating that the device verification information couldn't be found. For information on how to troubleshoot this error, see [Device verification failure and troubleshooting](#device-verification-failure-and-troubleshooting).

1. On the **End user agreement** page, select **Accept**. The **Set up Microsoft Teams Room account** page will appear.

   :::image type="content" source="../media/otp-screen.png" alt-text="Screenshot that shows the one-time password the user has to enter to sign in the device." lightbox="../media/otp-screen.png":::

   For information on how to get a one-time password from an IT administrator, see [Create a one-time password](create-otp.md#create-a-one-time-password).

   > [!NOTE]
   > If you don't have a one-time password, you can do the device setup manually. For more information, see [Set up consoles manually](#set-up-consoles-manually).

1. On the **Set up Microsoft Teams Room account** page, put in the one-time password that was provided to you by the IT administrator, and then select **Continue**.

   :::image type="content" source="../media/enter-otp-select-continue.png" alt-text="Screenshot that shows the boxes in which you must enter the OTP to sign in the device." lightbox="../media/enter-otp-select-continue.png":::

   The page displaying the sign-in status of the device appears.

   :::image type="content" source="../media/otp-status.png" alt-text="Screenshot that shows the status of the device sign in after the OTP has been entered." lightbox="../media/otp-status.png":::

    After you select **Continue**, a message on the page will tell you whether the one-time password has been approved automatically or is pending approval from an IT administrator.

   When the one-time password is approved - either automatically or by the IT administrator - this page will be displayed on the console that shows it was set up and then signed in successfully.

   :::image type="content" source="../media/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/device-signed-in-notification.png":::

## Set up consoles manually

If you don't have a one-time password, you can still set up a Teams Rooms console but you will need to do it manually.

The process of setting up consoles manually (without a one-time password) is the same as the Out Of Box Experience (OOBE), that is, the same as specified in [Set up consoles using one-time password](#set-up-consoles-through-one-time-password). However, you won't see:

- The page containing a notification message about device verification, which appeared when setting up the device through a one-time password.
  OR
- The **End user agreement** page.

To set up a Microsoft Teams Rooms console manually,  follow these steps:

1. Repeat Steps 1 through 4 in [Set up consoles through one-time password](#set-up-consoles-through-one-time-password). 

1. On the **Set up Microsoft Teams Room account** page, select **Manual setup**.

   :::image type="content" source="../media/manual-setup-option.png" alt-text="Screenshot that shows the OTP screen in which the Manual setup option is available to select." lightbox="../media/manual-setup-option.png":::

   The **Account setup** page appears.

1. On the **Account setup** page, put in the email and password that is used for the console or device in the **Email** and **Password** fields. If you don't know what those are, please contact your IT admin. You must enable the **Modern authentication** option.

   :::image type="content" source="../media/account-information-manual-setup.png" alt-text="Screenshot that shows the Account screen in which the user must enter credentials." lightbox="../media/account-information-manual-setup.png":::

1. Select **Finish**. The page displayed in the following screenshot appears, showing that the console was set up and then signed in successfully.

   :::image type="content" source="../media/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/device-signed-in-notification.png":::

### Device verification failure and troubleshooting

The device verification is an automatic process. However, sometimes the process may fail and you'll see the following page:

:::image type="content" source="../media/device-verification-screen.png" alt-text="Screenshot that shows the error that occurred in the device verification process." lightbox="../media/device-verification-screen.png":::

If the device verification process fails, you can try one or more of the following troubleshooting options:

- Insert an HDMI Ingest module that came with the device.
- Contact your IT administrator.