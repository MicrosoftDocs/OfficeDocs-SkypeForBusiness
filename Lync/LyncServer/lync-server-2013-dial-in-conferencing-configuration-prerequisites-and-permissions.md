---
title: 'Dial-in conferencing configuration prerequisites and permissions'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Dial-in conferencing configuration prerequisites and permissions
ms:assetid: b3b251e5-78ac-44a2-8c36-2a061c9b2314
ms:mtpsurl: https://technet.microsoft.com/en-us/library/Gg412865(v=OCS.15)
ms:contentKeyID: 48185165
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Dial-in conferencing configuration prerequisites and permissions in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-06-20_

Dial-in conferencing is an optional component of the Lync Server 2013 Conferencing workload. The components you need to install before you can configure dial-in conferencing are deployed when you use the Topology Builder to design your topology and then set up your Front End pool or Standard Edition server. This topic describes what you need to have accomplished before you can configure dial-in conferencing.

This section assumes that you have read the planning sections related to the Conferencing workload and dial-in conferencing in particular.

<div>

## Dial-in Conferencing Configuration Prerequisites

Dial-in conferencing requires the following Lync Server 2013 components:

  - Unified Communications Application Service (UCAS) (called the *Application service*)

  - Conferencing Attendant application

  - Conferencing Announcement application

  - Dial-in Conferencing Settings webpage

  - At least one Lync Server 2013 Mediation Server and at least one PSTN gateway

You deploy these components when you use the Topology Builder to define and publish your topology and then deploy a Front End pool or a Standard Edition server. If you are deploying Enterprise Voice, you should deploy it before you configure dial-in conferencing. If you are not deploying Enterprise Voice, you can deploy a Mediation Server and a public switched telephone network (PSTN) gateway when you deploy your Front End pool or Standard Edition server.

<div>


> [!NOTE]
> If you are upgrading from Office Communications Server 2007 R2 to Lync Server 2013, deploy dial-in conferencing in every pool that you plan to use to host Lync Server 2013 conferences. For details about migrating dial-in conferencing, see <A href="migration-from-office-communications-server-2007-r2-to-lync-server-2013.md">Migration from Office Communications Server 2007 R2 to Lync Server 2013</A>.



</div>

This section assumes that you have done the following:

  - Applied the latest updates to your Office Communications Server 2007 R2 environment, if you are migrating to Lync Server 2013.

  - Used Topology Builder to design and configure your topology. While specifying the Conferencing workload, you selected the dial-in conferencing option. For details about defining your topology, see [Defining and configuring the topology in Lync Server 2013](lync-server-2013-defining-and-configuring-the-topology.md) in the Deployment documentation.

  - Published your topology, and set up the Front End pool or Standard Edition server. For details about publishing the topology and installing Lync Server 2013, see [Deploying Lync Server 2013](lync-server-2013-deploying-lync-server.md) in the Deployment documentation.
    
    <div>
    

    > [!NOTE]
    > When you install your published topology, the Dial-in Conferencing Settings webpage is installed on the Front End Server or Standard Edition server as part of Web Services.

    
    </div>
    
    <div>
    

    > [!IMPORTANT]
    > If you change the path for the File Store in Topology Builder after you deploy Lync Server 2013, you need to restart the Conferencing Attendant and Conferencing Announcement applications to use the new path.

    
    </div>

  - Deployed Enterprise Voice. If you are not deploying Enterprise Voice, you either collocated a Mediation Server on the Enterprise Edition Front End Server or the Standard Edition server, or you deployed a stand-alone Mediation Server, and you deployed a PSTN gateway. For details about deploying Enterprise Voice, see [Deploying Enterprise Voice in Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md) in the Deployment documentation. For details about installing a stand-alone Mediation Server and PSTN gateway, see [Deploying Mediation Servers and defining peers in Lync Server 2013](lync-server-2013-deploying-mediation-servers-and-defining-peers.md) in the Deployment documentation.

The following flowchart shows the steps that you must perform before you can configure dial-in conferencing and the steps that you perform to configure dial-in conferencing.

**Deploying dial-in conferencing**

![Dial-in Conferencing Deployment flowchart](images/Gg412865.fde8c246-b5ed-4323-a6e7-af1983a5ec86(OCS.15).jpg "Dial-in Conferencing Deployment flowchart")

</div>

<div>

## Dial-in Conferencing Permissions

To configure dial-in conferencing, you need to use the following administrative tools:

  - Lync Server 2013 Control Panel

  - Lync Server Management Shell

You use these administrative tools to configure dial-in conferencing settings, and the dial plans, policies, and other settings that dial-in conferencing requires.

Configuring dial-in conferencing requires any of the following administrative roles, depending on the task:

  - **CsVoiceAdministrator**   This administrator role can create, configure, and manage voice-related settings and policies.

  - **CsUserAdministrator**   This administrator role can enable and disable users for Lync Server and assign existing policies, such as conferencing policies and PIN policies, to users.

  - **CsAdministrator**   This administrator role can perform all of the tasks of CsVoiceAdministrator and CsUserAdministrator.

</div>

<div>

## See Also


[Deploying Enterprise Voice in Lync Server 2013](lync-server-2013-deploying-enterprise-voice.md)  
  

</div>

</div>

<span> </span>

</div>

</div>

</div>

