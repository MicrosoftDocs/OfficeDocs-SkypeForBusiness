---
title: "Get-CcSiteDirectory"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/31/2017
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: a243758e-6774-4437-ad2e-d5cea5f04eb6
description: "The Get-CcSiteDirectory cmdlet shows the current directory where site level configuration files are stored. The folder contains the base VHD and Skype for Business Cloud Connector Edition installation files. This folder should be shared with all other appliances of a Cloud Connector site."
---

# Get-CcSiteDirectory
 
The Get-CcSiteDirectory cmdlet shows the current directory where site level configuration files are stored. The folder contains the base VHD and Skype for Business Cloud Connector Edition installation files. This folder should be shared with all other appliances of a Cloud Connector site.
  
This cmdlet applies to Cloud Connector Edition 1.4.1, 1.4.2.
  
```
Get-CcSiteDirectory
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example shows the current folder where the configuration and virtual machines files of Cloud Connector components are stored:
  
```
Get-CcSiteDirectory
```

## Detailed Description
<a name="DetailedDescription"> </a>

To provide gateway affinity and high availability, Cloud Connector appliances can be combined in sites. Users are assigned to sites instead of Cloud Connector appliances. Each site has a shared folder where the base VHD and Cloud Connector installation files are stored. Appliances use this folder during the deployment. The default folder is C:\Users\%userprofile%\CloudConnector\SiteRoot. You can change the path by using the Set-CcSiteDirectory cmdlet.
  
## Input Types
<a name="InputTypes"> </a>

None. The Get-CcSiteDirectory cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

This command returns a file path.
  
## See also
<a name="ReturnTypes"> </a>

[Set-CcSiteDirectory](set-ccsitedirectory.md)
  

