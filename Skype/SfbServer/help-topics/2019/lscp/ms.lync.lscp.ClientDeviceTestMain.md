---
title: "Test Device"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.audience: ITPro
ms.topic: article
f1_keywords:
- ms.lync.lscp.ClientDeviceTestMain
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a1ea564c-f403-4f61-a36b-5a429708e7ca
ROBOTS: NOINDEX, NOFOLLOW
description: "You can add a test device to the Test Device page and then use this device to verify the functionality of new updates before deploying the updates to production devices. You can test a device globally (throughout your entire environment) or within a single site. You identify a test device by its Media Access Control (MAC) address or serial number. When you add a device, it appears in the list on the Test Device page of the Skype for Business Server Control Panel."
---

# Test Device

You can add a test device to the **Test Device** page and then use this device to verify the functionality of new updates before deploying the updates to production devices. You can test a device globally (throughout your entire environment) or within a single site. You identify a test device by its Media Access Control (MAC) address or serial number. When you add a device, it appears in the list on the **Test Device** page of the Skype for Business Server Control Panel.

## Tasks you can perform

You can perform the following tasks on the **Test Device** page:

- Add a test device globally or for a particular site.

- Modify the options for an existing test device.

## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.

- **New** You can add a new test device with the following scope:

  - Global

  - Site

- **Edit** You can change the options of a test device in the list. Using this option, you can do the following:

  - **Show details** This option opens a dialog box in which you can change the options for a test device.

  - **Select All** This option selects all test devices in the list.

  - **Delete** This option deletes all selected test devices.

- **Refresh** You can refresh the test device list to verify the status of the options of all test devices.

For details about testing devices, see [Add a Device to Test Update Functionality](https://technet.microsoft.com/library/ce509fd1-17b3-4b78-b269-fe5d06fe2e1d.aspx) in the Operations documentation.
## See also

[Test Device: Create New or Edit Existing](ms.lync.lscp.ClientDeviceTestEdit.md)

[New-CsTestDevice](https://docs.microsoft.com/powershell/module/skype/new-cstestdevice?view=skype-ps)

[Set-CsTestDevice](https://docs.microsoft.com/powershell/module/skype/set-cstestdevice?view=skype-ps)

[View Software Updates for Devices in Your Organization](https://technet.microsoft.com/library/d2cca12b-ed43-4e1f-90ab-d14bca8b482c.aspx)
