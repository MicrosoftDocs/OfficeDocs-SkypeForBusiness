---
title: 'Lync Server 2013: Configuring and assigning Archiving policies'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Configuring and assigning Archiving policies
ms:assetid: acd18ea8-c7f1-4178-871a-cd3b75bdaa8b
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205175(v=OCS.15)
ms:contentKeyID: 48185121
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Configuring and assigning Archiving policies in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-01_

In Lync Server 2013, you use policies to enable and disable archiving for internal communications and external communications for users who are homed on Lync Server 2013. This includes the following Archiving policies:

  - A global policy that is created by default when you deploy Lync Server 2013.

  - Optional site-level and user-level policies that you can create and use to specify how archiving is implemented for specific sites or users.

You initially set up Archiving policies when you deploy Archiving, but you can change, add, and delete policies after deployment. In Lync Server 2013 Control Panel, you can use the **Archiving Policy** page of the **Archiving and Monitoring** group to manage policies at the global level, site level, and user level.

<div>


> [!NOTE]  
> To control the implementation of Archiving, you must specify options in Archiving configurations, such as whether to archive IM or conferencing, the use of critical mode, and purging options. By default no options are enabled in the global Archiving configuration or any site or pool Archiving configuration. You should specify all appropriate options in the Archiving configurations before enabling Archiving for internal or external communications in the Archiving policies. For details, see <A href="lync-server-2013-managing-archiving-configuration-options-for-your-organization-sites-and-pools.md">Managing Archiving configuration options in Lync Server 2013 for your organization, sites, and pools</A> in the Operations documentation.<BR>If you integrate your Lync Server storage with Exchange 2013 storage, the Exchange user policies take precedence over the Lync Server 2013 archiving policies but only for those users who are homed on Exchange 2013 who have had their mailboxes put on In-Place Hold.



</div>

For details about how policies are implemented, including the hierarchy of policies, see [How Archiving works in Lync Server 2013](lync-server-2013-how-archiving-works.md) in the Planning documentation, Deployment documentation, or Operations documentation. For details about how to manage policies after deployment, see [Managing the Archiving of internal and external communications in Lync Server 2013](lync-server-2013-managing-the-archiving-of-internal-and-external-communications.md) in the Operations documentation.

<div>

## In This Section

  - [Configuring the global policy for Archiving in Lync Server 2013](lync-server-2013-configuring-the-global-policy-for-archiving.md)

  - [Setting up site policies for Archiving in Lync Server 2013](lync-server-2013-setting-up-site-policies-for-archiving.md)

  - [Setting up Archiving policies for users in Lync Server 2013](lync-server-2013-setting-up-archiving-policies-for-users.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

