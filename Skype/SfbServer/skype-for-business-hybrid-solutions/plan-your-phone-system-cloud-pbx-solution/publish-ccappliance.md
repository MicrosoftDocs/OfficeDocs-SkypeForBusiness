---
title: "Publish-CcAppliance"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: e7d5b63e-ba7c-4757-8670-f96b2a91e646
description: "The Publish-CcAppliance cmdlet gets high availability information from the online tenant configuration and publishes it to the Skype for Business Cloud Connector Edition appliance on the host server."
---

# Publish-CcAppliance
 
The Publish-CcAppliance cmdlet gets high availability information from the online tenant configuration and publishes it to the Skype for Business Cloud Connector Edition appliance on the host server. 
  
```
Publish-CcAppliance
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example gets high availability information from the online tenant configuration and publishes it to the Cloud Connector appliance on the host server:
  
```
Publish-CcAppliance
```

## Detailed Description
<a name="DetailedDescription"> </a>

High availability information contains the Mediation Server FQDNs and IP addresses of the PSTN site. New DNS A records are added to the AD Server for Mediation Server IP addresses. New topology items are updated to the Central Management Store for the Mediation Server FQDNs and IP addresses. 
  
## Input Types
<a name="InputTypes"> </a>

None. The Publish-CcAppliance cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Install-CcAppliance](install-ccappliance.md)
  
[Uninstall-CcAppliance](uninstall-ccappliance.md)
  
[Register-CcAppliance](register-ccappliance.md)
  
[Unregister-CcAppliance](unregister-ccappliance.md)
  

