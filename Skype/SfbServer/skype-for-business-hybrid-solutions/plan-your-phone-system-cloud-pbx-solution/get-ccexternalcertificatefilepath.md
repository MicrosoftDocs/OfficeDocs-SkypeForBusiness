---
title: "Get-CcExternalCertificateFilePath"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/20/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 62fdc9cc-e82e-463f-b8b3-05d5c6482ea2
description: "The Get-CcExternalCertificateFilePath cmdlet returns the external certificate file path for the Skype for Business Cloud Connector Edition deployment. The user prepares this certificate."
---

# Get-CcExternalCertificateFilePath
 
The Get-CcExternalCertificateFilePath cmdlet returns the external certificate file path for the Skype for Business Cloud Connector Edition deployment. The user prepares this certificate.
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2.
  
```
Get-CcExternalCertificateFilePath [[-Target] <string> {EdgeServer | MediationServer}]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example shows the path of the certificate for the Edge Server:
  
```
Get-CcExternalCertificateFilePath -Target EdgeServer
```

### Example 2

The following example shows the certificate set for the Mediation Server:
  
```
Get-CcExternalCertificateFilePath -Target MediationServer
```

## Detailed Description
<a name="DetailedDescription"> </a>

During deployment or when modifying the topology, you need to specify the path for the Edge Server certificate, and, optionally, for the Mediation Server. The certificate for the Mediation Server is required if TLS will be used between the gateway (s) and the Mediation Server. To change the path, use the Set-CcExternalCertificateFilePath cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|Target  <br/> |Optional  <br/> | System.Management.Automation.SwitchParameter <br/> |Type of file path requested. Types include:  <br/> EdgeServer (default)  <br/> MediationServer  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

The Get-CcExternalCertificateFilePath cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The command returns a file path.
  
## See also
<a name="ReturnTypes"> </a>

[Set-CcExternalCertificateFilePath](set-ccexternalcertificatefilepath.md)
  

