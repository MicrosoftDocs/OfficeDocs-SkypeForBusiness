---
title: "The maximum number of concurrent shells for this user in Skype for Business Online has been exceeded"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: b309efe8-a214-41ea-a345-93e6a36e0cb1
description: "Each administrator is allowed a maximum of three simultaneous remote connections to Skype for Business Online. If you have three remote Windows PowerShell connections up and running, any attempt to make a fourth simultaneous connection will fail, with the following error message:"
---

# The maximum number of concurrent shells for this user in Skype for Business Online has been exceeded
[]
Each administrator is allowed a maximum of three simultaneous remote connections to Skype for Business Online. If you have three remote Windows PowerShell connections up and running, any attempt to make a fourth simultaneous connection will fail, with the following error message:
  
```
New-PSSession : [admin.vdomain.com] Connecting to remote server admin.vdomain.com failed with the following error message : The WS-Management service cannot process the request. The maximum number of concurrent shells for this user has been exceeded. Close existing shells or raise the quota for this user. For more information, see the about_Remote_Troubleshooting Help topic.
```

The only way to resolve this issue is to close one or more of the previous connections. When you are finished with a Skype for Business Online session, we recommend that you use the **Remove-PSSession** cmdlet to terminate the session. This will help you to prevent this issue. 
  
## See also

#### 

[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

