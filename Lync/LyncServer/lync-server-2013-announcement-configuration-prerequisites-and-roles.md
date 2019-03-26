---
title: 'Lync Server 2013: Announcement configuration prerequisites and roles'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Announcement configuration prerequisites and roles
ms:assetid: 82f2dfe9-4c5e-4d65-96a1-96495d506ea4
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg398658(v=OCS.15)
ms:contentKeyID: 48184674
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Announcement configuration prerequisites and roles in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-02-25_

Announcement is an Enterprise Voice call management feature. This topic describes what you need to have in place before you can configure Announcement and the role assignments that you need to perform configuration tasks.

This section assumes that you have read the planning documentation related to Announcement (see [Planning for call management features in Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)).

<div>

## Announcement Configuration Prerequisites

The Announcement application requires the following components:

  - Application service

  - Response Group application

  - File Store, to hold audio files

All of these components are installed by default when you deploy Enterprise Voice.

</div>

<div>

## Announcement Configuration Roles

You can use the following administrative tools to configure announcements:

  - Lync Server Control Panel

  - Lync Server Management Shell

Configuring Announcement application requires one of the following administrative roles:

  - **CsVoiceAdministrator**   This administrator role can create, configure, and manage all voice-related settings and policies, including Announcement settings.

  - **CsServerAdministrator**   This administrator role can manage, monitor, and troubleshoot servers and services, and configure all Announcement settings.

  - **CsAdministrator**   This administrator role can perform all administrative tasks and modify all settings.

  - **CsViewOnlyAdministrator**   This administrator role can view the deployment to monitor deployment health.

<div>


> [!NOTE]  
> For details about administrative user rights, see <A href="lync-server-2013-planning-for-role-based-access-control.md">Planning for role-based access control in Lync Server 2013</A> in the Planning documentation.



</div>

</div>

<div>

## See Also


[Deploying Enterprise Voice in Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md)  


[Planning for call management features in Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

