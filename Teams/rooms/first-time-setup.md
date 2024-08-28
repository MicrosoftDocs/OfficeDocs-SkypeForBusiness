---
title: Set up Microsoft Teams Rooms consoles through one-time passwords
ms.author: tonysmit
author: mstonysmith
manager: pamgreen
audience: ITPro
ms.reviewer: sohailta
ms.date: 08/21/2024
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

- [Set up consoles using a one-time password](#set-up-consoles-using-a-one-time-password)
- [Set up consoles manually](#set-up-consoles-manually)

## Set up consoles using a one-time password

To set up consoles by using a one-time password, perform the following steps:

1. Sign in to the Microsoft Teams Rooms Pro Management portal.
1. Unbox the Microsoft Teams Rooms console that you want to set up and plug it in. The **Welcome** page appears on the console.

1. On the **Welcome** page, select **Get started**. The **End user agreement** page appears.

   On selecting **Get started**, you might see a page that has a message stating that the device verification information couldn't be found. For information on how to troubleshoot this error, see [Device verification failure and troubleshooting](#device-verification-failure-and-troubleshooting).

1. On the **End user agreement** page, select **Accept**. The **Set up Microsoft Teams Room account** page will appear.

   For information on how to get a one-time password from an IT administrator, see [Create a one-time password](create-otp.md#create-a-one-time-password).

   > [!NOTE]
   > If you don't have a one-time password, you can do the device setup manually. For more information, see [Set up consoles manually](#set-up-consoles-manually).

1. On the **Set up Microsoft Teams Room account** page, put in the one-time password that was provided to you by the IT administrator, and then select **Continue**.

   The page displaying the sign-in status of the device appears.

   After you select **Continue**, a message on the page will tell you whether the one-time password has been approved automatically or is pending approval from an IT administrator.

   When the one-time password is approved - either automatically or by the IT administrator - this page will be displayed on the console that shows it was set up and then signed in successfully.

   :::image type="content" source="../media/mtr-devices/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/mtr-devices/device-signed-in-notification.png":::

## Set up consoles manually

If you don't have a one-time password, you can still set up a Teams Rooms console but you'll need to do it manually.

The process of setting up consoles manually (without a one-time password) is the same as the Out Of Box Experience (OOBE), that is, the same as specified in [Set up consoles using one-time password](#set-up-consoles-using-a-one-time-password).

To set up a Microsoft Teams Rooms console manually,  follow these steps:

1. Repeat Steps 1 through 4 in [Set up consoles through one-time password](#set-up-consoles-using-a-one-time-password). 

1. On the **Set up Microsoft Teams Room account** page, select **Manual setup**.

   The **Account setup** page appears.

1. On the **Account setup** page, put in the email and password that is used for the console or device in the **Email** and **Password** fields. If you don't know what those are, please contact your IT admin.

1. Select **Finish**. The page displayed in the following screenshot appears, showing that the console was set up and then signed in successfully.

   :::image type="content" source="../media/mtr-devices/device-signed-in-notification.png" alt-text="Screenshot that shows the user that the device has been signed in." lightbox="../media/mtr-devices/device-signed-in-notification.png":::

### Device verification failure and troubleshooting

The device verification is an automatic process to ensure that the device being deployed is a certified Microsoft Teams Rooms device. However, sometimes the process may fail and you'll see an error message as depicted in the following screenshot:

If the device verification process fails, you can try one or more of the following troubleshooting options:

- Use the HDMI ingest module that came with the Teams Rooms console. Connect this HDMI ingest module to the Teams Rooms console and restart the console.
- If you continue to have problems after connecting the HDMI ingest module to the console, contact the manufacturer or the seller.
