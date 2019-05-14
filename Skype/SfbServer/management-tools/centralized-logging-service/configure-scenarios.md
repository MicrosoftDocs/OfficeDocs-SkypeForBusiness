---
title: "Configure scenarios for the Centralized Logging Service in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
ms.date: 12/20/2018
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.collection: IT_Skype16
ms.assetid: 6c3bf826-e7fd-4002-95dc-01020641ef01
description: "Summary: Learn how to create, modify, and remove scenarios for the Centralized Logging Service in Skype for Business Server 2015."
---

# Configure scenarios for the Centralized Logging Service in Skype for Business Server 2015
 
**Summary:** Learn how to create, modify, and remove scenarios for the Centralized Logging Service in Skype for Business Server 2015.
  
Scenarios define the scope (that is, global, site, pool, or computer) and what providers to use in the Centralized Logging Service. By using scenarios, you enable or disable tracing on providers (for example, S4, SIPStack, IM, and Presence). By configuring a scenario, you can group all of the providers for a given logical collection that address a specific problem condition. If you find that a scenario needs to be modified to meet your troubleshooting and logging needs, the Skype for Business Server 2015 Debug Tools provides you a Windows PowerShell module named ClsScenarioEdit.psm1 that contains a function namedEdit-CsClsScenario. The purpose of the module is to edit the properties of the named scenario. Examples of how this module works are provided in this topic. Download the Skype for Business Server 2015 [Debugging Tools](https://go.microsoft.com/fwlink/p/?LinkId=285257) before going any further.
  
> [!IMPORTANT]
> For any given scope—site, global, pool or computer—you can run a maximum of two scenarios at any given time. To determine which scenarios are currently running, use Windows PowerShell and [Get-CsClsScenario](https://docs.microsoft.com/powershell/module/skype/get-csclsscenario?view=skype-ps). By using Windows PowerShell and [Set-CsClsScenario](https://docs.microsoft.com/powershell/module/skype/set-csclsscenario?view=skype-ps), you can dynamically change which scenarios are running. You can modify which scenarios are running during a logging session to adjust or refine the data you are collecting and from which providers. 
  
To run the Centralized Logging Service functions by using the Skype for Business Server Management Shell, you must be a member of either the CsAdministrator or the CsServerAdministrator role-based access control (RBAC) security groups, or a custom RBAC role that contains either of these two groups. To return a list of all the RBAC roles this cmdlet has been assigned to, including any custom RBAC roles you have created yourself, run the following command from the Skype for Business Server Management Shell or the Windows PowerShell prompt:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Skype for Business Server 2015 cmdlet"}
```

For example:
  
```
Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}
```

The remainder of this topic focuses on how to define a scenario, modify a scenario, retrieve what scenarios are running, remove a scenario, and specify what a scenario contains to optimize your troubleshooting. You can use the Skype for Business Server Management Shell to issue Windows PowerShell commands. When you use Windows PowerShell, you can define new scenarios for use in your logging sessions.
  
As introduced in [Centralized Logging Service in Skype for Business 2015](centralized-logging-service.md), the elements of a scenario are:
  
- **Providers** If you are familiar with OCSLogger, providers are the components that you choose to tell OCSLogger what the tracing engine should collect logs from. The providers are the same components, and in many cases have the same name as the components in OCSLogger. If you are not familiar with OCSLogger, providers are server role specific components that the Centralized Logging Service can collect logs from. For details about the configuration of providers, see [Configure providers for Centralized Logging Service in Skype for Business Server 2015](configure-providers.md).
    
- **Identity** The parameter -Identity sets the scope and name of the scenario. For example, you could set a scope of "global" and identify the scenario with "LyssServiceScenario". When you combine the two, you define the Identity (for example, "global/LyssServiceScenario").
    
    Optionally, you can use the -Name and -Parent parameters. You define the Name parameter to uniquely identify the scenario. If you use Name, you must also use Parent to add the scenario to either global or site. 
    
    > [!IMPORTANT]
    > If you use the Name and Parent parameters, you cannot use the **-Identity** parameter.
  
### To create a new scenario with the New-CsClsScenario cmdlet

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. To create a new scenario for a logging session, use [New-CsClsProvider](https://docs.microsoft.com/powershell/module/skype/new-csclsprovider?view=skype-ps) and define the name of the scenario (that is, how it will be uniquely identified). Choose a type of logging format from WPP (that is, Windows software tracing preprocessor and is the default), EventLog (that is, Windows event log format), or IISLog (that is, ASCII format file based on the IIS log file format). Next, define Level (as the defined under Logging Levels in this topic), and Flags (as defined under Flags in this topic).
    
    For this example scenario, we use LyssProvider as the example provider variable.
    
    To create a scenario using the options defined, type:
    
   ```
   New-CsClsScenario -Identity <scope>/<unique scenario name> -Provider <provider variable>
   ```

    For example:
    
   ```
   New-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider $LyssProvider
   ```

    The alternate format using -Name and -Parent:
    
   ```
   New-CsClsScenario -Name "LyssServiceScenario" -Parent "site:Redmond" -Provider $LyssProvider
   ```

### To create a new scenario with multiple providers with the New-CsClsScenario cmdlet

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. You are limited to two scenarios per scope. However, you are not limited to a set number of providers. In this example, assume that we have created three providers, and you want to assign all three to the scenario you are defining. The provider variable names are LyssProvider, ABServerProvider, and SIPStackProvider. To define and assign multiple providers to a scenario, type the following at a Skype for Business Server Management Shell or Windows PowerShell command prompt:
    
   ```
   New-CsClsScenario -Identity "site:Redmond/CollectDataScenario" -Provider @{Add=$LyssProvider, $ABServerProvider,  $SIPStackProvider}
   ```

    > [!NOTE]
    > As it is known in Windows PowerShell, the convention for creating a hash table of values using  `@{<variable>=<value1>, <value2>, <value>…}` is known assplatting. For details about splatting in Windows PowerShell, see [https://go.microsoft.com/fwlink/p/?LinkId=267760](https://go.microsoft.com/fwlink/p/?LinkId=267760). 
  
### To modify an existing scenario with the Set-CsClsScenario cmdlet

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. You are limited to two scenarios per scope. You can change which scenarios are running at any time, even when a logging capture session is in process. If you redefine the running scenarios, the current logging session will stop using the scenario that was removed and then begin using the new scenario. However, the logging information that was captured with the removed scenario remains in the captured logs. To define a new scenario, do the following (that is, assuming the addition of an already defined provider named "S4Provider"):
    
   ```
   Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Add=<new provider to add>}
   ```

    For example:
    
   ```
   Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Add=$S4Provider}
   ```

    If you want to replace providers, define a single provider or a comma separated list of providers to replace the current set. If you only want to replace one of many providers, add the current providers with the new providers to create a new set of providers that contains both new providers and existing providers. To replace all providers with a new set, type the following:
    
   ```
   Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Replace=<providers to replace existing provider set>}
   ```

    For example, to replace the current set of $LyssProvider, $ABServerProvider, and $SIPStackProvider with $LyssServiceProvider:
    
   ```
   Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider}
   ```

    To replace just the $LyssProvider provider from the current set of $LyssProvider, $ABServerProvider, and $SIPStackProvider with $LyssServiceProvider, type the following:
    
   ```
   Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider, $ABServerProvider, $SIPStackProvider}
   ```

### To remove an existing scenario with the Remove-CsClsScenario cmdlet

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. If you want to remove a scenario that has been previously defined, type the following:
    
   ```
   Remove-CsClsScenario -Identity <name of scope and scenario>
   ```

    For example, to remove the defined scenario site:Redmond/LyssServiceScenario:
    
   ```
   Remove-CsClsScenario -Identity "site:Redmond/LyssServiceScenario"
   ```

The **Remove-CsClsScenario** cmdlet removes the specified scenario, but the traces that have been captured are still available in the logs for you to search on.
### To load and unload the Edit-CsClsScenario cmdlet using the ClsScenarioEdit.psm1 module

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
    > [!IMPORTANT]
    > The ClsScenarioEdit.psm1 module is provided as a separate Web download. The module is part of the Skype for Business Server 2015 Debugging tools. By default, the debugging tools are installed in the directory C:\Program Files\Skype for Business Server 2015\Debugging Tools. 
  
2. From the Windows PowerShell, type:
    
   ```
   Import-Module "CDBurn\OCO\amd64\Support"
   ```

    > [!TIP]
    > Successful loading of the module returns you to the Windows PowerShell command prompt. To confirm that the module is loaded and that Edit-CsClsScenario is available, type  `Get-Help Edit-CsClsScenario`. You should see the basic synopsis of the syntax for EditCsClsScenario. 
  
3. To unload the modules, type:
    
   ```
   Remove-Module ClsController
   ```

    > [!TIP]
    > Successful unloading of the module returns you to the Windows PowerShell command prompt. To confirm that the module is unloaded, type  `Get-Help Edit-CsClsScenario`. Windows PowerShell will attempt to locate the help for the cmdlet and fail. 
  
### To remove an existing provider from a scenario with the Edit-ClsController module

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. From the Windows PowerShell, type:
    
   ```
   Import-Module "CDBurn\OCO\amd64\Support"
   ```

    > [!TIP]
    > Successful loading of the module returns you to the Windows PowerShell command prompt. To confirm that the module is loaded and that Edit-CsClsScenario is available, type  `Get-Help Edit-CsClsScenario`. You should see the basic synopsis of the syntax for EditCsClsScenario. 
  
3. To remove a provider from the AlwaysOn scenario, type:
    
   ```
   Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to remove> -Remove
   ```

   For Example:
    
   ```
   Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Remove
   ```

   The parameters ScenarioName and ProviderName are positional (that is, they must be defined in the expected position in the command line) parameters. The parameter name does not have to be explicitly defined if the scenario name is in position two and the provider is in position three, relative to the name of the cmdlet as position one. Using this information, the previous command would be typed as:
    
   ```
   Edit-CsClsScenario AlwaysOn ChatServer -Remove
   ```

   The positional placing of the parameter values applies only to -Scenario and -Provider. All other parameters must be explicitly defined.
    
### To add a provider to a scenario with the Edit-ClsController module

1. Start the Skype for Business Server Management Shell: Click **Start**, click **All Programs**, click **Skype for Business 2015**, and then click **Skype for Business Server Management Shell**.
    
2. To add a provider to the AlwaysOn scenario, type:
    
   ```
   Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to add> -Level <string of type level> -Flags <string of type flags>
   ```

    For Example:
    
   ```
   Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Level Info -Flags TF_COMPONENT
   ```

    -Loglevel can be of the type Fatal, Error, Warning, Info, Verbose, Debug, or All. -Flags can be any of the flags that the provider supports, such as TF_COMPONENT, TF_DIAG. -Flags can also be of value ALL
    
   The previous example can also be typed using the positional feature of the cmdlet. For example, to add the provider ChatServer to the AlwaysOn scenario, type:
    
   ```
   Edit-CsClsScenario AlwaysOn ChatServer -Level Info -Flags ALL
   ```
