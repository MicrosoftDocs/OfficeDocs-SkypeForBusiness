---
title: "Components used by Call Park in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: c7ffbee3-0ce1-48c0-bb56-af098b41d6d6
description: "The Call Park application is automatically installed when you deploy Enterprise Voice. You enable Call Park by configuring voice policy. The following Lync Server 2013 components support the Call Park application:"
---

# Components used by Call Park in Lync Server 2013
[]
The Call Park application is automatically installed when you deploy Enterprise Voice. You enable Call Park by configuring voice policy. The following Lync Server 2013 components support the Call Park application:
  
- **Application service** Application service provides a platform for deploying, hosting, and managing unified communications applications, such as the Call Park application. Application service is automatically installed on every Front End Server in a Front End pool and on every Standard Edition server. 
    
- **Call Park application** The Call Park application is one of the unified communications applications that are hosted by Application service. It is included automatically when you deploy Enterprise Voice. Call Park parks and retrieves calls and manages call park orbits. 
    
- **Music-on hold-file** If music in enabled, the music file is played while a call is parked. A default music file is included when the Call Park application is installed. 
    
- **File Store** The Call Park application uses File Store to hold custom audio files. 
    
- **Lync Server Control Panel** You can use Lync Server Control Panel to configure the call park orbit table and to enable Call Park for users. 
    
- **Lync Server Management Shell** All Call Park application configuration can be performed by using Lync Server Management Shell cmdlets. 
    

