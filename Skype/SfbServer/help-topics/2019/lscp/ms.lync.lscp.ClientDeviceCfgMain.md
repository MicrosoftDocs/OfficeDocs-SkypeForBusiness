---
title: "Device Log Configuration"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientDeviceCfgMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: c9b81f20-ce8c-40f1-8bed-50775cc35e58
ROBOTS: NOINDEX, NOFOLLOW
description: "Device Update Web service automatically creates log files that record device update activity. As part of your organization's data management strategy, you may want to set thresholds on log data cache size, log file size, or the length of time a log file is kept before it is purged. You can change these settings according to your organization's requirements. If you do not want Device Update Web service to purge log files automatically, you can purge them manually, as needed. Log settings can be changed globally or per site."
---

# Device Log Configuration

Device Update Web service automatically creates log files that record device update activity. As part of your organization's data management strategy, you may want to set thresholds on log data cache size, log file size, or the length of time a log file is kept before it is purged. You can change these settings according to your organization's requirements. If you do not want Device Update Web service to purge log files automatically, you can purge them manually, as needed. Log settings can be changed globally or per site.

> [!NOTE]
> You can also configure a time of day when you want Device Update Web service to automatically delete log files that are older than the number of days you configured the service to keep log files (by default, that is log files that are more than 10 days old). This setting cannot be modified using Skype for Business Server Control Panel. Instead, you must use Skype for Business Server Management Shell. To specify the time of day to delete expired log files, use the **New-CsDeviceUpdateConfiguration** cmdlet with the -LogCleanUpTimeOfDay parameter. For details, see [New-CsDeviceUpdateConfiguration](https://docs.microsoft.com/powershell/module/skype/new-csdeviceupdateconfiguration?view=skype-ps).

> [!CAUTION]
> Purging files permanently removes them from the file system. After you purge a file, it cannot be recovered.

## Tasks you can perform

You can perform the following tasks on the **Device Log Configuration** page:

- Add a device log configuration globally or for a particular site or pool.

- Modify the options for an existing device log configuration.

## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.

- **New** You can add a new device log configuration with the following scope:

  - Global

  - Site

- **Edit** You can change the options of a device log configuration in the list. Using this option, you can do the following:

  - **Show details** This option opens a dialog box in which you can change the options for a device log configuration.

  - **Select All** This option selects all device log configuration in the list.

  - **Delete** This option deletes all selected device log configuration.

- **Refresh** You can refresh the device log configuration list to verify the status of the options of all device log configuration.

## See also

[Modify Settings for Log Files of Device Update Activity](https://technet.microsoft.com/library/9b57f126-1853-43b3-bbd4-06401e6498bd.aspx)
