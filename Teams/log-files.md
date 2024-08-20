---
title: Configure log files for monitoring and troubleshooting in Teams
ms.reviewer: tejeshs
author: MicrosoftHeidi
ms.author: heidip
manager: jtremper
ms.date: 07/18/2023
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

- [Debug logs](#debug-logs)
  - [Continuous Debug/Web logs](#continuous-debug-logs)
- [Media logs](#media-logs)
- [Desktop logs](#desktop-logs)

This article describes these logs and how they are used. For information about troubleshooting specific issues, see: [Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams).

For information on collecting logs from Microsoft Teams Rooms devices, see [Download device logs](/microsoftteams/rooms/rooms-manage#download-device-logs).

For information about how to contact support, see [Get support](/microsoft-365/business-video/get-help-support).

> [!NOTE]
> In this article, the term **Debug logs** (also called Web logs) refers to the logs that are used for troubleshooting. However, the files that are generated for these logs will contain the term **diagnostic logs** in their names.

## Logs overview

It’s important to collect logs as soon as an issue occurs.

When creating a support request with Microsoft Support, the support engineer will require the debug logs. Having the debug logs on hand before creating the support request will allow Microsoft to quickly start troubleshooting the problem. **Media** or **Desktop** logs are only required if requested by Microsoft.

### Log collection

Debug/Web, Desktop, and Media logs will be collected in one folder with the name _MSTeams Diagnostics Log \<local date and time\>_ which will be placed in your Downloads directory. This folder can be compressed and shared when you open a support request with Microsoft Support. The folder will contain folders for Desktop, Meeting (Media), and Debug (Web).

- To collect logs for Windows:
  - Select the Microsoft Teams icon in your system tray and then select **Collect support files**.
- To collect logs for Mac:
  - Select the Help menu in Microsoft Teams and then select **Collect support files**.
- To collect logs for Linux:
  - Select the Microsoft Teams icon in your system tray and then select **Get Logs**.

You can also collect the files using the following keyboard shortcuts:
Windows and Linux: <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>
Mac: <kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>

If a problem occurs with a specific meeting or live event, it's helpful to have the URL associated with the meeting. The URL provides additional information to help pinpoint the exact meeting or live event in the logs. This information can be collected from any participant for a meeting or from presenter or producer for a live event. This URL can be captured by hovering over the join URL and choosing **Copy Hyperlink**.

The following table outlines the various clients and their associated logs. Prior to being collected, log files are stored in the Teams app folder with the folder's location being specific to the client and operating system.

- Windows: `%appdata%\Microsoft\Teams\`
- Mac: `~/Library/Application Support/Microsoft/Teams/`
- Linux: `~/.config/Microsoft/Microsoft Teams/`

|Client   |Debug    | Continuous Debug|Desktop  |Media    |
|---------|---------|-----------------|---------|---------|
|Web      |X        |-                |-        |-        |
|Windows  |X        |X                |X        |X        |
|Mac OSX  |X        |X                |X        |X        |
|iOS      |-        |-                |-        |-        |
|Android  |-        |-                |-        |-        |

For a complete list of supported operating systems and browsers, see [Get clients for Microsoft Teams](get-clients.md).

## Debug logs

Debug logs (also called Web logs) are produced by the Windows and Mac desktop clients, as well as by browser-based clients. The logs are text-based and are read from the bottom up. They can be read using any text-based editor, and new logs are created when logging into the client.

Debug logs show the following data flows:

- Login
- Connection requests to middle-tier services
- Call/conversation

## Continuous Debug logs

Continuous Debug logging (also called Continuous Web logging) is a feature that helps capture log data by automatically transferring logs from memory to the file system in a continuous fashion. On average there will be a full day's worth of log data available when enabled. The logs are read from the top down.

Continuous Debug/Web logging is turned on by default on Teams desktop for computers if your CPU is:

- Intel Core i3 and Core i5 (generation 10 or higher), Core i7 and Core i9 (any generation), excluding the following suffixes: U, Y, G1-G7, UE, UL, M, and QM
- Intel Xeon
- AMD Ryzen 5, 7, 9, and TR series, excluding the U suffix
- Apple Silicon

Otherwise, it is turned off by default.

### Admin Configuration

Managing Continuous Debug/Web logging for your end users provides a seamless troubleshooting experience, especially when issues are intermittent. Admins can use the TeamsMediaLoggingPolicy cmdlet to enable and manage Continuous Debug/Web logging for users.

See [Grant-CsTeamsMediaLoggingPolicy](/powershell/module/teams/grant-csteamsmedialoggingpolicy) for PowerShell cmdlets and more information.

## Media logs

Media logs contain diagnostic data about audio, video, and screen sharing in Teams meetings. They are required for support cases that are linked to call-related issues.
> [!NOTE]
> In **New Teams**, media logging is enabled by default due to performance improvements and optimization. There are no end-user or admin controls for media logging.

In **Classic Teams** media logging is turned on by default for computers if your CPU is:

- any Apple M1
- any Intel Xeon
- any Intel i9, except for the U, G7, M, and MQ series
- any 6th generation and later Intel i7, except for the U, G7, M, and MQ series

Otherwise, it is turned off by default. There are two ways to log diagnostic data for Teams meetings:

- Admin configuration - you can manage Media logs for your end users
- End user configuration - your end users can turn on Media logs

> [!NOTE]
> Media logs are not available on WebRTC-based platforms (Teams Browser clients and Classic Teams for VDI with optimized media).
> Please see [Browser logs and tracing for Teams](/microsoftteams/browser-logs-and-tracing-for-teams) for instructions on gathering additional WebRTC logs on Browser clients.
> Please contact your VDI provider for instructions on gathering WebRTC logs when using [Teams for VDI](/microsoftteams/teams-for-vdi).

### Admin configuration

Managing Media logs for your end users provides a seamless troubleshooting experience, especially when issues are intermittent. Admins can use the TeamsMediaLoggingPolicy cmdlet to enable and manage Media logging for users.

See [Grant-CsTeamsMediaLoggingPolicy](/powershell/module/teams/grant-csteamsmedialoggingpolicy) for PowerShell cmdlets and more information.

### End user configuration

For your end users to log diagnostic data for Teams meetings, they must turn on the option in the Teams client. They will go to **Settings** > **General**, select the **Enable media logs (diagnostic data for audio, video, and screen sharing)** check box, and reproduce the issue.

> [!NOTE]
> When your users sign out of Teams, Media logging resets to its default.

## Desktop logs

Desktop logs, also known as bootstrapper logs, contain log data that occurs between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text-based and can be read using any text-based editor in a top-down format.

## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)

[Browser logs and tracing for Teams](/MicrosoftTeams/browser-logs-and-tracing-for-teams)
