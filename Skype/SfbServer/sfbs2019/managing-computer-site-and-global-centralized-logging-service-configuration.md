---
title: "Managing computer, site and global Centralized Logging Service configuration in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 93b9a354-9aea-4b3a-a4fe-68a89f436196
description: "The Centralized Logging Service can be run at a scope that includes a single computer, a pool of computers, at a site scope (that is, a defined site such as the site Redmond that contains a collection of computer and pools in your deployment), or at a global scope (that is, all computers and pools in your deployment)."
---

# Managing computer, site and global Centralized Logging Service configuration in Lync Server 2013
[]
The Centralized Logging Service can be run at a scope that includes a single computer, a pool of computers, at a site scope (that is, a defined site such as the site Redmond that contains a collection of computer and pools in your deployment), or at a global scope (that is, all computers and pools in your deployment).
  
To configure the Centralized Logging Service scope by using the Lync Server Management Shell, you must be a member of either the CsAdministrator or the CsServerAdministrator role-based access control (RBAC) security groups, or a custom RBAC role that contains either of these two groups. To return a list of all the RBAC roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Lync Server Management Shell or the Windows PowerShell prompt:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "<Lync Server 2013 cmdlet>"}
```

For example:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}
```

> [!NOTE]
> Windows PowerShell provides you more options and additional configuration options that are not available by using CLSController.exe. CLSController offers a quick, concise method to run commands, but is limited to the set of commands available for the CLSController. Windows PowerShell is not limited to just the command available to the command processor of the CLSController, and provides a wider set of commands and a richer set of options. For example, CLSController.exe does provide you with a scope options for -computers and -pools. With Windows PowerShell, you can indicate computers or pools in most commands, and when you define new scenarios (CLSController has a finite number of scenarios that are not user modifiable) you can define a site or global scope. This powerful feature of Windows PowerShell enables you to define a scenario a site or global scope, but limit the actual logging to a computer or pool. > There are fundamental differences between the command-line commands that you can run in Windows PowerShell or CLSController. Windows PowerShell provides a rich method to configure and define scenarios, and to reuse those scenarios in a meaningful way for your troubleshooting scenarios. While CLSController does provide a fast and efficient way to issue commands and get results, the command set for CLSController is limited by the finite commands that you have available from the command line. Unlike the Windows PowerShell cmdlets, CLSController cannot define new scenarios, manage scope at a site or global level, and many other limitations of a finite command set that cannot be dynamically configured. While CLSController provides a means for fast execution, Windows PowerShell provides a means to extend the Centralized Logging Service functionality beyond what is possible with CLSController. 
  
A single computer scope can be defined during the execution of a [Search-CsClsLogging](search-csclslogging.md), [Show-CsClsLogging](show-csclslogging.md), [Start-CsClsLogging](start-csclslogging.md), [Stop-CsClsLogging](stop-csclslogging.md), [Sync-CsClsLogging](sync-csclslogging.md) and [Update-CsClsLogging](update-csclslogging.md) command using the -Computers parameter. The -Computers parameter accepts a comma separated list of fully qualified domain names (FQDNs) for the target computer. 
  
> [!TIP]
> You can also define -Pools and a comma separated list of pools that you want to run the logging commands on. 
  
Site and Global scopes are defined in the **New-**, **Set-**, and **Remove-** Centralized Logging Service cmdlets. The following examples demonstrate how to set a site and a global scope. 
  
> [!IMPORTANT]
> The commands shown may contain parameters and concepts that are covered in other sections. The example commands are intended to demonstrate the use of the **-Identity** parameter to define scope, and the other parameters are included for completeness and to specify the scope. For details about the **Set-CsClsConfiguration** cmdlets, see [Set-CsClsConfiguration](set-csclsconfiguration.md) in the Operations documentation. 
  
### To retrieve the current Centralized Logging Service configuration

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at the command-line prompt:
    
  ```
  Get-CsClsConfiguration
  ```

Use the **New-CsClsConfiguration** and **Set-CsClsConfiguration** cmdlets to create a new configuration or to update an existing configuration. When you run **Get-CsClsConfiguration**, it displays information similar to the following screen shot, where the deployment currently has the default Global configuration, but no site configurations defined: 
  
![Sample output from Get-CsClsConfiguration.](media/Ops_Get-CsClsConfiguration_Basic.jpg)
  
### To retrieve the current Centralized Logging Service configuration from the computer local store

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at the command-line prompt:
    
  ```
  Get-CsClsConfiguration -LocalStore
  ```

