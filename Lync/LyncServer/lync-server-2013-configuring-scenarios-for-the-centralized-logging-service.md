---
title: 'Lync Server 2013: Configuring scenarios for the Centralized Logging Service'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Configuring scenarios for the Centralized Logging Service
ms:assetid: 6c3bf826-e7fd-4002-95dc-01020641ef01
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688085(v=OCS.15)
ms:contentKeyID: 49733682
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring scenarios for the Centralized Logging Service in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-02-05_

Scenarios define the scope (that is, global, site, pool, or computer) and what providers to use in the Centralized Logging Service. By using scenarios, you enable or disable tracing on providers (for example, S4, SIPStack, IM, and Presence). By configuring a scenario, you can group all of the providers for a given logical collection that address a specific problem condition. If you find that a scenario needs to be modified to meet your troubleshooting and logging needs, the Lync Server 2013 Debug Tools provides you a Windows PowerShell module named *ClsController.psm1* that contains a function named *Edit-CsClsScenario*. The purpose of the module is to edit the properties of the named scenario. Examples of how this module works are provided in this topic. The Lync Server 2013 Debug Tools are downloaded from the following link: [http://go.microsoft.com/fwlink/?LinkId=285257](http://go.microsoft.com/fwlink/?linkid=285257)

<div>


> [!IMPORTANT]  
> For any given scope—site, global, pool or computer—you can run a maximum of two scenarios at any given time. To determine which scenarios are currently running, use Windows PowerShell and <A href="https://docs.microsoft.com/powershell/module/skype/Get-CsClsScenario">Get-CsClsScenario</A>. By using Windows PowerShell and <A href="https://docs.microsoft.com/powershell/module/skype/Set-CsClsScenario">Set-CsClsScenario</A>, you can dynamically change which scenarios are running. You can modify which scenarios are running during a logging session to adjust or refine the data you are collecting and from which providers.



</div>

To run the Centralized Logging Service functions by using the Lync Server Management Shell, you must be a member of either the CsAdministrator or the CsServerAdministrator role-based access control (RBAC) security groups, or a custom RBAC role that contains either of these two groups. To return a list of all the RBAC roles this cmdlet has been assigned to, including any custom RBAC roles you have created yourself, run the following command from the Lync Server Management Shell or the Windows PowerShell prompt:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

For example:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

The remainder of this topic focuses on how to define a scenario, modify a scenario, retrieve what scenarios are running, remove a scenario, and specify what a scenario contains to optimize your troubleshooting. There are two ways to issue Centralized Logging Service commands. You can use the CLSController.exe that is located, by default, in the directory C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\CLSAgent. Or, you can use the Lync Server Management Shell to issue Windows PowerShell commands. The important distinction is that when you use CLSController.exe at the command line there is a finite selection of scenarios available. When you use Windows PowerShell, you can define new scenarios for use in your logging sessions.

As introduced in [Overview of the Centralized Logging Service in Lync Server 2013](lync-server-2013-overview-of-the-centralized-logging-service.md), the elements of a scenario are:

  - **Providers**   If you are familiar with OCSLogger, providers are the components that you choose to tell OCSLogger what the tracing engine should collect logs from. The providers are the same components, and in many cases have the same name as the components in OCSLogger. If you are not familiar with OCSLogger, providers are server role specific components that the Centralized Logging Service can collect logs from. For details about the configuration of providers, see [Configuring providers for Centralized Logging Service in Lync Server 2013](lync-server-2013-configuring-providers-for-centralized-logging-service.md).

  - **Identity**   The parameter –Identity sets the scope and name of the scenario. For example, you could set a scope of “global” and identify the scenario with “LyssServiceScenario”. When you combine the two, you define the Identity (for example, “global/LyssServiceScenario”).
    
    Optionally, you can use the –Name and –Parent parameters. You define the Name parameter to uniquely identify the scenario. If you use Name, you must also use Parent to add the scenario to either global or site.
    
    <div>
    

    > [!IMPORTANT]  
    > If you use the Name and Parent parameters, you cannot use the <STRONG>–Identity</STRONG> parameter.

    
    </div>

<div>

## To create a new scenario with the New-CsClsScenario cmdlet

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  To create a new scenario for a logging session, use [New-CsClsProvider](https://docs.microsoft.com/powershell/module/skype/New-CsClsProvider) and define the name of the scenario (that is, how it will be uniquely identified). Choose a type of logging format from WPP (that is, Windows software tracing preprocessor and is the default), EventLog (that is, Windows event log format), or IISLog (that is, ASCII format file based on the IIS log file format). Next, define Level (as the defined under Logging Levels in this topic), and Flags (as defined under Flags in this topic).
    
    For this example scenario, we use LyssProvider as the example provider variable.
    
    To create a scenario using the options defined, type:
    
        New-CsClsScenario -Identity <scope>/<unique scenario name> -Provider <provider variable>
    
    For example:
    
        New-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider $LyssProvider
    
    The alternate format using –Name and –Parent:
    
        New-CsClsScenario -Name "LyssServiceScenario" -Parent "site:Redmond" -Provider $LyssProvider

</div>

<div>

## To create a new scenario with multiple providers with the New-CsClsScenario cmdlet

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  You are limited to two scenarios per scope. However, you are not limited to a set number of providers. In this example, assume that we have created three providers, and you want to assign all three to the scenario you are defining. The provider variable names are LyssProvider, ABServerProvider, and SIPStackProvider. To define and assign multiple providers to a scenario, type the following at a Lync Server Management Shell or Windows PowerShell command prompt:
    
        New-CsClsScenario -Identity "site:Redmond/CollectDataScenario" -Provider @{Add=$LyssProvider, $ABServerProvider,  $SIPStackProvider}
    
    <div>
    

    > [!NOTE]  
    > As it is known in Windows PowerShell, the convention for creating a hash table of values using <CODE>@{&lt;variable&gt;=&lt;value1&gt;, &lt;value2&gt;, &lt;value&gt;...}</CODE> is known as <EM>splatting</EM>. For details about splatting in Windows PowerShell, see <A href="http://go.microsoft.com/fwlink/p/?linkid=267760">http://go.microsoft.com/fwlink/p/?LinkId=267760</A>.

    
    </div>

</div>

<div>

## To modify an existing scenario with the Set-CsClsScenario cmdlet

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  You are limited to two scenarios per scope. You can change which scenarios are running at any time, even when a logging capture session is in process. If you redefine the running scenarios, the current logging session will stop using the scenario that was removed and then begin using the new scenario. However, the logging information that was captured with the removed scenario remains in the captured logs. To define a new scenario, do the following (that is, assuming the addition of an already defined provider named “S4Provider”):
    
        Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Add=<new provider to add>}
    
    For example:
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Add=$S4Provider}
    
    If you want to replace providers, define a single provider or a comma separated list of providers to replace the current set. If you only want to replace one of many providers, add the current providers with the new providers to create a new set of providers that contains both new providers and existing providers. To replace all providers with a new set, type the following:
    
        Set-CsClsScenario -Identity <name of scope and scenario defined by New-CsClsScenario> -Provider @{Replace=<providers to replace existing provider set>}
    
    For example, to replace the current set of $LyssProvider, $ABServerProvider, and $SIPStackProvider with $LyssServiceProvider:
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider}
    
    To replace just the $LyssProvider provider from the current set of $LyssProvider, $ABServerProvider, and $SIPStackProvider with $LyssServiceProvider, type the following:
    
        Set-CsClsScenario -Identity "site:Redmond/LyssServiceScenario" -Provider @{Replace=$LyssServiceProvider, $ABServerProvider, $SIPStackProvider}

