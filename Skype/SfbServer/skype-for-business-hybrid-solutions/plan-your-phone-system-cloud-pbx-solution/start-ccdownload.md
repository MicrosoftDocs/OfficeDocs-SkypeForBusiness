---
title: "Start-CcDownload"
ms.reviewer: 
ms.author: crowe
author: CarolynRowe
manager: serdars
ms.date: 8/8/2017
audience: ITPro
ms.topic: conceptual
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: 19338a34-1bfb-4787-b057-5e34a333711d
description: "The Start-CcDownload cmdlet downloads the Skype for Business Cloud Connector Edition bits and msi file synchronously."
---

# Start-CcDownload
 
The Start-CcDownload cmdlet downloads the Skype for Business Cloud Connector Edition bits and msi file synchronously.
  
With Cloud Connector version 2.0 and later, you can also specify the DownloadBitsOnly parameter.
  
```
Start-CcDownload [[-DownloadUrlRoot] <string>] [-DownloadBitsOnly]  [<CommonParameters>]
```

## Examples
<a name="Examples"> </a>

### Example 1

The following example downloads the Cloud Connector bits and msi file synchronously from the Cloud Connector public download site:
  
```
Start-CcDownload
```

### Example 2

The next example downloads the Cloud Connector bits and msi file synchronously from a private download site:
  
```
Start-CcDownload -DownloadUrlRoot "http://downloadserver/cloudconnector/latest"
```

### Example 3

The third example downloads the Cloud Connector bits and msi file synchronously from a private download site.
  
```
Start-CcDownload -DownloadBitsOnly
```

## Detailed Description
<a name="DetailedDescription"> </a>

If there's a new version available in the download site, Start-CcDownload will download and install the msi file from the download site, and then download the Cloud Connector bits synchronously. If there is no new version of the msi file, Start-CcDownload will download the Cloud Connector bits only. If the Cloud Connector bits are already downloaded, Start-CcDownload does not execute.
  
## Parameters
<a name="DetailedDescription"> </a>

|**Parameter**|**Required**|**Type**|**Description**|
|:-----|:-----|:-----|:-----|
|DownloadUrlRoot  <br/> | Optional <br/> |System.String  <br/> | The full URL of a specific version of Cloud Connector in the private download site. Use this parameter with caution—be sure you are aware of which version of Cloud Connector you are downloading. <br/> |
|DownloadBitsOnly  <br/> |Optional  <br/> |System.Management.Automation.SwitchParameter  <br/> |Skip the step to download and install MSI from download site, download the Cloud Connector bits only.  <br/> |
   
## Input Types
<a name="InputTypes"> </a>

None. The Start-CcDownload cmdlet does not accept pipelined input.
  
## Return Types
<a name="ReturnTypes"> </a>

None
  
## See also
<a name="ReturnTypes"> </a>

None
  

