---
title: 'Lync Server 2013: Supporting large meetings'
ms.reviewer: 
ms.author: v-lanac
author: lanachin
TOCTitle: Supporting large meetings using Lync Server
ms:assetid: 509a424f-a33d-4e72-8f87-a3ec7bb1ddeb
ms:mtpsurl: https://technet.microsoft.com/en-us/library/JJ204894(v=OCS.15)
ms:contentKeyID: 48184136
ms.date: 07/23/2014
manager: serdars
mtps_version: v=OCS.15
---

<div data-xmlns="http://www.w3.org/1999/xhtml">

<div class="topic" data-xmlns="http://www.w3.org/1999/xhtml" data-msxsl="urn:schemas-microsoft-com:xslt" data-cs="http://msdn.microsoft.com/en-us/">

<div data-asp="http://msdn2.microsoft.com/asp">

# Supporting large meetings using Lync Server 2013

</div>

<div id="mainSection">

<div id="mainBody">

<span> </span>

_**Topic Last Modified:** 2012-10-03_

Large meetings do not follow the test model described in the previous section because they have the following characteristics:

  - The meeting format is a one-to-many presentation.

  - One or a few users are presenters, and everyone else participates only as attendees.

  - PowerPoint presentation sharing is the main data collaboration activity.

  - Audio is required and video may also be used.

  - A dedicated person, generally either the meeting organizer or an assistant to the organizer sets up the meeting well in advance.

  - Dedicated staff (not the presenters) runs the meeting, including connecting to an online meeting, verifying that audio, video, and slide sharing work, managing lobby and user roles, muting and unmuting participants, taking questions, and managing recordings, as appropriate.

Supporting large meetings of up to 1000 users requires addressing the issues related to both the shared hardware model and the no-reservation model.

To have sufficient CPU and memory resources for meetings of up to 1000 users, the hosting Front End Servers should not host any other instant messaging (IM) and presence or Enterprise Voice workloads. It should also not host any other meetings, regardless of the size of the other meetings. This means that hosting meetings of up to 1000 users requires setting up a separate Lync Server pool that is dedicated to hosting large meetings of up to 1000 users.

A Lync Server pool that is dedicated to hosting large meetings should host one and only one meeting of up to 1000 users at the same time, so meeting times need to be reserved in advance via an out of band scheduling process to ensure dedicated support from the Front End Servers. To support more than one large meeting at the same time, we recommend setting up multiple dedicated large-meeting pools.

We recommend that a dedicated person run and monitor the online portion of a large meeting. This person might be the organizer, delegate of the organizer or presenter, or a member of the dedicated large meeting support team, depending on the organization’s preferences.

In the following sections, we describe how to implement a dedicated pool for large meetings, including best practices for using Lync Server 2013 to support large meeting scenarios.

<div>

## In This Section

  - [Setting up support for large meetings in Lync Server 2013](lync-server-2013-setting-up-support-for-large-meetings.md)

  - [Managing large meetings in Lync Server 2013](lync-server-2013-managing-large-meetings.md)

</div>

</div>

<span> </span>

</div>

</div>

</div>

