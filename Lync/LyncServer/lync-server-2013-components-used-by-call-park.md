---
title: 'Lync Server 2013: Components used by Call Park'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components used by Call Park
ms:assetid: c7ffbee3-0ce1-48c0-bb56-af098b41d6d6
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398824(v=OCS.15)
ms:contentKeyID: 48185374
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components used by Call Park in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-13_

The Call Park application is automatically installed when you deploy Enterprise Voice. You enable Call Park by configuring voice policy. The following Lync Server 2013 components support the Call Park application:

  - **Application service**   Application service provides a platform for deploying, hosting, and managing unified communications applications, such as the Call Park application. Application service is automatically installed on every Front End Server in a Front End pool and on every Standard Edition server.

  - **Call Park application**   The Call Park application is one of the unified communications applications that are hosted by Application service. It is included automatically when you deploy Enterprise Voice. Call Park parks and retrieves calls and manages call park orbits.

  - **Music-on hold-file**   If music in enabled, the music file is played while a call is parked. A default music file is included when the Call Park application is installed.

  - **File Store**   The Call Park application uses File Store to hold custom audio files.

  - **Lync Server Control Panel**   You can use Lync Server Control Panel to configure the call park orbit table and to enable Call Park for users.

  - **Lync Server Management Shell**   All Call Park application configuration can be performed by using Lync Server Management Shell cmdlets.

</div>

<span> </span>

</div>

</div>

</div>

