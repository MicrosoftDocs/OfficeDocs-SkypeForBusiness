---
title: How to make Teams push notifications work in your Xiaomi phone?
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: divank
ms.date: 04/29/2024
ms.topic: article
ms.service: msteams
ms.subservice: itpro-devices
audience: Admin
appliesto: 
  - Microsoft Teams
ms.collection: 
  - teams-rooms-devices
  - Teams_ITAdmin_Devices
  - Tier1
f1.keywords: 
  - NOCSH
search.appverid: MET150
description: This article provides guidance on how to enable push notifications in your Xiaomi Android phones.
---

# How to make Teams push notifications work in your Xiaomi phone?

Microsoft Teams integrates with Mi push directly to optimize the push notification experience in Xiaomi devices, but it needs some specific configuration setup in Xiaomi phone to turn on the Mi push. Use this article to learn how to set up the configuration in Xiaomi phones and about the known limitation you may experience.

## Configure Mi push in Xiaomi Android phones

To configure the Mi push in Xiaomi Android phones, perform the following steps:

> [!NOTE]
> The notification configuration panel under **Setting** might be different in different Xiaomi phone series and in different MIUI versions.

1. Download the Teams application from Xiaomi Application Store.
1. Install the Teams application.
1. Sign in to Teams using your Office 365 account.
1. Launch the **Setting** application.
1. Select **Notifications & Control Center > App Notification > Teams**.
1. Ensure all the options that enable display of notifications are checked.
1. Scroll down to the bottom of this configuration page for Teams application, find and select **Mi Push (小米推送)**.
   > [!NOTE]
   > You may not be able to find the **Operational message** in the configuration panel. Hence, perform the steps specified in [Activate Operational message](#activate-operational-message).

1. Enable all permissions associated with  the operational message.

### Activate operational message

To activate the operational message, perform the following steps:

1. Sign in to Teams with your Office 365 account.
1. Close Teams.
1. Restart Teams.
1. Send several chat messages from another Office 365 account to this account (the signed-in Teams account) OR, reboot your Xiaomi mobile device.

## Limitations

There are several limitations in the solution that configures Mi push to Xiaomi Android phones:

1. When Teams isn't in the foreground, Teams message notification includes just the generic information such as **You have received a message**.
1. The Teams Incoming call will have the notification message **Incoming call** only, unless you explicitly tap the incoming call notification to answer or reject the VOIP calls.
1. Behavior in Xiaomi devices/series with different Android or MIUI versions may be different due to the native Android or MIUI’s handling logic on notification.
1. After installing the new Teams client, you need to send several messages before you can see the operational message in your OS’ notification configuration panel for Teams.

   > [!NOTE]
   > Android 7 doesn’t support operational message.

