---
title: "Delete an existing collection of meeting configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 92ff8a91-05c5-4047-a533-5dff12f22299
description: "You can delete a site or user configuration. The global configuration cannot be removed. If you delete the global configuration, it is automatically reset to the default values."
---

# Delete an existing collection of meeting configuration settings in Lync Server 2013
[]
You can delete a site or user configuration. The global configuration cannot be removed. If you delete the global configuration, it is automatically reset to the default values.
  
### To delete a site or user meeting configuration

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Conferencing** and then click **Meeting Configuration**.
    
4. In the list of meeting configurations, click the site or pool configuration that you want to delete, click **Edit**, and then click **Delete**.
    
## Removing Meeting Configuration Settings by Using Windows PowerShell Cmdlets

Meeting settings can be deleted by using Windows PowerShell and the Remove-CsMeetingConfiguration cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specified collection of meeting configuration settings

- This command removes the meeting configuration settings applied to the Redmond site:
    
  ```
  Remove-CsMeetingConfiguration -Identity "site:Redmond"
  ```

### To remove all the meeting configuration settings applied to the site scope

- This command removes all the meeting configuration settings applied to the site scope:
    
  ```
  Get-CsMeetingConfiguration -Filter "site:*" | Remove-CsMeetingConfiguration
  ```

### To remove all the meeting configuration settings that admit anonymous users by default

- And this one removes all the settings that allow anonymous users to be admitted by default:
    
  ```
  Get-CsMeetingConfiguration | Where-Object {$_.AdmitAnonymousUsersByDefault -eq $True} | Remove-CsMeetingConfiguration
  ```

For more information, see the help topic for the [Remove-CsMeetingConfiguration](remove-csmeetingconfiguration.md) cmdlet. 
  

