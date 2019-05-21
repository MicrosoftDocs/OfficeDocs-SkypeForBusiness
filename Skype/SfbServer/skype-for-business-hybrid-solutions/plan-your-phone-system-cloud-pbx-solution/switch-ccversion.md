---
title: "Switch-CcVersion"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 95e37b13-525b-4690-be32-839312e4ffe3
description: "The Switch-CcVersion cmdlet disconnects the running appliance and switches to a newly deployed or backup appliance."
---

# Switch-CcVersion
 
The Switch-CcVersion cmdlet disconnects the running appliance and switches to a newly deployed or backup appliance. 
  
```
Switch-CcVersion [-Force]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example drains the services of the current running appliance, and then switches to a newly deployed or backup appliance:
  
```
Switch-CcVersion
```

### Example 2

The next example drains the services of the current running appliance, and stops services forcibly if draining the services fails. The command then switches to a newly deployed or backup appliance:
  
```
Switch-CcVersion -Force
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Switch-CcVersion cmdlet drains the Cloud Connector services on the Mediation Server and Edge Server. All running calls will be completed, but the appliance will reject any new calls. After draining, the cmdlet disconnects the running appliance from the corporate and Internet networks, turns off all the virtual machines belonging to the appliance, and then connects the backup appliance to the corporate and Internet networks.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| Force <br/> | Optional <br/> |System.Management.Automation.SwitchParameter  <br/> | Stops services forcibly if draining the services fails. <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

None
  

