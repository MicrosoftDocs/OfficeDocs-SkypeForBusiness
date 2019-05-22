---
title: "Backup-CcCertificationAuthority"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 47ed4559-fb63-42cd-8ecd-b7d1617e91d3
description: "The Backup-CcCertificationAuthority cmdlet backs up the Skype for Business Cloud Connector Edition certification authority service to a file and saves it to the CA folder under the site share directory."
---

# Backup-CcCertificationAuthority
 
The Backup-CcCertificationAuthority cmdlet backs up the Skype for Business Cloud Connector Edition certification authority service to a file and saves it to the CA folder under the site share directory.
  
```
Backup-CcCertificationAuthority 
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example backs up the certification authority service to a file and saves it to the CA folder under the site share directory:
  
```
Backup-CcCertificationAuthority 
```

## Detailed Description
<a name="DetailedDescription"> </a>

Certification authority backup can be useful if you plan to redeploy a Cloud Connector appliance with the same certificate in case of a disaster, or if you want to move the appliance to new hardware. The command saves the copy of the Cloud Connector certification authority service from the AD Server to  "\<SiteRootDirectory\>\CA\SfB CCE Root.p12".
  
## Input Types
<a name="InputTypes"> </a>

None. The Backup-CcCertificationAuthority cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Remove-CcCertificationAuthorityFile](remove-cccertificationauthorityfile.md)
  

