---
title: "WMI could not be accessed on the Lync Server"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 1f81caad-a23e-43f9-9d6f-d20f37d74870
description: "Issue: The WMI service on the Lync Server could not be accessed."
---

# WMI could not be accessed on the Lync Server
[]
Issue: The WMI service on the Lync Server could not be accessed.
  
## Description of the Issue

The Office 365 Best Practices Analyzer queries the Win32_ComputerSystem Windows Management Instrumentation (WMI) class to determine whether a value is set for the **Name** key. If the WMI query fails, and the Lync Server is not running on Windows Server 2008 R2, Windows Server 2012, or Windows Server 2012 R2, the Office 365 Best Practices Analyzer displays an error. 
  
## Issue Resolution

There are two likely causes for this error:
  
- The account that runs the Office 365 Best Practices Analyzer does not have sufficient permissions to query WMI classes.
    
- A network issue is preventing the Office 365 Best Practices Analyzer from contacting the computer.
    
 **To correct this error:**
  
1. Make sure that the Lync Server computer has been started and is connected to the network.
    
2. Use the PING command to see if the Lync Server computer is reachable.
    
3. If there is a firewall, check to see if remote procedure call (RPC) ports are blocked.
    
4. Examine the permissions for the account under which the Office 365 Best Practices Analyzer is running. The account under which the Office 365 Best Practices Analyzer is running must have local Administrator permissions on each Lync Server that it is scanning.
    
    Alternatively, you can grant specific WMI permission to the account under which the Office 365 Best Practices Analyzer is running:
    
1. On the Lync Server computer, open the **Computer Management** Microsoft Management Console (MMC). 
    
2. Under **Services and Applications**, right-click **WMI Control**, and then click **Properties**.
    
3. On the **WMI Controls Property** page, click the **Security** tab, and then expand **Root**.
    
4. Select the **CIMV2** folder, and click **Security**.
    
5. On the **Security for ROOT\CIMV2** page, add the account under which the Office 365 Best Practices Analyzer runs. 
    
5. Select the account that you added in Step 5 above. In Permissions for Selected_Account, under the **Allow** column, select both **Remote Enable** and **Read Security**, and then click **OK**.
    

