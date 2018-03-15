---
title: "Operating System GlobalFlag has been set"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: e74cebc3-71a8-42de-8676-348746006422
description: "Issue: Operating System GlobalFlag value has been set to a value other than 0 or null."
---

# Operating System GlobalFlag has been set
[]
 **Issue:** Operating System **GlobalFlag** value has been set to a value other than 0 or null. 
  
## Description of the Issue

The Office 365 Best Practices Analyzer tool for Lync Server reads the following registry entry to determine the value for the **GlobalFlag** entry: 
  
 **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager**
  
If the analyzer finds the value for the **GlobalFlag** to be present and configured with any value other than 0 or null, a warning is displayed. 
  
The **GlobalFlag** registry value setting is a bitmask that determines what debugging options have been enabled for the operating system. Unless you are actively engaged in debugging or tracing a problem with the help of Microsoft Product Support Services, it is recommended that you set the **GlobalFlag** value to 0 at all times. 
  
The **GlobalFlag** registry value is set to 0 by default. If this value has been altered from the default value of 0, you can use the [Gflags](https://go.microsoft.com/fwlink/p/?LinkId=399386) tool to set the value. Alternatively, you can manually set the value to 0 by using a registry editor. Both procedures are described in this topic. 
  
## Issue Resolution

To resolve this issue, set the value for the **GlobalFlag** to 0 or null using one of the following procedures. 
  
> [!IMPORTANT]
> This article contains information about editing the registry. Before you edit the registry, make sure you understand how to restore the registry if a problem occurs. For information about how to restore the registry, view the "Restore the Registry" Help topic in Regedit.exe or Regedt32.exe. 
  
### To correct this issue using GFlags

1. Download and install the [Gflags](https://go.microsoft.com/fwlink/p/?LinkId=399386) tool. 
    
2. Select **Start**, select **Run**, and in the **Open** field type **GFlags**. The Global Flags user interface opens.
    
3. Clear all of the check boxes and click **Apply**.
    
4. Click **OK** to exit the GFlags tool, and then restart the computer for the change to take effect. 
    
### To correct this error using a registry editor

1. Open a registry editor, such as Regedit.exe or Regedt32.exe.
    
2. Navigate to: **HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\Session Manager**
    
3. Double-click the value named **GlobalFlag** and set its Value data to 0. 
    
4. Exit the registry editor and restart the computer for the change to take effect.
    

