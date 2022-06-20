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

This article describes these logs and how they are used. For information about troubleshooting specific issues, see: [Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams). For information about how to contact support, see [Get support](/microsoft-365/business-video/get-help-support). When creating a support request with Microsoft Support, the support engineer will require the debug logs. Having the debug logs on hand before creating the support request will allow Microsoft to quickly start troubleshooting the problem. **Media** or **Desktop** logs are only required if requested by Microsoft.

> [!NOTE]
> In this article, the term **Debug logs** refers to the logs that are used for troubleshooting. However, the files that are generated for these logs will contain the term **diagnostic logs** in their names.  

## Collect and enable logging

It’s important to collect logs as soon as an issue occurs. The logs can be collected together with just a couple of clicks.

- Windows:
  Right-click on the Teams icon in the system tray and choose **Collect support files**. 

- Mac:
  Select the Help menu and choose **Collect support files**.

Debug, Desktop, and Media logs will be collected in one folder with the name _MSTeams Diagnostics Log \<local date and time\>_. This folder can be compressed and shared when you open a support request with Microsoft Support. The folder will contain folders for Desktop, Meeting (Media), and Debug (web). You can collect the files using the following keyboard shortcuts:

- Windows:
  <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>

- Mac:
  <kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>


Media logging is turned on by default only for some CPUs, described in [Media logs](#media-logs). Otherwise, it is off by default. To enable Media logging, users must turn on the option in the Teams client. Go to **Settings** > **General**, and select **Enable logging for meeting diagnostics (requires restarting Teams)**. The Teams client must be restarted for logging to begin (restart it by right-clicking the icon in your dock (Mac) or taskbar (Windows) and selecting **Quit**. After you quit, just click the app icon to open it again).

If a problem occurs with a specific meeting or live event, it's helpful to have the URL associated with the meeting. This provides additional information to help pinpoint the exact meeting or live event in the logs. This information can be collected from any participant for a meeting or from presenter or producer for a live event. This URL can be captured by hovering over the join URL and choosing **Copy Hyperlink**.

> [!NOTE]
> If Media logging is enabled, there will be additional files included in the Meeting folder which are necessary for investigating audio and video issues. If Media logging is not enabled, there will be a limited number of logs available.
  
> [!NOTE]
> The debug logs were previously collecting using the keyboard shortcuts below. These still function and will complete the same log capture as the **Collect support files** option.
>
> - Windows:
>   <kbd>Crtl</kbd> + <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>
>
> - Mac:
>   <kbd>Option</kbd> + <kbd>Command</kbd> + <kbd>Shift</kbd> + <kbd>1</kbd>


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

See the _Collect and enable logging_ section for Windows and Mac instructions. Debug logs are produced by the Windows and Mac desktop clients, as well as by browser-based clients. The logs are text-based and are read from the bottom-up. They can be read using any text-based editor, and new logs are created when logging into the client.

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

See the _Collect and enable logging_ section for Windows and Mac instructions. Media logs contain diagnostic data about audio, video, and screen sharing in Teams meetings. They are required for support cases that are linked to call-related issues.

Media logging is turned on by default for computers if your CPU is:
- any Apple M1
- any Intel Xeon
- any Intel i9, except for the U, G7, M, and MQ series
- any 6th generation and later Intel i7, except for the U, G7, M, and MQ series

Otherwise, it is turned off by default. There are two ways to log diagnostic data for Teams meetings:

### Admin configuration

Managing Media logs for your end users provides a seamless troubleshooting experience, especially when issues are intermittent. Admins can use the TeamsMediaLoggingPolicy cmdlet to manage enabling Media logging for users.

Assign this policy by running the below cmdlets in PowerShell.

To return information about the Teams Media logging policy:

```PowerShell
Get-CsTeamsMediaLoggingPolicy 
```

> [!NOTE]
> Admins can add and remove users from an existing policy instance but can’t create new policy instances.

To assign a Teams Media logging policy to a user or tenant:

```PowerShell
Grant-CsTeamsMediaLoggingPolicy 
```

To force enable Media logging:

- For a single user:

```PowerShell
Grant-CsTeamsMediaLoggingPolicy -PolicyName Enabled -Identity <sip|email>
```

- For the entire tenant:

```PowerShell
Grant-CsTeamsMediaLoggingPolicy -PolicyName Enabled -Global
```

To remove force enabling:

- For a single user:

```PowerShell
Grant-CsTeamsMediaLoggingPolicy -PolicyName $null -Identity <sip|email>
```

- For the entire tenant:

```PowerShell
Grant-CsTeamsMediaLoggingPolicy -PolicyName $null -Global
```

> [!NOTE]
> When you remove force enabling, Media logging resets to its default setting.

Read [Grant-CsTeamsUpgradePolicy](/powershell/module/skype/grant-csteamsupgradepolicy) for more information on policy management.

### End user configuration

For end users to log diagnostic data for Teams meetings, they must turn on the option in the Teams client. Go to **Settings** > **General**, select the **Enable logging for meeting diagnostics (requires restarting Teams**) check box, restart Teams, and reproduce the issue.

> [!NOTE]
> When users sign out of Teams, Media logging resets to its default.

When you send the log files to Microsoft support, please verify the timestamp of the log files to ensure the logs cover the time frame when you reproduced the issue.

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

See the _Collect and enable logging_ section for Windows and Mac instructions. Desktop logs, also known as bootstrapper logs, contain log data that occurs between the desktop client and the browser. Like media logs, these logs are only needed if requested by Microsoft. The logs are text-based and can be read using any text-based editor in a top-down format.

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

## Browser trace

For some categories of errors, Microsoft Support might require you to collect a browser trace. This information can provide important details about the state of the Teams client when the error occurs.

Before you start the browser trace, make sure that you’re signed in to Teams. It's important to do this before you start the trace so that the trace doesn't contain sensitive sign-in information.

After you’re signed in, select one of the following links, as appropriate for your browser, and follow the provided steps. 

-   [Chrome & Edge (Chromium)](/azure/azure-portal/capture-browser-trace#google-chrome-and-microsoft-edge-chromium?preserve-view=true#resolution)

-   [Edge](/azure/azure-portal/capture-browser-trace#microsoft-edge-edgehtml?preserve-view=true#resolution)

-   [Safari](/azure/azure-portal/capture-browser-trace#apple-safari?preserve-view=true#resolution)

-   [Firefox](/azure/azure-portal/capture-browser-trace#firefox?preserve-view=true#resolution)

> [!NOTE]
> In the steps, replace all references to the Azure portal with the Teams client.
  
## WebRTC logs in browsers
WebRTC logs can assist Microsoft Support by providing connection details for audio and video calls. Follow the steps to access the WebRTC logs in Edge (Chromium) or Chrome: 
  
1.  Open a new tab and go to one of the following URLs:
    -   Edge (Chromium): `edge://webrtc-internals/`
    -   Chrome: `chrome://webrtc-internals/`
  
2.  Open the Teams Web application and reproduce the problem.
  
3.  Go back to the tab that was accessed in step 1 and you will see at least two tabs:
    -   GetUserMedia Requests
    -   `https://teams.microsoft.com/url`

4.  Choose the tab with the name of the Teams application and save the page content.

## Related topics

[Teams Troubleshooting](/MicrosoftTeams/troubleshoot/teams)
