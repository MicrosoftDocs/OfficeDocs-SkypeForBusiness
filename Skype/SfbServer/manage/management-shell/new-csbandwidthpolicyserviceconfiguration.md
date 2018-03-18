---
title: "New-CsBandwidthPolicyServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 0cb07eda-ffbe-48e2-b6bc-995737e5ba32
description: "Creates a new bandwidth policy service configuration. This cmdlet was introduced in Lync Server 2010."
---

# New-CsBandwidthPolicyServiceConfiguration
 
Creates a new bandwidth policy service configuration. This cmdlet was introduced in Lync Server 2010.
  
```
New-CsBandwidthPolicyServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableLogging <$true | $false>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-LogCleanUpInterval <TimeSpan>] [-MaxLogFileSizeMb <UInt32>] [-MaxTokenLifetime <TimeSpan>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

This example creates a new bandwidth policy service configuration at the site Redmond ( `-Identity site:Redmond`). No other parameters are specified, so the defaults are used for all configuration values.
  
```
New-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond
```

### EXAMPLE 2

In this example we again create a new bandwidth policy service configuration, this time for the Dublin site ( `-Identity site:Dublin`). For this site, rather than accepting the default values, we want to enable logging and set the number of days that pass before logs are cleaned up to 30 days. We do this by passing a value of True ($True) to the EnableLogging parameter, and then passing a value of 30.00:00:00 to the parameter LogCleanupInterval. The LogCleanupInterval value is a TimeSpan object, which is in the format dd.hh:mm:ss, where d is days, h is hours, m is minutes, and s is seconds.
  
```
New-CsBandwidthPolicyServiceConfiguration -Identity site:Dublin -EnableLogging $True -LogCleanupInterval 30.00:00:00
```

## Detailed Description

Call admission control (CAC) is a way of determining whether to allow real-time communications sessions, such as voice or video calls, to be established based on bandwidth constraints. Within the Skype for Business Server 2015 implementation of CAC, regions, sites, and subnets are defined within a network along with the relationships and links between those entities in order to place bandwidth constraints between them. Bandwidth Policy service is the component that performs CAC functionality in the Skype for Business Server 2015 deployment, enabling the decision as to whether sufficient bandwidth exists for a call to be established. This cmdlet configures a new bandwidth policy service at the site level.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |A unique identifier that contains the scope and name of the configuration. This configuration can be created only at the site scope, so the Identity will be in the following format: site:\<site name\>, where \<site name\> is the name of the site to which the configuration applies.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableLogging_ <br/> |Optional  <br/> |System.Boolean  <br/> |Set this parameter to True to generate CAC failure and link status logs related to the bandwidth policy service.  <br/> Default: False  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
| _LogCleanUpInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The period of time after which CAC failure and link status logs will be removed.  <br/> This value must be within the range 1 day through 60 days. The value must be entered in the format dd.hh:mm:ss, where d is days, h is hours, m is minutes, and s is seconds.  <br/> Default: 10 days (10.00:00:00)  <br/> |
| _MaxLogFileSizeMb_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum size the log file is allowed to reach. The value for this parameter must be a positive number; it specifies the file size in megabytes.  <br/> Default: 3 (MB)  <br/> |
| _MaxTokenLifetime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The maximum amount of time the token issued by the Bandwidth Policy Authentication service will exist.  <br/> This value must be in the range 1 hour through 24 hours. The value must be entered in the format dd.hh:mm:ss, where d is days, h is hours, m is minutes, and s is seconds.  <br/> Default: 8 hours (08:00:00)  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

None.
  
## Return Types

Creates an object of type Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration.
  
## See also

#### 

[Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)
  
[Set-CsBandwidthPolicyServiceConfiguration](set-csbandwidthpolicyserviceconfiguration.md)
  
[Get-CsBandwidthPolicyServiceConfiguration](get-csbandwidthpolicyserviceconfiguration.md)

