---
title: "Device Update"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 3/23/2015
audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientDeviceUpdateMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6f6b7f73-f8f5-41dc-9e2a-727baaaa828b
description: "Microsoft periodically releases a new set of device firmware updates for Skype for Business Phone Edition, which you can import to your servers and distribute to users. You can obtain the latest set of device update rules by going to the Help and Support page on the Microsoft website and searching forPhone Edition.Download the latest update package and extract the files to a folder on the computer where the updates are to be uploaded. After the files have been extracted, you can then use the Import-CsDeviceUpdate cmdlet to import the device update rules found in the extracted .CAB file (which will have the name UCUpdates.cab). For details, see Import-CsDeviceUpdate."
---

# Device Update

Microsoft periodically releases a new set of device firmware updates for Skype for Business Phone Edition, which you can import to your servers and distribute to users. You can obtain the latest set of device update rules by going to the Help and Support page on the Microsoft website and searching for "Phone Edition." Download the latest update package and extract the files to a folder on the computer where the updates are to be uploaded. After the files have been extracted, you can then use the **Import-CsDeviceUpdate** cmdlet to import the device update rules found in the extracted .CAB file (which will have the name UCUpdates.cab). For details, see [Import-CsDeviceUpdate](https://docs.microsoft.com/powershell/module/skype/import-csdeviceupdate?view=skype-ps).

After the device update rules have been imported, you can use the **Device Update** page to view and manage these rules for your organization's devices.

> [!TIP]
> You can test the firmware updates and then, assuming the tests succeed, make the updates available to all the relevant devices used in the organization.

## Tasks you can perform

You can perform the following tasks on the **Device Update** page:

- Approve device updates in the list.

- Cancel or restore pending device updates.

- Delete device updates from the list.

## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.

- **Edit** You can use this option to do the following:

  - **Select All** This option selects all device updates in the list.

  - **Delete** This option deletes all selected device updates.

- **Action** You can select one or more updates in the list and take the following actions:

  - **Cancel pending updates** This option prevents the selected update from being deployed to your organization's devices.

  - **Approve** This option allows the selected update to be deployed to your organization's devices.

  - **Restore** This option allows a previously approved update to be deployed to your organization's devices

- **Refresh** You can refresh the list to verify the status of all device updates.

For details about Device Update Web service, see [View Software Updates for Devices in Your Organization](https://technet.microsoft.com/library/d2cca12b-ed43-4e1f-90ab-d14bca8b482c.aspx) in the Planning documentation.
## See also

[Import-CsDeviceUpdate](https://docs.microsoft.com/powershell/module/skype/import-csdeviceupdate?view=skype-ps)
