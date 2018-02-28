---
title: "Set-CsBandwidthPolicyServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: b39af1ca-465d-4598-96a3-e19283ddf731
description: "Modifies an existing bandwidth policy service configuration. This cmdlet was introduced in Lync Server 2010."
---

# Set-CsBandwidthPolicyServiceConfiguration
[]
Modifies an existing bandwidth policy service configuration. This cmdlet was introduced in Lync Server 2010.
  
```
Set-CsBandwidthPolicyServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples

### EXAMPLE 1

This example modifies the bandwidth policy service configuration for the site Redmond (-Identity site:Redmond). The configuration is modified to enable logging, change the maximum lifetime of a token to three hours, and the number of days before log cleanup to five days. This is all accomplished in this one command. To enable logging, the EnableLogging parameter is set to True ($true). Next the MaxTokenLifetime parameter receives a value of 3:00:00, which represents three hours. Finally, the LogCleanUpInterval parameter receives a value of 5.00:00:00, which signifies five days.
  
```
Set-CsBandwidthPolicyServiceConfiguration -Identity site:Redmond -EnableLogging $true -MaxTokenLifetime 3:00:00 -LogCleanUpInterval 5.00:00:00
```

## Detailed Description

Call admission control (CAC) is a way of determining whether to allow real-time communications sessions, such as voice or video calls, to be established based on bandwidth constraints. Within the Skype for Business Server 2015 implementation of CAC, regions, sites, and subnets are defined within a network along with the relationships and links between those entities in order to place bandwidth constraints between them. Bandwidth Policy service is the component that performs CAC functionality in the Skype for Business Server 2015 deployment, enabling the decision as to whether sufficient bandwidth exists for a call to be established. This cmdlet modifies an existing bandwidth policy service configuration.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableLogging_ <br/> |Optional  <br/> |System.Boolean  <br/> |Set this parameter to True to generate CAC failure and link status logs related to the bandwidth policy service.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses any confirmation prompts that would otherwise be displayed before making changes.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |The unique identifier of the configuration you want to change. This identifier will consist of the scope (for the global configuration) or the scope and name (for a site-level configuration, such as site:Redmond).  <br/> |
| _Instance_ <br/> |Optional  <br/> |BandwidthPolicyServiceConfiguration  <br/> |A reference to a bandwidth policy service configuration object. This object must be of type BandwidthPolicyServiceConfiguration, which can be retrieved by calling the **Get-CsBandwidthPolicyServiceConfiguration** cmdlet. <br/> |
| _LogCleanUpInterval_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The period of time after which CAC failure and link status logs will be removed.  <br/> This value must be within the range 1 day through 60 days. The value must be entered in the format dd.hh:mm:ss, where d is days, h is hours, m is minutes, and s is seconds. For example, 20 days would be 20.00:00:00.  <br/> |
| _MaxLogFileSizeMb_ <br/> |Optional  <br/> |System.UInt32  <br/> |The maximum size the log file is allowed to reach. The value for this parameter must be a positive number and specifies the file size in megabytes. For example, to allow the log file to reach a maximum size of 10 megabytes, enter the value 10.  <br/> |
| _MaxTokenLifetime_ <br/> |Optional  <br/> |System.TimeSpan  <br/> |The maximum amount of time the token issued by the Bandwidth Policy Authentication service will exist.  <br/> This value must be in the range 1 hour through 24 hours. The value must be entered in the format dd.hh:mm:ss, where d is days, h is hours, m is minutes, and s is seconds. For example, the value for 12 hours would be 12:00:00.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types

Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration object. Accepts pipelined input of bandwidth policy service configuration objects.
  
## Return Types

This cmdlet does not return a value. It modifies an object of type Microsoft.Rtc.Management.WritableConfig.Settings.BandwidthPolicyServiceConfiguration.BandwidthPolicyServiceConfiguration.
  
## See also

#### 

[New-CsBandwidthPolicyServiceConfiguration](new-csbandwidthpolicyserviceconfiguration.md)
  
[Remove-CsBandwidthPolicyServiceConfiguration](remove-csbandwidthpolicyserviceconfiguration.md)
  
[Get-CsBandwidthPolicyServiceConfiguration](get-csbandwidthpolicyserviceconfiguration.md)

