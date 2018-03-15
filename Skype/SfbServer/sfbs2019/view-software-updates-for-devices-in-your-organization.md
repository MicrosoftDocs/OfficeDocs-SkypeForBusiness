---
title: "View software updates for devices in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: d2cca12b-ed43-4e1f-90ab-d14bca8b482c
description: "With Lync Server 2013, you use Device Update Web service to view and manage software updates for your organization's devices. These updates are available in .cab (cabinet) files from the Microsoft Support website at https://go.microsoft.com/fwlink/p/?linkId=204091. After you download the .cab file, run the Import-CSDeviceUpdate cmdlet to import the device update rules from the .cab file. For details about the Import-CSDeviceUpdate cmdlet, see Import-CsDeviceUpdate in the Lync Server Management Shell documentation."
---

# View software updates for devices in Lync Server 2013
[]
With Lync Server 2013, you use Device Update Web service to view and manage software updates for your organization's devices. These updates are available in .cab (cabinet) files from the Microsoft Support website at [https://go.microsoft.com/fwlink/p/?linkId=204091](https://go.microsoft.com/fwlink/p/?linkId=204091). After you download the .cab file, run the **Import-CSDeviceUpdate** cmdlet to import the device update rules from the .cab file. For details about the **Import-CSDeviceUpdate** cmdlet, see [Import-CsDeviceUpdate](import-csdeviceupdate.md) in the Lync Server Management Shell documentation. 
  
> [!TIP]
> Before deploying a new update to your organization, verify that it functions correctly on a test device. 
  
### To view software updates for UC devices

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. From the Microsoft Support website at [https://go.microsoft.com/fwlink/p/?linkId=204091](https://go.microsoft.com/fwlink/p/?linkId=204091), download the .cab file to a location on a Lync Server 2013 computer (for example, C:\Updates\UCUpdates.cab).
    
3. Import the device update rules from the C:\Updates\UCUpdates.cab file by running one of the following cmdlets:
    
  - If the .cab file is located on the same computer as the one running the service to be updated (service:Redmond-websvc-2), run the following cmdlet:
    
  ```
  Import-CsDeviceUpdate -Identity service:Redmond-websvc-2 -FileName C:\Updates\UCUpdates.cab
  ```

  - If the .cab file is located on a different computer than the one running the service to be updated (service:Redmond-websvc-3), run the following cmdlet:
    
  ```
  Import-CsDeviceUpdate -Identity service:Redmond-websvc-3 -ByteInput C:\Updates\UCUpdates.cab
  ```

4. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
5. In the left navigation bar, click **Clients**, and then click **Device Update**.
    
6. On the **Device Update** page, click an update in the list, and then do one of the following: 
    
  - **Cancel a pending update.** To prevent the selected update from being deployed to your organization's devices, click the **Action** menu, and then click **Cancel pending updates**.
    
  - **Approve an update.** To allow the selected update to be deployed to your organization's devices, click the **Action** menu, and then click **Approve**.
    
  - **Restore an update.** To allow a previously approved update to be deployed to your organization's devices, click the **Action** menu, and then click **Restore**.
    
## See also

#### 

[Managing devices, phones, and client applications in Lync Server 2013](managing-devices-phones-and-client-applications.md)

