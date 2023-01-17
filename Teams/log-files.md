---
title: Configure log files for monitoring and troubleshooting in Teams
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

# Configure log files for monitoring and troubleshooting in Teams

There are three types of log files automatically produced by the client, which can be leveraged to assist in monitoring and troubleshooting Teams:

-   [Debug logs](#debug-logs)

-   [Media logs](#media-logs)

-   [Desktop logs](#desktop-logs)

This article describes these logs and how they are used. For information about troubleshooting specific issues, see: [Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams). 

For information on collecting logs from Microsoft Teams Rooms devices, see [Download device logs](/microsoftteams/rooms/rooms-manage#download-device-logs).

For information about how to contact support, see [Get support](/microsoft-365/business-video/get-help-support).

> [!NOTE]
> In this article, the term **Debug logs** refers to the logs that are used for troubleshooting. However, the files that are generated for these logs will contain the term **diagnostic logs** in their names.  

## Logs overview

It’s important to collect logs as soon as an issue occurs.

When creating a support request with Microsoft Support, the support engineer will require the debug logs. Having the debug logs on hand before creating the support request will allow Microsoft to quickly start troubleshooting the problem. **Media** or **Desktop** logs are only required if requested by Microsoft.

Debug, Desktop, and Media logs will be collected in one folder with the name _MSTeams Diagnostics Log \<local date and time\>_. This folder can be compressed and shared when you open a support request with Microsoft Support. The folder will contain folders for Desktop, Meeting (Media), and Debug (web). You can collect the files using the following keyboard shortcuts:

- Windows:
  <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>

- Mac:
  <kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>


If a problem occurs with a specific meeting or live event, it's helpful to have the URL associated with the meeting. The URL provides additional information to help pinpoint the exact meeting or live event in the logs. This information can be collected from any participant for a meeting or from presenter or producer for a live event. This URL can be captured by hovering over the join URL and choosing **Copy Hyperlink**.

> [!NOTE]
> If Media logging is enabled, there will be additional files included in the Meeting folder which are necessary for investigating audio and video issues. If Media logging is not enabled, there will be a limited number of logs available.
  
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

Debug logs are produced by the Windows and Mac desktop clients, as well as by browser-based clients. The logs are text-based and are read from the bottom-up. They can be read using any text-based editor, and new logs are created when logging into the client.

Debug logs show the following data flows:

-   Login

-   Connection requests to middle-tier services

-   Call/conversation

To collect logs for Linux:
- Keyboard shortcut: <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>  
- The files will be available in `~/Downloads`

To collect logs for Browser and Windows:
- Keyboard shortcut: <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>  
- The files will be available in `%userprofile%\Downloads`

To collect logs for Mac:
- Keyboard shortcut: <kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>  
- The files will be available in `~/Downloads`

## Media logs

Media logs contain diagnostic data about audio, video, and screen sharing in Teams meetings. They are required for support cases that are linked to call-related issues.

Media logging is turned on by default for computers if your CPU is:
- any Apple M1
- any Intel Xeon
- any Intel i9, except for the U, G7, M, and MQ series
- any 6th generation and later Intel i7, except for the U, G7, M, and MQ series

Otherwise, it is turned off by default. There are two ways to log diagnostic data for Teams meetings:

- Admin configuration- you can manage Media logs for your end users
- End user configuration- your end users can turn on Media logs

### Admin configuration

Managing Media logs for your end users provides a seamless troubleshooting experience, especially when issues are intermittent. Admins can use the TeamsMediaLoggingPolicy cmdlet to  enable and manage Media logging for users.

Read [Grant-CsTeamsMediaLoggingPolicy](/powershell/module/teams/grant-csteamsmedialoggingpolicy) for PowerShell cmdlets and more information.

### End user configuration

For your end users to log diagnostic data for Teams meetings, they must turn on the option in the Teams client. They will go to **Settings** > **General**, select the **Enable media logs (diagnostic data for audio, video, and screen sharing)** check box, and reproduce the issue.

> [!NOTE]
> When your users sign out of Teams, Media logging resets to its default.

### Collecting and sending Media logs

Before you send the log files to Microsoft support, verify the timestamp of the log files to ensure the logs cover the time frame when you reproduced the issue.

To collect logs for Linux:  
- The files will be available in the following locations:
  - `~/.config/Microsoft/Microsoft Teams/media-stack/\*\.blog`
  - `~/.config/Microsoft/Microsoft Teams/skylib/\*\.blog`

To collect logs for Windows:  
- The files will be available in the following locations:
  - `%appdata%\Microsoft\Teams\media-stack\\\*\.blog`
  - `%appdata%\Microsoft\Teams\skylib\\\*\.blog` 

To collect logs for Mac:
- The files will be available in the following locations:
  - `~/Library/Application Support/Microsoft/Teams/media-stack\\\*\.blog`
  - `~/Library/Application Support/Microsoft/Teams/skylib\\\*\.blog`

Here's a list of the log files that are generated and the information they contain.

<br/>

|Log file name  |Description  |
|---------|---------|
|`Teams.msrtc-0-s1039525249.blog`     | Contains information related to the media stack. This includes channel status such as resolution, decoders and encoders used, and the number of frames sent and received, and camera and video-based screen sharing (VBSS) session status.         |
|`rtmcontrol.msrtc-0-2415069487.blog`      |Records information related to remote control actions, such as the time stamp when control is given, and mouse pointer information.          |
|`Teams_MediaStackETW-2-U-xr-U.etl`      |Records media stack trace events.         |
|`Debug-0-s2790420889.blog`    | Contains information related to the media agent, including rendering quality.          |
|`tscalling-0-2061129496.blog`   |Records events in the ts-calling API.       |

## Desktop logs

Desktop logs, also known as bootstrapper logs, contain log data that occurs between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text-based and can be read using any text-based editor in a top-down format.

To collect logs for Linux:
- Click on the Microsoft Teams icon in your system tray, and select **Get Logs**.
- The files will be available in `~/.config/Microsoft/Microsoft Teams/logs.txt`.

To collect logs for Mac:
- Click the Help menu in Microsoft Teams, and select **Collect support files**.
- The `logs.txt` file will be in the Desktop folder inside the _MSTeams Diagnostics Log \<local date and time>_ folder.

To collect logs for Windows:
- Click the Microsoft Teams icon in your system tray, and select **Collect support files**.
- The `logs.txt` file will be opened in Notepad automatically.

When investigating problems signing into Teams, you might need to manually collect the desktop logs. These log files are located at %appdata%\Microsoft\Teams in Windows.

## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)

[Browser logs and tracing for Teams](/MicrosoftTeams/browser-logs-and-tracing-for-teams)