When you use the first example where **Get-CsClsConfiguration** does not specify any parameters, the command references the Central Management store for the data. If you specify the parameter -LocalStore, the command references the computer LocalStore instead of the Central Management store. 
### To retrieve a listing of scenarios currently defined

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at the command-line prompt:
    
  ```
  Get-CsClsConfiguration -Identity <scope and name> | Select-Object -ExpandProperty Scenarios
  ```

    For example, to retrieve the scenarios that is defined at the global scope:
    
  ```
  Get-CsClsConfiguration -Identity "global" | Select-Object -ExpandProperty Scenarios
  ```

The cmdlet **Get-CsClsConfiguration** always displays the scenarios that are a part of a given scope's configuration. In most cases, all scenarios are not displayed, and are truncated. The command used here lists all of the scenarios and partial information about what providers, settings, and flags are used. 
### To update a global scope for the Centralized Logging Service by using Windows PowerShell

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at the command-line prompt:
    
  ```
  Set-CsClsConfiguration -Identity <scope> -EtlFileRolloverSizeMB <size for logging file in megabytes>
  ```

    For example:
    
  ```
  Set-CsClsConfiguration -Identity "global" -EtlFileRolloverSizeMB 40
  ```

The command tells the CLSAgent on each computer and pool in the deployment to set the size of the rollover value on the tracing file to 40 megabytes. Computers and pools in all sites are affected by the command, and will set their configured trace log rollover value to 40 megabytes.
### To update a site scope for the Centralized Logging Service by using Windows PowerShell

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at the command-line prompt:
    
  ```
  Set-CsClsConfiguration -Identity <scope/site name> -EtlFileRolloverSizeMB <size for logging file in megabytes> -EtlFileFolder <default location %TEMP%\Tracing>
  ```

    For example:
    
  ```
  Set-CsClsConfiguration -Identity "site/Redmond" -EtlFileRolloverSizeMB 40 -EtlFileFolder "C:\LogFiles\Tracing" 
  ```

    > [!NOTE]
    > As noted in the example, the default location of the log files is %TEMP%\Tracing. However, because it is actually CLSAgent that is writing the file and CSLAgent runs as Network Service, the %TEMP% variable expands to %WINDIR%\ServiceProfiles\NetworkService\AppData\Local. 
  
The command tells the CLSAgent on each computer and pool in the site Redmond to set the size of the rollover value on the tracing file to 40 megabytes. Computers and pools in other sites will not be affected by the command, and will continue to use the currently configured trace log rollover value defined either by default (20 megabytes) or during the start of the logging session.
### To create a new Centralized Logging Service configuration

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at the command-line prompt:
    
  ```
  New-CsClsConfiguration -Identity <scope and name> [CsClsConfiguration options for this site]
  ```

    > [!NOTE]
    > New-CsClsConfiguration provides access to a large number of optional configuration settings. For details about the configuration options, see [Get-CsClsConfiguration](get-csclsconfiguration.md) and [Understanding Centralized Logging Service configuration settings in Lync Server 2013](understanding-centralized-logging-service-configuration-settings.md). 
  
    For example, to create a new configuration that defines a network folder for cache files, rollover time period for the log files and rollover size for the log files, you would type:
    
  ```
  New-CsClsConfiguration -Identity "site:Redmond" -CacheFileNetworkFolder "\\fs01.contoso.net\filestore\logfiles" -EtlFileRolloverMinutes 120 -EtlFileRolloverSizeMB 40
  ```

You should carefully plan the creation of new configurations and how you define new properties for the Centralized Logging Service. You should be cautious about making changes and make sure you understand the impact on your ability to properly log problem scenarios. You should make changes to the configuration that will enhance your ability to manage logs to a size and a rollover period that will allow problem solving when it arises.
### To remove an existing Centralized Logging Service configuration

1. Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
2. Type the following at the command-line prompt:
    
  ```
  Remove-CsClsConfiguration -Identity <scope and name>
  ```

    For example, to remove a Centralized Logging Service configuration that you created to increase the log file rollover time, increase the rollover log file size, and set the log file cache location to a network share as follows:
    
  ```
  Remove-CsClsConfiguration -Identity "site:Redmond"
  ```

    > [!NOTE]
    > This is the new configuration that was created in the procedure "To create a new Centralized Logging Service configuration." 
  
If you choose to remove a site-level configuration, the site will use the global settings.
## See also

#### 

[Overview of the Centralized Logging Service in Lync Server 2013](overview-of-the-centralized-logging-service.md)
#### 

[Managing the Centralized Logging Service configuration settings in Lync Server 2013](managing-the-centralized-logging-service-configuration-settings.md)
  
[Set-CsClsConfiguration](set-csclsconfiguration.md)
  
[Get-CsClsConfiguration](get-csclsconfiguration.md)
  
[New-CsClsConfiguration](new-csclsconfiguration.md)
  
[Remove-CsClsConfiguration](remove-csclsconfiguration.md)

