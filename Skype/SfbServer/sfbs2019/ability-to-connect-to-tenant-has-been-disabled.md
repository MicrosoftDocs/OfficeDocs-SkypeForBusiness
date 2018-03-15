---
title: "Ability to connect to tenant has been disabled in Skype for Business Online"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 7365d31b-173e-4339-b0a3-98ab73a9558f
description: "To use Windows PowerShell in order to manage Skype for Business Online, the EnableRemotePowerShellAccess property of your tenant Windows PowerShell policy must be set to True. If it is not, your connection will fail, and you'll receive the following error message:"
---

# Ability to connect to tenant has been disabled in Skype for Business Online
[]
To use Windows PowerShell in order to manage Skype for Business Online, the EnableRemotePowerShellAccess property of your tenant Windows PowerShell policy must be set to True. If it is not, your connection will fail, and you'll receive the following error message:
  
```
New-PSSession : [admin.vdomain.com] Processing data from remote server admin.vdomain.com failed with the following error message: The ability to connect to this tenant by using a remote PowerShell session has been disabled. Please contact Lync Help to check Tenant Powershell Policy of this tenant. For more information, see the about_Remote_Troubleshooting Help topic.
```

If you see this error message, you'll need to contact Office 365 Support and get remote Windows PowerShell access enabled.
  
## See also

#### 

[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

