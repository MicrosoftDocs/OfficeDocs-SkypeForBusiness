---
title: "Components used by the Announcement application in Lync Server 2013"
ms.author: kenwith
author: kenwith
manager: laurawi
ms.date: 11/17/2014
ms.audience: ITPro
ms.topic: concetpual
ms.prod: office-online-server
localization_priority: Normal
ms.assetid: 7b1a0281-cf31-459d-a734-5f10a129089c
description: "In Lync Server 2013, the Announcement application is a component of the Response Group application. When you deploy Enterprise Voice, the Announcement application is automatically installed and activated along with the Response Group application. This section describes the components that support the Announcement application."
---

# Components used by the Announcement application in Lync Server 2013
[]
In Lync Server 2013, the Announcement application is a component of the Response Group application. When you deploy Enterprise Voice, the Announcement application is automatically installed and activated along with the Response Group application. This section describes the components that support the Announcement application. 
  
## Announcement Application Components

The following Lync Server components support the Announcement application:
  
- **Application service** Application service provides a platform for deploying, hosting, and managing unified communications applications. Application service is automatically installed on every Front End Server in a Front End pool and on every Standard Edition server. 
    
- **Response Group application** The Response Group application is one of the unified communications applications that are hosted by Application service. When an unassigned phone number range is configured to route to an announcement, the Response Group application is required to route the calls made to the phone number. (Response Group application is not required if all the ranges are configured to route to Exchange Unified Messaging (UM).) 
    
- **Audio files** Audio files are used for the announcements. 
    
- **File Store** The Announcement application uses File Store to store its audio files. 
    
- **Lync Server Control Panel** You can use Lync Server Control Panel to configure the unassigned number table. 
    
- **Lync Server Management Shell** You can use Lync Server Management Shell cmdlets to configure Announcement settings and the unassigned number table. 
    

