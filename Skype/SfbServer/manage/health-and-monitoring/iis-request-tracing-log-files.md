---
title: "Monitoring IIS request tracing log files in Skype for Business Server 2015"
ms.reviewer: 
ms.author: v-lanac
author: lanachin
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: skype-for-business-itpro
localization_priority: Normal
ms.assetid: b6730e92-6d74-4fa7-a83f-50b7bdadbffa
description: "Summary: Learn about the Mobility Service (Mcx) in Skype for Business Server 2015  support for legacy clients."
---

# Monitoring IIS request tracing log files in Skype for Business Server 2015
 
**Summary:** Learn about the Mobility Service (Mcx) in Skype for Business Server 2015 support for legacy clients.
  
This topic applies to deployments supporting Lync 2010 Lync Mobile clients only, and is intended for the Mobility Service (Mcx).

> [!NOTE]
> MCX (Mobility Service) support for legacy mobile clients is no longer available in Skype for Business Server 2019. All current Skype for Business mobile clients already use Unified Communications Web API (UCWA) to support instant messaging (IM), presence, and contacts. Users with legacy clients using MCX will need to upgrade to a current client.
  
When you enable Internet Information Services (IIS) request tracing for the Skype for Business Server Mobility Service (Mcx), the log files that are generated can consume up to three gigabytes of disk space per day. IIS trace logging is enabled by default. You should monitor the Front End Servers to make sure that they do not run out of disk space. 
  
By default, IIS stores the log files at %SystemDrive%\inetpub\logs\LogFiles.
  
To turn off IIS request tracing for an entire server, at the command line, type the following:
  
```
%SystemDrive%\Windows\System32\inetsrv\appcmd set config /section:httpLogging /dontLog:True
```

For details about the **httpLogging** command, see [the command reference](https://go.microsoft.com/fwlink/p/?linkId=234927).
  

