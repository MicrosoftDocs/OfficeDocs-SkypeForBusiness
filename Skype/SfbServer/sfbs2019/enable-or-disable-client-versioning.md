---
title: "Enable or disable client versioning in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 33a98cb9-a979-4bb6-afb2-512f601d7ac5
description: "Client version configuration settings are used to turn client version control on or off, either globally or for particular sites. The global client version configuration installs with Lync Server 2013 and is used to enable or disable client version control for the entire server deployment. When the global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can disable the global client version configuration if you do not want any client version control to occur. You can enable or disable client versioning from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# Enable or disable client versioning in Lync Server 2013
[]
Client version configuration settings are used to turn client version control on or off, either globally or for particular sites. The global client version configuration installs with Lync Server 2013 and is used to enable or disable client version control for the entire server deployment. When the global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can disable the global client version configuration if you do not want any client version control to occur. You can enable or disable client versioning from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
> [!NOTE]
> Because anonymous users are not associated with a user, site, or service, anonymous users are affected by global-level policies only. 
  
### To enable or disable client versioning by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Client Version Configuration** navigation button. 
    
4. Do the following:
    
  - To globally enable or disable client versioning, double-click the **Global** configuration, and then modify the settings. 
    
  - To enable or disable client versioning for a particular site, click **New**, select the site, click **OK**, and then modify the settings for the site.
    
## Enabling or Disabling Client Versioning by Using Windows PowerShell Cmdlets

You can enable or disable client versioning by using the **Set-CsClientVersionConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876). 
  
### To enable client versioning

- You can enable client versioning by setting the **Enabled** property to True ($True). 
    
  ```
  Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True
  ```

### To disable client versioning

- You can disable client versioning by setting the **Enabled** property to False ($False). 
    
  ```
  Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True
  ```

For details, see the Help topic for the [Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md) cmdlet. 
  

