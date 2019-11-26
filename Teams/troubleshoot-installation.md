---
title: Troubleshoot Microsoft Teams installation and update issues on Windows
author: lanachin
ms.author: v-lanac
manager: serdars
ms.reviewer: lenatarhun
ms.topic: article
ms.service: msteams
audience: Admin
ms.collection: 
- M365-collaboration
appliesto: 
- Microsoft Teams
localization_priority: Normal
search.appverid: MET150
description: Learn how to troubleshoot installation and update issues for the Teams desktop client app on Windows. 
---

# Troubleshoot Microsoft Teams installation and update issues on Windows

This article provides guidance for how to diagnose and troubleshoot installation and update issues for the Teams desktop client app running on Windows.

## Check whether Teams is updated successfully

Follow these steps to check whether a Teams update is successfully installed.

1. In Teams, select your profile picture, and then click **About** > **Version**.
2. On the same menu, click **Check for updates**.
3. Wait for the banner at the top of the app to indicate that a “refresh” of Teams is needed. The link should be shown about a minute later as this process downloads the new version of Teams. The banner also lets you know if you’re already running the latest version in which case, no update is necessary.
4. Click the refresh link in the banner.
5. Wait until Teams restarts, and then repeat step 1 to see whether the app is updated.
6. If you see a failure message or if the version number is the same as step 4, the update process failed.

## Troubleshoot installation and update issues

### Troubleshoot installation issues

When Teams is installed, the Teams installer logs the sequence of events to %LocalAppData%\SquirrelTemp\SquirrelSetup.log. The first thing to look for is an error message or a call stack near the end of the log. Note that call stacks at the beginning of the log may not mean that an installation issue exists. It can be easier to compare your log against the log from a successful installation (even on another machine) to see what's expected.

If SquirrelSetup.log doesn't indicate the cause or if you need more information to troubleshoot the issue, see [Collect and analyze application and system logs](#collect-and-analyze-application-and-system-logs).

### Troubleshoot update issues

When Teams is successfully installed, the log location switches from %LocalAppData%\SquirrelTemp to %AppData%\Microsoft\Teams. At this location, there are two log files of interest, SquirrelSetup.log and logs.txt.

- The SquirrelSetup.log file at this location is written by Update.exe, which is an executable that services the Teams app.
- The Logs.txt file is used by the Teams app (specifically Teams.exe) to record significant application events. It will likely contain failure information.

These log files contain personally identifiable information (PII) and so they're not sent to Microsoft.

Teams can automatically start the update process (depending on the policy) or users can manually check for updates by going to their profile picture > **Check for updates**. Both methods use the following sequence of events.

1. **Check for updates**. Teams makes a web request and includes the current app version and deployment ring information. The goal of this step is to get the download link. A failure at this step is logged in Logs.txt.
2. **Download update**. Teams downloads the update by using the download link obtained from step 1. When the download is complete, Teams calls Update.exe to stage the download. A download failure is also logged in Logs.txt.
3. **Stage the update**. The downloaded content is verified and unpacked into an intermediate folder, %LocalAppData%\Microsoft\Teams\stage), which is done by Update.exe. Failures at this step are logged in SquirrelTemp.log.
4. **Install the update**. There are multiple ways to start Teams. The system automatically starts Teams when a user logs in or you can start Teams through a shortcut. In this step, Update.exe checks for the presence of the staging folder, verifies the content again, and performs file operations to un-stage the app. The old application folder in %LocalAppData%\Microsoft\Teams\current is backed up to %LocalAppData%\Microsoft\Teams\previous and the stage folder is renamed to "current". Failures at this step are logged in SquirrelTemp.log.

If SquirrelTemp.log or Logs.txt don't contain sufficient information to determine the underlying cause and you need more information to troubleshoot the issue, go to [Collect and analyze application and system logs](#collect-and-analyze-application-and-system-logs).

## Collect and analyze application and system logs

Follow these steps to collect and analyze application and system logs to get more comprehensive information to troubleshoot the issue.

### Collect logs

