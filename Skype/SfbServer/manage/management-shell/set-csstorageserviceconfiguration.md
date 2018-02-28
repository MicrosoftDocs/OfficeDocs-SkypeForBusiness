---
title: "Set-CsStorageServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: a69b9b0b-6f53-4d33-a28c-5d4cb1246647
description: "Modifies existing instances of the Skype for Business Server 2015 Storage Service. The storage service provides a common infrastructure that enables Skype for Business Server 2015 components to use Exchange as a back-end data store. Note that, at this point in time, there are no property values that can be modified by using this cmdlet."
---

# Set-CsStorageServiceConfiguration
[]
Modifies existing instances of the Skype for Business Server 2015 Storage Service. The storage service provides a common infrastructure that enables Skype for Business Server 2015 components to use Exchange as a back-end data store. Note that, at this point in time, there are no property values that can be modified by using this cmdlet.
  
This cmdlet was introduced in Skype for Business Server 2015.
  
```
Set-CsStorageServiceConfiguration [-Identity <XdsIdentity>] <COMMON PARAMETERS>

```

## Examples
<a name="Examples"> </a>

At this point in time there are no property values that can be modified by using the Set-CsStorageServiceConfiguration cmdlet.
  
## Detailed Description
<a name="Examples"> </a>

The Skype for Business Server 2015 Storage Service enables Skype for Business Server 2015 components, such as archiving, to use Exchange as a back-end data store. This helps to reduce operating costs: for example, you do not need to have separate storage solutions for Exchange archiving and for Skype for Business Server 2015 archiving. The Storage Service also enables Skype for Business Server 2015 to leverage the heavy investment that has been made in Exchange archiving and storage, and prevents administrators from having to use multiple tools to retrieve archived data.
  
Separate instances of the Skype for Business Server 2015 Storage Service can be configured at the global, site, and service scope (for the Registrar service only). By default, Skype for Business Server 2015 provides you with a single, global collection of Storage Service configuration settings. Administrators have the option of creating custom settings by using the **New-CsStorageServiceConfiguration** cmdlet. At this point in time, however, these Storage service instances do not include any settings that can managed by using the Set-CsStorageServiceConfiguration cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Set-CsStorageServiceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="Examples"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableAsyncAdaptorTaskAbort_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableAutoImportFlushedData_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableFabricReplicationSetReduction_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _FabricInvalidStateTimeoutDuration_ <br/> |Optional  <br/> |System.UInt64  <br/> |PARAMVALUE: UInt64  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any nonfatal error message that might occur when running the command.  <br/> |
| _Identity_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the storage service configuration settings to be modified. Storage service configuration settings can be applied to the global, site, or service scope (for the Registrar service only).  <br/> To modify the global settings, use this syntax:  <br/>  `-Identity "global"` <br/> To modify settings configured at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To modify settings at the service level, use syntax similar to this:  <br/>  `-Identity "service:Registar:atl-cs-001.litwareinc.com"` <br/> |
| _Instance_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.WritableConfig.Settings.storageService.StorageServiceSettings object  <br/> |Allows you to pass a reference to an object to the cmdlet rather than set individual parameter values.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _AttachmentCacheTimeout_ <br/> |Optional  <br/> |System.UInt64  <br/> |PARAMVALUE: UInt64  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableAttachmentCache_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableEwsTaskTimeout_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableLightweightFinalization_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _FilteredAdapterIdList_ <br/> |Optional  <br/> |System.String  <br/> |PARAMVALUE: String  <br/> |
| _SingleSecondaryMissingTimeoutDuration_ <br/> |Optional  <br/> |System.UInt64  <br/> |PARAMVALUE: UInt64  <br/> |
| _SingleSecondaryQuorumEventLogInterval_ <br/> |Optional  <br/> |System.UInt64  <br/> |PARAMVALUE: UInt64  <br/> |
   
## Input Types
<a name="Examples"> </a>

The **Set-CsStorageServiceConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.StorageService.StorageServiceSettings object.
  
## Return Types
<a name="Examples"> </a>

None. The **Set-CsStorageServiceConfiguration** cmdlet does not return any data or objects.
  
## See also
<a name="Examples"> </a>

#### 

[Get-CsStorageServiceConfiguration](get-csstorageserviceconfiguration.md)
  
[New-CsStorageServiceConfiguration](new-csstorageserviceconfiguration.md)
  
[Remove-CsStorageServiceConfiguration](remove-csstorageserviceconfiguration.md)

