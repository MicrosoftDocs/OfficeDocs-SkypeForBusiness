---
title: "Update-CcServerCertificate"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 7/11/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: cd2889c4-0eb1-4752-9274-93a5a68a8080
description: "The Update-CcServerCertificate cmdlet renews the certificates for Skype for Business Cloud Connector Edition when they are near expiration or already expired."
---

# Update-CcServerCertificate
 
The Update-CcServerCertificate cmdlet renews the certificates for Skype for Business Cloud Connector Edition when they are near expiration or already expired. 
  
```
Update-CcServerCertificate [[-Roles] <array> {Cms | MS | Edge}]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example renews the certificates for the Central Management Store, Mediation Server, and Edge Server when the certificates are near expiration or already expired:
  
```
Update-CcServerCertificate
```

### Example 2

The next example renews the certificates for Mediation Server and Edge Server when they are near expiration or already expired:
  
```
Update-CcServerCertificate-Roles @("MS", "Edge")
```

## Detailed Description
<a name="DetailedDescription"> </a>

Cloud Connector internal certificates issued to the Central Management Store, Mediation Server, and Edge Server are valid for two years after they are issued from a Certificate Authority service. If certificates are near expiration or already expired, run the Update-CcServerCertificate cmdlet to renew the certificates. 
  
This command replaces the Renew-CcServerCertificate cmdlet in Cloud Connector 2.0 and later releases.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|Roles  <br/> |Optional  <br/> |System.Array  <br/> | Array of Cloud Connector server roles. <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Update-CcServerCertificate cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Reset-CcCACertificate](reset-cccacertificate.md)
  
[Renew-CcServerCertificate](renew-ccservercertificate.md)
  
[Export-CcRootCertificate](export-ccrootcertificate.md)
  

