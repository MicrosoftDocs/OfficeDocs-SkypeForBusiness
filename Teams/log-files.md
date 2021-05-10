---
title: Use log files in troubleshooting Microsoft Teams
ms.reviewer: tejeshs
author: CarolynRowe
ms.author: crowe
manager: serdars
ms.date: 05/06/2021
audience: admin
ms.topic: troubleshooting
ms.service: msteams
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
search.appverid: MET150
description: Learn about Debug, Media, and Desktop logs produced by Microsoft Teams, where they can be found, and how they can help with monitoring and troubleshooting.
appliesto: 
  - Microsoft Teams
---

# Use log files to monitor and troubleshoot Microsoft Teams

There are three types of log files automatically produced by the client, which can be leveraged to assist in monitoring and troubleshooting Teams:

-   [Debug logs](#debug-logs)

-   [Media logs](#media-logs)

-   [Desktop logs](#desktop-logs)

This article describes the three logs and how they are used. 

For information about troubleshooting specific issues, see: [Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams). For information about how to contact support, see [Get support](/microsoft-365/business-video/get-help-support).

When creating a support request with Microsoft Support, the support engineer will require the debug logs. Having the debug logs on hand before creating the support request will allow Microsoft to quickly start troubleshooting the problem. **Media** or **Desktop** logs are only required if requested by Microsoft.

> [!NOTE]
> In this article, the term **Debug logs** refers to the logs that are used for troubleshooting. However, the files that are generated for these logs will contain the term **diagnostic logs** in their names.  

The following table outlines the various clients and their associated logs. Log files are stored in locations specific to the client and operating system.


|Client |Debug|Desktop|Media|
|---------|---------|---------|---------|
|Web    |X         |-         |-         |
|Windows     |X         |X         |X         |
|Mac OSX     |X         |X         |X         |
|Linux     |X         |X         |X         |
|iOS     |-         |-         |-         |
|Android     |-         |-         |-         |

For a complete list of supported operating systems and browsers, see [Get clients for Microsoft Teams](get-clients.md).

## Debug logs

These are the most common logs and are required for all Microsoft support cases. Debug logs are produced by the Windows and Mac desktop clients, as well as by browser-based clients. The logs are text based and are read from the bottom-up. They can be read using any text-based editor, and new logs are created when logging into the client.

Debug logs show the following data flows:

-   Login

-   Connection requests to middle-tier services

-   Call/conversation

The debug logs are produced using the following OS-specific methods:

-   Windows:

      Keyboard shortcut: Ctrl + Alt + Shift + 1

-   Mac OSX:

      Keyboard shortcut: Option + Command + Shift+1

-   Linux:

      Keyboard shortcut: Ctrl + Alt + Shift + 1

The debug logs are automatically downloaded to the following folders:

-   Windows: %userprofile%\\Downloads

-   Mac OSX: ~/Downloads

-   Linux: ~/Downloads

-   Browser: You will be prompted to save the debug log to default save location

## Media logs

Media logs contain diagnostic data about audio, video, and screen sharing in Teams meetings. They are required for support cases that are linked to call-related issues.

Media logging is turned off by default. To log diagnostic data for Teams meetings, users must turn on the option in the Teams client. Go to **Settings** > **General**, select the **Enable logging for meeting diagnostics (requires restarting Teams**) check box, restart Teams, and reproduce the issue. 

The following table outlines the media log locations. When you send the log files to Microsoft support, please verify the timestamp of the log files to ensure the logs cover the time frame when you reproduced the issue.

|Client |Location |
|---------|---------|
|Windows     |%appdata%\Microsoft\Teams\media-stack\\*.blog         |
|            |%appdata%\Microsoft\Teams\skylib\\*.blog
|            |%appdata%\Microsoft\Teams\media-stack\\*.etl         |
|Mac OSX     |~/Library/Application Support/Microsoft/Teams/media-stack/*.blog         |
|            |~/Library/Application Support/Microsoft/Teams/skylib/*.blog         |
|Linux       |~/.config/Microsoft/Microsoft Teams/media-stack/*.blog         |
|            |~/.config/Microsoft/Microsoft Teams/skylib/*.blog         |

Here's a list of the log files that are generated and the information they contain.

|Log file name  |Description  |
|---------|---------|
|Teams.msrtc-0-s1039525249.blog     | Contains information related to the media stack. This includes channel status such as resolution, decoders and encoders used, and the number of frames sent and received, and camera and video-based screen sharing (VBSS) session status.         |
|rtmcontrol.msrtc-0-2415069487.blog      |Records information related to remote control actions, such as the time stamp when control is given, and mouse pointer information.          |
|Teams_MediaStackETW-2-U-xr-U.etl      |Records media stack trace events.         |
|Debug-0-s2790420889.blog    | Contains information related to the media agent, including rendering quality.          |
|tscalling-0-2061129496.blog   |Records events in the ts-calling API.       |

## Desktop logs

Desktop logs, also known as bootstrapper logs, contain log data that occurs between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text based and can be read using any text-based editor in a top-down format.

Windows:

 - Right-click the **Microsoft Teams** icon in your system tray, and select **Get Logs**.

Mac OsX:

 - Choose **Get Logs** from the **Help** pull-down menu.

Linux:

 - Click on the **Microsoft Teams** icon in your system tray, and select **Get Logs**.

|Client |Location |
|---------|---------|
|Windows     |%appdata%\Microsoft\Teams\logs.txt         |
|Mac OSX     |~/Library/Application Support/Microsoft/Teams/logs.txt         |
|Linux       |~/.config/Microsoft/Microsoft Teams/logs.txt         |


Browser trace
---------------------------

For some categories of errors, Microsoft Support might require you to collect a browser trace. This information can provide important details about the state of the Teams client when the error occurs.

Before you start the browser trace, make sure that you’re signed in to Teams. It's important to do this before you start the trace so that the trace doesn't contain sensitive sign-in information.

After you’re signed in, select one of the following links, as appropriate for your browser, and follow the provided steps. 

-   [Chrome & Edge (Chromium)](/azure/azure-portal/capture-browser-trace#google-chrome-and-microsoft-edge-chromium?preserve-view=true#resolution)

-   [Edge](/azure/azure-portal/capture-browser-trace#microsoft-edge-edgehtml?preserve-view=true#resolution)

-   [Safari](/azure/azure-portal/capture-browser-trace#apple-safari?preserve-view=true#resolution)

-   [Firefox](/azure/azure-portal/capture-browser-trace#firefox?preserve-view=true#resolution)

> [!NOTE]
> In the steps, replace all references to the Azure portal with the Teams client. 

## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
