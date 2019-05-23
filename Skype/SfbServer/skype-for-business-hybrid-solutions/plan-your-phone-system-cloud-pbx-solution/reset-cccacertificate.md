---
title: "Reset-CcCACertificate"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 6/22/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 5ada7e55-df9b-4b4e-b752-2468f4e28b8a
description: "The Reset-CcCACertificate cmdlet reinstalls the Certification Authority Service AD Server to create a new root CA certificate."
---

# Reset-CcCACertificate
 
The Reset-CcCACertificate cmdlet reinstalls the Certification Authority Service AD Server to create a new root CA certificate.
  
```
Reset-CcCACertificate
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example reinstalls the Certification Authority Service AD Server to create a new root CA certificate:
  
```
Reset-CcCACertificate
```

## Detailed Description
<a name="DetailedDescription"> </a>

If the root CA certificate is compromised or no longer secure, you must update the root CA certificate, and all certificates issued by the root CA. The Reset-CcCACertificate cmdlet revokes all certificates, uninstalls and reinstalls the Certificate Authority, and then cleans up all certificates related to the old Certification Authority service. 
  
For more information, see "Certificate authority certificates or internal certificates issued to CMS, Mediation Server, and Edge Server are near expiration or are compromised" in Troubleshooting your Cloud Connector deployment.
  
## Input Types
<a name="InputTypes"> </a>

None. The Reset-CcCACertificate cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None.
  
## See also
<a name="ReturnTypes"> </a>

[Renew-CcCACertificate](renew-cccacertificate.md) Version 1.4.2 only
  
[Renew-CcServerCertificate](renew-ccservercertificate.md) Version 1.4.2 only
  
[Update-CcCACertificate](update-cccacertificate.md) Version 2.0 and later
  
[Renew-CcServerCertificate](renew-ccservercertificate.md) Version 2.0 and later
  
[Export-CcRootCertificate](export-ccrootcertificate.md)
  

