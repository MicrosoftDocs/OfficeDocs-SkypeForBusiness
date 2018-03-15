---
title: "View client version configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c72df4e6-a889-4cb6-86f7-8334d7774c6e
description: "Client version configuration settings are used to turn client version control on or off. The global client version configuration installs with Lync Server 2013 and is used to enable or disable client version control for the entire server deployment. When the Global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can view client version configuration settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# View client version configuration settings in Lync Server 2013
[]
Client version configuration settings are used to turn client version control on or off. The global client version configuration installs with Lync Server 2013 and is used to enable or disable client version control for the entire server deployment. When the Global configuration is enabled, any client version policies you have in place will take effect when users attempt to log on. You can view client version configuration settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
> [!NOTE]
> Because anonymous users are not associated with a user, site, or service, anonymous users are affected by global-level policies only. 
  
### To view client version configuration settings by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Client Version Configuration** navigation button. 
    
4. Double-click the name of the client version configuration you want to view.
    
## Viewing Client Version Configuration Settings by Using Windows PowerShell Cmdlets

You can view client version configuration settings by using the **Get-CsClientVersionConfiguration** cmdlet. This cmdlet can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To view client version configuration information

- To view information about all your client version configuration settings, type the following command in the Lync Server Management Shell and then press ENTER:
    
  ```
  Get-CsClientVersionConfiguration
  ```

    That will return information similar to this:
    
  ```
  Identity      : Global
  DefaultAction : Allow
  DefaultURL    :
  Enabled       : True
  
  ```

For details, see the Help topic for the [Get-CsClientVersionConfiguration](get-csclientversionconfiguration.md) cmdlet. 
  

