---
title: 'Lync Server 2013: Setting up support for large meetings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Setting up support for large meetings
ms:assetid: 8e22d34b-b395-408d-9d48-8f2a3abe9513
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ205074(v=OCS.15)
ms:contentKeyID: 48184763
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Setting up support for large meetings in Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2014-05-12_

Supporting large meetings of up to 1000 users requires creating an appropriate topology, meeting hardware and software prerequisites, and configuring the environment appropriately.

<div>

## Topology Requirements

A single large meeting requires at least one Front End Server and one Back End Server. However, to provide high availability, we recommend a two Front End Server pool with mirrored Back End Servers.

The user who hosts the large meetings must have their user account homed in this pool. However, we do not recommend that you host other user accounts in this pool. Instead, use it only for the large meetings. The best practice is to create a special user account in this pool to be used only to host large meetings. Since the large meeting setting is optimized for performance, using it as a normal user could have problems such as the inability to promote a P2P session to a meeting when a PSTN endpoint is involved.

Managing a pool with exactly two Front End Servers requires some special considerations. For more information, see [Topologies and components for Front End Servers, instant messaging, and presence in Lync Server 2013](lync-server-2013-topologies-and-components-for-front-end-servers-instant-messaging-and-presence.md).

Additionally, if you want to optionally provide disaster recovery backup and failover for the pool used for large meetings, you can pair it with a similarly set up dedicated pool in a different data center. For details, see [Planning for high availability and disaster recovery in Lync Server 2013](lync-server-2013-planning-for-high-availability-and-disaster-recovery.md).

![Large Meetings pool configuration](images/JJ205074.ee00e1c0-c3b2-464d-aa89-a1e877cd034d(OCS.15).jpg "Large Meetings pool configuration")

Additional notes about the topology include:

  - A file share is required for storing meeting content and, if Archiving Server is deployed and enabled, for storing the archiving files. The file share can be dedicated to the pool or can be the same file share used by another pool at the site in which the pool is deployed. For details about configuring the file share, see [Configure file storage for Lync Server 2013](lync-server-2013-configure-dfs-file-storage.md).

  - A Office Web Apps Server is required for enabling the PowerPoint presentation functionality in large meetings. The Office Web Apps Server can be dedicated to the large meeting pool or, it can be the same Office Web Apps Server used by other pools at the site in which the dedicated pool is deployed.

  - Load balancing of the Front End Servers requires hardware load balancing for the HTTP traffic (such as meeting content download). DNS load balancing is recommended for SIP traffic. For details see [Load balancing requirements for Lync Server 2013](lync-server-2013-load-balancing-requirements.md).

  - If you want to use Monitoring Server for the dedicated large-meeting pool, we recommend using the Monitoring Server and its database that are shared across all of the Front End Server pools in your Lync Server deployment.

</div>

<div>

## Hardware and Software Requirements

The hardware requirements for servers in a dedicated large-meeting pool are the same as for your other Lync Server 2013 servers. For details about hardware requirements, see "[Server hardware platforms for Lync Server 2013](lync-server-2013-server-hardware-platforms.md).

Servers in a dedicated large-meeting pool must meet all Lync Server 2013 software requirements. For details about software requirements, please see the following documentation:

  - [Server and tools operating system support in Lync Server 2013](lync-server-2013-server-and-tools-operating-system-support.md)

  - [Database software support in Lync Server 2013](lync-server-2013-database-software-support.md)

  - [Additional software requirements for Lync Server 2013](lync-server-2013-additional-software-requirements.md)

Additionally, both Lync Server 2013 and all Lync Server 2013 clients must have the latest updates.

</div>

<div>

## Configuration Requirements

We recommend creating a new conferencing policy specifically for large meetings, and then assigning the conferencing policy to the users who are homed on the dedicated large-meeting pool. Configure the conferencing policy using the following settings:

  - Set the **MaxMeetingSize** option to **1000**. (The default is **250**.)

  - Set the **AllowLargeMeetings** option to **True**.

  - Set the **EnableAppDesktopSharing** option to **None**.

  - Set the **AllowUserToScheduleMeetingsWithAppSharing** option to **False**.

  - Set the **AllowSharedNotes** option to **False**.

  - Set the **AllowAnnotations** option to **False**.

  - Set the **DisablePowerPointAnnotations** option to **True**.

  - Set the **AllowMultiview** option to **False**.

  - Set the **EnableMultiviewJoin** option to **False**.

<div>


> [!NOTE]  
> The support for 1000 user large meetings in Lync Server 2013 requires the <STRONG>AllowLargeMeetings</STRONG> setting in the conferencing policy for the meeting scheduler to be set to true. When this setting is set to true, the Lync experience will be optimized for extra large meetings when users joins such meeting. Specifically, in a large meeting, Lync will not show the initial or update of the full meeting participant list, which is a performance bottleneck for both the client and Lync Server 2013. Instead, Lync will only show information about the user and the list of presenters of the meeting. Lync will still properly shows total number of participants available in the large meetings.



</div>

Except for the **Maximum meeting size** setting, all the other conferencing policy settings specified here are required in order to disable conferencing capabilities that are not necessary in large meetings.

Additionally, you need to configure the dedicated large-meeting pool so that each Lync Server 2013 user that is homed on the pool and responsible for managing the meeting schedule has the appropriate permissions. To do this, do the following:

  - Set the **Designate as presenter** option to **None**. Typically, one or just a few users of all the participants of a large meeting are presenters, so participants should not be automatically admitted to large meetings as presenters. Instead, the presenters should be explicitly designated at meeting scheduling time, or be explicitly promoted during the large meeting.

  - Make sure that the **Assigned conference type by default** check box is not selected. This setting controls whether the Online Meeting Add-in for Lync 2013 always schedules conferences using the organizer’s assigned conference, which means that scheduled meetings have the same join URL and audio information. In small group collaboration scenarios, having such assigned conference type works well because everyone has their own individual assigned conference, and the constant join URL and audio information helps to facilitate faster meeting joining. However, in the large-meeting scenario, the large meeting support staff schedules the large meetings using a single set of user credentials, and then provides join URLs and audio information to the meeting requesters. In this case, using a different URL to join each meeting works better.

  - Ensure that the **Admit anonymous users by default** check box is not selected, unless it is required. This setting affects the default meeting access type scheduled by the Online Meeting Add-in for Lync 2013 when not using an assigned conference. The appropriate option for this setting depends on your organization’s needs. If most large meetings for your organization are internal meetings, do not select this option. If most large meetings require that external users be able to join, select this option.

</div>

</div>

<span> </span>

</div>

</div>

</div>

