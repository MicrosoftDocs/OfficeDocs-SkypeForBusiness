---
title: "Renew-CcCACertificate"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 7/18/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 44da2f8d-0bf5-4f3e-b2e7-bb181dbbe646
description: "The Renew-CcCACertificate cmdlet renews the Skype for Business Cloud Connector Edition root CA certificate that is near expiration or already expired. This command was changed to Update-CcCACertificate in Cloud Connector 2.0 and later releases."
---

# Renew-CcCACertificate
 
The Renew-CcCACertificate cmdlet renews the Skype for Business Cloud Connector Edition root CA certificate that is near expiration or already expired. This command was changed to Update-CcCACertificate in Cloud Connector 2.0 and later releases.
  
```
Renew-CcCACertificate
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example renews the root CA certificate: 
  
```
Renew-CcCACertificate 
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Cloud Connector root CA certificate is valid for five years from the date that the Certificate Authority service is installed.
  
If the root certificate is near expiration or already expired, run the Renew-CcCACertificate cmdlet to renew the certificate. After the root certificate is renewed, the AD Server, Central Management Store, and Edge Server will be issued new certificates automatically.
  
If there are multiple appliances in the same PSTN site, run the Renew-CcCACertificate cmdlet in all appliances of the same PSTN site.
  
As the last step, run Export-CcRootCertificate to export the root certificate to a local file in the first appliance, then copy and install the exported certificate to your PSTN gateways.
  
## Input Types
<a name="InputTypes"> </a>

None. The Renew-CcCACertificate cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Reset-CcCACertificate](reset-cccacertificate.md)
  
[Renew-CcServerCertificate](renew-ccservercertificate.md)
  
[Export-CcRootCertificate](export-ccrootcertificate.md)
  

