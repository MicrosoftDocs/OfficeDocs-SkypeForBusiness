---
title: Use log files in troubleshooting Microsoft Teams
ms.reviewer: tejeshs
author: SerdarSoysal
ms.author: serdars
manager: serdars
ms.date: 09/25/2017
audience: admin
ms.topic: troubleshooting
ms.service: msteams
f1.keywords:
- NOCSH
ms.collection: 
  - M365-collaboration
search.appverid: MET150
description: Learn about Debug, Media, and Desktop logs produced by Microsoft Teams, where they can be found, and how they can help with troubleshooting.
appliesto: 
  - Microsoft Teams
---

Use log files in troubleshooting Microsoft Teams
=================================================

There are three types of log files automatically produced by the client, which can be leveraged to assist in troubleshooting Microsoft Teams:

-   Debug logs

-   Media logs

-   Desktop logs

Collect and enable logging
---------------------------

It’s important to collect logs as soon as an issue occurs. The logs can be collected together with just a couple of clicks.

Windows:
Right-click on the Teams icon in the system tray and choose **Collect support files**. 

Mac:
Select the Help menu and choose **Collect support files**.

Debug, Desktop, and Media logs will be collected in one folder with the name MSTeams Diagnostics Log <local data and time>. This folder can be compressed and shared when you open a support request with Microsoft Support. The folder will contain folders for Desktop, Meeting (Media), and Debug (web). You can collect the files using the following keyboard shortcuts:

Windows
Crtl + Alt + Shift + 1

Mac
Option + Command + Shift + 1

Media logging is turned off by default. To enable Media logging, users must turn on the option in the Teams client. Go to Settings > General, select the Enable logging for meeting diagnostics (requires restarting Teams). The Teams client must be restarted for logging to begin.

> [!NOTE]
>  If Media logging is enabled there will be additional files included in the Meeting folder which are necessary for investigating audio and video issues. If Media logging isnot enabled there will be a limited number of logs available.


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

Debug logs
---------------------------

See the	Collect and enable logging section for Windows and Mac instrutions. Debug logs are produced by the Windows and Mac desktop clients, as well as by browser-based clients. The logs are text based and are read from the bottom-up. They can be read using any text-based editor, and new logs are created when logging into the client.

Debug logs show the following data flows:

-   Login

-   Connection requests to middle-tier services

-   Call/conversation

To collect logs for Linux:
      Keyboard shortcut: Ctrl + Alt + Shift + 1
      The files will be available in ~/Downloads

To collect logs for Browser:
      Keyboard shortcut: Crtl + Alt + Shift + 1
      The files will be available in %userprofile%\Downloads

Media logs
---------------------------

See the	Collect and enable logging section for Windows and Mac instrutions. Media logs contain diagnostic data about audio, video, and screen sharing in Teams meetings. They are required for support cases that are linked to call-related issues.

Media logging is turned off by default. To log diagnostic data for Teams meetings, users must turn on the option in the Teams client. Go to **Settings** > **General**, select the **Enable logging for meeting diagnostics (requires restarting Teams**) check box, restart Teams, and reproduce the issue. 

The following table outlines the media log locations. When you send the log files to Microsoft support, please verify the timestamp of the log files to ensure the logs cover the time frame when you reproduced the issue.

To collect logs for Linux:
The files will be available ~/.config/Microsoft/Microsoft Teams/media-stack/*.blog and ~/.config/Microsoft/Microsoft Teams/skylib/*.blog.

Here's a list of the log files that are generated and the information they contain.

|Log file name  |Description  |
|---------|---------|
|Teams.msrtc-0-s1039525249.blog     | Contains information related to the media stack. This includes channel status such as resolution, decoders and encoders used, and the number of frames sent and received, and camera and video-based screen sharing (VBSS) session status.         |
|rtmcontrol.msrtc-0-2415069487.blog      |Records information related to remote control actions, such as the time stamp when control is given, and mouse pointer information.          |
|Teams_MediaStackETW-2-U-xr-U.etl      |Records media stack trace events.         |
|Debug-0-s2790420889.blog    | Contains information related to the media agent, including rendering quality.          |
|tscalling-0-2061129496.blog   |Records events in the ts-calling API.       |

Desktop logs
---------------------

See the	Collect and enable logging section for Windows and Mac instrutions. Desktop logs, also known as bootstrapper logs, contain log data that occurs between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text based and can be read using any text-based editor in a top-down format.

To collect logs for Linux:
Click on the **Microsoft Teams** icon in your system tray, and select **Get Logs**.
The files will be available ~/.config/Microsoft/Microsoft Teams/logs.txt.  


## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
