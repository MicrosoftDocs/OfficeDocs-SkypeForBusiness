---
title: "Uninstall-CcAppliance"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 2/23/2018
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e1b3cdd7-08e9-41a6-843a-3b4baf886cd0
description: "The Uninstall-CcAppliance cmdlet uninstalls the running Skype for Business Cloud Connector Edition appliance from the host server."
---

# Uninstall-CcAppliance
 
The Uninstall-CcAppliance cmdlet uninstalls the running Skype for Business Cloud Connector Edition appliance from the host server. 
  
```
Uninstall-CcAppliance [-Version <string>] [-Force] [-Confirm <bool>] [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example drains and uninstalls the Cloud Connector appliance from the host server:
  
```
Uninstall-CcAppliance
```

### Example 2

The next example drains and forcibly uninstalls the running Cloud Connector appliance on the host server even if the drain process failed:
  
```
Uninstall-CcAppliance -Force
```

### Example 3

The next example uninstalls a Cloud Connector backup version without the user's confirmation:
  
```
Uninstall-CcAppliance -Version 1.3.8 -Confirm:$false
```

## Detailed Description
<a name="DetailedDescription"> </a>

If you are uninstalling the current running version of Cloud Connector, drain services are first run on the Mediation Server and Edge Server to let concurrent calls finish before uninstalling the virtual machines. If you are uninstalling a backup version, draining is not performed.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| Version <br/> | Optional <br/> |System.String  <br/> | The version of Cloud Connector that will be uninstalled from the host server. If not specified, uninstall the current running version. <br/> |
|Force  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |If uninstalling the current running version, attempt to drain servers on Mediation Server and Edge Server before uninstalling the virtual machines. If you specify the "Force" switch, even if the drain services fail, the virtual machines will be uninstalled. This parameter is only used to uninstall the current running version.  <br/> |
|Confirm  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Ask user's confirmation to uninstall the virtual machines. Default value is TRUE.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Uninstall-CcAppliance cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Install-CcAppliance](install-ccappliance.md)
  
[Publish-CcAppliance](publish-ccappliance.md)
  
[Register-CcAppliance](register-ccappliance.md)
  
[Unregister-CcAppliance](unregister-ccappliance.md)
  

