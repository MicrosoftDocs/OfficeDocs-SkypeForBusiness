---
title: "Enable-CsReplica"
ms.author: kenwith
author: kenwith
manager: johmar
ms.date: 3/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 4a745da5-5b09-4b5a-8ab6-8b8b03d7afc6
description: "Adds the local computer to the Skype for Business Server 2015 replication path. This cmdlet was introduced in Lync Server 2010."
---

# Enable-CsReplica
 
Adds the local computer to the Skype for Business Server 2015 replication path. This cmdlet was introduced in Lync Server 2010.
  
```
Enable-CsReplica [-Confirm [<SwitchParameter>]] [-Force <SwitchParameter>] [-GlobalCatalog <Fqdn>] [-GlobalSettingsDomainController <Fqdn>] [-Report <String>] [-WhatIf [<SwitchParameter>]]

```

## Examples

### EXAMPLE 1

The command shown in Example 1 adds the local computer to the Skype for Business Server 2015 replication path. 
  
```
Enable-CsReplica
```

## Detailed Description

When a service or server role is installed on a computer, that computer needs to be added to the replication path; doing so enables the computer to receive the topology and configuration files from the Central Management store. The **Enable-CsReplica** cmdlet provides a way for you to manually add a computer to the replication path. As a general rule, you will not need to manually add a computer to the replication path. Instead, this will automatically take place when you install Skype for Business Server 2015 on a computer.
  
## Parameters

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| _Confirm_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Prompts you for confirmation before executing the command.  <br/> |
| _Force_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Suppresses the display of any non-fatal error message that might occur when running the command.  <br/> |
| _GlobalCatalog_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |Fully qualified domain name (FQDN) of a global catalog server in your domain. This parameter is not required if you are running the **Enable-CsReplica** cmdlet on a computer with an account in your domain. <br/> |
| _GlobalSettingsDomainController_ <br/> |Optional  <br/> |Microsoft.Rtc.Management.Deploy.Fqdn  <br/> |FQDN of a domain controller where global settings are stored. If global settings are stored in the System container in Active Directory Domain Services, then this parameter must point to the root domain controller. If global settings are stored in the Configuration container, then any domain controller can be used and this parameter can be omitted.  <br/> |
| _Report_ <br/> |Optional  <br/> |System.String  <br/> |Enables you to specify a file path for the log file created when the cmdlet runs. For example:  <br/>  `-Report "C:\Logs\EnableReplica.html"` <br/> |
| _WhatIf_ <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Describes what would happen if you executed the command without actually executing the command.  <br/> |
   
## Input Types

None. The **Enable-CsReplica** cmdlet does not accept pipelined input.
  
## Return Types

None. The **Enable-CsReplica** cmdlet does not return any values or objects.
  
## See also

#### 

[Get-CsManagementStoreReplicationStatus](get-csmanagementstorereplicationstatus.md)

