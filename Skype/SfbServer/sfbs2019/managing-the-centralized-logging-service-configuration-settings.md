---
title: "Managing the Centralized Logging Service configuration settings in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: f455c3aa-0061-413d-bdfb-a3e78f82723d
description: "The Centralized Logging Service is controlled and configured by settings and parameters that are created and used by the Centralized Logging Service Controller (CLSController) to send commands to the individual computer's Centralized Logging Service Agent (CLSAgent). The agent processes the commands that are sent to it and (in the case of a Start command) uses the configuration of the scenarios, providers, log size, trace duration, and flags to begin collecting trace logs according to the configuration information provided."
---

# Managing the Centralized Logging Service configuration settings in Lync Server 2013
[]
The Centralized Logging Service is controlled and configured by settings and parameters that are created and used by the Centralized Logging Service Controller (CLSController) to send commands to the individual computer's Centralized Logging Service Agent (CLSAgent). The agent processes the commands that are sent to it and (in the case of a Start command) uses the configuration of the scenarios, providers, log size, trace duration, and flags to begin collecting trace logs according to the configuration information provided.
  
> [!IMPORTANT]
>  Not all Windows PowerShell cmdlets listed for the Centralized Logging Service are intended for use with Lync Server 2013 on-premises deployments. Although they may appear to work, the following cmdlets are not designed to function with Lync Server 2013 on-premises deployments: > **CsClsRegion cmdlets:**[Get-CsClsRegion](get-csclsregion.md) , [Set-CsClsRegion](set-csclsregion.md), [New-CsClsRegion](new-csclsregion.md), and [Remove-CsClsRegion](remove-csclsregion.md). > **CsClsSearchTerm cmdlets:**[Get-CsClsSearchTerm](get-csclssearchterm.md) and [Set-CsClsSearchTerm](set-csclssearchterm.md). > **CsClsSecurityGroup cmdlets:**[Get-CsClsSecurityGroup](get-csclssecuritygroup.md) , [Set-CsClsSecurityGroup](set-csclssecuritygroup.md), [New-CsClsSecurityGroup](new-csclssecuritygroup.md), and [Remove-CsClsSecurityGroup](remove-csclssecuritygroup.md). >  The settings defined in these cmdlets will not hinder or cause any adverse behavior, but they are designed for use with Microsoft Office 365 and will not yield the expected results in on-premises deployments. This is not to say that there is no use for these cmdlets in on-premises deployments, but their use is a more advanced topic that is not covered in this documentation. 
  
## In this section

The topics in this section define the configuration options, parameters, and settings for the Centralized Logging Service. Information about how to configure the Centralized Logging Service, how to retrieve the configuration settings, creation of scenarios, management of security groups for Centralized Logging Service, searching, and more is contained in the following topics.
  
- [Managing computer, site and global Centralized Logging Service configuration in Lync Server 2013](managing-computer-site-and-global-centralized-logging-service-configuration.md)
    
- [Configuring providers for Centralized Logging Service in Lync Server 2013](configuring-providers-for-centralized-logging-service.md)
    
- [Configuring scenarios for the Centralized Logging Service in Lync Server 2013](configuring-scenarios-for-the-centralized-logging-service.md)
    
## See also

#### 

[Overview of the Centralized Logging Service in Lync Server 2013](overview-of-the-centralized-logging-service.md)
  
[Centralized Logging cmdlets in Lync Server 2013](centralized-logging-cmdlets.md)

