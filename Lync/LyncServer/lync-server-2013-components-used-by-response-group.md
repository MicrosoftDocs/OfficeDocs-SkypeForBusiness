---
title: 'Lync Server 2013: Components used by Response Group'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Components used by Response Group
ms:assetid: 2b058785-47ca-43b7-b3de-6928a60dc685
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425768(v=OCS.15)
ms:contentKeyID: 48183693
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Components used by Response Group in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-11_

The Response Group application is automatically enabled when you deploy Enterprise Voice. This section describes the components that support the Response Group application.

<div>

## Response Group Components

The following Microsoft Lync Server 2013 components support the Response Group application:

  - **Application service**   Application service provides a platform for deploying, hosting, and managing unified communications applications, such as Response Group. The Application service is automatically installed on every Front End Server in a Front End pool and on every Standard Edition server.

  - **Response Group application**   The Response Group application is one of the unified communications applications that are hosted by Application service. It is included automatically when you deploy Response Group. The Response Group application routes and queues incoming calls to groups of agents.

  - **Language pack**   A language pack is required to support text-to-speech and speech recognition. These speech technologies are used when you configure messages, such as the welcome message and other prompts, and interactive voice response (IVR) questions and answers. By default, the 26 supported language packs are installed when you deploy Lync Server 2013.

  - **Audio files**   Audio files are used for messages and on-hold music.

  - **File Store**   Response Group uses File store to store audio files. Multiple Response Group pools can use the same instance of File store.

  - **Response Group Configuration Tool**   The Response Group Configuration Tool is a web-based tool that is used to create and configure response groups. The Response Group Configuration Tool is included when you install Web Services.

  - **Microsoft Lync Server 2013 Control Panel**   You can use Lync Server Control Panel to setup and configure agent groups and queues for response groups.

  - **Lync Server Management Shell**   All Response Group settings can be configured by using Lync Server Management Shell cmdlets.

  - **Microsoft Lync 2013**   Formal agents (agents who are required to sign in to the group before they can accept calls for the group) use Lync 2013 to sign in to and sign out from the group. If an agent group is configured for formal agents, the agents click a menu item in Lync 2013 to open Internet Explorer and display a webpage console for signing in and out of the group.

  - **Web Services**   Web Services is required for Response Group Configuration Tool, the agents’ sign-in and sign-out console, Lync Server Control Panel, and Response Group client web service.

  - **Response Group Client Web Service**   Response Group application provides a client web service, which can be used by third-party applications to retrieve information about agents, agent group membership, agent sign-in status, call status for groups, and the groups that support anonymous calls. Lync 2013 and Lync 2010 Attendant use Response Group Client Web service to retrieve the list of response groups that agents can use to make anonymous calls. The client web service is included when you install Web Services.

</div>

</div>

<span> </span>

</div>

</div>

</div>

