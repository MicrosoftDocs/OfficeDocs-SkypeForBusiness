---
title: 'Lync Server 2013: Configuring providers for Centralized Logging Service'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring providers for Centralized Logging Service
ms:assetid: 6a197ecf-b56b-45e0-8e7c-f532ec5164ff
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ688082(v=OCS.15)
ms:contentKeyID: 49733678
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring providers for Centralized Logging Service in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-03-19_

The concepts and configuration of *providers* in Centralized Logging Service is one of the most important to grasp. The *providers* map directly to Lync Server server role components in the Lync Server tracing model. The provider defines the components of a Lync Server 2013 that will be traced, the type of messages (for example, fatal, error, or warning) to collect, and the flags (for example, TF\_Connection or TF\_Diag). Providers are the traceable components in each Lync Server server role. By using providers, you define the level and type of tracing on components (for example, S4, SIPStack, IM and Presence). The defined provider is used in a scenario to group all of the providers for a given logical collection that address a specific problem condition.

To run the Centralized Logging Service functions using the Lync Server Management Shell, you must be a member of either the CsAdministrator or the CsServerAdministrator role-based access control (RBAC) security groups, or a custom RBAC role that contains either of these two groups. To return a list of all the role-based access control (RBAC) roles this cmdlet has been assigned to (including any custom RBAC roles you have created yourself), run the following command from the Lync Server Management Shell or the Windows PowerShell prompt:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Lync Server 2013 cmdlet"}

For example:

    Get-CsAdminRole | Where-Object {$_.Cmdlets -match "Set-CsClsConfiguration"}

The remainder of this topic focuses on how to define providers, modify a provider and what a provider definition contains to optimize your troubleshooting. There are two ways to issue Centralized Logging Service commands. You can use the CLSController.exe that is located, by default, in the directory C:\\Program Files\\Common Files\\Microsoft Lync Server 2013\\CLSAgent. Or, you can use the Lync Server Management Shell to issue Windows PowerShell commands. The important distinction is that when you use CLSController.exe at the command line there is a finite selection of scenarios available in which the providers are already defined and are not changeable, but you can define the log level. By using Windows PowerShell, you can define new providers for use in your logging sessions, and have complete control over their creation, what they collect, and at what level they collect data.

<div class="">


> [!IMPORTANT]  
> As mentioned, providers are very powerful. However, scenarios are more powerful because they contain the embodiment of all information needed to set and execute tracing on the components that the providers represent. With scenarios being a collection of providers, this could be loosely compared to running a batch file containing hundreds of commands to collect a lot of information versus issuing hundreds of commands, one at a time, at the command line.<BR>Instead of requiring you to dig deeply into the details of providers, the Centralized Logging Service provides a number of scenarios that are already defined for you. The provided scenarios cover the vast majority of possible issues that you will encounter. In rare cases, you may need to create and define providers and assign them to scenarios. We strongly recommend that you become familiar with each of the scenarios provided before you investigate the need to create new providers and scenarios. While information about creating providers is found here to familiarize you with how the scenarios use the provider elements to collect trace information, details on the providers themselves are not provided at this time.



</div>

Introduced in [Overview of the Centralized Logging Service in Lync Server 2013](lync-server-2013-overview-of-the-centralized-logging-service.md), the key elements of defining a provider for use in a scenario are:

  - **Providers**   If you are familiar with OCSLogger, providers are the components that you choose to tell OCSLogger what the tracing engine should collect logs from. The providers are the same components, and in many cases have the same name as the components in OCSLogger. If you are not familiar with OCSLogger, providers are server-role specific components that the Centralized Logging Service can collect logs from. In the case of the Centralized Logging Service, the CLSAgent is the architectural part of the Centralized Logging Service that is doing the tracing of the components that you define in the providers configuration.

  - **Logging levels**   OCSLogger provided the option to choose a number of levels of detail for the data collected. This feature is an integral part of the Centralized Logging Service and scenarios, and is defined by the **Type** parameter. You can choose from the following:
    
      - **All**   Collects trace messages of type fatal, error, warning, and info to the log for the defined provider.
    
      - **Fatal**   Collects only the trace messages that indicate a failure for the defined provider.
    
      - **Error**   Collects only the trace messages that indicate an error for the defined provider, plus fatal messages.
    
      - **Warning**   Collects only the trace messages that indicate a warning for the defined provider, plus fatal and error messages.
    
      - **Info**   Collects only the trace messages that indicate an informational message for the defined provider, plus fatal, error, and warning messages.
    
      - **Verbose**   Collects all trace messages of type fatal, error, warning and info for the defined provider.

  - **Flags**   OCSLogger provided the option to choose flags for each provider that defined what type of information you could retrieve from the trace files. You can chose the following flags, based on the provider:
    
      - **TF\_Connection**   Provides connection-related log entries. These logs include information about connections established to and from a particular component. This may also include significant network-level information (that is, for components without the concept of a connection).
    
      - **TF\_Security**   Provides all events/log entries related to security. For example, for SipStack, these are security events such as domain validation failure, and client authentication/authorization failures.
    
      - **TF\_Diag**   Provides diagnostics events that you can use to diagnose or troubleshoot the component. For example, for SipStack, these are certificate failures, or DNS warnings/errors.
    
      - **TF\_Protocol**   Provides protocol messages such as SIP and Combined Community Codec Pack messages.
    
      - **TF\_Component**   Enables logging on the components specified as part of the providers.
    
      - **All**   Sets all available flags available for the provider.

