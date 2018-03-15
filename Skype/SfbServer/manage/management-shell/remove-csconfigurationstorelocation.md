---
title: "Remove-CsConfigurationStoreLocation"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 141be225-c6e4-4377-913b-ba61528929d4
description: "Removes the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010."
---

# Remove-CsConfigurationStoreLocation
 
Removes the Active Directory service control point for the Central Management store. This cmdlet was introduced in Lync Server 2010.
  
```
Remove-CsConfigurationStoreLocation [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 removes the Active Directory service control point for the Central Management store. To restore this SCP (or to create a new SCP), you must run the **Set-CsConfigurationStoreLocation** cmdlet.
  
```
Remove-CsConfigurationStoreLocation
```

### EXAMPLE 2

Example 2 also removes the Active Directory service control point for the Central Management store. In addition to deleting the SCP, this command records information about the success (or failure) of the operation to the log file C:\Logs\Store_Location.html. To create this log file, the command uses the Report parameter followed by the path to the log file where information should be recorded. If this file already exists, the contents will be overwritten when the command runs. If the file does not exist, it will be created when the command runs.
  
```
Remove-CsConfigurationStoreLocation -Report C:\Logs\Store_Location.html
```

## Detailed Description

Active Directory Domain Services uses service control points (SCP) to help computers locate services. For example, when you install Skype for Business Server 2015, an SCP is created that provides location information for the Central Management store used to maintain Skype for Business Server 2015 data. Computers that need access to the database connect to Active Directory and use the information contained in the SCP to help them locate the correct computer and the correct instance of SQL Server.
  
As noted, when you install Skype for Business Server 2015, an SCP for the Central Management store is automatically created for you. Typically, you do not want to delete that SCP; if you do, computers will not be able to locate the database. However, there might be times (perhaps when troubleshooting a problem) when you will need to delete the SCP. To do that, use the **Remove-CsConfigurationStoreLocation** cmdlet. After the SCP has been deleted, you can recreate it (or create a new service control point) by using the **Set-CsConfigurationStoreLocation** cmdlet.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a domain controller where global settings are stored. If global settings are stored in the Active Directory System container, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  `-Report "C:\Logs\ConfigurationStore.html"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **Remove-CsConfigurationStoreLocation** cmdlet does not accept pipelined input.
  
## Return Types

The **Remove-CsConfigurationStoreLocation** cmdlet does not return any objects or values.
  
## See also

#### 

[Get-CsConfigurationStoreLocation](get-csconfigurationstorelocation.md)
  
[Set-CsConfigurationStoreLocation](set-csconfigurationstorelocation.md)

