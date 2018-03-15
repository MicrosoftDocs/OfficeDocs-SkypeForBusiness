---
title: "Deleting an Archiving configuration in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a8744d39-5cf2-474c-9a99-a0f3a37f846f
description: "You can delete a site configuration or pool configuration. The global configuration cannot be removed. If you delete the global configuration, it is automatically reset to the default values. For details about how Archiving configurations are implemented, including which options you can specify and the hierarchy of Archiving configurations, see How Archiving works in Lync Server 2013 in the Planning documentation, Deployment documentation, or Operations documentation."
---

# Deleting an Archiving configuration in Lync Server 2013
[]
You can delete a site configuration or pool configuration. The global configuration cannot be removed. If you delete the global configuration, it is automatically reset to the default values. For details about how Archiving configurations are implemented, including which options you can specify and the hierarchy of Archiving configurations, see [How Archiving works in Lync Server 2013](how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. 
  
### To delete a site or pool configuration for archiving

1. From a user account that is assigned to the CsArchivingAdministrator or CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Monitoring and Archiving**, and then click **Archiving Configuration**.
    
4. In the list of archiving configurations, click the site or pool configuration that you want to delete, click **Edit**, and then click **Delete**.
    
5. Click **Commit**.
    
## Removing Archiving Configuration Settings by Using Windows PowerShell Cmdlets

Archiving configuration settings can be deleted by using Windows PowerShell and the **Remove-CsArchivingConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To remove a specified collection of archiving configuration settings

- The following command removes the archiving configuration settings applied to the Redmond site:
    
  ```
  Remove-CsArchivingConfiguration -Identity "site:Redmond"
  ```

### To remove all the archiving configuration settings applied to the site scope

- This command removes all the archiving configuration settings applied to the service scope:
    
  ```
  Get-CsArchivingConfiguration -Filter "site:*" | Remove-CsArchivingConfiguration
  ```

### To remove archiving configuration settings based on a specified property value

- This command removes all the archiving configuration settings where Exchange archiving has been disabled:
    
  ```
  Get-CsArchivingConfiguration | Where-Object {$_.EnableExchangeArchiving -eq $False} | Remove-CsArchivingConfiguration
  ```

For more information, see the help topic for the [Remove-CsArchivingConfiguration](remove-csarchivingconfiguration.md) cmdlet. 
  
## See also

#### 

[How Archiving works in Lync Server 2013](how-archiving-works.md)
#### 

[Managing the Archiving of internal and external communications in Lync Server 2013](managing-the-archiving-of-internal-and-external-communications.md)

