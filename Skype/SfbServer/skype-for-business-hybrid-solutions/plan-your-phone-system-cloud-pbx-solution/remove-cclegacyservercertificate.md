---
title: "Remove-CcLegacyServerCertificate"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 6/22/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: ff21cecb-5035-48fd-9705-11ea81ce7df6
description: "The Remove-CcLegacyServerCertificate cmdlet removes legacy server certificates on the Central Management Store, Mediation Server, and Edge Server after you execute the Renew-CcCACertificate or Renew CcServerCertificate cmdlets."
---

# Remove-CcLegacyServerCertificate
 
The Remove-CcLegacyServerCertificate cmdlet removes legacy server certificates on the Central Management Store, Mediation Server, and Edge Server after you execute the Renew-CcCACertificate or Renew CcServerCertificate cmdlets.
  
```
Remove-CcLegacyServerCertificate [[-Roles] <array> {Cms | MS | Edge}] 
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example removes legacy certificates issued for the Central Management Store, Mediation Server, and Edge Server after you have renewed the certificates:
  
```
Remove-CcLegacyServerCertificate
```

### Example 2

The next example removes certificates issued for Mediation Server and Edge Server after you have renewed the certificates: 
  
```
Remove-CcLegacyServerCertificate -Roles @("MS", "Edge") 
```

## Parameters
<a name="Examples"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| Roles <br/> |Optional  <br/> |System.Array  <br/> | Array of Cloud Connector server roles. <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Remove-CcLegacyServerCertificate cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Renew-CcServerCertificate](renew-ccservercertificate.md)
  
[Reset-CcCACertificate](reset-cccacertificate.md)
  
[Renew-CcCACertificate](renew-cccacertificate.md)
  
[Update-CcCACertificate](update-cccacertificate.md)
  

