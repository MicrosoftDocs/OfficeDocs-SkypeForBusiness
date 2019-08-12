---
title: "Renew-CcServerCertificate"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 7/18/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 7844b55e-b7e9-4599-9962-f0322728405a
description: "The Renew-CcServerCertificate cmdlet renews the certificates for Skype for Business Cloud Connector Edition when they are near expiration or already expired. This command was changed to Update-CcServerCertificate in Cloud Connector 2.0 and later releases."
---

# Renew-CcServerCertificate
 
The Renew-CcServerCertificate cmdlet renews the certificates for Skype for Business Cloud Connector Edition when they are near expiration or already expired. This command was changed to Update-CcServerCertificate in Cloud Connector 2.0 and later releases. 
  
```
Renew-CcServerCertificate [[-Roles] <array> {Cms | MS | Edge}]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example renews the certificates for the Central Management Store, Mediation Server, and Edge Server when the certificates are near expiration or already expired:
  
```
Renew-CcServerCertificate
```

### Example 2

The next example renews the certificates for Mediation Server and Edge Server when they are near expiration or already expired:
  
```
Renew-CcServerCertificate-Roles @("MS", "Edge")
```

## Detailed Description
<a name="DetailedDescription"> </a>

Cloud Connector internal certificates issued to the Central Management Store, Mediation Server, and Edge Server are valid for two years after they are issued from a Certificate Authority service. If certificates are near expiration or already expired, run the Renew-CcServerCertificate cmdlet to renew the certificates. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|Roles  <br/> |Optional  <br/> |System.Array  <br/> | Array of Cloud Connector server roles. <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Renew-CcServerCertificate cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Reset-CcCACertificate](reset-cccacertificate.md)
  
[Renew-CcServerCertificate](renew-ccservercertificate.md)
  
[Export-CcRootCertificate](export-ccrootcertificate.md)
  

