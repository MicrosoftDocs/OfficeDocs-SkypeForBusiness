---
title: "Get-CcSiteLogDirectory"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 3/20/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 6625494d-1b63-4d99-a589-c8c69c4addba
description: "The Get-CcSiteLogDirectory cmdlet shows the current directory where the site level logs for Skype for Business Cloud Connector Edition are stored."
---

# Get-CcSiteLogDirectory
 
The Get-CcSiteLogDirectory cmdlet shows the current directory where the site level logs for Skype for Business Cloud Connector Edition are stored. 
  
This cmdlet applies to Skype for Business Cloud Connector Edition 1.4.1, 1.4.2.
  
```
Get-CcSiteLogDirectory
```

## Parameters

None
  
## Examples
<a name="Examples"> </a>

### Example 1

The following example shows the current folder where the log files for the Cloud Connector site are stored:
  
```
Get-CcSiteLogDirectory
```

## Detailed Description
<a name="DetailedDescription"> </a>

The default folder is C:\Users\%userprofile%\CloudConnector\SiteRoot\Logs. You can change the folder by running the Set-CcSiteDirectory cmdlet. There is no separate cmdlet that changes only the log folder location without changing the site directory.
  
## Input Types
<a name="InputTypes"> </a>

None. The Get-CcSiteLogDirectory cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

The command returns a file path.
  
## See also
<a name="ReturnTypes"> </a>

[Set-CcSiteDirectory](set-ccsitedirectory.md)
  

