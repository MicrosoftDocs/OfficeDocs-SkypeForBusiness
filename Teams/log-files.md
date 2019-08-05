---
title: Use log files in troubleshooting Microsoft Teams
ms.reviewer: 
author: LolaJacobsen
ms.author: lolaj
manager: serdars
ms.date: 09/25/2017
ms.topic: troubleshooting
ms.service: msteams
MS.collection: 
- Teams_ITAdmin_Help
- M365-collaboration
search.appverid: MET150
description: Learn about Debug, Media, and Desktop logs produced by Microsoft Teams, where they can be found, and how they can help with troubleshooting.
appliesto: 
- Microsoft Teams
---

Use log files in troubleshooting Microsoft Teams
=================================================

There are three types of log files automatically produced by the client that can be leveraged to assist in troubleshooting Microsoft Teams.

-   Debug logs

-   Media logs

-   Desktop logs

When creating a support request with Microsoft Support, the support engineer will require the debug logs. Having these logs on hand before creating the support request will allow Microsoft to quickly start troubleshooting the problem. Media or desktop logs are only required if requested by Microsoft.

The following table outlines the various clients, and their associated logs. Log files are stored in locations specific to the client and operating system.


|Client |Debug|Desktop|Media|
|---------|---------|---------|---------|
|Web    |X         |-         |-         |
|Windows     |X         |X         |X         |
|Mac OSX     |X         |X         |X         |
|iOS     |-         |-         |-         |
|Android     |-         |-         |-         |

For a complete list of supported operating systems and browsers, see [Get clients for Microsoft Teams](get-clients.md).

Debug logs
---------------------------

These are the most common logs and are required for all Microsoft support cases. Debug logs are produced by the Windows and Mac desktop clients, as well as browser based clients. The logs are text based and are read from the bottom up. They can be read using any text based editor and new logs are created when logging into the client.

Debug logs show the following data flows:

-   Login

-   Connection requests to middle tier services

-   Call/conversation

The debug logs are produced using the following OS specific methods:

-   Windows:

      Keyboard shortcut: Ctrl + Alt + Shift + 1

-   Mac OSX:

      Keyboard shortcut: Option + Command + Shift+1

The debug logs are automatically downloaded to the following folders.

-   Windows: %userprofile%\\Downloads

-   Mac OSX: Downloads

-   Browser: You will be prompted to save the debug log to default save location

Media Logs
---------------------------

Media logs contain diagnostic data about audio, video and screen sharing. They are required for support cases only upon request and can only be inspected by Microsoft. The following table outlines the log location.


|Client |Location |
|---------|---------|
|Windows     |%appdata%\Microsoft\Teams\media-stack\\*.blog         |
|            |%appdata%\Microsoft\Teams\skylib\\*.blog
|            |%appdata%\Microsoft\Teams\media-stack\\*.etl         |
|Mac OSX     |~/Library/Application Support/Microsoft/Teams/media-stack/*.blog         |
|            |~/Library/Application Support/Microsoft/Teams/skylib/*.blog         |



Desktop logs
---------------------

Desktop logs, also known as bootstrapper logs, contains log data that occurs between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text based and can be read using any text based editor in a top down format.

Windows:

1.  Right-click **the Microsoft Teams icon in** your application tray, select **Get Logs**

Mac OsX:

1.  Choosing **Get Logs** from the **Help** pull-down menu

|Client |Location |
|---------|---------|
|Windows     |%appdata%\Microsoft\Teams\logs.txt         |
|Mac OSX     |~/Library/Application Support/Microsoft/Teams/logs.txt         |
