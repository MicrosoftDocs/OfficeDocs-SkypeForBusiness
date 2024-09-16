---
title: Manually update a Microsoft Teams Rooms device
author: mstonysmith
ms.author: tonysmit
manager: pamgreen
ms.reviewer: travis-snoozy
ms.date: 08/20/2024
ms.topic: article
audience: Admin
ms.service: msteams
ms.subservice: itpro-rooms
appliesto: 
  - Microsoft Teams
ms.collection: 
  - M365-collaboration
  - teams-rooms-devices
  - Tier1
f1.keywords: 
  - NOCSH
ms.localizationpriority: medium
description: Learn how to manually update your Microsoft Teams Rooms device to the latest version.
---

# Manually update a Microsoft Teams Rooms device

The Microsoft Teams Rooms app is distributed through the Microsoft Store, and update automatically through Windows; this is the recommended method to get updates. However, there are some situations where a Teams Rooms device can't receive updates from the Microsoft Store.

If you can't get updates from the Microsoft Store, you can use an offline app update PowerShell script to manually update your Teams Rooms devices to a newer version of the Teams Rooms app. Follow the steps in this article to manually update your Teams Rooms devices.

> [!NOTE]
> This process can only update a Teams Rooms device with the Teams Rooms app already installed. It can't be used to perform a new installation. It also can't be used to downgrade the app to an older version.

## Step 1: Download the offline app update script

First, download the latest version of the offline app update script. To download the script, click <https://go.microsoft.com/fwlink/?linkid=2151817>. The script will be downloaded to the default downloads folder on your device.

Downloaded files may be marked as blocked by Windows. If you need to run the script without any interaction, you'll need to unblock the script. To unblock the script, do the following:

1. Right-click on the file in File Explorer
2. Click **Properties**
3. Select **Unblock**
4. Click **OK**

To unblock the script using PowerShell, see [Unblock-File](/powershell/module/microsoft.powershell.utility/unblock-file).

After the offline app update script is downloaded, transfer the file to the Teams Rooms device. You can transfer a file to the device by using a USB drive or by accessing the file from a network file share while in Admin Mode on the device. Be sure to note where you save the file on the device.

## Step 2: Run the script to update the Teams Rooms app

The offline app update script needs to be run from an elevated command prompt while the Skype user (the user under which the app runs) is still signed in. For more information about how to log into an admin account to use the elevated command prompt while the Skype user is still logged in, see [Switching to Admin Mode and back when the Microsoft Teams Rooms app crashes](rooms-operations.md#switching-to-admin-mode-and-back-when-the-microsoft-teams-rooms-app-is-frozen).

Do the following to run the script from an elevated command prompt:

1. Switch to Admin Mode
2. Click the Start icon, type **Command Prompt**, and then select **Run as administrator**
3. Run the following command where `<path to script>` includes the full path to the script and the name of the script file:

    ```console
    PowerShell -ExecutionPolicy Unrestricted "<path to script>"
    ```

For example, if the script file is located in `C:\Users\Admin\Downloads`, and the script file name is `MTR-Update-4.5.6.7.ps1`, run the following command:

```console
PowerShell -ExecutionPolicy Unrestricted "C:\Users\Admin\Downloads\MTR-Update-4.5.6.7.ps1"
```

Allow the script to run.

## Step 3: Verify the app has been updated successfully

Check the output from the script - it will indicate if the script did or did not complete successfully.

If the script completes successfully, the Teams Rooms device will run the updated version of the Teams Rooms app on next reboot.

If the script encounters a problem, it will indicate what the problem is on the command line and record its output to a file. Follow any instructions that the script provides. If you need to contact Microsoft Support, make sure to include the log file along with the support request. The log file can be found in `C:\Users\Skype\AppData\Local\Packages\Microsoft.SkypeRoomSystem_8wekyb3d8bbwe\LocalState\Tracing\MTR-Update`.
