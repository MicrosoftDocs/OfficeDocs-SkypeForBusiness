---
title: "Delete an existing collection of client version configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 70bf1216-d0d2-45ce-881f-b8edadf3cec7
description: "If you want to remove the client configuration settings that have been previously configured for a site, you can remove the settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# Delete an existing collection of client version configuration settings in Lync Server 2013
[]
If you want to remove the client configuration settings that have been previously configured for a site, you can remove the settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
### To remove client configuration settings by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Client Version Configuration** navigation button. 
    
4. Select the site, click **Edit**, click **Delete**, and then click **OK**.
    
## Removing Client Version Configuration Settings by Using Windows PowerShell Cmdlets

You can delete client version configuration settings by using the **Remove-CsClientVersionConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
### To remove a specified collection of client version configuration settings

- The following command removes the client version configuration settings applied to the Redmond site:
    
  ```
  Remove-CsClientVersionConfiguration -Identity "site:Redmond"
  ```

### To remove all the client version configuration settings applied to the site scope

- This command removes all the client version configuration settings configured at the site scope:
    
  ```
  Get-CsClientVersionConfiguration -Filter site:* | Remove-CsClientVersionConfiguration
  ```

### To remove all the client version configuration settings based on the value of the DefaultAction property

- And this command removes all the client version configuration settings where the default action has been set to "Block":
    
  ```
  Get-CsClientVersionConfiguration | Where-Object {$_.DefaultAction -eq "Block" | Remove-CsClientVersionConfiguration
  ```

For details, see the Help topic for the [Remove-CsClientVersionConfiguration](remove-csclientversionconfiguration.md) cmdlet. 
  