1. Download [SysInternals tools](https://download.sysinternals.com/files/SysinternalsSuite.zip).
2. Extract the zip file to the %TEMP% folder on your local drive.
3. Open an elevated command prompt, and then do the following:

    1. Run the following to go to your TEMP folder:

        ```
        cd /d %TEMP%
        ```
    2. Copy the setup and application logs. Note that depending on the point of failure, some of these logs may not be present.

        ```
        copy %LocalAppData%\SquirrelTemp\SquirrelSetup.log SquirrelSetup.log
        copy %AppData%\Microsoft\Teams\logs.txt logs.txt
        copy %LocalAppData%\Microsoft\Teams\SquirrelSetup.log SquirrelSetup_Teams.log
        ```
    3. Run the following to capture the open handles.

        ```
        handle > handles.txt
        ```

    4. Run the following to capture the opened DLLs.

        ```
        listdlls -v Teams > dlls.txt
        ```
    5. Run the following to capture the drivers that are running.

        ```
        driverquery /v > driverquery.txt
        ```

    6. Run the following to capture the access control lists (ACLs) of the Teams folder.

        ``` 
        icacls %LOCALAPPDATA%\Microsoft\Teams /save icacls.txt /T
        ```

### Analyze logs (for advanced users)

A failed update can result in unpredictable app behavior. For example, users may be unable to exit Teams, have a stale version of Teams, or can't start Teams. If you experience an issue during an update, the first place to look to find the cause is SquirrelTemp.log. Here are the different types of update failures, listed from most common to least common, and how to analyze and troubleshoot them using logs.

#### Unable to exit Teams

As Teams determines that it needs to update itself to a newer version, it downloads and stages the new app, and then waits for an opportunity to restart itself the next time the machine is idle. A common issue during this process is when another process or a file system driver locks up the Teams.exe process, which prevents Teams.exe from exiting. As a result, the Teams app can't be replaced by the newly-downloaded and staged app.

Troubleshooting tips:

- To confirm that is the issue that you're experiencing, quit Teams (right-click Teams on the task bar, and then click **Quit**). Then, open Task Manager in Windows to see whether an instance of Teams is still running.  
- If you’re not on the computer that's having this issue, inspect the SquirrelTemp.log collected from the computer that's experiencing this issue and look for a "Program: Unable to terminate the process in the log" entry.
- To determine what's preventing Teams.exe from exiting, look at the Dlls.txt and Handles.txt logs. These tell you the processes that prevented Teams from exiting.
- Another culprit that can prevent Teams from exiting is the kernel-mode file system filter driver. Use the SysInternals tool, Procdump.exe, to collect the kernel-mode process dump by running ```procdump -mk <pid>```, where <pid> is the process ID obtained from Task Manager. You can also inspect the Driverquery.txt log file to see the active filter drivers that may interfere with Teams.
- To recover from this state, restart the computer.

#### File permissions

Teams creates a number of subfolders and files in the user's profile throughout the installation and update process. Because the app and the updater runs as a non-elevated user, read and write permissions must be granted on the following folders:

|Folder  |Used by  |
|---------|---------|
|%LocalAppData%\SquirrelTemp     | Teams installer (for example, Teams_Windows_x64.exe) during installation phase        |
|%LocalAppData%\Microsoft\Teams  | Teams updater (Update.exe) to extract and stage the app package during update process        |
|%AppData%\Microsoft\Teams   |  Teams app (Teams.exe) to save settings, app states, and the (pre-staged) downloaded update package       |

If Teams is denied access because it can't write write a file, another software application may be interfering or a security descriptor entry may be limiting write access to a folder.

Troubleshooting tips:

- Look for "access denied" evidence in SquirrelTemp.log or Logs.txt. Check these files to see whether there was an attempt to write to a file that failed.
- Open Icacls.txt and look for the effective access control entry (ACE) that blocks write operations by a user who is not an admin. Typically, this is in one of the DACL entries. For more information, see the [icacls documentation](https://docs.microsoft.com/windows-server/administration/windows-commands/icacls).

#### File corrupted

In some cases, encryption software can change files in the %LocalAppData%\Microsoft\Teams folder, which can prevent Teams from starting. This can happen at any time, even when the app isn't being updated. Unfortunately, when a file is corrupted, the only way to recover from this state is to uninstall and re-install Teams.

> [!NOTE]
> If you can't determine the underlying cause of the issue by using any of these steps, you may want to try a Process Monitor session. Process Monitor is a SysInternals tool that records access to the registry and file system.

## Related topics

- [Get clients for Teams](get-clients.md)
- [Teams client updates](teams-client-update.md)