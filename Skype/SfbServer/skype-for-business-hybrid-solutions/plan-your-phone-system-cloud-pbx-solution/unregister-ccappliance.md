---
title: "Unregister-CcAppliance"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 3d516e65-fb9b-4a0b-8296-969fc9eda334
description: "The Unregister-CcAppliance cmdlet unregisters the current Skype for Business Cloud Connector Edition appliance from a PSTN site in the online tenant configuration."
---

# Unregister-CcAppliance
 
The Unregister-CcAppliance cmdlet unregisters the current Skype for Business Cloud Connector Edition appliance from a PSTN site in the online tenant configuration.
  
```
Unregister-CcAppliance [[-SiteName] <string>] [[-ApplianceName] <string>] [-Local]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example unregisters a current appliance from the online tenant configuration:
  
```
Unregister-CcAppliance
```

### Example 2

The next example checks the configuration for unregistering locally without connecting to the online tenant configuration:
  
```
Unregister-CcAppliance -Local
```

### Example 3

The next example unregisters the current appliance with the name "Appliance1" to PSTN site "Site1":
  
```
Unregister-CcAppliance -SiteName Site1 -ApplianceName Appliance1
```

## Detailed Description
<a name="DetailedDescription"> </a>

Similar to the Register-CcAppliance cmdlet, SiteName combined with the Edge Server external FQDN in the CloudConnector.ini file is considered a PSTN site identity. Likewise, ApplianceName combined with the Mediation Server FQDN in the CloudConnector.ini file is considered an appliance identity.
  
After the appliance is unregistered, restart the Cloud Connector management service and log on as the NetworkService account.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| SiteName <br/> |Optional  <br/> |System.String  <br/> |PSTN site name where the appliance is registered. Default value is SiteName value in CloudConnector.ini file.  <br/> |
|ApplianceName  <br/> |Optional  <br/> |System.String  <br/> |Name of the current appliance. Default value is the computer name of the host server.  <br/> |
|Local  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Check configuration for registration locally without connecting to an online tenant configuration.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Unregister-CcAppliance cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Register-CcAppliance](register-ccappliance.md)
  
[Install-CcAppliance](install-ccappliance.md)
  
[Uninstall-CcAppliance](uninstall-ccappliance.md)
  
[Publish-CcAppliance](publish-ccappliance.md)
  

