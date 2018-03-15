---
title: "Import-Module error in Skype for Business Online caused by Windows PowerShell execution policy"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 12/9/2016
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 4bc093ca-fd30-44c9-a0a3-16f78698df2b
description: "The Windows PowerShell execution policy helps to determine which configuration files can be loaded into the Windows PowerShell console, and which scripts a user can run from that console. At a minimum, the Skype for Business Online Connector module cannot be imported unless the execution policy has been set to RemoteSigned. If it has not, then you will receive the following error message when you attempt to import the module:"
---

# Import-Module error in Skype for Business Online caused by Windows PowerShell execution policy
[]
The Windows PowerShell execution policy helps to determine which configuration files can be loaded into the Windows PowerShell console, and which scripts a user can run from that console. At a minimum, the Skype for Business Online Connector module cannot be imported unless the execution policy has been set to RemoteSigned. If it has not, then you will receive the following error message when you attempt to import the module:
  
```
Import-Module : File C:\Program Files\Common Files\Microsoft Lync Server 2013\Modules\LyncOnlineConnector\LyncOnlineConnectorStartup.psm1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at https://go.microsoft.com/fwlink/?LinkID=135170.
```

To resolve this issue, start Windows PowerShell as an administrator, and then run the following command:
  
```
Set-ExecutionPolicy RemoteSigned
```

For details about execution policy, see the Help topic at [https://go.microsoft.com/fwlink/?LinkID=135170](https://go.microsoft.com/fwlink/?LinkID=135170).
  
## See also

#### 

[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

