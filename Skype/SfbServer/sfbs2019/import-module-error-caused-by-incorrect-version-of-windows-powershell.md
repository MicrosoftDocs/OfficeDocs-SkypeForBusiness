---
title: "Import-Module error in Skype for Business Online caused by incorrect version of Windows PowerShell"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 6c209f41-2b97-4dda-b0b7-e5b582d3e6b6
description: "The Skype for Business Online Connector module can be run only under Windows PowerShell 3.0. If you try to import the module under a previous version of Windows PowerShell, the import process will fail with an error message similar to this:"
---

# Import-Module error in Skype for Business Online caused by incorrect version of Windows PowerShell
[]
The Skype for Business Online Connector module can be run only under Windows PowerShell 3.0. If you try to import the module under a previous version of Windows PowerShell, the import process will fail with an error message similar to this:
  
```
Import-Module : The version of the loaded PowerShell is '2.0'. The module 'D:\Program Files\Common Files\Microsoft Lync Server 2013\Modules\LyncOnlineConnector\LyncOnlineConnector.psd1' requires a minimum PowerShell version of '3.0' to execute. Please verify the installation of the PowerShell and try again.
```

The only way to fix this problem is to install Windows PowerShell 3.0, which is available from the Microsoft Downloads Center at [http://www.microsoft.com/en-us/download/details.aspx?id=29939](http://www.microsoft.com/en-us/download/details.aspx?id=29939).
  
## See also

#### 

[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

