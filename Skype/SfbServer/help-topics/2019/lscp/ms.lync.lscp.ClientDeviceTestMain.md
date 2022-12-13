---
title: "Test Device"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.lscp.ClientDeviceTestMain
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
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

For details about testing devices, see [Add a Device to Test Update Functionality](/previous-versions/office/lync-server-2013/lync-server-2013-create-a-device-to-test-update-functionality) in the Operations documentation.
## See also

[Test Device: Create New or Edit Existing](ms.lync.lscp.ClientDeviceTestEdit.md)

[New-CsTestDevice](/powershell/module/skype/new-cstestdevice?view=skype-ps)

[Set-CsTestDevice](/powershell/module/skype/set-cstestdevice?view=skype-ps)

[View Software Updates for Devices in Your Organization](/previous-versions/office/lync-server-2013/lync-server-2013-view-software-updates-for-devices-in-your-organization)