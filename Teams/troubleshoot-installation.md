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
6. If you see a failure message or if the version number is the same as step 1, the update process failed.

## Troubleshoot installation and update issues

### Troubleshoot installation issues

During the installation phase, the Teams installer logs the sequence of events to %LocalAppData%\SquirrelTemp\SquirrelSetup.log. The first thing to look at is an error message or a call stack near the end of the log. Note that call stacks at the beginning of the log may not mean that an installation issue exists. It can be easier to compare your log against the log from a successful installation (even on another machine) to see what's expected.

If SquirrelSetup.log doesn't indicate the cause or if you need more information to troubleshoot the issue, see [Collect and analyze application and system logs](#collect-and-analyze-application-and-system-logs).

### Troubleshoot update issues

When Teams is successfully installed, the log location switches from %LocalAppData%\SquirrelTemp to %AppData%\Microsoft\Teams. At this location, there are two log files of interest, SquirrelSetup.log and logs.txt.

- The SquirrelSetup.log file at this location is written by Update.exe, which is an executable for servicing the Teams app. 
- The Logs.txt file is used by the Teams app (specifically Teams.exe) to record significant application events. It will likely contain failure information.

These log files contain personally identifiable information (PII) and so they're not sent to Microsoft.

Teams can automatically start the update process (depending on the policy) or users can manually check for updates by going to their profile picture > **Check for updates**. Both methods use the following sequence of events.

1. **Check for updates**. Teams makes a web request and includes the current app version and deployment ring information. The goal of this step is to get the download link. A failure at this step is logged in Logs.txt.
2. **Download update**. Teams downloads the update by using the download link obtained from step 1. When the download is complete, Teams calls Update.exe to stage the download. A download failure is also logged in Logs.txt.
3. **Stage the update**. The downloaded content is verified and unpacked into an intermediate folder, %LocalAppData%\Microsoft\Teams\stage), which is done by Update.exe. Failures at this step are logged in SquirrelTemp.log.
4. **Install the update**. There are multiple ways to start Teams. The system automatically starts Teams when a user logs in or you can start Teams through a shortcut. In this step, Update.exe checks for the presence of the staging folder, verifies the content again, and performs file operations to un-stage the app. The old application folder in %LocalAppData%\Microsoft\Teams\current is backed up to %LocalAppData%\Microsoft\Teams\previous and the stage folder is renamed to "current". Failures at this step are logged in SquirrelTemp.log.

If SquirrelTemp.log or Logs.txt don't contain sufficient information to troubleshoot the issue, go to [Collect and analyze application and system logs](#collect-and-analyze-application-and-system-logs).

## Collect and analyze application and system logs

Follow these steps to collect and analyze application and system logs to diagnose installation and update issues.

### Collect logs

1. Download [SysInternals tools](https://download.sysinternals.com/files/SysinternalsSuite.zip).
2. Extract the zip file to the %TEMP% folder on your local drive.
3.	Open an elevated command prompt, and then do the following:
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
    3. Run the following to capture the opened handles.

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

A failed update can result in unpredictable app behavior, ranging from being stuck to a stale version of Teams to an inability to start Teams. If a problem occurred during update, start by looking at the SquirrelTemp.log. Failures can be categorized into the buckets below.

#### Unable to exit Teams

#### File permission

#### File corrupted

## Related topics

- [Get clients for Teams](get-clients.md)
- [Teams client updates](teams-client-update.md)