<div>

## To review information about existing Centralized Logging Service scenario providers

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  To review the configuration of existing providers, type the following:
    
        Get-CsClsScenario -Identity <scope and scenario name> 
    
    For example, to review information about the global conferencing attendant, type:
    
        Get-CsClsScenario -Identity "global/CAA"
    
    The command displays a list of providers with the associated flags, settings, and components. If the information displayed is not enough or the list is too long for the default Windows PowerShell list format, you can display additional information by defining a different output method. To do this, type:
    
        Get-CsClsScenario -Identity "global/CAA" | Select-Object -ExpandProperty Provider
    
    The output of this command displays each provider displayed in a five line format with the provider name, type of logging, logging level, flags, GUID, and role, each one on a separate line.

</div>

<div>

## To define a new Centralized Logging Service scenario provider

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  A scenario provider consists of a component to trace, flags to use, and a level of detail to collect. You do this by typing:
    
        $<variableName> = New-CsClsProvider -Name <provider component> -Type <log type> -Level <log level detail type> -Flags <provider trace log flags>
    
    For example, a trace provider definition that defines what to collect and to what level of detail from the Lyss provider looks like the following:
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Info" -Flags "All"

The –Level collects fatal, error, warning, and information messages. The flags used are all of those defined for the Lyss provider, and include TF\_Connection, TF\_Diag and TF\_Protocol.

After the variable $LyssProvider is defined, you can use it with the **New-CsClsScenario** cmdlet to collect traces from the Lyss provider. To complete the creation and assignment of the provider to a new scenario, type:

    New-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider $LyssProvider

Where $LyssProvider is the variable containing the defined scenario created with **New-CsClsProvider**.

</div>

<div>

## To change an existing Centralized Logging Service scenario provider

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  To update or change the configuration of an existing provider, type:
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Debug" -Flags "TF_Connection, TF_Diag"
    
    You then update the scenario to assign the provider by typing the following:
    
        Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider $LyssProvider

The end result of the command is that the scenario site:Redmond/RedmondLyssInfo will have updated flags and level for the provider assigned to it. You can view the new scenario by using Get-CsClsScenario. For details, see [Get-CsClsScenario](https://docs.microsoft.com/powershell/module/skype/Get-CsClsScenario).

<div class="">


> [!WARNING]  
> <STRONG>New-ClsCsProvider</STRONG> does not check to determine whether the flags are valid. Make sure that the spelling of the flags (for example, TF_DIAG or TF_CONNECTION) is spelled correctly. If the flags are not spelled correctly, the provider cannot return the expected log information.



</div>

If you want to add additional providers to this scenario, type the following:

    Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider @{Add=$ABSProvider, $CASProvider, S4Provider}

Where each provider defined with the Add directive has already been defined using the **New-CsClsProvider** process.

</div>

<div>

## To remove a scenario provider

1.  Start the Lync Server Management Shell: Click **Start**, click **All Programs**, click **Microsoft Lync Server 2013**, and then click **Lync Server Management Shell**.

2.  The cmdlets provided allow you to update existing providers and create new providers. To remove a provider, you must use the Replace directive for the Provider parameter to **Set-CsClsScenario**. The only way to completely remove a provider is to replace it with a redefined provider of the same name and use the Update directive. For example, our provider LyssProvider is defined with WPP as the log type, level set to Debug, and flags set are TF\_CONNECTION and TF\_DIAG. You need to change the flags to “All”. To change the provider, type the following:
    
        $LyssProvider = New-CsClsProvider -Name "Lyss" -Type "WPP" -Level "Debug" -Flags "All"

     &nbsp;
    
        Set-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo" -Provider @{Replace=$LyssProvider}

3.  If you want to completely remove a scenario and the providers associated with it, type the following:
    
        Remove-CsClsScenario -Identity <scope and name of scenario>
    
    For example:
    
        Remove-CsClsScenario -Identity "site:Redmond/RedmondLyssInfo"
    
    <div class="">
    

    > [!WARNING]  
    > The cmdlet <STRONG>Remove-CsClsScenario</STRONG> does not prompt you for confirmation. The scenario is deleted, along with the providers that were assigned to it. You can recreate the scenario by re-running the commands used to create it initially. There is no procedure to recover removed scenarios or providers.

    
    </div>

When you remove a scenario by using the **Remove-CsClsScenario** cmdlet, you completely remove the scenario from the scope. To use the scenarios that you created and the providers that were a part of the scenario, you create new providers and assign them to a new scenario.

</div>

<div>

## See Also


[Get-CsClsScenario](https://docs.microsoft.com/powershell/module/skype/Get-CsClsScenario)  
[New-CsClsScenario](https://docs.microsoft.com/powershell/module/skype/New-CsClsScenario)  
[Remove-CsClsScenario](https://docs.microsoft.com/powershell/module/skype/Remove-CsClsScenario)  
[Set-CsClsScenario](https://docs.microsoft.com/powershell/module/skype/Set-CsClsScenario)  
[New-CsClsProvider](https://docs.microsoft.com/powershell/module/skype/New-CsClsProvider)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

