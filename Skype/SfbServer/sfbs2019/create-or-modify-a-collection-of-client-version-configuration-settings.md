---
title: "Create or modify a collection of client version configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4e6faffd-a36f-40f1-8734-78d84b7df921
description: "Client version configuration settings are used to turn client version control on or off. The global client version configuration installs with Lync Server and is used to enable or disable client version control for the entire server deployment. You can also configure client version configuration settings for individual sites. You can create or modify client version configuration settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell."
---

# Create or modify a collection of client version configuration settings in Lync Server 2013
[]
Client version configuration settings are used to turn client version control on or off. The global client version configuration installs with Lync Server and is used to enable or disable client version control for the entire server deployment. You can also configure client version configuration settings for individual sites. You can create or modify client version configuration settings from Lync Server 2013 Control Panel or Lync Server 2013 Management Shell.
  
> [!NOTE]
> Because anonymous users are not associated with a user, site, or service, anonymous users are affected by global-level policies only. 
  
### To create or modify client version configuration settings by using Lync Server Control Panel

1. From a user account that is assigned to the CsUserAdministrator role or the CsAdministrator role, log on to any computer in your internal deployment.
    
2. Open a browser window, and then enter the Admin URL to open the Lync Server Control Panel. For details about the different methods you can use to start Lync Server Control Panel, see [Open Lync Server 2013 administrative tools](open-lync-server-administrative-tools.md).
    
3. In the left navigation bar, click **Clients**, and then click the **Client Version Configuration** navigation button. 
    
4. On the **Client Version Configuration** page, do the following: 
    
  - To create a new configuration, click **New**, select a site, click **OK** name, and update the settings. 
    
  - To modify a configuration, select the configuration, click **Edit**, click **Show details**, and make changes to the settings.
    
## Creating or Modifying Client Version Configuration Settings by Using Windows PowerShell Cmdlets

You can create client version configuration settings by using the **New-CsClientVersionConfiguration** cmdlet, and modify them by using the **Set-CsClientVersionConfiguration** cmdlet. These cmdlets can be run either from the Lync Server 2013 Management Shell or from a remote session of Windows PowerShell. For details about using remote Windows PowerShell to connect to Lync Server, see the Lync Server Windows PowerShell blog article "Quick Start: Managing Microsoft Lync Server 2010 Using Remote PowerShell" at [https://go.microsoft.com/fwlink/p/?linkId=255876](https://go.microsoft.com/fwlink/p/?linkId=255876).
  
### To create a new collection of client version configuration settings

- The following command creates a new collection of client version configuration settings applied to the Redmond site. In this example, client versioning is disabled for the Redmond site.
    
  ```
  New-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $False
  ```

### To enable client versioning for a site

- This command enables client versioning for the Redmond site.
    
  ```
  Set-CsClientVersionConfiguration -Identity "site:Redmond" -Enabled $True
  ```

### To disable client versioning throughout the organization

- In this example, client versioning is disabled for all the client version configuration settings in use in the organization.
    
  ```
  Get-CsClientVersionConfiguration | Set-CsClientVersionConfiguration  -Enabled $False
  ```

For details, see the Help topic for the [New-CsClientVersionConfiguration](new-csclientversionconfiguration.md) and [Set-CsClientVersionConfiguration](set-csclientversionconfiguration.md) cmdlets. 
  

