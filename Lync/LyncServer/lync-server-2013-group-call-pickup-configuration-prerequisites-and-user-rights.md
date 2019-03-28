---
title: 'Group Call Pickup configuration prerequisites and user rights'
ms.reviewer: 
ms.author: kenwith
author: kenwith
TOCTitle: Group Call Pickup configuration prerequisites and user rights
ms:assetid: 8757b1d3-751d-49c3-b1b8-b678f663f18e
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ945641(v=OCS.15)
ms:contentKeyID: 51541495
ms.date: 07/23/2014
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Group Call Pickup configuration prerequisites and user rights in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2013-01-30_

Group Call Pickup is a call management feature that is installed by default when you deploy Enterprise Voice. This topic describes what you need to have in place before you can configure Group Call Pickup and the user rights that you need to perform configuration tasks.

This section assumes that you have read the planning documentation related to Group Call Pickup (see [Planning for Group Call Pickup in Lync Server 2013](lync-server-2013-planning-for-group-call-pickup.md)).

<div>

## Group Call Pickup Configuration Prerequisites

Group Call Pickup requires the following components:

  - Application service

  - Call Park application

These components are installed automatically when you deploy Enterprise Voice.

</div>

<div>

## Group Call Pickup Configuration User Rights

You use the following administrative tools to configure Group Call Pickup:

  - Lync Server Management Shell

  - SEFAUtil resource kit tool

Use Lync Server Management Shell to create and manage call pickup groups in the Call Park orbit table. Use the SEFAUtil resource kit tool to assign a call pickup group and enable Group Call Pickup for users or to disable Group Call Pickup for users.

Configuring Group Call Pickup requires any of the following administrative roles, depending on the task:

  - **CsVoiceAdministrator:** This administrator role can create, configure, and manage all voice-related settings and policies.

  - **CsUserAdministrator:** This administrator role can enable Group Call Pickup for users. This administrator role also has read-only view access to all voice configurations.

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

