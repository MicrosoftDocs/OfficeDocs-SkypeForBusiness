---
title: 'Lync Server 2013: Call Park configuration prerequisites and user rights'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Call Park configuration prerequisites and user rights
ms:assetid: 25b8cfe0-e4e7-487c-9e78-8c040f629059
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg425730(v=OCS.15)
ms:contentKeyID: 48183648
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Call Park configuration prerequisites and user rights in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-09-10_

Call Park is a call management feature that is installed by default when you deploy Enterprise Voice. This topic describes what you need to have in place before you can configure Call Park and the user rights that you need to perform configuration tasks.

<div>


> [!IMPORTANT]  
> Customized music-on-hold files for the Call Park application are not backed up as part of the Lync Server 2013 disaster recovery process, and the files will be lost if the files uploaded to the pool are damaged, corrupted, or erased. Always keep a separate backup copy of the customized music-on-hold files that you have uploaded for Call Park.



</div>

This section assumes that you have read the planning documentation related to Call Park (see [Planning for call management features in Lync Server 2013](lync-server-2013-planning-for-call-management-features.md)).

<div>

## Call Park Configuration Prerequisites

Call Park requires the following components:

  - Application service

  - Call Park application

These components are installed automatically when you deploy Enterprise Voice.

If you want callers to hear music while the call is parked, a music-on-hold file is also required. A default music-on-hold file is installed automatically when you deploy Enterprise Voice. You can substitute the default file with your own music-on-hold file. Call Park uses File Store to hold the audio file.

</div>

<div>

## Call Park Configuration User Rights

You can use the following administrative tools to configure Call Park:

  - Lync Server Control Panel

  - Lync Server Management Shell

You use these tools to set up the Call Park orbit table and to configure other settings used by Call Park.

Configuring Call Park requires any of the following administrative roles, depending on the task:

  - **CsVoiceAdministrator:** This administrator role can create, configure, and manage all voice-related settings and policies.

  - **CsUserAdministrator:** This administrator role can enable Call Park in voice policy. This administrator role also has read-only view access to all voice configurations.

  - **CsServerAdministrator:** This administrator role can manage, monitor, and troubleshoot servers and services.

  - **CsAdministrator:** This administrator role can perform all of the tasks of CsVoiceAdministrator, CsServerAdministrator, and CsUserAdministrator.

<div>


> [!NOTE]  
> For details about administrative rights, see <A href="lync-server-2013-planning-for-role-based-access-control.md">Planning for role-based access control in Lync Server 2013</A> in the Planning documentation.



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

