---
title: 'Lync Server 2013: Exchange and SharePoint integration support'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Exchange and SharePoint integration support
ms:assetid: 72bf8aa5-55b1-4851-8a59-c96bf85d215a
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205005(v=OCS.15)
ms:contentKeyID: 48184504
ms.date: 01/20/2017
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Exchange and SharePoint integration support in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2017-01-18_

Lync Server 2013 and Lync 2013 can securely and seamlessly communicate with other applications and server products, including Office 2013, Exchange Server 2013, Exchange Server 2016, and SharePoint, if you integrate these products. Integrating Lync Server 2013 and Office provides users with in-context access to the instant messaging (IM), enhanced presence, telephony, and conferencing capabilities of Lync. Office users can access Lync features from within the Outlook 2013 messaging and collaboration client and other Office programs or from a SharePoint page. Users can also view a record of Lync conversations in the Outlook Conversation History folder. When integrated with Exchange 2013, Exchange 2016, or Exchange Online, Lync Server 2013 also supports the following:

  - Unified contact store, which enables users to store all contact information in Exchange or Exchange Online so that the information is available globally across Lync 2013, Exchange, Outlook, and Outlook Web App.

  - Conversation history and Web conferencing history, which is stored in Exchange user folders.

  - Archived content from Lync, such as IM and meeting content, can be stored in Exchange storage.

<div>


> [!NOTE]  
> Lync Server 2013 supports integration with previous versions of Microsoft Exchange Server and SharePoint Server, but not all functionality is supported with these previous versions, such as integration of Archiving storage with Microsoft Exchange.<BR>If you are migrating your users to Exchange 2013 or Exchange 2016, you can use both Exchange storage and Lync Server storage on an interim basis, while you complete the migration. Permanent use of both Exchange and Lync Server storage is not supported.



</div>

Integration of Lync Server 2013 with Exchange Server and SharePoint Server requires server-to-server authentication between servers running Lync Server 2013, Exchange Server, and SharePoint Server. Lync Server 2013 supports OAuth (Open Authorization) protocol for server-to-server authentication and authorization. For on-premises server-to-server authentication between two Microsoft servers, there is no need to use a third-party token server. Lync Server 2013, Exchange Server, and SharePoint Server have a built-in token server that can be used for authentication purposes with each other. For example, Lync Server 2013 can issue and sign a security token by itself, and use that token when communicating with Exchange. In this case, there is no need to use a third-party token server.

Lync Server 2013 supports the two server-to-server authentication scenarios. These include configuration of server-to-server authentication between the following:

  - An on-premise installation of Lync Server 2013 and an on-premises installation of Exchange Server 2013, Exchange Server 2016, and/or SharePoint Server.

  - A pair of Office components (for example, between Microsoft Exchange 365 and Microsoft Lync Server 365, or between Microsoft Lync Server 365 and Microsoft SharePoint 365).

<div>


> [!NOTE]  
> Server-to-server authentication between an on-premises server and an Office 365 component is not supported in this Lync Server 2013 release. Among other things, this means that you cannot set up server-to-server authentication between an on-premises installation of Lync Server 2013 and Microsoft Exchange 365.



</div>

For details about server-to-server authentication, see [Managing server-to-server authentication (OAuth) and partner applications in Lync Server 2013](lync-server-2013-managing-server-to-server-authentication-oauth-and-partner-applications.md) in the Deployment documentation or Operations documentation.

</div>

<span> </span>

</div>

</div>

</div>

