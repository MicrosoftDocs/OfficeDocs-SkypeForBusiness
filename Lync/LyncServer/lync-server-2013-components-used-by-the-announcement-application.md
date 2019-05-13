---
title: 'Lync Server 2013: Components used by the Announcement application'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Components used by the Announcement application
ms:assetid: 7b1a0281-cf31-459d-a734-5f10a129089c
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398608(v=OCS.15)
ms:contentKeyID: 48184595
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components used by the Announcement application in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-13_

In Lync Server 2013, the Announcement application is a component of the Response Group application. When you deploy Enterprise Voice, the Announcement application is automatically installed and activated along with the Response Group application. This section describes the components that support the Announcement application.

<div>

## Announcement Application Components

The following Lync Server components support the Announcement application:

  - **Application service**   Application service provides a platform for deploying, hosting, and managing unified communications applications. Application service is automatically installed on every Front End Server in a Front End pool and on every Standard Edition server.

  - **Response Group application**   The Response Group application is one of the unified communications applications that are hosted by Application service. When an unassigned phone number range is configured to route to an announcement, the Response Group application is required to route the calls made to the phone number. (Response Group application is not required if all the ranges are configured to route to Exchange Unified Messaging (UM).)

  - **Audio files**   Audio files are used for the announcements.

  - **File Store**   The Announcement application uses File Store to store its audio files.

  - **Lync Server Control Panel**   You can use Lync Server Control Panel to configure the unassigned number table.

  - **Lync Server Management Shell**   You can use Lync Server Management Shell cmdlets to configure Announcement settings and the unassigned number table.

</div>

</div>

<span> </span>

</div>

</div>

</div>

