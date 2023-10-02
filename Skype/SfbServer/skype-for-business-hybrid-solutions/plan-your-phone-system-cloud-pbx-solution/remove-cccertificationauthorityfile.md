---
title: "Remove-CcCertificationAuthorityFile"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/20/2017
audience: ITPro
ms.topic: conceptual
ms.service: skype-for-business-server
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.assetid: 3600af8d-04de-4b9a-88ac-2491ca06494d
description: "The Remove-CcCertificationAuthorityFile cmdlet removes the certification authority service backup file in the CA folder under the site share directory for Skype for Business Cloud Connector Edition."
---

# Remove-CcCertificationAuthorityFile
 
The Remove-CcCertificationAuthorityFile cmdlet removes the certification authority service backup file "&lt;SiteRootDirectory&gt;\CA\SfB CCE Root.p12" in the CA folder under the site share directory for Skype for Business Cloud Connector Edition. 
  
```powershell
Remove-CcCertificationAuthorityFile
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example removes the certification authority service backup file "&lt;SiteRootDirectory&gt;\CA\SfB CCE Root.p12" in the CA folder under the site share directory:
  
```powershell
Remove-CcCertificationAuthorityFile
```

## Input Types
<a name="InputTypes"> </a>

None. The Remove-CcCertificationAuthorityFile cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Backup-CcCertificationAuthority](backup-cccertificationauthority.md)
  

