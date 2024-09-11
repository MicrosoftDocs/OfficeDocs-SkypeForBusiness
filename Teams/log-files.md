---
title: Collect log files for monitoring and troubleshooting in Teams
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.reviewer: mastank
ms.date: 09/11/2024
audience: admin
ms.topic: troubleshooting
ms.service: msteams
f1.keywords:
- NOCSH
ms.collection:
  - M365-collaboration
ms.custom: 
- asset-status-active
search.appverid: MET150
description: Learn about collecting Teams logs for support engineers, where they can be found, and how they can help with monitoring and troubleshooting.
appliesto:
  - Microsoft Teams
---

# Collect Teams client diagnostic logs for Microsoft support

There are two types of logs that are automatically created upon request, which can be used to assist Microsoft support in troubleshooting Teams.

- MS Teams Support Log Files, which contain media and signaling logs in addition to platform logs (not created when collecting logs while using the Teams browser client).
- Weblogs, which contain application event logs. You may see multiple weblog files depending on the types of users logged in and using the client (when using the Teams browser client, there will only be one log).
  - Public Enterprise  = Prod-Weblogs
  - Public Consumer = Life-Weblogs
  - GCCH = GCCH-Weblogs
  - DOD = DOD-Weblogs

> [!NOTE]
> The media and signaling logs are encrypted and can only be decrypted by Microsoft Support. Weblogs are text files and readable by any text editor. Additionally, performance enhancements have made it possible to always enable media logging. Accordingly, the administrative policy to control media logging has been deprecated.

## Logs overview

It’s important to collect logs as soon as an issue occurs.

> [!NOTE]
> To preserve disk space, the size of logs files for Microsoft Teams Virtual Desktop (VDI) clients is limited by default. If an issue is encountered on a VDI client, turn **Extended Logging** on in Teams Privacy settings before reproducing the issue and collecting logs.

When creating a support request with Microsoft Support, the support engineer will require the diagnostic logs. Having the diagnostic logs on hand before creating the support request will allow Microsoft to quickly start troubleshooting the problem.

> [!NOTE]
> Times in logs are recorded in Coordinated Universal Time (UTC). When opening a support case, be sure to inform the support agent of the time difference between the local time the issue occurred, and UTC time.

## Log collection

Both sets of logs will be collected in the Downloads folder by default. The Prod-Weblogs will already be compressed, but the MS Teams Support Log Files will need to be compressed before uploading to Microsoft Support.

To collect logs for Windows: 

- Select the Microsoft Teams icon in your system tray and then select **Collect support files**, or use the Ctrl + Alt + Shift + 1 keyboard shortcut.

To collect logs for Mac: 

- Select the **Help** menu in Microsoft Teams and then select **Collect support files**, or use the Option + Command + Shift + 1 keyboard shortcut.

> [!NOTE]
> Wait until the banner showing **Downloading web logs** is dismissed from the Teams client before retrieving logs from the download location. To collect logs from Teams browser client, use the keyboard shortcut.
