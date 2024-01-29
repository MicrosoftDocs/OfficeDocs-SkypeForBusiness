---
title: "Export-CcRootCertificate"
ms.reviewer: 
ms.author: serdars
author: CarolynRowe
manager: serdars
ms.date: 9/20/2017
audience: ITPro
ms.topic: conceptual
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 1499e33c-6a7c-46b9-b9a1-f78d7853b45d
description: "The Export-CcRootCertificate cmdlet exports the root CA certificate to a local file on the Skype for Business Cloud Connector Edition host server."
---

# Export-CcRootCertificate
 
The Export-CcRootCertificate cmdlet exports the root CA certificate to a local file on the Skype for Business Cloud Connector Edition host server. 
  
```powershell
Export-CcRootCertificate [[-Path] <string>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example sets the Path parameter as a directory path—not a file path. It generates the file c:\test\CCERootCertificates.p7b.
  
```powershell
Export-CcRootCertificate -Path "C:\test" 
```

## Detailed Description
<a name="DetailedDescription"> </a>

The Export-CcRootCertificate cmdlet allows you to save the root and intermediate certificates to a file path. This can be useful if there's a disaster recovery scenario. 
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|Path  <br/> |Required  <br/> |System.String  <br/> |File path where the certificate is stored.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Export-CcRootCertificate cmdlet doesn't accept pipelined input. 
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

None
  

