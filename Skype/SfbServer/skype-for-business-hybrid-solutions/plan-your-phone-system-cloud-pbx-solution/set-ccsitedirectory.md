---
title: "Set-CcSiteDirectory"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 2/23/2018
ms.audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b1cd89fd-6968-4ace-a4aa-c4105231cf7b
description: "The Set-CcSiteDirectory cmdlet sets the directory where site level configuration files for Skype for Business Cloud Connector Edition will be stored. The folder will contain the base VHD and Cloud Connector configuration files."
---

# Set-CcSiteDirectory
 
The Set-CcSiteDirectory cmdlet sets the directory where site level configuration files for Skype for Business Cloud Connector Edition will be stored. The folder will contain the base VHD and Cloud Connector configuration files.
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2.
  
```
Set-CcSiteDirectory [[-Path] <string>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example sets the site root directory to \\SiteShare\CloudConnector:
  
```
Set-CcSiteDirectory -Path "\\SiteShare\CloudConnector"
```

## Detailed Description
<a name="DetailedDescription"> </a>

To provide gateway affinity and high availability, Cloud Connector appliances can be combined in sites. Users are assigned to sites instead of Cloud Connector appliances. Each site has a shared folder where the base VHD and Cloud Connector installation files are stored. Appliances use this folder during the deployment. This folder should be shared with all other appliances in a Cloud Connector site.
  
The default folder is C:\Users\%userprofile%\CloudConnector\SiteRoot. The path can be viewed by using the Get-CcSiteDirectory cmdlet.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
| Path <br/> | Required <br/> | System.String <br/> |Provides the path to the folder where Cloud Connector site files will be stored.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Set-CcSiteDirectory cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

[Get-CcSiteDirectory](get-ccsitedirectory.md)
  

