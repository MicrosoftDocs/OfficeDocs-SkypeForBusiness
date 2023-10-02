---
ms.date: 03/17/2018
title: "Registrar SBA Settings Expander"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
f1.keywords:
- CSH
ms.custom:
- ms.lync.tb.RegistrarSBASettingsExpander
ms.service: skype-for-business-server
ms.localizationpriority: medium
ms.assetid: 68ea1fc0-9cd1-4e0a-995e-b53845493477
ROBOTS: NOINDEX, NOFOLLOW
description: "You edit the settings for Resiliency and configure the following properties:"
---

# Registrar SBA Settings Expander

You edit the settings for **Resiliency** and configure the following properties:

- Select **Associated User service and backup Registrar pool** from the list.

    Optionally, select the **Automatic failover and failback for Voice** check box.

    Configure the **Voice failure detection interval (sec)** and the **Voice failback interval (sec)**. By default, the intervals are 120 seconds for Voice failure detection and 240 seconds for Voice failback.

    > [!CAUTION]
    > The number of seconds that you define for the failover and failback intervals should be carefully tested to ensure that the resiliency works as expected. Setting the interval to low (that is, less than 120 seconds) or the failover and failback set too closely may result in the actual failover and failback not working as expected.

  **OK** Accepts and commits changes to the dialog.

  **Cancel** Discards changes and closes the dialog.

  **Help** Displays this help screen.

## See also

[Planning for Enterprise Voice Resiliency](/previous-versions/office/lync-server-2013/lync-server-2013-planning-for-enterprise-voice-resiliency)