</div>

<div>

## To remove an existing scenario with the Remove-CsClsScenario cmdlet

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  If you want to remove a scenario that has been previously defined, type the following:
    
        Remove-CsClsScenario -Identity <name of scope and scenario>
    
    For example, to remove the defined scenario site:Redmond/LyssServiceScenario:
    
        Remove-CsClsScenario -Identity "site:Redmond/LyssServiceScenario"

The **Remove-CsClsScenario** cmdlet removes the specified scenario, but the traces that have been captured are still available in the logs for you to search on.

</div>

<div>

## To load and unload the Edit-CsClsScenario cmdlet using the ClsController.psm1 module

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.
    
    <div>
    

    > [!IMPORTANT]  
    > The ClsController.psm1 module is provided as a separate Web download. The module is part of the Lync Server 2013 Debugging tools. By default, the debugging tools are installed in the directory C:\Program Files\Lync Server 2013\Debugging Tools.

    
    </div>

2.  From the Windows PowerShell, type:
    
        Import-Module "C:\Program Files\Lync Server 2013\Debugging Tools\ClsController.psm1"
    
    <div>
    

    > [!TIP]  
    > Successful loading of the module returns you to the Windows PowerShell command prompt. To confirm that the module is loaded and that Edit-CsClsScenario is available, type <CODE>Get-Help Edit-CsClsScenario</CODE>. You should see the basic synopsis of the syntax for EditCsClsScenario.

    
    </div>

3.  To unload the modules, type:
    
        Remove-Module ClsController
    
    <div>
    

    > [!TIP]  
    > Successful unloading of the module returns you to the Windows PowerShell command prompt. To confirm that the module is unloaded, type <CODE>Get-Help Edit-CsClsScenario</CODE>. Windows PowerShell will attempt to locate the help for the cmdlet and fail.

    
    </div>

</div>

<div>

## To remove an existing provider from a scenario with the Edit-ClsController module

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  To remove a provider from the AlwaysOn scenario, type:
    
        Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to remove> -Remove
    
    For Example:
    
        Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Remove
    
    The parameters ScenarioName and ProviderName are positional (that is, they must be defined in the expected position in the command line) parameters. The parameter name does not have to be explicitly defined if the scenario name is in position two and the provider is in position three, relative to the name of the cmdlet as position one. Using this information, the previous command would be typed as:
    
        Edit-CsClsScenario AlwaysOn ChatServer -Remove
    
    The positional placing of the parameter values applies only to –Scenario and –Provider. All other parameters must be explicitly defined.

</div>

<div>

## To add a provider to a scenario with the Edit-ClsController module

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  To add a provider to the AlwaysOn scenario, type:
    
        Edit-CsClsScenario -ScenarioName <string of the scenario to edit> -ProviderName <string of the provider to add> -Level <string of type level> -Flags <string of type flags>
    
    For Example:
    
        Edit-CsClsScenario -ScenarioName AlwaysOn -ProviderName ChatServer -Level Info -Flags TF_COMPONENT
    
    \-Loglevel can be of the type Fatal, Error, Warning, Info, Verbose, Debug, or All. –Flags can be any of the flags that the provider supports, such as TF\_COMPONENT, TF\_DIAG. –Flags can also be of value ALL
    
    The previous example can also be typed using the positional feature of the cmdlet. For example, to add the provider ChatServer to the AlwaysOn scenario, type:
    
        Edit-CsClsScenario AlwaysOn ChatServer -Level Info -Flags ALL

</div>

</div>

<span> </span>

</div>

</div>

</div>

