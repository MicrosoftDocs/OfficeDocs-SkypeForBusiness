---
title: "Remove-CsStorageServiceConfiguration"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/28/2017
ms.audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: f943f453-d4fc-4fbf-93e4-24f7d44e8ff5
description: "Removes existing instances of the Skype for Business Server 2015 Storage Service. The storage service provides a common infrastructure that enables Skype for Business Server 2015 components to use Skype for Business Server 2015 as a back-end data store."
---

# Remove-CsStorageServiceConfiguration
 
Removes existing instances of the Skype for Business Server 2015 Storage Service. The storage service provides a common infrastructure that enables Skype for Business Server 2015 components to use Skype for Business Server 2015 as a back-end data store.
  
 This cmdlet was introduced in Skype for Business Server 2015.
  
```
Remove-CsStorageServiceConfiguration -Identity <XdsIdentity> [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-WhatIf [<SwitchParameter>]]

```

## Examples
<a name="Examples"> </a>

### Example 1

The command shown in Example 1 deletes the storage service configuration settings applied to the Redmond site.
  
```
Remove-CsStorageServiceConfiguration -Identity "site:Redmond"
```

### Example 2

In Example 2, all the storage service settings applied to the site scope are deleted. To carry out this task, the command first uses the **Get-CsStorageServiceConfiguration** cmdlet and the Filter parameter to return all the settings configured at the site scope. That collection is then piped to the **Remove-CsStorageServiceConfiguration** cmdlet, which deletes each item in the collection.
  
```
Get-CsStorageServiceConfiguration -Filter "site:*" | Remove-CsStorageServiceConfiguration
```

## Detailed Description
<a name="Examples"> </a>

The Skype for Business Server 2015 Storage Service enables Skype for Business Server 2015 components (such as archiving) to use Exchange as a back-end data store. This helps to reduce operating costs: for example, you do not need to have separate storage solutions for Exchange archiving and for Skype for Business Server 2015 archiving. The Storage Service also enables Skype for Business Server 2015 to leverage the heavy investment that has been made in Exchange archiving and storage, and prevents administrators from having to use multiple tools to retrieve archived data.
  
Separate instances of the Skype for Business Server 2015 Storage Service can be configured at the global, site, and service scope (for the Registrar service only). By default, Skype for Business Server 2015 provides you with a single, global collection of Storage Service configuration settings. However, administrators have the option of creating custom settings by using the **New-CsStorageServiceConfiguration** cmdlet. Those custom settings can later be deleted by using the **Remove-CsStorageServiceConfiguration** cmdlet.
  
> [!NOTE]
> The **Remove-CsStorageServiceConfiguration** cmdlet can also be run against the global settings collection. In that case, however, the global collection will not be deleted. Instead, any properties within the global collection will be reset to their default values.
  
 **Skype for Business Server Control Panel:** The functions carried out by the **Remove-CsStorageServiceConfiguration** cmdlet are not available in the Skype for Business Server Control Panel.
  
## Parameters
<a name="Examples"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Identity_ <br/> |Required  <br/> |Microsoft.Rtc.Management.Xds.XdsIdentity  <br/> |Unique identifier for the collection of storage service configuration settings to be removed. To remove a collection applied to the site scope, use syntax similar to this:  <br/>  `-Identity "site:Redmond"` <br/> To remove a collection applied to the service scope, use syntax like this:  <br/>  `-Identity "service:Registrar:atl-cs-001.litwareinc.com"` <br/> Note that you can also run the **Remove-CsStorageServiceConfiguration** cmdlet against the global collection of settings. In that case, however, the global settings will not actually be removed. Instead, the properties within that collection will all be reset to their default values. <br/> |
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
| _BypassDualWrite_ <br/> |Optional  <br/> |System.Boolean  <br/> |PARAMVALUE: $true | $false  <br/> |
   
## Input Types
<a name="Examples"> </a>

The **Remove-CsStorageServiceConfiguration** cmdlet accepts pipelined instances of the Microsoft.Rtc.Management.WritableConfig.Settings.StorageService.StorageServiceSettings object.
  
## Return Types
<a name="Examples"> </a>

None. The **Remove-CsStorageServiceConfiguration** cmdlet does not return any objects or data.
  
## See also
<a name="Examples"> </a>

#### 

[Get-CsStorageServiceConfiguration](get-csstorageserviceconfiguration.md)
  
[New-CsStorageServiceConfiguration](new-csstorageserviceconfiguration.md)
  
[Set-CsStorageServiceConfiguration](set-csstorageserviceconfiguration.md)

