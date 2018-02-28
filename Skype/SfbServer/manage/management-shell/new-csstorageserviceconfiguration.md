---
title: "New-CsStorageServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 194b507b-19d0-4950-8334-67d677d7dfe5
description: "Creates new instances of the Skype for Business Server 2015 Storage Service. The storage service provides a common infrastructure that enables Skype for Business Server 2015 components to use Exchange as a backend data store."
---

# New-CsStorageServiceConfiguration
[]
Creates new instances of the Skype for Business Server 2015 Storage Service. The storage service provides a common infrastructure that enables Skype for Business Server 2015 components to use Exchange as a backend data store.
  
 This cmdlet was introduced in Skype for Business Server 2015.
  
```
New-CsStorageServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-EnableAsyncAdaptorTaskAbort <$true | $false>] [-EnableAutoImportFlushedData <$true | $false>] [-EnableFabricReplicationSetReduction <$true | $false>] [-FabricInvalidStateTimeoutDuration <UInt64>] [-Force <SwitchParameter>] [-InMemory <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 creates a new collection of storage service configuration settings applied to the Redmond site. 
  
```
New-CsStorageServiceConfiguration -Identity "site:Redmond" 
```

## Detailed Description
<a name="Examples"> </a>

The Skype for Business Server 2015 Storage Service enables Skype for Business Server 2015 components, such as archiving, to use Exchange as a back-end data store. This helps to reduce operating costs: for example, you do not need to have separate storage solutions for Exchange archiving and for Skype for Business Server 2015 archiving. The Storage Service also enables Skype for Business Server 2015 to leverage the heavy investment that has been made in Exchange archiving and storage, and prevents administrators from having to use multiple tools to retrieve archived data.
  
Separate instances of the Skype for Business Server 2015 Storage Service can be configured at the global, site, and service scope (for the Registrar service only). By default, Skype for Business Server 2015 provides you with a single, global collection of Storage Service configuration settings. However, administrators have the option of creating custom settings by using the **New-CsStorageServiceConfiguration** cmdlet. Those custom settings can later be deleted by using the **Remove-CsStorageServiceConfiguration** cmdlet.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **New-CsStorageServiceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="Examples"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the new collection of storage service configuration settings to be created. Storage service settings can be created at the site scope or the service scope (but only for the Registrar service). To create a new collections of settings at the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To create settings at the service scope, use syntax similar to this:  <br/>  `-Identity "service:Registrar:atl-cs-001.litwareinc.com"` <br/> Note that your command will fail if the specified site or service already hosts a collection of storage service configuration settings.  <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _EnableAsyncAdaptorTaskAbort_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableAutoImportFlushedData_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _EnableFabricReplicationSetReduction_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
| _FabricInvalidStateTimeoutDuration_ <br/> |Optional  <br/> |System.UInt64  <br/> |PARAMVALUE: UInt64  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any nonfatal error message that might occur when running the command.  <br/> |
| _InMemory_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Creates an object reference without actually committing the object as a permanent change. If you assign the output of this cmdlet called with this parameter to a variable, you can make changes to the properties of the object reference and then commit those changes by calling this cmdlet's matching **Set-\<cmdlet\>**. <br/> |
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

None. The **New-CsStorageServiceConfiguration** cmdlet does not accept pipelined input.
  
## Return Types
<a name="Examples"> </a>

The **New-CsStorageServiceConfiguration** cmdlet creates new instances of the Microsoft.Rtc.Management.WritableConfig.Settings.StorageService.StorageServiceSettings object.
  
## See also
<a name="Examples"> </a>

#### 

[Get-CsStorageServiceConfiguration](get-csstorageserviceconfiguration.md)
  
[Remove-CsStorageServiceConfiguration](remove-csstorageserviceconfiguration.md)
  
[Set-CsStorageServiceConfiguration](set-csstorageserviceconfiguration.md)

