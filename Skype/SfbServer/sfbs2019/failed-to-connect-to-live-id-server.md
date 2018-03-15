---
title: "Skype for Business Online failed to connect to Live ID Server"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 6/22/2015
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: Ent_O365_Hybrid
ms.assetid: 701af721-dd6a-4f48-96f9-94e89c644201
description: "There are typically three reasons why your connection attempt might fail with the following error message:"
---

# Skype for Business Online failed to connect to Live ID Server
[]
There are typically three reasons why your connection attempt might fail with the following error message:
  
```
Get-CsWebTicket : Failed to connect live id servers. Make sure proxy is enabled or machine has network connection to live id servers.
```

Often this error means that the Microsoft Online Services Sign-in Assistant is not running. You can verify the status of this service by running the following command from the Windows PowerShell prompt:
  
```
Get-Service "msoidsvc"
```

If the service is not running, start the service by using this command:
  
```
Start-Service "msoidsvc"
```

If the service is running, you might be encountering problems with the network connection between your computer and the Microsoft Live ID Authentication Server. To check this, open Internet Explorer and navigate to [https://login.microsoftonline.com/.](https://login.microsoftonline.com/.) Try logging on to Office 365 from there. If this fails, you are probably experiencing network connection issues. 
  
Less commonly, it is possible that the Connection URI for Microsoft Live ID Authentication Server has been configured to the wrong value. If you've already determined that the Sign-In Assistant is running and that you are not experiencing network connectivity issues, this might be the issue. In this case, contact Office 365 Support.
  
## See also

#### 

[Diagnosing and resolving connection problems with Skype for Business Online](diagnosing-and-resolving-connection-problems-with-skype-for-business-online.md)

