---
title: "Test Device Create New or Edit Existing"
ms.reviewer: 
ms.author: serdars
author: SerdarSoysal
manager: serdars
audience: ITPro
ms.topic: article
ms.custom:
- ms.lync.lscp.ClientDeviceTestEdit
ms.prod: skype-for-business-itpro
f1.keywords:
- CSH
ms.localizationpriority: medium
ms.assetid: 8f9125dd-04b3-4a6d-9f41-4f19ddaf7a2d
ROBOTS: NOINDEX, NOFOLLOW
description: "The Test Device feature works in conjunction with the Device Update feature. You can add a test device to the Test Device page and then use this device to verify the functionality of new updates before deploying the updates to production devices. You can test a device globally (throughout your entire environment) or within a single site. You identify a test device by its Media Access Control (MAC) address or serial number. When you add a device, it appears in the list on the Test Device page of the Skype for Business Server Control Panel."
---

# Test Device: Create New or Edit Existing

The Test Device feature works in conjunction with the Device Update feature. You can add a test device to the **Test Device** page and then use this device to verify the functionality of new updates before deploying the updates to production devices. You can test a device globally (throughout your entire environment) or within a single site. You identify a test device by its Media Access Control (MAC) address or serial number. When you add a device, it appears in the list on the **Test Device** page of the Skype for Business Server Control Panel.

## Tasks you can perform

You can perform the following tasks on the **New Test Device** or **Edit Test Device** page:

- Add a new test device.

- Modify the properties of an existing test device.

## UI Reference

The following lists describe the menus, commands, fields, and properties on the page.

- **Scope** Identifies the scope (Global or Site) of the test device.

- **Name** You can add or modify the name of the test device.

- **Device name** You can add or modify the name of the test device.

- **Identifier type** You can select the method to use to identify the device by selecting one of the following:

  - **MAC address**

  - **Serial number**

- **Unique identifier** You can type the MAC address or serial number of the device.

For details about testing devices, see [Add a Device to Test Update Functionality](/previous-versions/office/lync-server-2013/lync-server-2013-create-a-device-to-test-update-functionality) in the Operations documentation.
## See also

[Test Device](ms.lync.lscp.ClientDeviceTestMain.md)

[New-CsTestDevice](/powershell/module/skype/new-cstestdevice?view=skype-ps)

[Set-CsTestDevice](/powershell/module/skype/set-cstestdevice?view=skype-ps)

[View Software Updates for Devices in Your Organization](/previous-versions/office/lync-server-2013/lync-server-2013-view-software-updates-for-devices-in-your-organization)